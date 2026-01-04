---
description: "Review code for project guidelines compliance and bug detection"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Review Code Quality

Review code for adherence to project guidelines, bugs, and quality issues with high-precision confidence-based filtering.

**Review Scope:** "$ARGUMENTS" (defaults to unstaged changes from `git diff`)

## What This Command Does

Uses the `code-reviewer` agent to perform thorough code review:

### Project Guidelines Compliance
- Import patterns and framework conventions
- Language-specific style from CLAUDE.md
- Function declarations and error handling
- Logging, testing, and naming conventions

### Bug Detection
- Logic errors and null/undefined handling
- Race conditions and memory leaks
- Security vulnerabilities
- Performance problems

### Code Quality
- Code duplication
- Missing critical error handling
- Accessibility issues
- Inadequate test coverage

## Confidence Scoring

Each issue is rated 0-100:
- **91-100**: Critical bug or explicit CLAUDE.md violation
- **76-90**: Important issue requiring attention
- **51-75**: Valid but low-impact
- **26-50**: Minor nitpick
- **0-25**: Likely false positive

**Only issues with confidence ≥ 80 are reported.**

## How to Use

```
# Review unstaged changes (default)
/pr-review-toolkit:review-code

# Review specific files
/pr-review-toolkit:review-code src/api/handlers.ts

# Review staged changes
/pr-review-toolkit:review-code staged
```

## Output Format

Issues grouped by severity:

**Critical (90-100)**
- `file.ts:42` - [Issue] - [Fix suggestion]

**Important (80-89)**
- `file.ts:15` - [Issue] - [Fix suggestion]

If no high-confidence issues: "Code meets standards" with brief summary.

## When to Use

- After writing or modifying code
- Before committing changes
- Before creating a pull request
- As part of `/pr-review-toolkit:review-pr` workflow
