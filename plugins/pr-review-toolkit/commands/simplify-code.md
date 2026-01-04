---
description: "Simplify code for clarity and maintainability while preserving functionality"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Edit", "Task"]
---

# Simplify Code

Simplify recently modified code for clarity, consistency, and maintainability while preserving exact functionality.

**Scope:** "$ARGUMENTS" (defaults to recent modifications)

## What This Command Does

Uses the `code-simplifier` agent to enhance code:

### 1. Preserve Functionality
- Never changes what code does
- All original features remain intact
- Only improves how it's written

### 2. Apply Project Standards
- ES modules with proper imports
- Prefer `function` keyword over arrows
- Explicit return type annotations
- Proper React component patterns
- Consistent naming conventions

### 3. Enhance Clarity
- Reduce unnecessary complexity
- Eliminate redundant abstractions
- Improve variable and function names
- Remove obvious comments
- **Avoid nested ternaries** - prefer if/else or switch
- Choose clarity over brevity

### 4. Maintain Balance
Avoids over-simplification that could:
- Reduce maintainability
- Create overly clever solutions
- Combine too many concerns
- Prioritize fewer lines over readability

## How to Use

```
# Simplify recent changes (default)
/pr-review-toolkit:simplify-code

# Simplify specific files
/pr-review-toolkit:simplify-code src/components/Modal.tsx

# Simplify a directory
/pr-review-toolkit:simplify-code src/utils/
```

## Refinement Process

1. Identify recently modified sections
2. Analyze for elegance opportunities
3. Apply project-specific standards
4. Ensure functionality unchanged
5. Verify improved maintainability
6. Document significant changes

## When to Use

- After completing a feature
- After fixing a bug
- After performance optimization
- Before creating a pull request
- As the final polish step
