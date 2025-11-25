# Copilot Instructions for slsa-github-generator

This document provides instructions for GitHub Copilot when working on this repository.

## Repository Overview

slsa-github-generator is a set of tools for generating SLSA Build Level 3+
provenance for native GitHub projects. It provides secure, non-forgeable
provenance using GitHub Actions reusable workflows.

The project includes:

- **Builders**: Build and generate provenance (Go, Node.js, Maven, Gradle, Bazel, Container-based)
- **Generators**: Generate provenance for existing artifacts (Generic file, Container)
- **BYOB Framework**: Build Your Own Builder framework for creating custom SLSA builders

## Project Structure

- `actions/` - GitHub Actions (TypeScript)
- `.github/actions/` - Internal GitHub Actions (TypeScript)
- `.github/workflows/` - GitHub Actions workflows (YAML)
- `internal/` - Internal Go packages and builders
- `signing/` - Signing-related code
- `slsa/` - SLSA-related utilities
- `e2e/` - End-to-end test utilities

## Preferred Languages

Use the following languages for new code:

- **Go**: For builders and generators
- **TypeScript**: For GitHub Actions
- **Bash**: For scripts in GitHub Actions and workflows
- **YAML**: For GitHub Actions workflows

Do not introduce memory-unsafe languages (e.g., C, C++) or memory-unsafe code
patterns (e.g., Go's `unsafe` package).

## Development Commands

### Building and Testing

```bash
# Show all available make targets
make

# Run all unit tests
make unit-test

# Run Go unit tests only
make go-test

# Run TypeScript tests only
make ts-test
```

### Formatting

```bash
# Run all formatters
make format

# Individual formatters
make yaml-format    # Format YAML files with prettier
make md-format      # Format Markdown files with prettier
make ts-format      # Format TypeScript files with prettier
make go-format      # Format Go files with gofumpt
make shfmt          # Format shell scripts with shfmt
make markdown-toc   # Update table of contents in markdown files
make autogen        # Add license headers to code files
```

### Linting

```bash
# Run all linters
make lint

# Individual linters
make actionlint     # Lint GitHub Actions workflows
make markdownlint   # Lint Markdown files
make golangci-lint  # Lint Go code
make shellcheck     # Lint shell scripts
make eslint         # Lint TypeScript code
make yamllint       # Lint YAML files
```

## Code Style and Conventions

### General

- All code files must include a copyright notice and license header (Apache 2.0)
- Run `make autogen` to add missing license headers

### Go

- Format with `gofumpt`
- Lint with `golangci-lint`
- Configuration: `.golangci.yml`

### TypeScript

- Format with `prettier`
- Lint with `eslint`
- Each action has its own `package.json` and Makefile

### Shell Scripts

- Format with `shfmt` (2-space indentation)
- Lint with `shellcheck`

### YAML

- Format with `prettier`
- Lint with `yamllint`
- Configuration: `.yamllint.yaml`

### Markdown

- Format with `prettier`
- Lint with `markdownlint`
- Configuration: `.markdownlint.yaml`
- Use `markdown-toc` for table of contents

## Pull Request Guidelines

### PR Titles

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

- `fix:` - Bug fixes
- `feat:` - New features
- `docs:` - Documentation changes
- `chore:` - Maintenance tasks (e.g., dependency updates)
- `refactor:` - Code improvements without behavior changes
- `style:` - Code style/formatting changes
- `build:` - Build system changes
- `ci:` - CI/CD configuration changes
- `perf:` - Performance improvements
- `revert:` - Reverts a previous change
- `test:` - Test additions or corrections

### Commit Requirements

- Sign off on all commits (`git commit -s`) to establish Developer Certificate of Origin
- Ensure all unit tests pass (`make unit-test`)
- Ensure all linters pass (`make lint`)

## Security Considerations

- Never introduce memory-unsafe code
- All PRs are reviewed by CODEOWNERS
- Report vulnerabilities via GitHub Security Advisories
- See `SECURITY.md` for the full security policy

## Testing

### Unit Tests

- Go tests are in `*_test.go` files
- TypeScript tests use Jest and are in `__tests__/` directories
- Run `make unit-test` before submitting PRs

### End-to-End Tests

- E2E tests are in the [example-package](https://github.com/slsa-framework/example-package) repository
- E2E tests run daily via scheduled workflows

## Versioning

The project follows [Semantic Versioning](https://semver.org/):

- MAJOR: Incompatible API changes
- MINOR: Backward compatible new functionality
- PATCH: Backward compatible bug fixes
