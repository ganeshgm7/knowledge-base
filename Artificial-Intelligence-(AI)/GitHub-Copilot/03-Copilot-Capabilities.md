# Domain 3: GitHub Copilot Features & Capabilities

> **Weight: 25–30%** | ~25–30 questions — Highest weight domain (tied with Domain 2)!

---

## 3.1 Copilot Modes: Agent Mode vs Edit Mode vs Plan Mode

| Mode | What It Does | Scope | User Control |
|------|-------------|-------|-------------|
| **Inline Suggestions** | Real-time code completions as you type | Current cursor position | Accept/Dismiss |
| **Edit Mode** | Make targeted edits across multiple files | Multi-file, specified scope | Review diffs before applying |
| **Agent Mode** | Autonomous end-to-end task completion with tool use | Whole repo, can run commands | Iterative, human-in-the-loop |
| **Plan Mode** | Creates a plan of action before executing | Multi-file | Approve plan before execution |

### Agent Mode (Deep Dive)
- **Most autonomous** mode — Copilot acts like an AI developer agent
- Can: read files, write files, run terminal commands, search the web, call tools
- Uses **sub-agents** and **tool calls** to accomplish complex tasks
- Requires explicit **approval** for potentially destructive actions (file deletion, etc.)
- Maintains an **Agent Session** — context and state across multiple steps
- Best for: "Implement a full REST API endpoint" or "Fix all failing tests"

### Edit Mode (Deep Dive)
- Designed for **targeted multi-file edits**
- You specify the files to edit and the change to make
- Copilot shows a **diff preview** before applying
- More controlled than Agent Mode, more powerful than inline
- Best for: "Rename this function across all files" or "Add error handling to these 3 files"

### Plan Mode (Deep Dive)
- Copilot first **describes what it will do** (the plan)
- You review the plan and can modify/reject before execution
- Execution only begins after explicit approval
- Prevents surprise mass edits
- Best for complex, high-risk changes where you want to preview impact

---

## 3.2 Agent Sessions & Sub-Agents

### Agent Sessions
- A persistent context maintained across multiple Copilot Agent interactions
- State (files read, commands run, decisions made) is preserved across steps
- Allows complex multi-step tasks without losing context
- Session ends when task completes or user terminates

### Sub-Agents
- In complex tasks, Copilot Agent may **delegate** to sub-agents
- Sub-agents handle specific sub-tasks (e.g., one for testing, one for docs)
- **Optimized context usage** — each sub-agent gets only the context it needs
- Prevents context window overflow on large tasks
- Sub-agents report back to the orchestrating agent

> **Exam distinction:** Sub-agents are about **delegation for context optimization**, not just parallelism.

---

## 3.3 MCP — Model Context Protocol

### What is MCP?
- **Model Context Protocol** — an open standard for connecting AI models to external tools and data sources
- Allows Copilot to interact with external systems: databases, APIs, browsers, file systems
- Think of it as a plugin system for AI agents

### MCP in GitHub Copilot
- Copilot Agent can use MCP servers to access external tools
- Examples: fetch a webpage, query a database, call an API, search files
- Configured in VS Code settings or at the organization level
- Extends what Agent Mode can do beyond the local codebase

### MCP Architecture
```
Copilot Agent
    ↕
MCP Client (in Copilot)
    ↕
MCP Server (tool provider)
    ↕
External Tool/Data Source (DB, API, browser, etc.)
```

---

## 3.4 Copilot Code Review

### What It Is
- AI-powered code review that can automatically review pull requests
- Provides inline comments on PRs with suggestions and explanations
- Can be triggered manually or set up as an automatic review policy

### How It Works
1. Developer opens a PR or requests review
2. Copilot analyzes the diff (changed code)
3. Generates inline review comments with explanations
4. Suggests specific code improvements

