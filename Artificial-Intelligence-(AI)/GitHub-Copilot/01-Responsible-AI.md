# Domain 1: Use GitHub Copilot Responsibly

> **Weight: 15–20%** | ~15–20 questions

---

## 1.1 Microsoft's 6 Responsible AI Principles

| Principle | What It Means |
|-----------|--------------|
| **Fairness** | AI systems should treat all people fairly |
| **Reliability and Safety** | AI systems should perform reliably and safely |
| **Privacy and Security** | AI systems should be secure and respect privacy |
| **Inclusiveness** | AI systems should empower everyone and engage people |
| **Transparency** | AI systems should be understandable |
| **Accountability** | People should be accountable for AI systems |

> **Remember the six principles:** Fairness → Reliability and Safety → Privacy and Security → Inclusiveness → Transparency → Accountability

---

## 1.2 Risks and Limitations of Generative AI

| Risk | Description |
|------|-------------|
| **Hallucination** | AI generates plausible-sounding but factually incorrect output |
| **Bias** | Training data biases reflected in suggestions (gender, race, cultural bias) |
| **Copyright / IP Issues** | Suggestions may resemble copyrighted code; duplication detection helps |
| **Security Vulnerabilities** | AI may suggest insecure code (SQL injection, hardcoded credentials, etc.) |
| **Outdated Information** | LLM knowledge has a cutoff date; newer APIs/libraries may be wrong |
| **Context Loss** | LLMs work within a context window; large codebases lose context |
| **Over-reliance** | Developers may accept suggestions without understanding them |
| **Non-determinism** | Same prompt can produce different results each time |

---

## 1.3 Potential Harms of AI Usage

### Harms to Individuals
- Privacy violations (exposing PII in prompts)
- Discrimination from biased outputs
- Dependence reducing skill development

### Harms to Organizations
- Security breaches from insecure AI-generated code
- Legal liability from copyright-infringing code
- Reputational damage from poor AI outputs

### Harms to Society
- Propagation of misinformation
- Reinforcing systemic biases at scale
- Displacement of human judgment in critical decisions

---

## 1.4 Mitigation Strategies

| Strategy | How It Helps |
|----------|-------------|
| **Human review** | Always review AI output before accepting |
| **Validation & testing** | Run tests on AI-generated code |
| **Duplication detection** | Copilot flags suggestions resembling public code |
| **Security scanning** | Use Copilot security warnings + external SAST tools |
| **Content exclusions** | Exclude sensitive files from Copilot's context |
| **Clear prompts** | Well-structured prompts reduce ambiguous/wrong output |
| **Stay informed** | Understand Copilot's limitations and data handling |
| **Least privilege** | Don't paste sensitive credentials/PII into prompts |

---

## 1.5 Validating AI Output

**Why validation is critical:**
- Copilot is a **suggestion tool**, not a replacement for developer judgment
- Suggestions are probabilistic — statistically likely, not guaranteed correct
- Code may compile but still be logically wrong or insecure

**How to validate:**
1. Read and understand every suggestion before accepting
2. Run unit tests and integration tests
3. Use static analysis / linting tools
4. Perform code review (human or Copilot Code Review)
5. Check for security issues with security scanners
6. Verify API usage against official documentation

---

## 1.6 Operating GitHub Copilot Responsibly

| Practice | Detail |
|----------|--------|
| **Don't share secrets** | Never include API keys, passwords, tokens in prompts |
| **Don't share PII** | Don't include personal identifiable information in code context |
| **Review before commit** | Never auto-commit AI suggestions without review |
| **Use content exclusions** | Configure content exclusions via GitHub Settings (repo/org/enterprise) for sensitive files |
| **Respect IP/licenses** | Check suggestion origins; be aware of license implications |
| **Enable security warnings** | Turn on Copilot's vulnerable code detection |
| **Provide feedback** | Use thumbs up/down to improve Copilot responses |

---

## Exam Tips for Domain 1

> **Tricky Exam Questions:**
> - "Which Microsoft responsible AI principle ensures AI doesn't discriminate?" → **Fairness**
> - "What is hallucination in AI?" → Confident but factually incorrect output (NOT a bug or error)
> - "What is the primary mitigation for AI bias?" → **Human review + diverse training data**
> - "Who is accountable when AI-generated code causes a security breach?" → **The developer/organization** (not the AI)
> - "What should you do before accepting a Copilot suggestion?" → **Review and validate it**
