# Domain 2: Use GitHub Copilot Features

> **Weight: 25–30%** | ~25–30 questions — Highest weight domain!

---

## 2.1 GitHub Copilot Plans

| Plan | Target | Premium Requests/mo | Key Notes |
|------|--------|---------------------|-----------|
| **Copilot Free** | Individual (free) | 50 | Limited completions & chat |
| **Copilot Pro** | Individual ($10/mo) | 300 | Unlimited base completions, chat, cloud agent |
| **Copilot Pro+** | Power users ($39/mo) | 1,500 | Full model access, highest request limits |
| **Copilot Business** | Organizations ($19/user/mo) | Varies | Org policy management, audit logs, centralized mgmt |
| **Copilot Enterprise** | Enterprises ($39/user/mo) | Varies | All Business features + advanced enterprise capabilities |

> **Note:** "Premium requests" are for premium AI models (e.g., GPT-4o, Claude Sonnet). Base model completions are unlimited on Pro and above. Features and availability vary by plan — org/enterprise plans add admin controls, audit logs, and organization-wide policies.
>
> **Billing change:** Starting June 1, 2026, GitHub is moving from request-based to usage-based billing.

---

## 2.2 Enabling Copilot in the IDE

### Supported IDEs (as of 2026)
- **VS Code** (primary, most features)
- **Visual Studio**
- **JetBrains IDEs** (IntelliJ, PyCharm, WebStorm, etc.)
- **Neovim**
- **Azure Data Studio**
- **Xcode** (via extension)
- **Eclipse** (via extension)

### Enabling Steps (VS Code)
1. Install the **GitHub Copilot** extension from the marketplace
2. Sign in with your GitHub account
3. Ensure you have an active Copilot subscription or free trial
4. Extension shows status in the bottom status bar (Copilot icon)

### IDE Status Indicators
| Icon State | Meaning |
|-----------|---------|
| Active (white/colored) | Copilot is enabled and working |
| Spinning | Copilot is fetching a suggestion |
| Warning/Yellow | Issue with authentication or subscription |
| Disabled (crossed) | Copilot is disabled for this file/repo |

---

## 2.3 Inline Suggestions (Code Completions)

**What it is:** Ghost text that appears as you type — Copilot predicts what you want to write next.

### Key Shortcuts (VS Code)

| Action | Windows/Linux | macOS |
|--------|--------------|-------|
| Accept suggestion | `Tab` | `Tab` |
| Dismiss suggestion | `Esc` | `Esc` |
| Next suggestion | `Alt + ]` | `Option + ]` |
| Previous suggestion | `Alt + [` | `Option + [` |
| Open all suggestions (panel) | `Ctrl + Enter` | `Ctrl + Enter` |
| Trigger inline suggestion | `Alt + \` | `Option + \` |
| Accept word by word | `Ctrl + →` | `Cmd + →` |

### How Copilot Generates Inline Suggestions
1. Captures current file content (prefix + suffix)
2. Captures open tabs as context
3. Captures cursor position
4. Sends prompt to model via proxy
5. Returns ghost text suggestion

### Best Practices for Better Suggestions
- Write descriptive function/variable names
- Add comments describing what you want
- Keep related files open as tabs (they become context)
- Write a function signature first, then let Copilot fill the body

---

## 2.4 Copilot Chat

### Chat Interfaces
| Interface | How to Access (VS Code) |
|-----------|------------------------|
| **Chat Panel** (sidebar) | Click Copilot icon in Activity Bar |
| **Inline Chat** | `Ctrl+I` (Windows/Linux) / `Cmd+I` (macOS) |
| **Quick Chat** | `Ctrl+Shift+Alt+L` (Windows/Linux) / `Shift+Option+Cmd+L` (macOS) |
| **Terminal Chat** | Click Copilot icon in the terminal panel |
| **GitHub.com Chat** | Available on github.com |

### Chat Participants (@ Operators)

> Type `@` in the chat box to see all available participants in your IDE — availability varies by IDE and plan.

| Participant | Scope | Example |
|-------------|-------|---------|
| `@workspace` | Entire project/repo (VS Code) | `@workspace explain the architecture` |
| `@vscode` | VS Code settings, extensions (VS Code only) | `@vscode how do I change theme` |
| `@terminal` | Terminal context (VS Code only) | `@terminal how do I list running processes` |
| `@github` | GitHub.com skills, web search, repo info | `@github #web what's new in Node.js 22` |

> `@github` is the confirmed cross-platform participant with GitHub-specific skills and web search (`#web`).

### Chat Slash Commands

> Type `/` in the chat prompt box to see all commands available in your specific IDE — the list **varies by IDE**.

| Command | What It Does | Availability |
|---------|-------------|-------------|
| `/explain` | Explain selected code or a concept | Widely available |
| `/fix` | Suggest a fix for selected code or error | Widely available |
| `/tests` | Generate unit tests for selected code | Widely available |
| `/doc` | Generate documentation/comments for code | Widely available |
| `/new` | Scaffold a new project or file | IDE-dependent |
| `/help` | Show available commands | Widely available |

> **Exam trap:** `/tests` generates tests; `/fix` suggests fixes. Don't confuse them.
> **Key rule:** Always type `/` to discover what's available — don't assume a command exists across all IDEs.

