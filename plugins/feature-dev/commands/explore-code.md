---
description: "Deeply analyze an existing feature's implementation, architecture, and dependencies"
argument-hint: "<feature-to-explore>"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task", "TodoWrite"]
---

# Explore Existing Code Feature

Deeply analyze how a specific feature is implemented in the codebase by tracing execution paths, mapping architecture layers, understanding patterns, and documenting dependencies.

**Feature to Explore:** "$ARGUMENTS"

## What This Command Does

Uses the `code-explorer` agent to provide complete understanding of how a feature works:

1. **Feature Discovery**
   - Find entry points (APIs, UI components, CLI commands)
   - Locate core implementation files
   - Map feature boundaries and configuration

2. **Code Flow Tracing**
   - Follow call chains from entry to output
   - Trace data transformations at each step
   - Identify all dependencies and integrations
   - Document state changes and side effects

3. **Architecture Analysis**
   - Map abstraction layers (presentation → business logic → data)
   - Identify design patterns and architectural decisions
   - Document interfaces between components
   - Note cross-cutting concerns (auth, logging, caching)

4. **Implementation Details**
   - Key algorithms and data structures
   - Error handling and edge cases
   - Performance considerations
   - Technical debt or improvement areas

## How to Use

```
/feature-dev:explore-code authentication flow
/feature-dev:explore-code user registration
/feature-dev:explore-code payment processing
/feature-dev:explore-code search functionality
```

## Output Format

The agent provides a comprehensive analysis including:

- **Entry Points**: File paths and line numbers where the feature starts
- **Execution Flow**: Step-by-step path with data transformations
- **Key Components**: Each component's responsibilities
- **Architecture Insights**: Patterns, layers, design decisions
- **Dependencies**: External and internal dependencies
- **Observations**: Strengths, issues, improvement opportunities
- **Essential Files**: Core files needed to understand the feature

## When to Use

- Before modifying an existing feature
- When onboarding to understand a codebase
- Before extending a feature with new functionality
- When documenting system architecture
- When investigating bugs or performance issues
