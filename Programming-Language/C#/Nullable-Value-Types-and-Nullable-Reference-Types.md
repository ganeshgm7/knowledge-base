# 📘 Nullable Value Types in C#

Nullable value types in C# allow value types like `int`, `bool`, `double`, etc. to store either a **normal value** or **null**, representing the absence of a value.

---

## 🔹 What Are Nullable Value Types?

In C#, value types like `int`, `bool`, `DateTime` cannot store `null` by default.

```
int age = null; // ❌ Error: int cannot be null
```

Using **nullable value types**, you can allow them to hold `null`:

```
int? age = null; // ✅ OK
```

The `?` makes the value type nullable.

---

## 🔹 Why Were Nullable Value Types Introduced?

### 🧩 The Problem

- Value types **must always** contain a value.
- In real-world applications, values are sometimes:
  - Unknown
  - Optional
  - Not yet entered
- Databases and forms often contain **nulls**

### ✅ The Solution

C# introduced **nullable value types** to handle **missing or optional data**.

```
int? salary = null; // Represents "no data"
```

---

## 🔹 Declaring Nullable Value Types

You can make any value type nullable using `?`.

| Value Type  | Nullable Version |
|-------------|------------------|
| `int`       | `int?`           |
| `bool`      | `bool?`          |
| `double`    | `double?`        |
| `DateTime`  | `DateTime?`      |

### Example

```
int? age = null;
bool? isVerified = true;
```

---

## 🔹 Checking for Value or Null

### ✅ `HasValue`

Returns `true` if a value is assigned.

```
int? age = 25;

if (age.HasValue)
{
    Console.WriteLine("Age is: " + age.Value);
}
else
{
    Console.WriteLine("No age provided.");
}
```

### ✅ `Value`

Accesses the actual value (only use if `HasValue` is `true`).

```
int? age = 30;
int realAge = age.Value;
```

---

## 🔹 Null Coalescing Operator (`??`)

Returns a default value if the nullable type is `null`.

```
int? age = null;
int displayAge = age ?? 0; // Returns 0 if age is null
```

---

## 🔹 Null Conditional Access (`?.`)

Allows safe access to members of a nullable type.

```
DateTime? birthdate = null;
int? year = birthdate?.Year; // Returns null if birthdate is null
```

---

## 🔹 Converting Between Nullable and Non-Nullable

### Explicit Cast (Unsafe if null)

```
int? x = 100;
int y = (int)x;
```

### Using `GetValueOrDefault()`

Returns value or a default (`0` for `int`, `false` for `bool`, etc.)

```
int? x = null;
int y = x.GetValueOrDefault(); // Returns 0
```

---

## 🔹 When to Use Nullable Value Types

Use when:

- Handling **optional fields**
- Working with **databases**
- Managing **form inputs** where fields might be empty
- Representing **unknown or missing data**

---

## 🔹 Summary Table

| Feature               | Description                        | Example                     |
|-----------------------|------------------------------------|-----------------------------|
| `T?`                  | Nullable value type                | `int? x = null`             |
| `.HasValue`           | Checks if it’s not null            | `x.HasValue`                |
| `.Value`              | Gets the actual value              | `x.Value`                   |
| `??`                  | Default fallback if null           | `x ?? 0`                    |
| `?.`                  | Null-safe property/method access   | `date?.Year`                |
| `GetValueOrDefault()` | Gets value or type default         | `x.GetValueOrDefault()`     |

---

## 🔹 Example Code

```
using System;

class Program
{
    static void Main()
    {
        int? age = null;

        if (age.HasValue)
        {
            Console.WriteLine("Age: " + age.Value);
        }
        else
        {
            Console.WriteLine("Age not provided.");
        }

        int displayAge = age ?? 18;
        Console.WriteLine("Display Age: " + displayAge);
    }
}
```

---

## 🧠 Final Thoughts

