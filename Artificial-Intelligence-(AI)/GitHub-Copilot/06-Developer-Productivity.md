# Domain 6: Improve Developer Productivity with GitHub Copilot

> **Weight: 10–15%** | ~10–15 questions

---

## 6.1 Code Generation

### What Copilot Can Generate
- Functions and methods from descriptions or comments
- Classes and data models
- API endpoints (REST, GraphQL)
- Database queries (SQL, ORM)
- Configuration files (YAML, JSON, TOML)
- Boilerplate code (constructors, getters/setters, interfaces)
- Algorithm implementations

### How to Trigger Code Generation
| Method | How |
|--------|-----|
| Comment → Code | Write a comment describing what you want, press Enter |
| Function signature | Write the function name and parameters, let Copilot fill the body |
| Chat `/new` | Ask Copilot Chat to generate a new file or component |
| Agent Mode | Describe the full feature, let Agent implement it |

### Example Pattern
```python
# Calculate the median of a list of numbers
# Handle empty list (return None) and even-length lists (average of two middles)
def calculate_median(numbers: list[float]) -> float | None:
    # Copilot generates the complete implementation
```

---

## 6.2 Code Refactoring

### Refactoring Tasks Copilot Handles Well
| Task | How to Ask |
|------|-----------|
| Rename across files | Edit Mode: "Rename `getUserData` to `fetchUserProfile` across all files" |
| Extract method | Select code block → `/fix` or ask in chat |
| Convert to async/await | "Convert this callback-based code to use async/await" |
| Simplify conditionals | "Simplify this nested if-else using early returns" |
| Convert data structures | "Convert this array of arrays to array of objects" |
| Apply design patterns | "Refactor this to use the Strategy pattern" |
| Remove duplication | "Identify and eliminate duplicate code in this file" |

### Refactoring Best Practices with Copilot
1. **Commit before refactoring** — gives you a safe rollback point
2. **Use Edit Mode** for multi-file refactors
3. **Review diffs carefully** before accepting
4. **Run tests after** to verify behavior unchanged

---

## 6.3 Documentation Generation

### Types of Documentation Copilot Generates
| Type | Command/How |
|------|------------|
| **Inline comments** | Select code → ask in chat: "Add comments to explain this code" |
| **JSDoc / PyDoc / XML doc** | Select function → ask in chat: "Generate documentation for this function" |
| **README files** | Ask in chat: "Generate a README for this project" |
| **API documentation** | Ask in chat: "Document this API endpoint with examples" |
| **Change logs** | Ask in chat: "Write a changelog entry for these changes" |
| **Architecture docs** | Ask in chat: "Describe the architecture of this module" |

> Note: `/doc` may be available as a slash command in some IDEs — type `/` to check what's available in your IDE.

### Example — Generating a JSDoc Comment
```typescript
// Before: no docs
function processPayment(amount: number, currency: string, userId: string): Promise<TransactionResult>

// After Copilot /doc:
/**
 * Processes a payment for a user.
 * @param amount - The payment amount in the smallest currency unit
 * @param currency - ISO 4217 currency code (e.g., "USD", "EUR")
 * @param userId - The unique identifier of the user making the payment
 * @returns A promise that resolves to the transaction result
 * @throws {PaymentError} When the payment processing fails
 */
```

---

## 6.4 Accelerated Learning & Reducing Context Switching

### Accelerated Learning
- Use `/explain` to understand unfamiliar code
- Ask Copilot to explain libraries, frameworks, design patterns
- Use chat to ask "What does this regular expression match?"
- Learn new languages faster by asking for idiomatic patterns

### Reducing Context Switching
- Don't leave the IDE to look up documentation — ask Copilot Chat
- Ask Copilot for shell command help directly in the terminal chat panel
- Use Copilot for Stack Overflow-style questions directly in IDE
- PR summaries reduce need to fully read every diff

### Benefits Summary
| Old Way | With Copilot |
|---------|-------------|
| Google → Stack Overflow → Read → Adapt | Ask in chat → Adapted answer |
| Switch to browser for docs | `/explain` or ask chat |
| Write boilerplate manually | Auto-generated in seconds |
| Look up regex syntax | Ask "Write regex that matches email addresses" |

---

## 6.5 Generating Sample Data

### Use Cases
- Generate mock data for testing
- Create seed data for databases
- Generate JSON/CSV fixtures for unit tests
- Generate realistic-looking test user profiles

### How to Ask
```
# In chat:
"Generate 10 sample User objects in JSON format with realistic names, 
emails (using example.com domain), ages between 18-65, and random UUIDs"

"Create a SQL INSERT statement with 20 rows of sample product data 
for an e-commerce catalog"
```

> **Important:** Always use fake data in tests — never use real PII as sample data.

---

## 6.6 Modernizing Legacy Code

