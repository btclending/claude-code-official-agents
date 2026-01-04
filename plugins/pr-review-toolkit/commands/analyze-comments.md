---
description: "Analyze code comments for accuracy, completeness, and long-term maintainability"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Analyze Code Comments

Review code comments for accuracy, completeness, and long-term maintainability to prevent comment rot and technical debt.

**Scope:** "$ARGUMENTS" (defaults to changed files)

## What This Command Does

Uses the `comment-analyzer` agent to analyze comments:

### 1. Verify Factual Accuracy
- Function signatures match documentation
- Described behavior aligns with code
- Referenced types/functions exist
- Edge cases mentioned are handled
- Performance claims are accurate

### 2. Assess Completeness
- Critical assumptions documented
- Non-obvious side effects mentioned
- Important errors described
- Complex algorithms explained
- Business logic rationale captured

### 3. Evaluate Long-term Value
- Flag comments that restate obvious code
- Prefer "why" over "what" explanations
- Identify comments likely to become outdated
- Write for least experienced maintainer

### 4. Identify Misleading Elements
- Ambiguous language
- Outdated references
- Invalid assumptions
- Incorrect examples
- Stale TODOs/FIXMEs

## How to Use

```
# Analyze comments in changed files
/pr-review-toolkit:analyze-comments

# Analyze specific files
/pr-review-toolkit:analyze-comments src/auth/login.ts

# Analyze a module
/pr-review-toolkit:analyze-comments src/database/
```

## Output Format

**Summary**: Overview of findings

**Critical Issues**: Factually incorrect or misleading
- Location: [file:line]
- Issue: [problem]
- Suggestion: [fix]

**Improvement Opportunities**: Could be enhanced
- Location: [file:line]
- Current: [what's lacking]
- Suggestion: [improvement]

**Recommended Removals**: Add no value
- Location: [file:line]
- Rationale: [why remove]

**Positive Findings**: Well-written examples

## When to Use

- After adding documentation
- Before finalizing a PR
- When reviewing existing comments
- After generating docstrings
- To prevent comment rot
