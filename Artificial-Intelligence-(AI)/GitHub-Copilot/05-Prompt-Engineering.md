# Domain 5: Apply Prompt Engineering & Context Crafting

> **Weight: 10–15%** | ~10–15 questions

---

## 5.1 What is Prompt Engineering?

**Prompt engineering** is the practice of designing inputs (prompts) to AI models to get better, more accurate, and more useful outputs.

> In the context of GitHub Copilot: it's how you write comments, questions, and instructions to guide Copilot toward the output you want.

---

## 5.2 Prompt Structure

### Anatomy of a Good Prompt

```
[Role / Persona]       → Who Copilot should act as
[Context]              → Background information about the task
[Task / Instruction]   → What you want Copilot to do
[Format / Constraints] → How the output should look
[Examples]             → Sample input/output (for few-shot)
```

### Example: Weak vs Strong Prompt

| Weak Prompt | Strong Prompt |
|-------------|--------------|
| "write a function" | "Write a TypeScript function that takes an array of User objects and returns only active users, sorted by lastName ascending. Use functional programming style." |
| "fix this" | "This function throws a TypeError when the input array is empty. Fix it to return an empty array in that case." |
| "add tests" | "Write Jest unit tests for the `calculateDiscount()` function. Cover: 0% discount, 50% discount, negative percentage (should throw), and null input (should throw)." |

---

## 5.3 How Copilot Determines Context

### Automatic Context Sources (No input needed)
1. **Current file** — everything before and after the cursor
2. **Open editor tabs** — related files you have open
3. **Language type** — detected from file extension
4. **Imports and dependencies** — libraries in scope
5. **File path** — helps infer project structure
6. **Comments** — in-line comments act as instructions

### Manual Context Sources (You provide these)
1. **Chat messages** — what you type in Copilot Chat
2. **`#file` references** — explicitly link files in chat
3. **`#selection`** — reference your current selection
4. **`@workspace`** — tell Copilot to use the whole project
5. **Instructions files** — `.github/copilot-instructions.md`
6. **Prompt files** — reusable prompt templates

### Context Priority (when context window is full)
1. Current file (highest priority)
2. Open tabs (similar/related files)
3. Recently accessed files
4. Instructions file
5. Rest of workspace (lowest priority)

---

## 5.4 Zero-Shot Prompting

**Definition:** Ask the model to complete a task WITHOUT providing any examples.

```
# Zero-shot example (no examples given):
# Write a function to validate an email address

def validate_email(email: str) -> bool:
    # Copilot generates the function from description alone
```

**When to use:**
- Simple, well-defined tasks
- Common programming patterns Copilot has seen many times
- When you trust Copilot's default interpretation

**Limitation:**
- Copilot may not understand your specific requirements
- Output style may not match your codebase conventions

---

## 5.5 Few-Shot Prompting

**Definition:** Provide 1–3 EXAMPLES of input/output in your prompt so Copilot understands the pattern.

```python
# Few-shot example:
# Format user names as "Last, First"
# John Smith -> Smith, John
# Jane Doe -> Doe, Jane
# Robert Johnson -> Johnson, Robert
# Now format: Michael Williams ->
```

**When to use:**
- Custom formatting or conventions
- Domain-specific patterns not in training data
- When zero-shot gives wrong results
- Establishing a consistent style

**Advantage:** Copilot learns the pattern from examples, even if it's unusual.

---

## 5.6 Prompt Crafting Best Practices

### The 4 S's of Good Prompts
| Principle | Description |
|-----------|-------------|
| **Specific** | Be precise about what you want; avoid vague requests |
| **Short** | Keep context focused; don't overwhelm with noise |
| **Single** | One task per prompt; avoid compound requests |
| **Sequential** | Break complex tasks into steps |

### Practical Best Practices

| Practice | Example |
|----------|---------|
| **Describe intent, not just output** | "Parse the CSV and validate each row" not "write a CSV parser" |
| **Specify language/framework** | "In React with TypeScript using hooks" |
| **Define input/output types** | "Takes string[], returns Record<string, number>" |
| **State constraints** | "Without using any external libraries", "max 20 lines" |
| **Reference existing code** | "Following the pattern used in `UserService`" |
| **Use inline comments** | Comments immediately above/next to cursor are highest priority |
| **Name things well** | `getUsersByActiveStatus()` prompts better than `getUsers()` |

### What to Avoid
- Vague requests: "make it better", "fix this", "clean up"
- Multiple unrelated tasks in one prompt
- Irrelevant context that dilutes the signal
- Contradictory instructions

---

## 5.7 Prompt Engineering Principles

### Principle 1: Clarity over Brevity
- A longer, clear prompt beats a short, ambiguous one
- Copilot generates more accurately with more context

### Principle 2: Iterative Refinement
- Start with a rough prompt, then refine based on output
- Use follow-up chat messages to correct and adjust

### Principle 3: Context is King
- The more relevant context Copilot has, the better
- Open related files as tabs; reference files in chat

### Principle 4: Leverage Comments as Prompts
```python
# Function to calculate compound interest
# Parameters: principal (float), rate (float as percentage), years (int)
# Returns: float rounded to 2 decimal places
# Formula: P * (1 + r/100)^n
def calculate_compound_interest(principal, rate, years):
    # Copilot fills this in based on the comment above
```

### Principle 5: Test Driven Prompting
- Write test cases first, then ask Copilot to implement to pass them
- Copilot works well in TDD mode

---

## 5.8 Prompt Process Flow

```
Developer Input
    ↓
Context Assembly (IDE gathers files, tabs, selection)
    ↓
Prompt Construction (prefix + suffix + context + instructions)
    ↓
Proxy Transmission
    ↓
LLM Inference (token prediction)
    ↓
Post-Processing (filtering, dedup check)
    ↓
Suggestion Returned
    ↓
Developer Accepts / Modifies / Rejects
    ↓
(If in chat: Chat history updated for next turn)
```

---

## 5.9 Chat History Usage

### How Chat History Helps
- Each message in a chat session builds on previous messages
- Copilot remembers what was asked and answered in the session
- Enables multi-turn refinement: "Now make it handle null values too"

### Chat History Limitations
- Chat history is session-specific (cleared when chat is cleared)
- Not persisted across VS Code restarts by default
- Context window limits apply — very long conversations lose early context

### Starting a Fresh Context
- To start a new, unrelated task in the same session, begin a new conversation in the chat panel
- This prevents old context from polluting new requests
- Available slash commands vary by IDE — type `/` to see what's available in yours

---

## 5.10 Prompt File Reuse

### What Are Prompt Files?
- Markdown files that contain reusable prompt templates
- Saved in the repo for team-wide consistency
- Referenced in chat: `#file:path/to/prompt-template.md`

### Use Cases
- Standard prompts for generating test files
- Code review checklists as prompts
- Documentation generation templates
- Security audit prompt templates

### Benefits
- **Consistency** across team members
- **Reusability** — write once, use many times
- **Version controlled** — changes tracked in git
- **Shareable** — anyone on the team can use the same prompt

---

## Exam Tips for Domain 5

> **Key Distinctions:**
> - **Zero-shot** = no examples, just instruction
> - **Few-shot** = 1–3 examples + instruction
> - **Prompt file** = saved reusable prompt template (referenced with `#file`)
> - **Instructions file** = always-on context for all Copilot interactions
> - Context priority: current file > open tabs > workspace
> - Chat history = same session only; start a new conversation to reset context
> - Good prompts: Specific, Short, Single task, Sequential steps
> - Comments immediately above cursor = highest priority context for inline suggestions
