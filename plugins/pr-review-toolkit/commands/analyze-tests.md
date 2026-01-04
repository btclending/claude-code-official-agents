---
description: "Analyze test coverage quality and completeness for a PR"
argument-hint: "[files-or-scope]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Analyze Test Coverage

Review test coverage quality and completeness for a pull request, focusing on behavioral coverage rather than line metrics.

**Scope:** "$ARGUMENTS" (defaults to PR changes)

## What This Command Does

Uses the `pr-test-analyzer` agent to evaluate tests:

### 1. Analyze Coverage Quality
- Focus on behavioral coverage
- Identify critical code paths
- Check edge cases and error conditions
- Verify async/concurrent behavior tested

### 2. Identify Critical Gaps
- Untested error handling
- Missing boundary conditions
- Uncovered business logic
- Absent negative test cases

### 3. Evaluate Test Quality
- Tests behavior, not implementation
- Would catch meaningful regressions
- Resilient to refactoring
- Uses DAMP principles (Descriptive And Meaningful Phrases)

### 4. Prioritize Recommendations
- Specific failure examples
- Criticality rating 1-10
- Explains what regression it prevents

## Rating Guidelines

- **9-10**: Critical - data loss, security, system failures
- **7-8**: Important - user-facing errors
- **5-6**: Edge cases - confusion or minor issues
- **3-4**: Nice-to-have - completeness
- **1-2**: Optional - minor improvements

## How to Use

```
# Analyze tests for PR
/pr-review-toolkit:analyze-tests

# Analyze specific test files
/pr-review-toolkit:analyze-tests src/__tests__/auth.test.ts

# Analyze tests for a feature
/pr-review-toolkit:analyze-tests src/features/checkout/
```

## Output Format

**Summary**: Brief coverage quality overview

**Critical Gaps** (rated 8-10)
- What to test
- Why it matters
- What failure it prevents

**Important Improvements** (rated 5-7)
- Suggested tests
- Expected benefit

**Test Quality Issues**
- Brittle tests
- Implementation-coupled tests

**Positive Observations**
- Well-tested areas
- Good practices found

## When to Use

- After creating a PR
- Before marking PR ready
- When updating PR with new logic
- To verify test completeness
- After adding new functionality
