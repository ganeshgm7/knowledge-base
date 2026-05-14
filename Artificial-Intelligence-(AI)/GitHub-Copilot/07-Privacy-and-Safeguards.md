# Domain 7: Configure Privacy, Content Exclusions & Safeguards

> **Weight: 10–15%** | ~10–15 questions

---

## 7.1 Privacy Settings Overview

### Where Privacy Settings Live

| Level | Location | Who Manages |
|-------|----------|-------------|
| **Individual** | github.com → Settings → Copilot | User |
| **Organization** | github.com → [Org] → Settings → Copilot | Org Admin |
| **Repository** | github.com → [Repo] → Settings → Copilot | Repo Admin |
| **IDE** | VS Code/JetBrains settings | User |

### Individual Privacy Settings (github.com → Settings → Copilot)

| Setting | Options | Default |
|---------|---------|---------|
| **Allow GitHub to use my code snippets for product improvements** | Enabled / Disabled | Enabled (for individuals) |
| **Suggestions matching public code** | Allow / Block | Allow |

> **Key:** Opting out means your prompts and suggestions are NOT retained after the session ends.

### Organization Privacy Controls

| Setting | Options |
|---------|---------|
| **Use prompts and suggestions for training** | Disabled for Business/Enterprise by default |
| **Allow members to opt in to data sharing** | Admin can control this |
| **Copilot telemetry** | Can be restricted org-wide |

---

## 7.2 Content Exclusions

### What Are Content Exclusions?
Rules that prevent specific files or repositories from being used as context by GitHub Copilot. Excluded content is:
- NOT sent to the AI model
- NOT used as context for suggestions
- NOT visible to Copilot in any form

### Why Use Content Exclusions?
- Protect secrets and credentials files (`.env`, `secrets.yaml`)
- Exclude proprietary/sensitive algorithms
- Prevent PII-containing files from being sent
- Comply with legal or regulatory requirements
- Exclude large auto-generated files (reduces noise)

### How to Configure Content Exclusions

Content exclusions are configured **only through GitHub Settings** — there is no `.copilotignore` file. Configuration is available at three levels:

**Repository Level**
- Go to: `github.com → [Repo] → Settings → Copilot → Content exclusion`
- Patterns apply only to that repository
- Example pattern format:
  ```
  - "/PATH/TO/DIRECTORY/OR/FILE"
  - "secrets.json"
  - "*.cfg"
  - "/scripts/**"
  ```

**Organization Level**
- Go to: `github.com → [Org] → Settings → Copilot → Content exclusion`
- Applies to seat holders across all repos in the org
- Can specify per-repo rules or use `"*"` for all repos:
  ```yaml
  "*":
    - "**/.env"
  octo-repo:
    - "/src/some-dir/kernel.rs"
  ```

**Enterprise Level**
- Enterprise owners: AI controls → Copilot → Content exclusion
- Enterprise rules apply to **all** Copilot users across the organization

> **Propagation:** Changes take **up to 30 minutes** to take effect. Reload your IDE window to apply changes immediately (VS Code: "Reload Window"; JetBrains/Visual Studio: close and reopen).

### Glob Pattern Examples

| Pattern | What It Excludes |
|---------|-----------------|
| `**/.env` | All `.env` files anywhere |
| `secrets/**` | Everything in the `secrets` folder |
| `**/*.pem` | All `.pem` certificate files |
| `config/production.*` | Production config files |
| `src/algorithms/proprietary/**` | Entire proprietary directory |
| `**/test-data/*.csv` | CSV files in any test-data folder |

> Patterns use **fnmatch notation** with case-insensitive matching.

### What Content Exclusion Does — Official Behavior
When a file is excluded, **all four of the following apply**:
1. **Copilot inline suggestions are not available** in the excluded file
2. **Excluded files do not inform suggestions** in other files
3. **Excluded files do not inform Copilot Chat responses**
4. **Excluded files are not reviewed** in Copilot Code Review

> **Critical limitation:** Content exclusion is **NOT supported** by:
> - GitHub Copilot CLI
> - Copilot cloud agent
> - Agent mode in Copilot Chat in IDEs

---

## 7.3 Editor (IDE) Settings

### VS Code Copilot Settings (settings.json)

| Setting | Purpose |
|---------|---------|
| `github.copilot.enable` | Enable/disable Copilot globally or per language |
| `github.copilot.inlineSuggest.enable` | Toggle inline suggestions |
| `github.copilot.chat.localeOverride` | Set chat language |
| `github.copilot.editor.enableAutoCompletions` | Auto or manual trigger |

### Disable Copilot for Specific Languages
```json
{
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": false,
    "yaml": false
  }
}
```

### Disable Copilot for a File (temporarily)
- Click the Copilot icon in the status bar
- Select "Disable for this file type" or "Disable globally"

---

## 7.4 Ownership of Copilot Outputs

### Key Points on IP Ownership
- GitHub's Terms of Service: you own the code you generate with Copilot
- GitHub and Microsoft do NOT claim ownership of generated suggestions
- **However:** If a suggestion closely matches public code, copyright of that original code still belongs to the original author

### Limitations on Output Ownership
- Copilot suggestions are NOT inherently licensed
- If a suggestion reproduces significant licensed code, the original license applies
- Use **duplication detection** to catch suggestions that resemble public code
- **Copilot does not grant a license** to underlying training data code

### Employer/Org Ownership
- Code written with Copilot at work is typically owned by the employer (per employment agreement)
- Organization's IP policies govern Copilot-generated code

---

## 7.5 Limitations of Copilot Outputs

