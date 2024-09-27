# 1. What is a Transaction in SQL?

**Theory:**
A transaction in SQL is a group of one or more operations (like `INSERT`, `UPDATE`, `DELETE`) executed as a single unit. If all operations succeed, the transaction is committed, making the changes permanent. If any operation fails, the transaction can be rolled back, undoing all the changes. This ensures data consistency and integrity. Transactions follow the ACID properties: Atomicity, Consistency, Isolation, and Durability.

**Example Scenario:**
Imagine transferring ₹1000 from Account A to Account B. This involves:

- Deducting ₹1000 from Account A.
- Adding ₹1000 to Account B.

If either operation fails, neither should complete, preventing any money loss or data inconsistency.

# 2. ACID Properties

**Theory:**
ACID properties ensure reliable transactions in a database system.

- **Atomicity:** All operations in a transaction are completed, or none are.
- **Consistency:** The database remains in a valid state before and after the transaction.
- **Isolation:** Transactions are isolated from each other; one transaction's changes are not visible to others until it’s committed.
- **Durability:** Once a transaction is committed, changes are permanent even in the case of a system failure.

**Example with Query:** Using the same Accounts table, if a transfer between accounts is interrupted (e.g., power outage), Atomicity ensures either both debit and credit happen, or none do, keeping the balances consistent.


# 3. What is a Join? Explain Different Types.

**Theory:**
A `JOIN` in SQL is used to combine rows from two or more tables based on a related column. There are several types of joins:

- **INNER JOIN:** Returns rows that have matching values in both tables.
- **LEFT JOIN (LEFT OUTER JOIN):** Returns all rows from the left table and matched rows from the right table. Unmatched rows in the right table are shown as `NULL`.
- **RIGHT JOIN (RIGHT OUTER JOIN):** Returns all rows from the right table and matched rows from the left table.
- **FULL JOIN (FULL OUTER JOIN):** Returns rows when there is a match in one of the tables.
- **CROSS JOIN:** Returns the Cartesian product of both tables, meaning all combinations.

**Example:**

### Tables:

**Employees**

| EmployeeID | Name  | DepartmentID |
|------------|-------|--------------|
| 1          | John  | 101          |
| 2          | Alice | 102          |
| 3          | Bob   | 101          |

**Departments**

| DepartmentID | DepartmentName |
|--------------|----------------|
| 101          | IT             |
| 102          | HR             |
| 103          | Finance        |

### INNER JOIN Query:

```
SELECT e.Name, d.DepartmentName
FROM Employees e
INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

| Name  | DepartmentName |
|-------|----------------|
| John  | IT             |
| Alice | HR             |
| Bob   | IT             |

**Explanation:**
Shows employees with their department names. Only includes employees with a matching `DepartmentID` in both tables.

## LEFT JOIN Query:

```
SELECT e.Name, d.DepartmentName
FROM Employees e
LEFT JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

