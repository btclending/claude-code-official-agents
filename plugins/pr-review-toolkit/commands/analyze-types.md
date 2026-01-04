---
description: "Analyze type design for encapsulation, invariants, and best practices"
argument-hint: "[types-or-files]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Analyze Type Design

Analyze type designs for encapsulation quality, invariant expression, and best practices.

**Scope:** "$ARGUMENTS" (defaults to new types in changes)

## What This Command Does

Uses the `type-design-analyzer` agent to evaluate types:

### 1. Identify Invariants
- Data consistency requirements
- Valid state transitions
- Field relationship constraints
- Business logic rules
- Preconditions and postconditions

### 2. Evaluate Encapsulation (1-10)
- Internal details hidden
- Invariants can't be violated externally
- Appropriate access modifiers
- Minimal, complete interface

### 3. Assess Invariant Expression (1-10)
- Clearly communicated through structure
- Enforced at compile-time where possible
- Self-documenting design
- Obvious constraints

### 4. Judge Invariant Usefulness (1-10)
- Prevents real bugs
- Aligned with business requirements
- Easier to reason about
- Neither too restrictive nor permissive

### 5. Examine Enforcement (1-10)
- Checked at construction
- Mutation points guarded
- Impossible to create invalid instances
- Appropriate runtime checks

## How to Use

```
# Analyze new types in changes
/pr-review-toolkit:analyze-types

# Analyze specific type file
/pr-review-toolkit:analyze-types src/types/User.ts

# Analyze types in a module
/pr-review-toolkit:analyze-types src/models/
```

## Output Format

```
## Type: UserAccount

### Invariants Identified
- Email must be valid format
- Password hash never empty
- Created date immutable

### Ratings
- **Encapsulation**: 8/10
  Good hiding, minor exposure

- **Invariant Expression**: 7/10
  Clear but could use branded types

- **Invariant Usefulness**: 9/10
  Prevents common bugs

- **Invariant Enforcement**: 6/10
  Missing validation in setters

### Strengths
- Immutable ID field
- Factory method pattern

### Concerns
- Email setter allows invalid format

### Recommended Improvements
- Add email validation in setter
- Consider Email branded type
```

## Anti-patterns Flagged

- Anemic domain models
- Exposed mutable internals
- Documentation-only invariants
- Too many responsibilities
- Missing construction validation
- External invariant reliance

## When to Use

- When introducing new types
- During PR review
- When refactoring types
- Before major releases
