---
description: "Analyze conversation to find behaviors worth preventing with hooks"
allowed-tools: ["Read", "Grep", "Task"]
---

# Analyze Conversation for Hook Opportunities

Analyze the current conversation to identify problematic behaviors that could be prevented with hooks.

## What This Command Does

Uses the `conversation-analyzer` agent to find patterns worth preventing:

1. **Search for User Frustration Signals**
   - Explicit corrections: "Don't use X", "Stop doing Y", "Never..."
   - Frustrated reactions: "Why did you do X?", "That's not what I meant"
   - Corrections and reversions
   - Repeated issues

2. **Identify Tool Usage Patterns**
   - Which tool caused the issue (Bash, Edit, Write, etc.)
   - What specific action was problematic
   - When it happened (during what task)
   - Why it was problematic

3. **Create Regex Patterns**
   - Convert behaviors into matchable patterns
   - Bash commands: `rm\s+-rf`, `sudo\s+`, `chmod\s+777`
   - Code patterns: `console\.log\(`, `eval\(`
   - File paths: `\.env$`, `/node_modules/`

4. **Categorize Severity**
   - **High**: Dangerous commands, security issues, data loss
   - **Medium**: Style violations, wrong file types
   - **Low**: Preferences, non-critical patterns

## How to Use

```
/hookify:analyze-conversation
```

## Output Format

```
## Hookify Analysis Results

### Issue 1: Dangerous rm Commands
**Severity**: High
**Tool**: Bash
**Pattern**: `rm\s+-rf`
**Occurrences**: 3 times
**Context**: Used rm -rf without verification
**User Reaction**: "Please be more careful"

**Suggested Rule:**
- Name: warn-dangerous-rm
- Event: bash
- Pattern: rm\s+-rf
- Message: "Dangerous rm command. Verify path."

---

## Summary
Found {N} behaviors worth preventing:
- {N} high severity
- {N} medium severity
- {N} low severity
```

## When to Use

- After experiencing repeated frustrations in a session
- When you want to create hooks from real mistakes
- Before ending a session to capture lessons learned
- When setting up project-specific protections

## Next Steps

After analysis, you can:
1. Review the suggested rules
2. Use `/hookify:configure` to set up rules
3. Use `/hookify:list` to see active rules
