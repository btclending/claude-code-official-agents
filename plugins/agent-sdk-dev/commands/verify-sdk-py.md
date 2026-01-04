---
description: "Verify a Python Agent SDK application for correct configuration and best practices"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "WebFetch", "Task"]
---

# Verify Python Agent SDK Application

Run comprehensive verification of a Python Agent SDK application to ensure it's properly configured, follows SDK best practices, and is ready for deployment.

## What This Command Does

Uses the `agent-sdk-verifier-py` agent to verify:

1. **SDK Installation**: Checks `requirements.txt` or `pyproject.toml` for `claude-agent-sdk`
2. **Python Environment**: Validates dependencies and version constraints
3. **SDK Usage Patterns**: Verifies correct imports, initialization, and configuration
4. **Code Quality**: Checks for syntax errors and proper structure
5. **Environment Security**: Validates `.env.example` exists, secrets aren't hardcoded
6. **Best Practices**: Compares against official Python SDK documentation
7. **Documentation**: Checks for README and setup instructions

## How to Use

Simply run this command in your Python Agent SDK project:

```
/agent-sdk-dev:verify-sdk-py
```

## Verification Process

1. The agent will read your project files (requirements.txt, main.py, etc.)
2. It will compare against official SDK documentation
3. It will produce a comprehensive report with:
   - **Overall Status**: PASS, PASS WITH WARNINGS, or FAIL
   - **Critical Issues**: Problems that prevent the app from functioning
   - **Warnings**: Suboptimal patterns or missing features
   - **Passed Checks**: What's correctly configured
   - **Recommendations**: Suggestions for improvement

## Example Output

```
**Overall Status**: PASS WITH WARNINGS

**Summary**: The application is properly configured but has minor issues.

**Critical Issues**: None

**Warnings**:
- Missing virtual environment documentation in README
- Consider using python-dotenv for environment variable loading

**Passed Checks**:
- SDK properly installed in requirements.txt
- API key not hardcoded
- Proper agent initialization pattern used

**Recommendations**:
- Add .env.example with required variables
- Document Python version requirements
```

## When to Use

- After creating a new Python Agent SDK application
- After modifying SDK configuration
- Before deploying or publishing your application
- When troubleshooting SDK-related issues
