# C# Language Instructions

## General C# Guidelines
- Use C# 12+ features compatible with .NET 8.
- Use explicit types for local variables. Avoid `var`.
- Use `string interpolation` for string formatting (e.g., `$"Hello {name}"`).
- Use `StringBuilder` for concatenating strings in loops, especially with large amounts of text.
- Prefer raw string literals to escape sequences or verbatim strings.
- Use language keywords for data types (e.g., `string` instead of `System.String`, `int` instead of `System.Int32`).
- Use `int` rather than unsigned types (e.g., `uint`).
- Avoid magic numbers/strings; use constants or enums.
- Utilize modern language features and avoid outdated constructs.
- Write code with clarity and simplicity in mind; avoid overly complex logic.
- Use concise forms of object instantiation (e.g., `ExampleClass instance = new();`) when the variable type matches the object type.
- Use object initializers to simplify object creation (e.g., `var obj = new ExampleClass { Property = value };`).
- Use target-typed `new()` only when the type is explicitly named on the left-hand side (e.g., `FileStream stream = new(...);`).
- Use `nameof(...)` instead of string literals whenever possible.
- Use Unicode escape sequences (\uXXXX) for non-ASCII characters in source code.
- Avoid `this.` unless absolutely necessary.
- Always specify visibility (e.g., `private string _foo`), as the first modifier.
- Make internal and private types `static` or `sealed` unless derivation is required.
- Place fields at the top within type declarations.

## Asynchronous Programming
- Use `async/await` for all I/O-bound operations (e.g., database calls, file I/O, HTTP requests).
- Name async methods with `Async` suffix (e.g., `GetUserAsync`).
- Use `Task` for fire-and-forget operations, but ensure proper exception handling.
- Avoid `async void` except in event handlers.
- Be cautious of deadlocks; use `Task.ConfigureAwait` when appropriate.

## Exception Handling
- Use try-catch blocks for expected exceptions; log errors with Serilog.
- Only catch exceptions that can be properly handled; avoid catching general `Exception`.
- Use specific exception types to provide meaningful error messages.
- Throw custom exceptions derived from `Exception` for business logic errors.
- Avoid catching `Exception` broadly; catch specific types.
- Use `finally` for cleanup (e.g., disposing resources).
- Simplify code with `using` statements instead of try-finally for `IDisposable`.

## Dependency Injection
- Register services in `Program.cs` (scoped for per-request, singleton for shared).
- Inject interfaces (e.g., `IUserManager`) into constructors.
- Use `IServiceProvider` sparingly; prefer constructor injection.

## Naming Conventions
- Classes/Interfaces: PascalCase (e.g., `UserManager`, `IUserDb`).
- Methods/Properties: PascalCase (e.g., `GetUserById`).
- Parameters/Variables: camelCase (e.g., `userId`).
- Private fields: camelCase with underscore prefix (e.g., `_logger`).
- Static fields: camelCase with `s_` prefix (e.g., `s_logger`).
- Thread static fields: camelCase with `t_` prefix.
- Enums: PascalCase for names and values.
- Primary constructor parameters: camelCase, not prefixed with `_` (assign to `_` fields if needed).
- Use `readonly` where possible; place after `static` (e.g., `static readonly`).

## Collections and LINQ
- Use `IEnumerable<T>` for read-only collections.
- Use collection expressions to initialize collections (e.g., `string[] vowels = ["a", "e", "i", "o", "u"];`).
- Prefer LINQ for querying (e.g., `users.Where(u => u.IsActive)`).
- Use `async` versions like `ToListAsync()` for EF queries.
- Use meaningful names for query variables.
- Use aliases for anonymous types to ensure Pascal casing.
- Rename properties in results to avoid ambiguity.
- Use implicit typing in LINQ queries for readability.
- Use explicit typing for loop variables in `foreach` loops, as the type may not be obvious.

## Delegates and Events
- Use `Func<>` and `Action<>` instead of defining custom delegate types.
- Use lambda expressions for event handlers that don't need removal.
- Call static members using the class name (e.g., `ClassName.StaticMember`).

## Code Structure
- Keep methods short; extract to private methods if needed.
- Use required properties instead of constructors for initialization.
- Follow SOLID principles: Single responsibility, Open/Closed, etc.
- Use file-scoped namespace declarations.
- Place `using` directives outside the namespace declaration, sorted alphabetically (System.* on top).
- Use Allman style for braces (open/close on new lines, aligned with indentation).
- Always use braces for `if`, `else`, and `else if` blocks, even for single statements.
- When using labels (for `goto`), indent one less than current indentation.
- Limit lines to 65 characters; break long statements.
- Add blank lines between method/property definitions; avoid more than one empty line.
- Use parentheses for clarity in expressions.
- Use `&&` and `||` for short-circuiting comparisons.
- Avoid spurious free spaces (e.g., no extra spaces in `if (someVar == 0)`).
- Write only one statement per line; one declaration per line.

## Comments
- Use single-line comments (`//`) for brief explanations.
- Use XML comments for public APIs (classes, methods, properties).
- Place comments on separate lines, start with uppercase, end with period.

---

When writing C# code, ensure it integrates seamlessly with the layered architecture and follows these patterns for maintainability.
