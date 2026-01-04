---
description: "Hunt for silent failures, inadequate error handling, and hidden errors"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Hunt Silent Failures

Identify silent failures, inadequate error handling, and inappropriate fallback behavior in code changes.

**Scope:** "$ARGUMENTS" (defaults to PR changes)

## What This Command Does

Uses the `silent-failure-hunter` agent with zero tolerance for hidden errors:

### Core Principles
1. **Silent failures are unacceptable**
2. **Users deserve actionable feedback**
3. **Fallbacks must be explicit and justified**
4. **Catch blocks must be specific**
5. **Mocks belong only in tests**

### Identifies Error Handling Code
- Try-catch/try-except blocks
- Error callbacks and handlers
- Conditional error branches
- Fallback logic and defaults
- Optional chaining that might hide errors

### Scrutinizes Each Handler

**Logging Quality**
- Appropriate severity used
- Sufficient context included
- Error IDs for tracking

**User Feedback**
- Clear, actionable messages
- Explains what went wrong
- Provides next steps

**Catch Block Specificity**
- Only catches expected errors
- Doesn't suppress unrelated errors

**Fallback Behavior**
- Explicitly requested by user
- Doesn't mask problems
- Not a mock in production

## How to Use

```
# Hunt in PR changes
/pr-review-toolkit:hunt-failures

# Hunt in specific files
/pr-review-toolkit:hunt-failures src/api/client.ts

# Hunt in error handling code
/pr-review-toolkit:hunt-failures src/handlers/
```

## Output Format

For each issue:

1. **Location**: File:line
2. **Severity**: CRITICAL/HIGH/MEDIUM
3. **Issue**: What's wrong
4. **Hidden Errors**: What could be suppressed
5. **User Impact**: How it affects debugging
6. **Recommendation**: How to fix
7. **Example**: Corrected code

## Severity Levels

- **CRITICAL**: Silent failure, broad catch
- **HIGH**: Poor error message, unjustified fallback
- **MEDIUM**: Missing context, could be more specific

## When to Use

- After implementing error handling
- When reviewing PRs with catch blocks
- After refactoring error handling
- Before deploying critical code
