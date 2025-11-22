---
applyTo: "**/*.go"
excludeAgent: "code-review"
---

# Go Code Instructions

## Language Version

- Go 1.23.1 or later
- Use Go modules for dependency management

## Code Style and Formatting

### Formatting Tools

- **gofumpt**: Primary formatter for Go code (stricter than gofmt)
- **goimports**: Automatically manages imports
- Run `make format` to format all Go code

### Linting

- **golangci-lint**: Comprehensive linter with multiple checks enabled
- Configuration in `.golangci.yml`
- Run `make lint` to check Go code
- All linter warnings must be addressed

### Key Linting Rules

- All code must pass `gosec` security checks
- Use `gofumpt` style formatting
- Follow standard Go conventions
- Avoid naked returns
- Minimize cognitive complexity
- Keep functions focused and concise

## Testing

### Running Tests

- `make go-test` - Run all Go unit tests
- Tests must pass before submitting changes
- Unit tests run as pre-submit checks

### Test Conventions

- Place tests in `*_test.go` files
- Use table-driven tests where appropriate
- Follow existing test patterns in the codebase
- Ensure adequate test coverage for new functionality

## Code Structure

### Package Organization

- `/internal/*` - Internal packages not meant for external use
- `/slsa/*` - Core SLSA provenance functionality
- `/github/*` - GitHub-specific utilities

### Imports

- Standard library imports first
- Third-party imports second
- Local imports last
- Groups separated by blank lines

## Security Requirements

### Memory Safety

- **NEVER** use the `unsafe` package
- Avoid pointer arithmetic
- Validate all inputs
- Handle errors explicitly

### Dependencies

- Vet all new dependencies for security issues
- Use `go.mod` for dependency management
- Keep dependencies up to date via Renovate

## Common Patterns

### Error Handling

- Always check and handle errors
- Use descriptive error messages
- Wrap errors with context when propagating
- Return errors rather than panicking in libraries

### Code Comments

- Add comments for exported functions and types
- Explain non-obvious logic
- Reference issues for TODOs
- Include copyright header (added automatically by autogen)

## Copyright Headers

All Go files must include the Apache 2.0 license header. This is enforced by `autogen` and applied automatically during formatting.
