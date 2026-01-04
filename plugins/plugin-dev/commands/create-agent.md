---
description: "Create a new agent with AI-assisted configuration"
argument-hint: "<agent-description>"
allowed-tools: ["Read", "Write", "Glob", "Task"]
---

# Create New Agent

Create a new agent using AI-assisted generation based on your description of what the agent should do.

**Agent Description:** "$ARGUMENTS"

## What This Command Does

Uses the `agent-creator` agent to generate a complete agent configuration:

1. **Extract Core Intent**
   - Identify purpose, responsibilities, and success criteria
   - Understand explicit and implicit requirements
   - Consider project context from CLAUDE.md

2. **Design Expert Persona**
   - Create compelling expert identity
   - Match deep domain knowledge to the task
   - Guide decision-making approach

3. **Architect Instructions**
   - Clear behavioral boundaries
   - Specific methodologies and best practices
   - Edge case handling
   - Output format expectations

4. **Create Identifier**
   - Concise, descriptive name
   - Lowercase with hyphens
   - 2-4 words, memorable

5. **Craft Triggering Examples**
   - 2-4 example blocks
   - Different phrasings for same intent
   - Context, user message, commentary

## How to Use

```
/plugin-dev:create-agent code review agent that checks for security issues
/plugin-dev:create-agent agent that generates unit tests
/plugin-dev:create-agent documentation generator for API endpoints
/plugin-dev:create-agent performance analyzer for database queries
```

## Output Format

The agent will:
1. Create `agents/[identifier].md` with full configuration
2. Provide summary:
   - **Name**: Agent identifier
   - **Triggers**: When it activates
   - **Model**: sonnet/opus/haiku/inherit
   - **Color**: Visual indicator
   - **Tools**: Permitted tools

3. Suggest testing and validation steps

## Agent File Structure

```markdown
---
name: agent-name
description: Use this agent when... Examples: <example>...</example>
model: inherit
color: green
tools: ["Tool1", "Tool2"]
---

[Complete system prompt]
```

## When to Use

- When you need a new specialized agent
- When automating repetitive review tasks
- When adding domain expertise to your plugin
- When creating agents for specific workflows
