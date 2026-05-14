# Domain 4: Understand GitHub Copilot Data & Architecture

> **Weight: 10–15%** | ~10–15 questions

---

## 4.1 How GitHub Copilot Works — Architecture Overview

```
Developer (IDE)
    ↓ [Prompt/context]
GitHub Copilot Extension
    ↓ [Sends to proxy]
GitHub Proxy Server
    ↓ [Input filtering & forwards]
AI Model (LLM — multiple models supported: GPT-4o, Claude, Gemini, o1, etc.)
    ↓ [Raw completions]
GitHub Proxy Server
    ↓ [Post-processing & output filtering]
Developer (IDE)
    ↑ [Filtered suggestions displayed]
```

---

## 4.2 The Code Suggestion Lifecycle

### Step-by-Step Flow

| Step | What Happens |
|------|-------------|
| **1. Context Capture** | IDE gathers: current file, cursor position, open tabs, comments, language type |
| **2. Prompt Building** | Extension assembles a prompt from gathered context (prefix + suffix + metadata) |
| **3. Proxy Transmission** | Prompt is sent to GitHub's proxy servers over HTTPS |
| **4. Proxy Filtering (Input)** | Proxy checks for content policy violations before forwarding to LLM |
| **5. LLM Processing** | The AI model generates completions based on the prompt |
| **6. Post-Processing** | Proxy filters, ranks, and validates LLM output |
| **7. Duplication Check** | Suggestions are checked against public code (if enabled) |
| **8. Delivery** | Filtered suggestions returned to IDE extension |
| **9. Display** | Ghost text shown to developer |
| **10. Acceptance/Rejection** | Developer accepts (Tab) or dismisses (Esc) |

---

## 4.3 Prompt Building

### What Goes into a Prompt

| Context Element | Description |
|----------------|-------------|
| **Prefix** | Code BEFORE the cursor |
| **Suffix** | Code AFTER the cursor (fill-in-the-middle) |
| **File path & language** | Helps model understand file type and context |
| **Open tabs** | Other files open in the editor (similar files prioritized) |
| **Imports/declarations** | Function names, class names, imported libraries |
| **Comments** | Inline and block comments near cursor |
| **Chat history** | In chat mode, previous conversation context |
| **Instructions file** | Content of `.github/copilot-instructions.md` |

### Fill-in-the-Middle (FIM)
- Copilot uses both prefix AND suffix context
- Model predicts what should go in the MIDDLE
- More accurate than prefix-only generation

### Context Window Limits
- LLMs have a fixed context window (number of tokens)
- If codebase is too large, not all context fits
- Copilot prioritizes: current file → open tabs → related files
- Large files may be truncated — only the most relevant portion is sent

---

## 4.4 Proxy Filtering

### Input Filtering (Before LLM)
- Checks prompts for content policy violations
- Removes or flags: hate speech, explicit content, PII patterns
- Applies content exclusion rules (excluded files blocked here)
- Rate limiting applied per user/org

### Output Filtering (Post-Processing / After LLM)
- Filters LLM output before returning to developer
- **Duplication detection:** Checks if suggestion matches public code (>150 chars)
- **Security filtering:** Flags code patterns matching known vulnerabilities
- **Prompt injection prevention:** Strips attempts to manipulate Copilot via code comments
- **Toxic content filtering:** Removes offensive suggestions

---

## 4.5 Data Usage & Sharing

### What Data Is Sent to GitHub/Microsoft

| Data Type | Sent? | Notes |
|-----------|-------|-------|
| Code context (prompt) | Yes | Current file + open tabs (excluding excluded files) |
| Accepted suggestions | Depends on settings | Used for product improvement (can opt out) |
| Rejected suggestions | Depends on settings | Used for training improvement (can opt out) |
| Chat messages | Yes | Sent as part of the prompt |
| File contents of excluded files | No | Exclusions are respected |
| GitHub account info | Yes | For authentication and billing |

### Individual Users (Copilot Pro)
- By default, GitHub **may use prompts and suggestions** to improve Copilot
- Users can **opt out** in GitHub personal settings: Settings → Copilot → Allow GitHub to use my code snippets

### Organizations (Copilot Business/Enterprise)
- **By default:** Prompts and suggestions are NOT used for training
- Organizations get stronger data protection guarantees
- No code is stored beyond the immediate request processing

### Data Retention
| Scenario | Retention |
|----------|-----------|
| Individual (opted in) | May be retained for model improvement |
| Individual (opted out) | Discarded after request |
| Business/Enterprise org | Discarded after request (not retained) |
| Telemetry/usage data | Retained (anonymized) |

---

## 4.6 Data Sharing with Third Parties

- GitHub Copilot supports **multiple AI model providers** (OpenAI, Anthropic, Google, etc.)
- When a third-party model is used, prompts may flow through that provider's infrastructure
- Third-party model providers do NOT use GitHub Copilot data for training (per contractual agreements)
- MCP servers (external tools) receive only the data needed for that specific tool call
- For enterprise deployments, data residency options may be available to keep data within specific regions

---

## 4.7 Limitations of LLMs

| Limitation | Explanation |
|-----------|-------------|
| **Knowledge cutoff** | LLM training data has a date cutoff; doesn't know recent events/APIs |
| **Context window** | Can only process a limited amount of text at once |
| **Hallucination** | Generates plausible but incorrect output with false confidence |
| **Non-determinism** | Same input can produce different outputs |
| **No true reasoning** | Pattern matching, not actual logical reasoning |
| **Sensitivity to phrasing** | Small prompt changes can produce very different outputs |
| **Token limits** | Long conversations lose early context (rolling window) |
| **Bias** | Reflects biases in training data |
| **No memory (by default)** | Each request is stateless unless context is provided |

---

## 4.8 Limitations of GitHub Copilot Specifically

| Limitation | Detail |
|-----------|--------|
| **No internet access (by default)** | Can't look up docs or check Stack Overflow (unless MCP/tools used) |
| **Stale API knowledge** | May suggest deprecated methods or outdated syntax |
| **No execution context** | Doesn't know if your tests pass; only suggests, doesn't verify |
| **Context window constraints** | Large repos: not all files fit in context |
| **Not 100% accurate** | Suggestions are probabilistic, not guaranteed correct |
| **Language quality varies** | Better at popular languages (Python, JS, TypeScript) than niche ones |
| **May suggest insecure code** | Security filtering reduces but doesn't eliminate this |
| **IDE-specific features** | Not all features available in all IDEs |
| **Plan-based feature access** | Some features (Spaces, PR summaries) require specific plans |

---

## Exam Tips for Domain 4

> **Architecture Questions:**
> - The order is: IDE → Proxy (input filter) → LLM → Proxy (post-process) → IDE
> - Proxy does **both** input AND output filtering
> - Duplication detection happens in **post-processing** (after LLM)
> - Fill-in-the-Middle (FIM) uses BOTH prefix and suffix — not just what's before cursor
> 
> **Data Questions:**
> - Business/Enterprise: data is **NOT used for training** by default
> - Individual: opted in by default (can opt out)
> - Third-party model providers do NOT train on GitHub Copilot data (contractual)
> - Excluded files = NOT sent to Copilot for inline, chat, and code review — but exclusion does NOT apply to CLI, cloud agent, or Agent mode
>
> **Limitation Questions:**
> - "Knowledge cutoff" = outdated API/library knowledge
> - "Context window" = can't process entire large codebases at once
> - "Hallucination" = confident but wrong output
