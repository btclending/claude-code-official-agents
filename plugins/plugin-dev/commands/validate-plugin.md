---
description: "Validate plugin structure, configuration, and components"
argument-hint: "[plugin-path]"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "Task"]
---

# Validate Plugin

Perform comprehensive validation of a Claude Code plugin's structure, configuration, and all components.

**Plugin Path:** "$ARGUMENTS" (defaults to current directory)

## What This Command Does

Uses the `plugin-validator` agent to check:

1. **Plugin Manifest** (`.claude-plugin/plugin.json`)
   - JSON syntax validity
   - Required fields: `name`
   - Optional fields: `version`, `description`, `author`, `mcpServers`
   - Name format (kebab-case)

2. **Directory Structure**
   - `commands/` for slash commands
   - `agents/` for agent definitions
   - `skills/` for skill directories
   - `hooks/hooks.json` for hooks

3. **Commands** (`commands/**/*.md`)
   - YAML frontmatter present
   - `description` field exists
   - Valid `allowed-tools` format
   - Markdown content exists

4. **Agents** (`agents/**/*.md`)
   - Valid frontmatter with `name`, `description`, `model`, `color`
   - Name format (lowercase, hyphens, 3-50 chars)
   - Description includes `<example>` blocks
   - Valid model and color values
   - Substantial system prompt

5. **Skills** (`skills/*/SKILL.md`)
   - SKILL.md file exists
   - Valid frontmatter with `name`, `description`
   - Proper directory structure

6. **Hooks** (`hooks/hooks.json`)
   - Valid JSON syntax
   - Valid event names
   - Proper matcher and hooks structure

7. **Security Checks**
   - No hardcoded credentials
   - MCP servers use HTTPS/WSS
   - No secrets in examples

## How to Use

```
# Validate current plugin
/plugin-dev:validate-plugin

# Validate specific plugin
/plugin-dev:validate-plugin plugins/my-plugin/
```

## Output Format

```
## Plugin Validation Report

### Plugin: my-plugin
Location: plugins/my-plugin/

### Summary
PASS - 2 warnings

### Critical Issues (0)
None

### Warnings (2)
- `agents/reviewer.md` - Missing example blocks
- `README.md` - Missing setup instructions

### Component Summary
- Commands: 3 found, 3 valid
- Agents: 2 found, 1 valid
- Skills: 1 found, 1 valid
- Hooks: present, valid
- MCP Servers: 0 configured

### Overall Assessment
PASS - Plugin is functional with minor improvements needed
```

## When to Use

- After creating a new plugin
- After modifying plugin components
- Before publishing or sharing a plugin
- To troubleshoot plugin issues
