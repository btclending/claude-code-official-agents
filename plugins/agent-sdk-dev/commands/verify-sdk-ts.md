---
description: "Verify a TypeScript Agent SDK application for correct configuration and best practices"
allowed-tools: ["Read", "Glob", "Grep", "Bash", "WebFetch", "Task"]
---

# Verify TypeScript Agent SDK Application

Run comprehensive verification of a TypeScript Agent SDK application to ensure it's properly configured, follows SDK best practices, and is ready for deployment.

## What This Command Does

Uses the `agent-sdk-verifier-ts` agent to verify:

1. **SDK Installation**: Checks `package.json` for `@anthropic-ai/claude-agent-sdk`
2. **TypeScript Configuration**: Validates `tsconfig.json` settings for ES modules
3. **SDK Usage Patterns**: Verifies correct imports, initialization, and configuration
4. **Type Safety**: Runs `npx tsc --noEmit` to check for type errors
5. **Build Configuration**: Validates package.json scripts (build, start, typecheck)
6. **Environment Security**: Validates `.env.example` exists, secrets aren't hardcoded
7. **Best Practices**: Compares against official TypeScript SDK documentation
8. **Documentation**: Checks for README and setup instructions

## How to Use

Simply run this command in your TypeScript Agent SDK project:

```
/agent-sdk-dev:verify-sdk-ts
```

## Verification Process

1. The agent will read your project files (package.json, tsconfig.json, src/*, etc.)
2. It will run type checking with `npx tsc --noEmit`
3. It will compare against official SDK documentation
4. It will produce a comprehensive report with:
   - **Overall Status**: PASS, PASS WITH WARNINGS, or FAIL
   - **Critical Issues**: Problems that prevent the app from functioning
   - **Warnings**: Suboptimal patterns or missing features
   - **Passed Checks**: What's correctly configured
   - **Recommendations**: Suggestions for improvement

## Example Output

```
**Overall Status**: PASS

**Summary**: The application is properly configured and ready for deployment.

**Critical Issues**: None

**Warnings**: None

**Passed Checks**:
- SDK properly installed in package.json
- tsconfig.json configured for ES modules
- Type checking passes without errors
- API key not hardcoded
- Proper agent initialization pattern used

**Recommendations**:
- Consider adding a "typecheck" npm script for CI
```

## When to Use

- After creating a new TypeScript Agent SDK application
- After modifying SDK configuration or TypeScript settings
- Before deploying or publishing your application
- When troubleshooting SDK-related issues or type errors
