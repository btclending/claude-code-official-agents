---
description: "Review code for bugs, security issues, and project guideline compliance"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task", "TodoWrite"]
---

# Review Code Quality

Review code for bugs, logic errors, security vulnerabilities, and adherence to project conventions using confidence-based filtering.

**Review Scope:** "$ARGUMENTS" (defaults to unstaged changes from `git diff`)

## What This Command Does

Uses the `code-reviewer` agent to perform high-precision code review:

1. **Project Guidelines Compliance**
   - Import patterns and framework conventions
   - Language-specific style requirements
   - Function declarations and error handling
   - Logging, testing, and naming conventions

2. **Bug Detection**
   - Logic errors and null/undefined handling
   - Race conditions and memory leaks
   - Security vulnerabilities
   - Performance problems

3. **Code Quality**
   - Code duplication
   - Missing critical error handling
   - Accessibility issues
   - Inadequate test coverage

## Confidence Scoring

Issues are rated 0-100:
- **0-25**: Likely false positive
- **26-50**: Minor nitpick
- **51-75**: Valid but low-impact
- **76-90**: Important issue
- **91-100**: Critical bug or CLAUDE.md violation

**Only issues with confidence ≥ 80 are reported.**

## How to Use

```
# Review unstaged changes (default)
/feature-dev:review-code

# Review specific files
/feature-dev:review-code src/components/Button.tsx

# Review a directory
/feature-dev:review-code src/api/

# Review staged changes
/feature-dev:review-code staged
```

## Output Format

For each high-confidence issue:
- Clear description with confidence score
- File path and line number
- Specific project guideline or bug explanation
- Concrete fix suggestion

Issues grouped by severity (Critical: 90-100, Important: 80-89).

## When to Use

- After writing new code
- Before committing changes
- Before creating a pull request
- When reviewing others' code
- After refactoring
