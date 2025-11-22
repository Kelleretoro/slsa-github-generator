---
applyTo: "**/*.sh"
excludeAgent: "code-review"
---

# Shell Script Instructions

## Shell Style and Formatting

### Formatting Tools

- **shfmt**: Formats shell scripts
- Run `make format` to format all shell scripts
- Use consistent indentation (typically 2 spaces)

### Linting

- **shellcheck**: Lints shell scripts for common errors
- All shellcheck warnings should be addressed
- Run `make lint` to check shell scripts

## Shell Script Conventions

### Script Headers

- Use `#!/bin/bash` shebang
- Include copyright header (Apache 2.0 license)
- Add brief description of script purpose

### Error Handling

- Use `set -euo pipefail` for strict error checking:
  - `-e`: Exit on error
  - `-u`: Exit on undefined variable
  - `-o pipefail`: Fail on pipe errors
- Handle errors explicitly where needed
- Provide meaningful error messages

### Script Organization

- Keep scripts focused on a single task
- Use functions for repeated logic
- Make scripts reusable when possible
- Document complex sections with comments

## Common Patterns

### Variables

- Use UPPER_CASE for environment variables
- Use lower_case for local variables
- Quote variables to prevent word splitting: `"$var"`
- Use `${var}` for clarity when needed

### Conditionals

- Use `[[ ]]` instead of `[ ]` for tests
- Quote strings in comparisons
- Use explicit comparisons (`-n`, `-z`, `==`, etc.)

### Loops

- Prefer `for` loops with proper quoting
- Use `while read` for processing file lines
- Handle empty cases appropriately

## Security Considerations

### Input Validation

- Validate all inputs
- Sanitize user-provided data
- Avoid command injection vulnerabilities

### File Operations

- Check file existence before operations
- Use proper permissions
- Clean up temporary files

### Secrets

- Never hardcode secrets
- Use environment variables for sensitive data
- Avoid logging secrets

## Scripts in Workflows

### Location

- Workflow scripts in `.github/workflows/scripts/`
- Organize by purpose (pre-submit, schedule, etc.)
- Keep scripts modular

### Workflow Integration

- Scripts should work well in GitHub Actions environment
- Handle `GITHUB_*` environment variables appropriately
- Output results in formats GitHub Actions can consume
- Use `::error::`, `::warning::`, `::notice::` for GitHub annotations

### Testing Scripts

- Test scripts locally when possible
- Verify behavior in GitHub Actions environment
- Include error cases in testing

## Best Practices

### Readability

- Use descriptive variable names
- Add comments for complex logic
- Keep functions small and focused
- Use consistent formatting

### Portability

- Stick to bash (not sh or zsh-specific features)
- Avoid GNU-specific extensions when possible
- Test on relevant platforms

### Performance

- Avoid unnecessary external commands
- Use built-in bash features when available
- Be mindful of loop efficiency

### Maintenance

- Keep scripts simple
- Avoid clever tricks that reduce readability
- Document non-obvious behavior
- Update scripts as requirements change