### Enabling Code Review
- **Repository level:** Settings → Copilot → Code Review
- **Organization level:** Org Settings → Copilot → Code Review Policies
- Can require Copilot review before merge (policy enforcement)

### Custom Review Standards
- Defined via **instructions files** (`.github/copilot-instructions.md`)
- Can specify coding standards, patterns to flag, security requirements
- Review adapts to organization-specific conventions

---

## 3.5 Instructions Files

### What They Are
- Markdown files that give Copilot persistent context about your project
- Copilot reads these automatically when generating suggestions/reviews

### Key Instructions Files

| File | Purpose |
|------|---------|
| `.github/copilot-instructions.md` | Repo-wide instructions — automatically applied to all Copilot interactions in that repo |
| `.github/instructions/NAME.instructions.md` | Path-specific instructions — applied to files matching the `applyTo` glob pattern in frontmatter |
| Personal instructions (user settings) | Set in GitHub settings; apply to all repos for that user |

### Priority Order (when multiple instruction types apply)
**Personal instructions → Repository instructions → Organization instructions**

### Path-Specific Instructions File Format
```markdown
---
applyTo: "src/components/**"
---
All React components must use functional components with hooks.
Never use class components.
```

> **Note:** Path-specific instructions are currently only supported for **Copilot cloud agent** and **Copilot Code Review** on GitHub.com.

### What to Put in Instructions Files
- Coding style guidelines ("We use tabs not spaces")
- Framework conventions ("We use Redux for state management")
- Security requirements ("Never suggest eval()")
- Test patterns ("All tests use Jest with React Testing Library")
- Architectural decisions ("Services must be stateless")

### Prompt File Reuse
- Save commonly used prompt patterns as files
- Reference them in chat with `#file:path/to/prompt.md`
- Ensures consistent prompting across the team
- Avoids repeating the same context in every chat session

---

## 3.6 Copilot Spaces

### What It Is
- Turns Copilot into a **project expert** by giving it a shared source of truth
- Lets you attach context from docs and repositories so Copilot always has the right background
- A persistent, shareable context layer for AI interactions on a project or team

### Key Features
- Add documentation, files, and repository content as context
- Copilot answers are informed by the sources you include in the Space
- Shared across team members — everyone gets the same grounded context
- Reduces repeated prompt setup; context persists across sessions

> Copilot Spaces is available across plans — check current GitHub documentation for the latest plan availability, as it continues to expand.

---

## 3.7 Copilot Spark (GitHub Spark)

### What It Is
- A feature to **build and deploy intelligent apps** using natural language
- Create full web applications from a description without manually writing all the code
- Available on **Copilot Pro+** plan ($39/month)

### Who It's For
- Developers and non-developers alike who want to rapidly prototype apps
- Anyone who wants to go from an idea to a deployed app quickly
- Accelerates the idea-to-prototype pipeline

### How It Works
1. Describe what you want to build in natural language
2. Copilot Spark generates the application
3. Iterate using natural language instructions to refine it
4. Deploy directly from Spark

---

## 3.8 Pull Request Summaries

### What It Is
- Copilot generates an AI-powered summary of what a PR changes — **only when a user manually requests it**
- Summaries are NOT automatically generated; they are triggered on demand

### What It Generates
- A prose overview of the changes
- A bulleted list of key changes, linked to the specific lines of code
- Helps reviewers understand the scope and intent of the PR quickly

### How to Trigger a PR Summary
Three locations where you can request a summary:
1. When **creating** a new PR — in the description editor
2. When **editing** an existing PR's opening comment
3. In a **comment** on the PR's main timeline

Click the Copilot icon in the description field to generate the summary.

### Important Limitations
- Files with more than **400 combined additions and deletions** are excluded from the summary
- PRs with **30+ files** may experience slower processing
- Only **English** is supported
- Processing typically takes ~40 seconds (can take up to a couple of minutes)
- Risk of hallucination — summaries may contain inaccuracies; always verify

---