```
SELECT e.Name, d.DepartmentName
FROM Employees e
LEFT JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

### Result:

| Name  | DepartmentName |
|-------|----------------|
| John  | IT             |
| Alice | HR             |
| Bob   | IT             |

### Explanation:

Shows all employees, and if a department doesn’t match, it shows `NULL`. Here, all departments match.

# 4. Delete, Truncate, Drop

## Theory:
These commands are used to remove data from a table, but they behave differently:

- **DELETE**: Removes rows based on a condition. It can be rolled back if inside a transaction. Slow because it logs each deletion.
- **TRUNCATE**: Removes all rows from a table without logging individual row deletions. Faster, but cannot be rolled back if not inside a transaction.
- **DROP**: Removes the entire table, including its structure. Cannot be undone.

## Example:
**Table**: Students

| StudentID | Name  | Age |
|-----------|-------|-----|
| 1         | Ravi  | 20  |
| 2         | Priya | 21  |
| 3         | Ankit | 22  |

### DELETE Query:

```
DELETE FROM Students WHERE Age > 20
```

**Result**:

| StudentID | Name | Age |
|-----------|------|-----|
| 1         | Ravi | 20  |

**Explanation**: Removes students older than 20. Ravi remains.

### TRUNCATE Query:
```
TRUNCATE TABLE Students
```

**Result**: The table is emptied, but the structure remains intact.

### DROP Query:
```
DROP TABLE Students
```

**Result**: The Students table is removed from the database completely.

# 5. Constraints in SQL

## Theory:
Constraints enforce rules at the table level to ensure valid data is entered into the database.

- **PRIMARY KEY**: Uniquely identifies each row. No duplicate or NULL values allowed.
- **FOREIGN KEY**: Establishes a relationship between two tables, ensuring referential integrity.
- **UNIQUE**: Ensures all values in a column are unique but allows a single NULL value.
- **CHECK**: Limits the values a column can hold based on a specified condition.
- **NOT NULL**: Ensures a column cannot have NULL values.

## Example:

```
CREATE TABLE Employees (
   EmployeeID INT PRIMARY KEY,                
   Name NVARCHAR(50) NOT NULL,                 
   Age INT CHECK (Age >= 18),                  
   DepartmentID INT,
   CONSTRAINT fk_Department 
   FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

### Explanation:
- **EmployeeID** uniquely identifies each employee.
- **Name** cannot be NULL.
- **Age** must be at least 18.
- **DepartmentID** must exist in the Departments table.

# 6. Unique vs Primary Key

## Theory:
- **UNIQUE Key**: Ensures all values in a column are unique but allows NULL values. A table can have multiple UNIQUE keys.
- **PRIMARY Key**: Uniquely identifies each row in a table and cannot have NULL values. Only one PRIMARY KEY is allowed per table.

## Example:
```
CREATE TABLE Products (
   ProductID INT PRIMARY KEY,             
   ProductCode NVARCHAR(50) UNIQUE,       
   ProductName NVARCHAR(100)
);
```

### Explanation:
- **ProductID** is the primary key, ensuring each product has a unique ID.
- **ProductCode** is unique, so no two products can have the same code, but it can be NULL.

# 7. Normalization Technique

## Theory:
Normalization organizes data to minimize redundancy and improve integrity.

- **1NF (First Normal Form)**: Each column should hold atomic (indivisible) values.
- **2NF (Second Normal Form)**: 1NF + all non-key attributes must depend on the whole primary key.
- **3NF (Third Normal Form)**: 2NF + no transitive dependency (non-key attributes depending on other non-key attributes).

## Example:

**Before Normalization (1NF)**: Orders

| OrderID | Product1 | Product2 | CustomerName |
|---------|----------|----------|--------------|
| 1       | Phone    | TV       | Rahul        |
| 2       | Laptop   | NULL     | Priya        |

**After 1NF**:

| OrderID | Product | CustomerName |
|---------|---------|--------------|
| 1       | Phone   | Rahul        |
| 1       | TV      | Rahul        |
| 2       | Laptop  | Priya        |

**After 2NF and 3NF (Separate Products and Customers)**: Orders

| OrderID | ProductID | CustomerID |
|---------|-----------|------------|
| 1       | 101       | 201        |
| 1       | 102       | 201        |
| 2       | 103       | 202        |

**Products**

| ProductID | ProductName |
|-----------|-------------|
| 101       | Phone       |
| 102       | TV          |
| 103       | Laptop      |

**Customers**

| CustomerID | CustomerName |
|------------|--------------|
| 201        | Rahul        |
| 202        | Priya        |

### Explanation:
- Redundancy is reduced, and each entity (Orders, Products, Customers) is in its own table.


# 8. Many-to-Many Relationship

## Theory:
A many-to-many relationship exists when multiple records in one table are associated with multiple records in another. This is implemented using a junction table.

## Example:

### Tables: 

**Students**

| StudentID | Name |
|-----------|------|
| 1         | Ravi |
| 2         | Priya|

**Courses**

| CourseID | CourseName |
|----------|------------|
| 101      | Math       |
| 102      | Science    |

### Junction Table: **StudentCourses**

| StudentID | CourseID |
|-----------|----------|
| 1         | 101      |
| 1         | 102      |
| 2         | 101      |

### Query:

> SELECT s.Name, c.CourseName  
> FROM Students s  
> JOIN StudentCourses sc ON s.StudentID = sc.StudentID  
> JOIN Courses c ON sc.CourseID = c.CourseID;

### Result:

| Name  | CourseName |
|-------|------------|
| Ravi  | Math       |
| Ravi  | Science    |
| Priya | Math       |

### Explanation:

This query displays all students and their enrolled courses, representing the many-to-many relationship.

# 9. CTE vs Temp Table

## Theory:
- **CTE (Common Table Expression)**: A temporary result set defined within the execution scope of a single `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. Useful for complex queries and recursive operations.
- **Temp Table**: A physical table created in the TempDB database. Used for storing intermediate results and can be referenced across multiple queries in the same session.

## Example:

### CTE Query:

> WITH SalesCTE AS (  
> SELECT EmployeeID, SalesAmount  
> FROM Sales  
> WHERE SalesAmount > 10000  
> )  
> SELECT * FROM SalesCTE;

### Explanation:

This CTE filters employees with sales greater than ₹10,000. It exists only for the duration of this query.

### Temp Table Query:

> CREATE TABLE #TempSales (  
> EmployeeID INT,  
> SalesAmount DECIMAL(10, 2)  
> );  
>   
> INSERT INTO #TempSales  
> SELECT EmployeeID, SalesAmount   
> FROM Sales   
> WHERE SalesAmount > 10000;  
>   
> SELECT * FROM #TempSales;

### Explanation:

This temporary table stores sales data with amounts over ₹10,000. It can be used across multiple queries in the same session.

# 10. Views in SQL

## Theory:
A view is a virtual table based on a `SELECT` query. It does not store data physically but displays data from one or more tables. Views are useful for simplifying complex queries, providing data security, and abstracting the database schema.

## Example:

### Creating a View:

> CREATE VIEW HighSalaryEmployees AS  
> SELECT Name, Department, Salary   
> FROM Employees   
> WHERE Salary > 50000;

### Using the View:

> SELECT * FROM HighSalaryEmployees;

### Explanation:

This view shows employees with a salary greater than ₹50,000. The view simplifies the query and abstracts the underlying table structure.

# 11. Triggers in SQL

## Theory:
A trigger is a special kind of stored procedure that automatically runs when specific events (like `INSERT`, `UPDATE`, `DELETE`) occur in a table. Triggers can enforce business rules, maintain audit trails, and automatically update related tables.

## Example:

### Creating a Trigger:

> CREATE TRIGGER trg_UpdateSalaryLog  
> ON Employees  
> AFTER UPDATE  
> AS  
> BEGIN  
> INSERT INTO SalaryLog (EmployeeID, OldSalary, NewSalary, ChangeDate)  
> SELECT d.EmployeeID, d.Salary, i.Salary, GETDATE()  
> FROM deleted d, inserted i  
> WHERE d.EmployeeID = i.EmployeeID AND d.Salary <> i.Salary;  
> END;

### Explanation:

Whenever an employee’s salary is updated, this trigger logs the change in the `SalaryLog` table, recording the old salary, new salary, and the date of change.
# 12. Clustered vs Non-Clustered Index

## Theory:
Indexes improve the speed of data retrieval operations on a table.

- **Clustered Index:** Physically sorts and stores the rows of data in the table based on the key columns. There can be only one clustered index per table because the data can be sorted only one way. It’s best for columns frequently used in range queries.
- **Non-Clustered Index:** Creates a separate structure that stores the key values and a pointer to the physical data. Multiple non-clustered indexes can exist on a table, improving search performance for columns frequently used in search criteria.

## Example:

**Clustered Index:**

> CREATE CLUSTERED INDEX IX_Employees_ID ON Employees(EmployeeID);

**Non-Clustered Index:**

> CREATE NONCLUSTERED INDEX IX_Employees_Name ON Employees(Name);

### Explanation:

- The `EmployeeID` index sorts and stores the table rows physically. Queries filtering by `EmployeeID` will be fast.
- The `Name` index does not sort the rows but provides a quick lookup for names.

# 13. ROW_NUMBER(), RANK(), DENSE_RANK()

## Theory:
These functions assign a rank or number to each row within a result set based on a specified order. They are used for data analysis and reporting.

- **ROW_NUMBER():** Assigns a unique sequential number to each row. No ties.
- **RANK():** Assigns the same rank to rows with the same value, but skips ranks for duplicates.
- **DENSE_RANK():** Similar to `RANK()`, but does not skip ranks.

## Example:

### Table: Employees

| EmployeeID | Name | Salary |
|------------|------|--------|
| 1          | John | 50000  |
| 2          | Alice| 60000  |
| 3          | Bob  | 50000  |

### Query:

> SELECT Name, Salary,  
> ROW_NUMBER() OVER (ORDER BY Salary DESC) AS RowNum,  
> RANK() OVER (ORDER BY Salary DESC) AS Rank,  
> DENSE_RANK() OVER (ORDER BY Salary DESC) AS DenseRank  
> FROM Employees;

### Result:

| Name  | Salary | RowNum | Rank | DenseRank |
|-------|--------|--------|------|-----------|
| Alice | 60000  | 1      | 1    | 1         |
| John  | 50000  | 2      | 2    | 2         |
| Bob   | 50000  | 3      | 2    | 2         |

### Explanation:

- **ROW_NUMBER:** Assigns unique numbers (1, 2, 3).
- **RANK:** Ties at 2 and skips 3.
- **DENSE_RANK:** Ties at 2 without skipping.

# 14. Stored Procedures vs User-Defined Functions

## Theory:
- **Stored Procedures:** Perform multiple operations and can return multiple values or no value. Used for business logic and operations that do not need to be called within a `SELECT` statement.
- **User-Defined Functions (UDF):** Return a single value or table. Used for calculations and can be called within a `SELECT` statement.

## Example:

### Stored Procedure:

> CREATE PROCEDURE GetHighSalaryEmployees  
> AS  
> BEGIN  
> SELECT * FROM Employees WHERE Salary > 50000;  
> END;

### Executing:

> EXEC GetHighSalaryEmployees;

### UDF:

> CREATE FUNCTION GetEmployeeCount()  
> RETURNS INT  
> AS  
> BEGIN  
> DECLARE @Count INT;  
> SELECT @Count = COUNT(*) FROM Employees;  
> RETURN @Count;  
> END;

### Using the Function:

> SELECT dbo.GetEmployeeCount();

### Explanation:

- **Stored procedures** can perform complex operations and return multiple result sets.
- **Functions** can be used in queries to calculate and return values directly.

# 15. What is an SQL Execution Plan?

## Theory:
An execution plan is a roadmap of how SQL Server will execute a query. It shows the order of operations, which indexes are used, and the cost of each operation. It helps in identifying performance issues like missing indexes or inefficient query structures.

## Example:

### Query to View Execution Plan:

> SET SHOWPLAN_TEXT ON;  
> GO  
> SELECT * FROM Employees WHERE Salary > 50000;  
> GO  
> SET SHOWPLAN_TEXT OFF;

### Explanation:

This shows a text-based execution plan indicating steps like Index Seek, Index Scan, or Table Scan.

# 16. Reading an Execution Plan

## Theory:
Reading an execution plan involves understanding the sequence of operations performed by the query optimizer and the cost of each step.

- **Index Seek:** Efficient, only relevant rows are accessed.
- **Index Scan:** Less efficient, reads all rows in the index.
- **Table Scan:** Most inefficient, reads all rows in the table.

## Example:
In SSMS, run the query and click on the "Display Estimated Execution Plan" button to view the graphical plan. Look for:

- **Thick Arrows:** Indicate a large number of rows processed, potentially a performance bottleneck.
- **Warning Symbols:** Indicate potential issues like missing indexes.

### Explanation:

Focus on operations with the highest cost percentage to optimize query performance.

# 17. Index Seek vs Index Scan

## Theory:
- **Index Seek:** The query engine uses the index to find specific rows quickly. It is like looking up a word in a dictionary using the alphabetical order.
- **Index Scan:** The query engine reads all the rows in the index. It’s like reading through the entire dictionary to find a word.

## Example:

### Query using Index Seek:

> SELECT * FROM Employees WHERE EmployeeID = 1;

### Query using Index Scan:

> SELECT * FROM Employees WHERE Salary > 50000;

### Explanation:

- **Index Seek** uses the primary key to directly find the row.
- **Index Scan** reads the entire index because there’s no specific key match.

# 18. Optimizing a Slow Query

## Theory:
- **Analyze Execution Plan:** Identify slow steps.
- **Create or Modify Indexes:** Add missing indexes or refine existing ones.
- **Query Refactoring:** Rewrite complex queries into simpler parts.
- **Avoid Cursors:** Use set-based operations instead of row-by-row operations.

## Example:

### Slow Query:

> SELECT * FROM Sales WHERE YEAR(SaleDate) = 2022;

### Optimized Query:

> SELECT * FROM Sales WHERE SaleDate BETWEEN '2022-01-01' AND '2022-12-31';

### Explanation:

The original query uses a function on the column, preventing index use.  
The optimized query uses a range search, allowing index usage.

# 19. Common Performance Tuning Techniques

## Theory:
- **Indexing:** Create and optimize indexes for frequently searched columns.
- **Query Optimization:** Use `EXISTS` instead of `IN` for subqueries, avoid `SELECT *`, and use joins efficiently.
- **Statistics Update:** Ensure table statistics are up-to-date to allow the query optimizer to choose the best execution plan.
- **Avoid Cursors:** Use set-based operations instead of looping through rows.

## Example:

### Poorly Optimized Query:

> SELECT * FROM Orders WHERE CustomerID IN (SELECT CustomerID FROM Customers WHERE Country = 'India');

### Optimized Query:

> SELECT o.* FROM Orders o  
> JOIN Customers c ON o.CustomerID = c.CustomerID  
> WHERE c.Country = 'India';

### Explanation:

Replaces the subquery with a join, making the query more efficient.

# 20. Paging in SQL Server

## Theory:
Paging allows you to retrieve rows in smaller chunks, improving performance when dealing with large datasets. It uses the `OFFSET` and `FETCH` clauses in combination with `ORDER BY`.

## Example:

### Query:

> SELECT * FROM Employees  
> ORDER BY EmployeeID  
> OFFSET 10 ROWS  
> FETCH NEXT 10 ROWS ONLY;

### Explanation:

This query skips the first 10 rows and retrieves the next 10 rows. Useful for displaying data in pages, like viewing search results or reports in small chunks.

# 21. Handling Deadlocks

## Theory:
Deadlocks occur when two or more transactions hold locks on resources the other needs, causing both to wait indefinitely. SQL Server resolves this by terminating one transaction, called the “deadlock victim.”

### Detect Deadlocks:
- Use SQL Server Profiler or system health extended events.

### Prevent Deadlocks:
- Keep transactions short, access resources in the same order, and use lower isolation levels.

## Example:

If Transaction A locks Table 1 and waits for Table 2, while Transaction B locks Table 2 and waits for Table 1, a deadlock occurs. SQL Server will kill one transaction, allowing the other to proceed.


# 22. Error Handling in SQL

## Theory:
Use `TRY...CATCH` blocks to handle errors gracefully in SQL Server. It allows you to catch errors, log them, and take corrective actions.

## Example:

> BEGIN TRY  
>    -- Attempt to divide by zero  
>    SELECT 1 / 0;  
> END TRY  
> BEGIN CATCH  
>    PRINT 'An error occurred: ' + ERROR_MESSAGE();  
> END CATCH;

### Explanation:

The `CATCH` block catches the divide-by-zero error and prints an error message.

# 23. Security in SQL Server

## Theory:
SQL Server security involves controlling access to data and database objects. Use authentication, authorization, and encryption techniques.

- **Authentication:** Windows or SQL Server authentication.
- **Authorization:** Use roles and permissions (`GRANT`, `REVOKE`, `DENY`) to control access.
- **Encryption:** Use Transparent Data Encryption (TDE) or Always Encrypted to protect sensitive data.

## Example:

> GRANT SELECT ON Employees TO HR_Role;  
> DENY SELECT ON Salaries TO HR_Role;

### Explanation:

Allows HR role to read Employees data but denies access to Salaries.

# 24. Best Practices for Security

## Theory:
- Use the principle of least privilege.
- Regularly audit permissions.
- Encrypt sensitive data using TDE or Always Encrypted.
- Use secure connections (SSL/TLS).
- Implement data masking and row-level security.

## Example:

Enable data masking to protect sensitive data.

> ALTER TABLE Employees  
> ALTER COLUMN SSN ADD MASKED WITH (FUNCTION = 'partial(1,"XXXXXX",4)');

### Explanation:

This masks the SSN column, showing only part of the data to unauthorized users.

# 25. Managing Permissions

## Theory:
Permissions define what actions a user can perform on database objects. Use roles to group permissions and commands like `GRANT`, `REVOKE`, and `DENY` to manage access.

## Example:

> CREATE ROLE SalesRole;  
> GRANT SELECT, INSERT ON Sales TO SalesRole;  
> EXEC sp_addrolemember 'SalesRole', 'SalesUser';

### Explanation:

Creates a role `SalesRole`, grants it permissions, and adds `SalesUser` to the role.

# 26. Transparent Data Encryption (TDE)

## Theory:
TDE encrypts the entire database, protecting data at rest from unauthorized access. It encrypts the data and log files, making it unreadable without the encryption key.

## Example:

> CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'YourPassword123';  
> CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My Certificate';  
> CREATE DATABASE ENCRYPTION KEY  
> WITH ALGORITHM = AES_256  
> ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
> ALTER DATABASE YourDatabase SET ENCRYPTION ON;

### Explanation:

This enables TDE for the specified database, securing data files.

# 27. Dynamic Data Masking

## Theory:
Dynamic Data Masking limits exposure of sensitive data by masking it to non-privileged users, allowing only authorized users to see the full data.

## Example:

> ALTER TABLE Employees  
> ALTER COLUMN PhoneNumber ADD MASKED WITH (FUNCTION = 'default()');

### Explanation:

Masks the `PhoneNumber` column, showing only partial data to unauthorized users.

# 28. Backup Types

## Theory:
- **Full Backup:** Backs up the entire database.
- **Differential Backup:** Backs up changes since the last full backup.
- **Transaction Log Backup:** Backs up the transaction log, allowing point-in-time recovery.

## Example:

### Full Backup:

> BACKUP DATABASE YourDatabase TO DISK = 'C:\Backups\YourDatabase.bak';

### Differential Backup:

> BACKUP DATABASE YourDatabase TO DISK = 'C:\Backups\YourDatabase_diff.bak' WITH DIFFERENTIAL;

### Log Backup:

> BACKUP LOG YourDatabase TO DISK = 'C:\Backups\YourDatabase_log.bak';

### Explanation:

These backups allow for complete and point-in-time restoration of the database.

# 29. Database Recovery

## Theory:
Recovery involves restoring the database to a previous state using backups. Use full, differential, and log backups for point-in-time recovery.

## Example:

> RESTORE DATABASE YourDatabase FROM DISK = 'C:\Backups\YourDatabase.bak' WITH NORECOVERY;  
> RESTORE DATABASE YourDatabase FROM DISK = 'C:\Backups\YourDatabase_diff.bak' WITH NORECOVERY;  
> RESTORE LOG YourDatabase FROM DISK = 'C:\Backups\YourDatabase_log.bak' WITH RECOVERY;

### Explanation:

Restores the database and transaction log to a specific point in time.

# 30. High Availability

## Theory:
High Availability (HA) ensures minimal downtime and data loss in the event of a failure. Techniques include SQL Server Always On, clustering, and log shipping.

## Example:

Configure Always On Availability Groups for automatic failover and high availability.

# 31. Always On Availability Groups

## Theory:
Provides high availability and disaster recovery by replicating databases across multiple servers. If the primary server fails, a secondary server automatically takes over.

## Example:

Use SSMS to configure an Availability Group, selecting primary and secondary replicas.

# 32. Log Shipping

## Theory:
Log shipping involves automatically sending transaction log backups from one server to another, providing disaster recovery and read-only reporting.

## Example:

1. Backup transaction logs on the primary server.
2. Copy log backups to the secondary server.
3. Restore the logs on the secondary server in a `RESTORE WITH NORECOVERY` mode.

# 33. Database Mirroring

## Theory:
Database mirroring keeps a database copy synchronized on a different server. It provides high availability, but only supports a single mirror database.

## Example:

Use SSMS to configure mirroring between principal and mirror servers.

# 34. SQL Server Agent

## Theory:
SQL Server Agent automates tasks like backups, maintenance, and monitoring. It runs jobs on a scheduled basis, simplifying administrative tasks.

## Example:

Create a job to back up a database every night at 2 AM.

# 35. Import and Export Data

## Theory:
Use tools like BCP, BULK INSERT, and SSIS to import and export data between SQL Server and other sources like CSV files, Excel, and other databases.

## Example:

### BCP Import:

> bcp YourDatabase.dbo.Employees in "C:\Data\employees.csv" -c -T -S localhost

### BULK INSERT:

> BULK INSERT Employees  
> FROM 'C:\Data\employees.csv'  
> WITH (FIELDTERMINATOR = ',', ROWTERMINATOR = '\n');

### Explanation:

Imports data from a CSV file into the Employees table.

# 36. SQL Server Profiler

## Theory:
SQL Server Profiler captures and analyzes SQL Server events. It helps troubleshoot performance issues, capture deadlocks, and analyze queries.

## Example:

Use SQL Server Profiler to trace all queries taking more than 5 seconds to execute.

# 37. Dynamic Management Views (DMVs)

## Theory:
DMVs provide insights into the health, performance, and activity of SQL Server. Use them to monitor server activity, troubleshoot issues, and optimize performance.

## Example:

Query to check index usage:

> SELECT * FROM sys.dm_db_index_usage_stats;

### Explanation:

Shows how often indexes are used, helping identify unused or missing indexes.
# 38. Index Maintenance

## Theory:
Regular index maintenance includes rebuilding or reorganizing indexes to improve query performance and reduce fragmentation.

## Example:

### Rebuild Index:

> ALTER INDEX ALL ON Employees REBUILD;

### Reorganize Index:

> ALTER INDEX ALL ON Employees REORGANIZE;

### Explanation:

- Rebuilding recreates the entire index.
- Reorganizing defragments the existing index.

# 39. Managing TempDB

## Theory:
TempDB is used for temporary objects and operations. Optimize by ensuring it has enough space, placing it on fast storage, and regularly monitoring usage.

## Example: Check TempDB usage:

> SELECT * FROM sys.dm_db_file_space_usage;

# 40. Database Maintenance Plan

## Theory:
A maintenance plan automates routine tasks like backups, index optimization, and integrity checks. Use SSMS to create and schedule these plans.

# 41. Data Lake vs Data Warehousing

## Theory:
- **Data Lake:** Stores raw, unstructured, and semi-structured data. Used for big data analytics.
- **Data Warehouse:** Stores structured, processed data for reporting and business intelligence.

# 42. Data Migration

## Theory:
Data migration involves transferring data between different systems. Ensure data integrity by validating row counts, using checksums, and performing ETL (Extract, Transform, Load) processes.

# 43. Handling Different Formats

## Theory:
Use tools like SSIS, PolyBase, and linked servers to combine and query data from multiple formats like SQL, NoSQL, text, and CSV.

## Example:

Create a linked server to access and query a CSV file.

# 44. Scalability of a Database

## Theory:
Ensure scalability by using partitioning, sharding, optimizing queries, and scaling vertically (adding resources to existing servers) or horizontally (adding more servers).

# 45. CI/CD Integration

## Theory:
Integrate SQL scripts into continuous integration (CI) pipelines using tools like Azure DevOps, Jenkins, or GitLab CI/CD. Automate testing and deployment of database changes.

## Example:

Create a pipeline in Azure DevOps to deploy SQL scripts to a staging database.

# 46. Partitioning

## Theory:
Partitioning divides large tables into smaller, manageable pieces, improving performance and maintenance. Horizontal partitioning is commonly used in SQL Server.

## Example:

Partition Sales table by year:

> CREATE PARTITION FUNCTION YearPartition (int)  
> AS RANGE LEFT FOR VALUES (2019, 2020, 2021);

### Explanation:

Splits data into separate partitions based on the year.

# 47. Database Snapshot

## Theory:
A database snapshot is a read-only, static view of a database at a point in time. It is useful for reporting and testing.

## Example:

> CREATE DATABASE YourDatabase_Snapshot ON   
> ( NAME = YourDatabaseDataFile, FILENAME = 'C:\Data\YourDatabaseSnapshot.ss' )  
> AS SNAPSHOT OF YourDatabase;

### Explanation:

Creates a snapshot that reflects the state of the database at the time it was created.

# 48. Resource Governor

## Theory:
Resource Governor controls SQL Server resource usage by allocating CPU and memory resources to specific workloads.

## Example:

Create a resource pool:

> CREATE RESOURCE POOL MyPool WITH (MAX_CPU_PERCENT = 50);

### Explanation:

Limits the CPU usage of workloads in the `MyPool` to 50%.

# 49. Query Store

## Theory:
Query Store captures a history of queries, plans, and runtime statistics, helping to monitor and optimize query performance.

## Example:

Enable Query Store:

> ALTER DATABASE YourDatabase SET QUERY_STORE = ON;

### Explanation:

Enables Query Store for monitoring query performance.

# 50. Handling Large Databases

## Theory:
Use partitioning, archiving, and indexing strategies to handle large databases. Regularly monitor performance and optimize queries.

# 51. Multi-Tenant Databases

## Theory:
Use row-level security, partitioning, and efficient indexing to handle multi-tenant databases, ensuring data separation and performance.

# 52. Extended Events

## Theory:
Extended Events provide lightweight event handling and monitoring in SQL Server, replacing SQL Profiler.

## Example:

Create an event session to monitor query execution.

> CREATE EVENT SESSION MySession ON SERVER   
> ADD EVENT sqlserver.sql_batch_completed  
> ADD TARGET package0.ring_buffer;

# 53. GDPR and Compliance

## Theory:
Use encryption, data masking, and auditing to comply with data protection regulations like GDPR.

## Example:

Implement Always Encrypted to protect sensitive data:

> CREATE COLUMN MASTER KEY MyCMK  
> WITH (  
> KEY_STORE_PROVIDER_NAME = 'MSSQL_CERTIFICATE_STORE',  
> KEY_PATH = 'CurrentUser\My\Certificate'  
> );

### Explanation:

Protects sensitive columns in the database with encryption.

This comprehensive set of explanations, examples, and queries covers the most important SQL Server topics, providing a solid foundation for understanding and working with SQL Server in a practical and effective manner.
