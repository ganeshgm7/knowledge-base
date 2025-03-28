# 🛠️ Constructors in C#

Constructor is a special method of the class which gets automatically invoked whenever an instance of the class is created. Constructors in C# are fundamental components of object-oriented programming. Like methods, It contains the collection of instructions that are executed at the time of Object creation. It is used to assign initial values to the data members of the same class. Some important points about Constructors are mentioned below:

- The constructor of a class must have the same name as the class name in which it resides.
- A class can have any number of constructors.
- A constructor can not be abstract, final, and Synchronized.
- A constructor doesn’t have any return type.

---

## 🔢 Type of Constructor

- Default Constructor
- Parameterized Constructor
- Static Constructor
- Private Constructor

---

## 🧱 Default Constructor

A default constructor is a type of constructor that has no parameters. It is automatically called when an object is created without passing any arguments.

### 🎯 Purpose of a Default Constructor

- To initialize an object with default values.
- To make sure the object is in a valid starting state.
- It allows the creation of objects even when no specific data is available at the time.

---

### 📌 Key Points

- It has the same name as the class.
- It does not take any input (no parameters).
- C# will automatically provide a default constructor if no other constructor is defined.
- If any other constructor is written manually, C# does not add a default one automatically — you must define it yourself.

---

### 🧪 Sample of a Default Constructor

```

public class Person
{
    public string Name;
    public int Age;

    // Default Constructor (no parameters)
    public Person()
    {
        Name = "Unknown";
        Age = 0;
    }
}

```

---

### 🚀 How to Use It

``csharp
Person p = new Person(); // Default constructor is called automatically
Console.WriteLine(p.Name); // Output: Unknown
Console.WriteLine(p.Age);  // Output: 0
``

# 🧩 Parameterized Constructor

A parameterized constructor is a constructor that takes one or more arguments (parameters).  
It allows you to pass values to an object at the time of creation, so you can initialize it with custom data.

---

## 🎯 Purpose of Parameterized Constructor

- To create objects with specific, meaningful values.
- To avoid using default values or setting properties manually after object creation.
- Helps keep object creation clean, safe, and consistent.

---

## 📌 Key Points

- It has the same name as the class.
- It includes parameters inside parentheses.
- You can define multiple constructors with different parameters – this is called **constructor overloading**.
- If you define only parameterized constructors, the default constructor will not be available unless you add it explicitly.

---

## 🕒 When to Use Parameterized Constructor

- When the object must have certain values set when it is created.
- To avoid partially-initialized objects.
- When you want to simplify and standardize object setup.

**Commonly used in:**

- Models  
- Entity classes  
- Business logic  
- Constructors in design patterns

---

## 🧪 Sample of Parameterized Constructor

``csharp
public class Person
{
    public string Name;
    public int Age;

    // Parameterized Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
``

---

## 🚀 How to Use It

``csharp
Person p = new Person("Alice", 28); // Passes data during object creation
Console.WriteLine(p.Name); // Output: Alice
Console.WriteLine(p.Age);  // Output: 28
``

# ⚙️ Static Constructor

A static constructor is a special type of constructor used to initialize static members of a class.  
It is called automatically once — only one time, and only once, for the entire class, not for each object.

---

## 🎯 Purpose of Static Constructor

- To initialize static fields or data when the class is first used.
- To perform one-time setup tasks, like loading configurations or settings shared across all instances.
- To prepare static resources before any static or instance members are accessed.

---

## 🕒 When is the Static Constructor Called?

A static constructor runs before:

- The first object is created
- Or any static member of the class is accessed

It ensures that all static data is ready before anything uses the class.

---

## ❓ Why Use a Static Constructor?

- To initialize static variables or constants.
- To perform class-level initialization that should happen only once.
- To ensure thread-safe initialization of static members.

---

## 🚫 Restrictions

| Restriction                          | Allowed? |
|-------------------------------------|----------|
| Parameters                          | ❌ Cannot have parameters |
| Manual invocation                   | ❌ Cannot be called manually |
| Overloading                         | ❌ Cannot be overloaded |
| Access modifiers (public/private)   | ❌ Cannot have access modifiers |

---

## 🧪 Sample of Static Constructor

``csharp
public class Logger
{
    public static string Config;

