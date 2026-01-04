---
description: "Design feature architecture with comprehensive implementation blueprints"
argument-hint: "<feature-to-design>"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task", "TodoWrite"]
---

# Design Feature Architecture

Create a comprehensive architecture blueprint for a new feature by analyzing existing codebase patterns and providing detailed implementation guidance.

**Feature to Design:** "$ARGUMENTS"

## What This Command Does

Uses the `code-architect` agent to deliver actionable architecture blueprints:

1. **Codebase Pattern Analysis**
   - Extract existing patterns, conventions, and architectural decisions
   - Identify technology stack, module boundaries, abstraction layers
   - Find similar features to understand established approaches
   - Review CLAUDE.md guidelines

2. **Architecture Design**
   - Design complete feature architecture based on patterns found
   - Make decisive choices with clear rationale
   - Ensure seamless integration with existing code
   - Design for testability, performance, and maintainability

3. **Implementation Blueprint**
   - Specify every file to create or modify
   - Define component responsibilities
   - Document integration points and data flow
   - Break implementation into clear phases

## How to Use

```
/feature-dev:architect user notification system
/feature-dev:architect real-time chat feature
/feature-dev:architect caching layer for API
/feature-dev:architect plugin architecture
```

## Output Format

The agent provides a decisive, complete blueprint including:

- **Patterns & Conventions Found**: Existing patterns with file:line references
- **Architecture Decision**: Chosen approach with rationale and trade-offs
- **Component Design**: Each component with file path, responsibilities, dependencies
- **Implementation Map**: Specific files to create/modify with detailed changes
- **Data Flow**: Complete flow from entry to output
- **Build Sequence**: Phased implementation checklist
- **Critical Details**: Error handling, state, testing, performance, security

## When to Use

- Before implementing a new feature
- When planning a significant refactor
- When adding new system components
- When you need a clear implementation roadmap
- Before starting complex cross-cutting changes