## 3.9 Copilot Chat — Limits, Feedback & Options

### Chat Limits (Premium Requests per Month)
| Plan | Premium Requests/mo | Notes |
|------|---------------------|-------|
| Free | 50 | Limited chat and completions |
| Pro | 300 | Unlimited base model completions |
| Pro+ | 1,500 | Full model access |
| Business | Varies | Centrally managed |
| Enterprise | Varies | Enterprise-grade controls |

> "Premium requests" are used when accessing premium AI models (GPT-4o, Claude Sonnet, Gemini, o1, etc.) in chat. Base model completions are unlimited on Pro and above. An **"Auto"** option selects the best available model and helps reduce rate limiting.

### Chat Feedback Options
- **Thumbs Up** — response was helpful
- **Thumbs Down** — response was not helpful (can provide a reason)
- **Copy** — copy response to clipboard
- **Insert at cursor** — insert code directly into the editor
- **Create new file** — create a file with the generated content

### Chat Model Selection
- Users can switch between AI models in chat (availability varies by plan and client)
- An **"Auto"** setting selects the best model based on availability and to help reduce rate limiting
- Available models vary by IDE client (VS Code, Visual Studio, JetBrains, Eclipse, Xcode, GitHub.com)

---

## 3.10 Organization-Wide Settings & Policies

### Accessing Org Settings
`github.com → [Org] → Settings → Copilot`

### Key Policy Controls

| Policy | Options |
|--------|---------|
| **Enable/Disable Copilot** | For all members, selected teams, no one |
| **Allow/Block suggestions matching public code** | Enabled/Disabled (duplication detection) |
| **Content exclusions** | Specify files/repos to exclude |
| **Editor availability** | Control which IDEs can use Copilot |
| **GitHub.com features** | Enable/disable Copilot on github.com |
| **Copilot Chat** | Enable/disable in IDE and github.com |
| **Copilot Code Review** | Set as required/optional review |

### Managing Feature Availability Across IDEs
- Org admins can restrict Copilot to specific IDEs
- Can enable/disable features per IDE type
- Settings cascade: Org → Repo → User

### Audit Log Events
| Event | What It Logs |
|-------|-------------|
| `copilot.enable` | User enables Copilot |
| `copilot.disable` | User disables Copilot |
| `copilot.settings_change` | Settings modified |
| `business.set_member_copilot_seats` | Seat assigned |
| Content exclusion events | When exclusions are added/removed |

**Where to find:** `github.com → [Org] → Settings → Audit Log`  
**Filter by:** Select "Copilot" in the action filter

### Managing Subscriptions via REST API
- GitHub provides REST API endpoints to manage Copilot seats
- Useful for automation and large organizations

| Endpoint | Purpose |
|----------|---------|
| `GET /orgs/{org}/copilot/billing` | Get billing details |
| `GET /orgs/{org}/copilot/billing/seats` | List assigned seats |
| `POST /orgs/{org}/copilot/billing/selected_users` | Add users to Copilot |
| `DELETE /orgs/{org}/copilot/billing/selected_users` | Remove users |
| `GET /orgs/{org}/copilot/metrics` | Usage metrics |

---

## Exam Tips for Domain 3

> **Key Distinctions:**
> - **Agent Mode** = autonomous multi-step, can run commands
> - **Edit Mode** = targeted multi-file edits, shows diff first
> - **Plan Mode** = shows plan first, waits for approval
> - **Sub-agents** = delegation for **context optimization** (not just speed)
> - **MCP** = protocol that lets Copilot connect to external tools/data
> - **Spaces** = shared project context/sources of truth for Copilot interactions; check current docs for plan availability
> - **Spark** = build and deploy apps using natural language; available on **Pro+** plan
> - **Instructions files** = `.github/copilot-instructions.md` (memorize this path!)
> - Audit logs are in **Organization Settings** → Audit Log
> - REST API can manage **seats/subscriptions** programmatically