    // Static Constructor
    static Logger()
    {
        Config = "Logging Enabled";
        Console.WriteLine("Static constructor executed");
    }
}
``

---

## 🚀 Usage

``csharp
Console.WriteLine(Logger.Config); 
// Output: 
// Static constructor executed
// Logging Enabled
``


# 🔒 Private Constructor

A private constructor is a constructor that has a private access modifier.  
This means it cannot be accessed or called from outside the class.

---

## 🎯 Purpose of a Private Constructor

- To restrict object creation from outside the class.
- To prevent instantiation of a class.

**Used when:**

- A class should have only one instance (**Singleton pattern**).
- You want to hide the constructor to control object creation.
- You are using a class with only static members (like utility/helper classes).

---

## ❓ Why Use a Private Constructor?

- To control how and when objects are created.
- To implement design patterns like:
  - **Singleton** (only one object allowed)
  - **Factory** (object created via static method)
- To create a class that is never meant to be instantiated.

---

## 🧪 Sample of Private Constructor

``csharp
public class Utility
{
    // Private Constructor
    private Utility()
    {
        // Prevents instantiation
    }

    public static void DoWork()
    {
        Console.WriteLine("Work done.");
    }
}
``

---

## 🚀 Usage

``csharp
Utility.DoWork();      // ✅ Allowed
// Utility u = new Utility(); // ❌ Error: Constructor is inaccessible
``

---

## 🧵 Private Constructor in Singleton Pattern

``csharp
public class Singleton
{
    private static Singleton instance;

    // Private Constructor
    private Singleton() { }

    public static Singleton GetInstance()
    {
        if (instance == null)
            instance = new Singleton();

        return instance;
    }
}
``


# 🚀 Advanced Constructor Concepts in C#

---

## 🔄 Constructor Overloading

### ✅ What is it?

When a class has multiple constructors with different sets of parameters.  
Helps create objects in different ways based on available data.

### 🧠 Key Points

- Improves flexibility
- Allows default values, partial input, or full data
- Makes code cleaner

### 🧾 Example

``csharp
public Person() { }
public Person(string name) { }
public Person(string name, int age) { }
``

---

## 🔗 Constructor Chaining (`this`)

### ✅ What is it?

When one constructor calls another within the same class using the keyword `this`.

### 📌 Purpose

- Avoid code duplication  
- Keep initialization logic centralized

### 🧾 Syntax

``csharp
public Person() : this("Unknown", 0) { }

public Person(string name, int age) {
    // Actual initialization logic here
}
``

---

## 🧬 Calling Base Class Constructor (`base`)

### ✅ What is it?

When a derived class constructor calls a constructor from the base (parent) class using `base(...)`.

### 📌 Purpose

- Ensure the base class is properly initialized  
- Useful when base class has required parameters

### 🧾 Syntax

``csharp
public class Employee : Person
{
    public Employee(string name, int age) : base(name, age) { }
}
``

---

## 🆚 Object Initializer vs Constructor

### ✅ What is an Object Initializer?

A way to set properties after using the default constructor, without needing a parameterized constructor.

### 🧾 Example

``csharp
Person p = new Person { Name = "Alice", Age = 25 };
``

# 🆕 Primary Constructor (C# 12)

A **Primary Constructor** is a new feature introduced in **C# 12** that allows you to declare constructor parameters directly in the class declaration line.  
These parameters are then available inside the class for use in initializing fields, properties, or for general logic.

---

## 🎯 Purpose of Primary Constructor

- To reduce boilerplate code in classes that simply accept input values and expose them.
- To make class definitions more concise and readable, especially for data-centric classes like models or DTOs.
- To support more declarative and expressive syntax for simple types.

---

## ⚙️ How It Works (Conceptually)

Traditionally, you write constructor parameters inside a constructor block and assign them to fields or properties.

With a **primary constructor**, the parameters are written in the class definition itself, and those parameters can be used throughout the class — just like local variables that exist across the class scope.

It’s especially useful in classes that don’t have complex logic in the constructor and mainly pass through values.

---

## 🧪 Primary Constructor Sample in C# 12

``csharp
public class Person(string name, int age)
{
    // readonly properties assigned using primary constructor parameters
    public readonly string Name = name;
    public readonly int Age = age;

    // Method to use the values
    public void Introduce()
    {
        Console.WriteLine($"Hi, I'm {Name} and I'm {Age} years old.");
    }
}
``

---

## 🚀 Usage

``csharp
var person = new Person("Alice", 30);
person.Introduce();
// Output: Hi, I'm Alice and I'm 30 years old.
``