### Chat Variables (# Operators)

| Variable | What It Includes |
|----------|-----------------|
| `#file` | Reference a specific file |
| `#selection` | Currently selected code |
| `#editor` | Currently open editor content |
| `#terminalLastCommand` | Last terminal command and output |
| `#web` | Invoke web search (used with `@github`) |

> Type `#` in the chat prompt box to see all available variables in your IDE.

---

## 2.5 Plan Mode

**What it is:** A mode where Copilot plans changes BEFORE making them — shows you what it will do first.

- Introduced to give developers more control over agentic tasks
- Copilot analyzes the request, creates a plan, shows it for review
- Developer approves/modifies the plan before execution begins
- Prevents surprise edits to many files at once

**When to use:**
- Complex refactoring across multiple files
- Architectural changes
- Any time you want to preview changes before they happen

---

## 2.6 GitHub Copilot CLI

### What is GitHub Copilot CLI?
A **chat-like interface in the terminal** that brings AI assistance to the command line. It can autonomously create and modify files, execute commands, and help with a wide range of development tasks — all through natural language.

> **Important:** The old `gh copilot` extension (installed via `gh extension install github/gh-copilot`) has been **retired**. GitHub Copilot CLI is now a separate, standalone tool replacing it.

### How It Benefits Developers
- Get AI help without leaving the terminal
- Generate and explain shell commands in plain English
- Automate file creation, refactoring, and environment setup from the CLI
- Run multi-step agentic tasks directly in the terminal

### Key Capabilities

| Capability | Description |
|-----------|-------------|
| **Command assistance** | Suggests and explains shell commands using natural language |
| **Code work** | Bug fixes, feature implementation, refactoring, test creation |
| **Documentation** | Create and update project documentation |
| **Environment setup** | Run terminal commands to configure project environments |
| **Script generation** | Generate bash, Python, PowerShell scripts from descriptions |
| **File management** | Create, modify, and manage files via natural language |

### Using Copilot CLI Interactively
- Copilot CLI operates as a **conversational session** in the terminal
- You type natural language requests; Copilot responds with commands or actions
- It iterates: you can refine, ask follow-ups, or redirect mid-session

### CLI Slash Commands (In-session)
| Command | Purpose |
|---------|---------|
| `/feedback` | Report an issue or provide feedback |
| `/delegate` | Hand off the session to GitHub's server-side Copilot (not available with custom model providers) |

### Permissions Model
By default, Copilot CLI requests **approval before**:
- Accessing files outside the current directory
- Modifying files
- Executing potentially dangerous commands

You can grant broader permissions with flags:
- `--allow-tool` — allow a specific tool
- `--allow-all-tools` — allow all tools without prompting
- `/allow-all` — grant full permissions within the session

### Generate Scripts with Copilot CLI
- Describe what you want in plain English: "Write a script that monitors disk usage and alerts when over 80%"
- Copilot generates the complete script in your requested language

### Manage Files with Copilot CLI
- "Create a config file for ESLint with TypeScript support"
- "Rename all `.js` files in this directory to `.ts`"
- Copilot handles the file operations with approval checkpoints

---

## 2.7 Excluding Files from Copilot

### How to Configure Content Exclusions
Content exclusions are configured **only through GitHub Settings** — there is no `.copilotignore` file. This is configured at three levels:

| Level | Location |
|-------|----------|
| **Repository** | github.com → [Repo] → Settings → Copilot → Content exclusion |
| **Organization** | github.com → [Org] → Settings → Copilot → Content exclusion |
| **Enterprise** | Enterprise admin → AI controls → Copilot → Content exclusion |

- Glob patterns are used to specify which files/paths to exclude
- Changes take **up to 30 minutes** to propagate to IDEs
- IDEs can be manually reloaded to apply changes immediately

### What Content Exclusion Does
When a file is excluded, **all four of the following apply**:
1. **Copilot inline suggestions are not available** in the excluded file
2. **Excluded files do not inform suggestions** in other files
3. **Excluded files do not inform Copilot Chat responses**
4. **Excluded files are not reviewed** in Copilot Code Review

> **Critical caveat:** Content exclusion is **NOT supported** by GitHub Copilot CLI, Copilot cloud agent, or Agent mode in Copilot Chat in IDEs.

---

## Exam Tips for Domain 2

> **Must Know:**
> - `Tab` = accept | `Esc` = dismiss | `Alt+]` / `Alt+[` = cycle suggestions
> - `Ctrl+Enter` = open all suggestions in a panel
> - Inline Chat = `Ctrl+I` | Quick Chat = `Ctrl+Shift+Alt+L` (Windows/Linux)
> - `@workspace` = project-wide context; `@vscode` = IDE settings; `@github` = GitHub.com
> - `/explain`, `/fix`, `/tests`, `/doc` are the most tested slash commands
> - **Old `gh copilot` extension is RETIRED** — the new Copilot CLI is a standalone terminal chat tool
> - Plan Mode = plan FIRST, execute AFTER approval
> - Content exclusions: NO `.copilotignore` file — configured only via GitHub Settings
> - Exclusions do NOT apply to: CLI, cloud agent, or Agent mode