| Limitation | What It Means |
|-----------|--------------|
| **Not legally reviewed** | Suggestions may have license/IP issues |
| **Not security-audited** | May contain vulnerabilities |
| **Not always correct** | Must be validated by the developer |
| **Not complete** | May produce partial or stub implementations |
| **Not optimized by default** | May work but not be performant |
| **Not accessible by default** | May not follow accessibility best practices |
| **Context-dependent quality** | Poor context = poor suggestions |

---

## 7.6 Duplication Detection

### What It Is
- Copilot checks code suggestions against public code on GitHub
- Flags suggestions that closely match public code to avoid accidentally reproducing copyrighted code
- Applies to inline code completions (not to chat responses)

### How to Enable/Configure
- **Organization level:** Settings → Copilot → "Suggestions matching public code" → Block
- **Individual level:** github.com → Settings → Copilot → toggle

### Two Modes

| Mode | Behavior |
|------|---------|
| **Allow** (default for individuals) | Suggestion shown even if it matches public code |
| **Block** | Suggestion suppressed if it matches public code |

### What "Matching Public Code" Means
- Algorithm compares the suggestion to GitHub's indexed public code
- If a suggestion closely matches indexed public code → flagged or suppressed (depending on mode)
- Does NOT check private repositories

---

## 7.7 Security Warnings

### Copilot Security Filtering
- Copilot has built-in filters to detect and suppress suggestions containing:
  - Known insecure code patterns (OWASP Top 10)
  - Hardcoded credentials or secrets
  - SQL injection patterns
  - Shell injection patterns
  - Known CVE-related code patterns

### Enabling Security Warnings (IDE)
- Warnings are shown inline when Copilot detects a security concern
- VS Code: Copilot shows a warning icon on the suggestion
- Can be configured in IDE settings

### What Security Warnings Look Like
- Yellow warning icon on the inline suggestion
- Notification in the Copilot Chat explaining the risk
- Suggestion may still be shown but flagged (developer decides)

### Copilot's Security Limitations
- Does NOT guarantee code is secure
- Not a replacement for proper security scanning tools
- SAST tools (Semgrep, CodeQL) should still be used
- Copilot is one layer of defense, not the only layer

---

## 7.8 Troubleshooting

### Troubleshooting Missing or Incorrect Suggestions

| Problem | Possible Cause | Fix |
|---------|---------------|-----|
| No suggestions appearing | Copilot disabled for file type | Check IDE settings, re-enable |
| No suggestions appearing | Auth issue | Sign out and back in |
| No suggestions appearing | Network/proxy issue | Check network connectivity |
| No suggestions appearing | File is excluded | Check content exclusion settings |
| Suggestions are irrelevant | Poor context | Add comments, open relevant files |
| Suggestions are outdated | LLM knowledge cutoff | Provide the API/pattern in a comment |
| Suggestions stop mid-file | Context window exceeded | Break into smaller chunks |
| Wrong language suggestions | Wrong language detected | Add file extension or set language in IDE |

### Troubleshooting Content Exclusion Issues

| Problem | Possible Cause | Fix |
|---------|---------------|-----|
| Excluded file still gets suggestions | Exclusion not saved/applied | Verify pattern syntax; check org vs repo level |
| Exclusion not working in IDE | Cache issue | Reload IDE window |
| Exclusion works in IDE but not github.com | Web interface may have different settings | Check both levels |
| Glob pattern not matching | Wrong syntax | Test glob pattern; use `**` for recursive matching |
| Team members still see suggestions | Exclusion not propagated | Check org-level settings (may take time to propagate) |

### Checking Copilot Status in VS Code
1. Look at the Copilot icon in the bottom status bar
2. Click it to see status details
3. Yellow = warning (check auth or exclusions)
4. Gray/Off = disabled

### Verifying Content Exclusion is Active
- When editing an excluded file, Copilot status bar icon changes
- A notification may appear: "Copilot suggestions are disabled for this file"
- No ghost text will appear when typing

---

## 7.9 Quick Reference: Privacy Config Checklist

| Task | Where to Configure |
|------|-------------------|
| Opt out of data for training (individual) | github.com → Settings → Copilot |
| Opt out org-wide from training data | Org Settings → Copilot → Policies |
| Block suggestions matching public code (org) | Org Settings → Copilot → Policies |
| Exclude files (enterprise-wide) | Enterprise Admin → AI controls → Copilot → Content Exclusion |
| Exclude files (org-wide) | Org Settings → Copilot → Content Exclusion |
| Exclude files (repo-specific) | Repo Settings → Copilot → Content Exclusion |
| Disable Copilot per language (IDE) | VS Code settings.json |
| View audit events | Org Settings → Audit Log → filter "Copilot" |

---

## Exam Tips for Domain 7

> **Must Know:**
> - **No `.copilotignore` file** — content exclusions are configured only in GitHub Settings (repo/org/enterprise)
> - Content exclusion affects: inline suggestions, context for other files, Chat responses, Code Review — all four
> - **Content exclusion does NOT apply to:** CLI, cloud agent, or Agent mode
> - Exclusion changes take **up to 30 minutes** to propagate; reload IDE to apply immediately
> - Business/Enterprise: data NOT used for training **by default**
> - Individual (Free/Pro): opted IN to data sharing by default; must manually opt out
> - Org-level exclusions apply to seat holders; Enterprise-level applies to all users
> - Ownership of output: **you own it**, but original licensed code's license still applies
> - Security warnings flag issues — they are NOT a guarantee of security
> - Troubleshooting missing suggestions: check auth → file exclusion → IDE settings → network
