---
applyTo: "**/*.yml,**/*.yaml"
excludeAgent: "code-review"
---

# YAML and Workflow Instructions

## Formatting

### Formatting Tools

- **prettier**: Formats YAML files
- Run `npm run format-yaml` or `make format`
- Configuration uses project standards

### Linting

- **yamllint**: Lints YAML syntax and style
- Configuration in `.yamllint.yaml`
- **actionlint**: Lints GitHub Actions workflows specifically
- Run `make lint` to check all YAML files

## GitHub Actions Workflows

### Workflow Organization

- `.github/workflows/` - All workflow files
- Naming conventions:
  - `pre-submit.*` - Pre-submit checks
  - `pre-release.*` - Pre-release workflows
  - `schedule.*` - Scheduled workflows
  - `e2e.*` - End-to-end test workflows
  - `generator-*` - Generator workflows
  - `delegator-*` - Delegator workflows

### Workflow Best Practices

- Use reusable workflows to reduce duplication
- Pin action versions to specific commits or tags
- Document workflow purpose in comments
- Keep workflows focused on a single responsibility

### Security Considerations

- Pin all action versions using commit SHAs where possible
- Avoid using `pull_request_target` unless absolutely necessary
- Minimize permissions granted to workflows
- Use secrets appropriately

## YAML Configuration Files

### Types of Config Files

- `.golangci.yml` - Go linter configuration
- `.markdownlint.yaml` - Markdown linter configuration
- `.yamllint.yaml` - YAML linter configuration
- `renovate.json` - Dependency update configuration (JSON)

### YAML Style

- Use 2-space indentation
- Use dash (`-`) for unordered lists
- Use proper quoting for strings when needed
- Keep lines readable (no strict line length limit)

## Workflow Scripts

### Scripts in Workflows

- Shell scripts in `.github/workflows/scripts/`
- Use bash for scripts
- Scripts should be formatted with `shfmt`
- Scripts should be linted with `shellcheck`

### Shell Script Conventions

- Include proper error handling
- Use `set -euo pipefail` for strict error checking
- Make scripts executable
- Document script purpose and usage

## Copyright Headers

All YAML files should include the Apache 2.0 license header when appropriate (especially for workflows and complex configurations).

## Testing Workflows

### Pre-submit Tests

- Run on every PR
- Must pass before merging
- Include unit tests, linting, and other checks

### End-to-End Tests

- More comprehensive testing
- May run on schedule or specific events
- Located in separate repository (example-package)

## Configuration Conventions

### Workflow Configurations

- Workflow-specific configs in subdirectories:
  - `configs-go/` - Go builder configurations
  - `configs-container/` - Container configurations
  - `configs-generic/` - Generic configurations
  - `configs-docker/` - Docker configurations

### Naming and Structure

- Use descriptive names for workflows and jobs
- Group related steps logically
- Use step names that clearly describe the action
