---
applyTo: "**/*.ts"
excludeAgent: "code-review"
---

# TypeScript Code Instructions

## Context

TypeScript is used for GitHub Actions in the `.github/actions/` directory.

## Code Style and Formatting

### Formatting Tools

- **prettier**: Primary formatter for TypeScript
- Configuration uses default Prettier settings
- Run `make format` to format all code

### Linting

- **eslint**: TypeScript linter
- Follow ESLint rules defined in the project
- All linting errors must be resolved

## Testing

### Test Framework

- **Jest**: Used for TypeScript unit tests
- Run `make ts-test` to execute tests
- Tests are located alongside source files

### Test Conventions

- Write tests for new functionality
- Follow existing test patterns
- Ensure all tests pass before submitting changes

## GitHub Actions Development

### Actions Structure

- Each action in `.github/actions/` has its own directory
- `src/main.ts` - Entry point for the action
- `package.json` - Node.js dependencies
- `dist/` - Compiled JavaScript (committed to repo)

### Building Actions

- TypeScript must be compiled to JavaScript
- The `dist/` directory contains compiled code and must be committed
- After changing TypeScript, rebuild using the appropriate build command
- For Renovate-Bot PRs updating dependencies, use the workflow:
  - `update-actions-dist-post-commit.yml` to recompile actions

### Dependencies

- Use `npm ci` for reproducible installs
- Keep `package-lock.json` in sync with `package.json`
- Renovate automatically updates dependencies

## Code Conventions

### Imports and Modules

- Use ES6 module syntax
- Organize imports logically
- Remove unused imports

### Type Safety

- Use TypeScript's type system effectively
- Avoid `any` types when possible
- Define interfaces for complex objects

### Error Handling

- Handle errors appropriately
- Provide meaningful error messages
- Use try/catch for async operations

## Copyright Headers

All TypeScript files should include the Apache 2.0 license header at the top.

## Common Actions Patterns

### Action Inputs/Outputs

- Use `@actions/core` for inputs and outputs
- Validate inputs before use
- Set outputs clearly

### GitHub API

- Use `@actions/github` for GitHub API interactions
- Handle API rate limits
- Include error handling for API calls
