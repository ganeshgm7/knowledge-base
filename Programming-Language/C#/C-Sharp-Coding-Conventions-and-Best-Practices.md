# C# Coding Conventions and Best Practices

## Naming Convention

- **Pascal Case:** The leading character of each word or phrase is capitalized. (Examples: `ProcessTransaction`, `TaxCalculation`)
- **Camel Case:** Like PascalCase except the first letter is lowercase. (Examples: `totalAmount`, `userName`)
- **Upper Snake Case:** All letters are capitalized, and words are separated with an underscore. (Example: `MAX_SIZE`)

### Specific Naming Guidelines

<div align="center">

|          Element          |        Case         |
|--------------------------|---------------------|
|       Class name         |     PascalCase      |
|     Namespace name       |     PascalCase      |
|    Constructor name      |     PascalCase      |
|       Method name        |     PascalCase      |
|     Properties name      |     PascalCase      |
|         Enum name        |     PascalCase      |
|  Field name (Public)     |     PascalCase      |
| Field name (Private)     |     _camelCase       |
|     Method arguments     |     camelCase       |
|      Local variables     |     camelCase       |
|       Constant name      | UPPER_SNAKE_CASE    |

</div>

## General Guidelines

- **Do not use var:** Always use the explicit type. Change to the explicit type when working on those blocks if already used.
- **Meaningful Names:** Use clear and descriptive names for classes, methods, properties, and variables.
- **LINQ Queries:** Use meaningful names for LINQ query variables.
- **Formatting and Indentation:** Maintain consistent formatting and indentation. (Use `CTRL + K + D` in Visual Studio)
- **Interfaces:** Prefix interfaces with the letter 'I'.
- **Unused Usings:** Remove unnecessary Namespace usings.
- **Database Calls:** Avoid database calls inside for/for-each loops.
- **KISS & DRY Principles:** Follow the KISS (Keep It Simple Stupid) and DRY (Don't Repeat Yourself) principles.
- **XML Comments:** Use XML comments to document classes, methods, and properties.

## Sample Code
  
````csharp
namespace Amaze.Api.Customer;

/// <summary>
/// A class representing a customer with Customer ID, name, address, date of birth, and status.
/// </summary>
public class Customer
{
    /// <summary>
    /// Unique Customer ID.
    /// </summary>
    public int CustomerId { get; set; }

    /// <summary>
    /// Name of the customer.
    /// </summary>
    public string Name { get; set; }

    /// <summary>
    ///Date of Birth of the customer.
    /// </summary>
    public DateTime DateOfBirth { get; set; }

    /// <summary>
    /// Current Status of the customer.
    /// </summary>
    public CustomerStatus Status { get; set; }
}

/// <summary>
/// Enumeration representing the status of a customer.
/// </summary>
public enum CustomerStatus
{
    Active,
    Inactive,
    Suspended
}

/// <summary>
/// A class providing methods to handle customer data.
/// </summary>
public class CustomerRepository
{
    private readonly List<Customer> _customers;

    private const int MAX_CUSTOMERS = 1000;

    public readonly int MaximumAgeLimit = 58;

    public CustomerRepository()
    {
        _customers = [];
    }

    /// <summary>
    /// Adds a new customer to the repository.
    /// </summary>
    /// <param name="customer">The customer to add.</param>
    /// <returns>Added customer ID</returns>
    public int AddCustomer(Customer customer)
    {
        if (_customers.Count >= MAX_CUSTOMERS)
        {
            throw new InvalidOperationException("Customer repository is full.");
        }
        _customers.Add(customer);

        return customer.CustomerId;
    }
}
````