- Nullable value types are essential for writing clean, error-free code where data may not be available.
- They make your code more flexible and safer when working with optional or external data sources.

---
---

# 📘 Nullable Reference Types in C#

Nullable Reference Types (NRTs) are a **feature introduced in C# 8.0** to help developers avoid one of the most common runtime bugs in .NET — the dreaded **`NullReferenceException`**.

They allow you to explicitly declare **whether a reference type can be `null`** or not, and let the **compiler warn you** when you're using null-unsafe code.

---

## 🔹 What Are Nullable Reference Types?

In older versions of C#, **reference types** (like `string`, `object`, or custom classes) could always be assigned `null`:

```
string name = null; // Allowed
```

This causes a major problem if you try to use it without checking:

```
Console.WriteLine(name.Length); // 💥 NullReferenceException at runtime
```

With Nullable Reference Types:

- `string` means **non-nullable** → must always have a value.
- `string?` means **nullable** → can be `null`, so you must check it before use.

---

## 🔹 Why Were Nullable Reference Types Introduced?

### 💥 The Problem

- Reference types can be `null` by default.
- Developers often **forget to check for null**.
- Leads to **runtime crashes**, especially when calling members on null objects.
- Null-related bugs are hard to detect and fix.

> 🔥 Tony Hoare (inventor of `null`) called it the "**billion-dollar mistake**".

---

## 🔹 The Solution: Nullable Reference Types

Starting from C# 8.0, you can now **tell the compiler** your intent:

- Use `string` for **non-nullable** references.
- Use `string?` for **nullable** references.

The compiler helps you catch mistakes at **compile time** instead of runtime.

---

## 🔹 How to Enable Nullable Reference Types

### ✅ Enable in a single file

Add this at the top of your C# file:

```
#nullable enable
```

### ✅ Enable for the whole project

Edit your `.csproj` file:

```
<PropertyGroup>
  <Nullable>enable</Nullable>
</PropertyGroup>
```

---

## 🔹 Example: Without and With Nullable Reference Types

### 🔴 Without Nullable Reference Types

```
string name = null;
Console.WriteLine(name.Length); // 💥 Crashes at runtime
```

### 🟢 With Nullable Reference Types

```
#nullable enable

string name = null; // ⚠️ Compiler warning
Console.WriteLine(name.Length); // ⚠️ Warning: possible null dereference
```

### ✅ Correct Usage with `string?`

```
#nullable enable

string? name = null;

if (name != null)
{
    Console.WriteLine(name.Length); // Safe!
}
```

---

## 🔹 Nullable vs Non-Nullable Reference Types

| Type       | Can Be Null | Compiler Warning if Used Unsafely |
|------------|-------------|-----------------------------------|
| `string`   | ❌ No        | ✅ Yes                            |
| `string?`  | ✅ Yes       | ✅ Yes (if used without checks)   |

---

## 🔹 Real-Life Example

```
#nullable enable

public class User
{
    public string Name { get; set; }         // Must not be null
    public string? Nickname { get; set; }    // Optional
}

void Greet(User user)
{
    Console.WriteLine($"Hi {user.Name}");

    if (user.Nickname != null)
    {
        Console.WriteLine($"You can also call me {user.Nickname}");
    }
}
```

---

## 🔹 Summary: What Problem Does It Solve?

| Problem                                | How Nullable Reference Types Help        |
|----------------------------------------|------------------------------------------|
| Reference types can be null by default | Now you must **explicitly declare nullability** |
| NullReferenceExceptions at runtime     | Caught by **compiler at compile-time**   |
| Unclear code contracts                 | Code becomes **self-documenting**        |
| No help from compiler on null checks   | Compiler gives **warnings and hints**    |

---

## 🧠 Final Thoughts

- Nullable Reference Types are **not about new runtime behavior** — they’re a **compile-time safety feature**.
- They help you write **cleaner**, **safer**, and **more predictable** C# code.
- Highly recommended for **modern C# projects (8.0+)**.

---