### Common Modernization Tasks
| Legacy Pattern | Modern Equivalent |
|---------------|------------------|
| Callbacks | Async/await |
| `var` | `let` / `const` |
| Function components (class) | React functional components + hooks |
| Old jQuery patterns | Native DOM APIs or modern frameworks |
| SQL string concatenation | Parameterized queries / ORM |
| Synchronous I/O | Asynchronous I/O |
| Manual memory management | Managed patterns |

### How to Use Copilot for Modernization
1. Select legacy code block
2. Ask: "Modernize this code to use current JavaScript (ES2022) best practices"
3. Or: "Convert this class component to a React functional component with hooks"
4. Review the changes and run tests

### Agent Mode for Large-Scale Modernization
- "Update all Promise chains in the `src/api` folder to use async/await"
- Agent Mode can do this across multiple files systematically

---

## 6.7 Generating Tests

### Unit Tests
**What they test:** Individual functions/methods in isolation

```
# How to ask:
Select the function → `/tests`
Or in chat: "Write unit tests for the `validatePassword()` function.
Cover: minimum 8 chars, requires uppercase, requires number, requires special char"
```

### Integration Tests
**What they test:** How multiple components work together

```
# How to ask:
"Write integration tests for the user registration flow:
POST /api/users → verify email → GET /api/users/{id}"
```

### Test Coverage Areas to Request
| Area | Prompt Pattern |
|------|---------------|
| Happy path | "Test the normal successful case" |
| Edge cases | "Identify and test edge cases" |
| Error cases | "Test all error conditions and exceptions" |
| Boundary values | "Test values at the boundaries (0, -1, max, max+1)" |
| Null/undefined | "Test null and undefined inputs" |
| Empty collections | "Test with empty arrays and empty strings" |

---

## 6.8 Identifying Edge Cases

### Copilot for Edge Case Discovery
- Ask: "What edge cases should I test for this function?"
- Copilot analyzes the function logic and suggests cases
- Useful for: boundary conditions, null inputs, empty states, overflow

### Example
```
# Function: divide(a, b)
# Copilot-identified edge cases:
# - b = 0 (division by zero)
# - a = 0 (zero numerator)
# - Very large numbers (overflow)
# - Negative numbers
# - Non-integer inputs
# - NaN inputs
```

---

## 6.9 Writing Assertions

### Copilot for Test Assertions
- Select test file and ask: "Add meaningful assertions to this test"
- Copilot suggests `expect()` statements that verify the right behavior
- Can generate assertions for: return values, state changes, side effects, thrown exceptions

```javascript
// Ask: "Write assertions to verify the sortUsers function works correctly"
expect(result).toHaveLength(3);
expect(result[0].lastName).toBe('Adams');
expect(result[result.length - 1].lastName).toBe('Williams');
expect(result).toEqual(expect.arrayContaining([expect.objectContaining({ active: true })]));
```

---

## 6.10 Security Improvements

### Security Issues Copilot Can Identify & Fix
| Vulnerability | How to Ask |
|--------------|-----------|
| SQL injection | "Check this query for SQL injection and fix it" |
| XSS | "Review this for XSS vulnerabilities" |
| Hardcoded secrets | "Find and remove hardcoded credentials" |
| Insecure dependencies | "Are any of these dependencies outdated or vulnerable?" |
| Missing input validation | "Add input validation to this API endpoint" |
| Insecure randomness | "Replace Math.random() with cryptographically secure random" |
| Missing authentication | "Add authentication check to this endpoint" |

> **Note:** Copilot can suggest improvements, but always use dedicated security tools (SAST, DAST) for formal security audits.

---

## 6.11 Performance Optimizations

### Performance Areas Copilot Addresses
| Area | Example Ask |
|------|------------|
| **Algorithm complexity** | "Optimize this from O(n²) to O(n log n)" |
| **Database queries** | "Optimize this query to avoid N+1 problem" |
| **Caching** | "Add caching to this expensive computation" |
| **Lazy loading** | "Convert this to lazy load data only when needed" |
| **Memory usage** | "Reduce memory allocation in this loop" |
| **Async operations** | "Run these independent API calls in parallel" |

---

## Exam Tips for Domain 6

> **Scenario-Based Questions — Key Answers:**
> - "Developer needs to understand unfamiliar code quickly" → `/explain` in Copilot Chat
> - "Generate tests for an existing function" → Select code → `/tests`
> - "Convert old callback code to modern style" → Ask Copilot to "modernize" or "convert to async/await"
> - "Find edge cases for a function" → Ask "What edge cases should I test?"
> - "Generate fake data for testing" → Ask Copilot Chat with specific format requirements
> - "Refactor across multiple files" → Use **Edit Mode** (not inline)
> - "Large-scale modernization" → Use **Agent Mode**
> - Copilot **suggests** security improvements; it does NOT audit or guarantee security
