# GitHub Copilot Instructions for slsa-github-generator

## Repository Overview

This repository contains the SLSA GitHub Generator - free tools to generate and verify SLSA Build Level 3 provenance for native GitHub projects using GitHub Actions. The project helps developers build software using a secure process that protects against supply chain attacks and tampering.

SLSA (Supply-chain Levels for Software Artifacts) is a security framework with standards and controls to prevent tampering and secure the software supply chain.

## Primary Technologies

This project uses multiple languages and technologies:

- **Go** - Primary language for builders and generators
- **TypeScript** - Used for GitHub Actions
- **YAML** - GitHub Actions workflows and configurations
- **Bash** - Scripts in GitHub Actions and workflows

**Language Preferences:**

- Prefer Go for builders/generators
- Prefer TypeScript for GitHub actions
- Prefer Bash for scripts in GitHub actions and workflows
- DO NOT introduce memory-unsafe languages or use of existing languages in memory-unsafe ways (e.g., Go's `unsafe` package)

## Development Setup

### Prerequisites

Required tools:

- [Go](https://go.dev/) - Go runtime
- [Node.js](https://nodejs.org/) - For TypeScript actions

### Optional Development Tools (for local linting/formatting)

- `actionlint` - Linting GitHub Actions workflows
- `gofumpt` - Formatting Go code
- `golangci-lint` - Linting Go code
- `shfmt` - Formatting shell code
- `shellcheck` - Linting shell code
- `yamllint` - Linting YAML

Vendored/auto-installed tools (no manual installation needed):

- `autogen` - License headers
- `prettier` - Formatting Markdown, YAML, TypeScript
- `markdown-toc` - Table of Contents in markdown
- `eslint` - Linting TypeScript

## Building and Testing

All development commands are in the `Makefile`. Run `make` or `make help` to see available targets.

### Testing Commands

```bash
# Run all unit tests
make unit-test

# Run Go unit tests only
make go-test

# Run TypeScript tests only
make ts-test
```

### Linting Commands

```bash
# Run all linters
make lint

# Individual linters
make actionlint        # GitHub Actions workflows
make markdownlint      # Markdown files
make golangci-lint     # Go code
make shellcheck        # Shell scripts
make eslint            # TypeScript code
make yamllint          # YAML files
make renovate-config-validator  # Renovate config
```

### Formatting Commands

```bash
# Run all formatters
make format

# Individual formatters
make yaml-format       # YAML files
make md-format         # Markdown files
make ts-format         # TypeScript files
make go-format         # Go files
make shfmt             # Shell scripts
make markdown-toc      # Update TOCs in markdown
make autogen           # Add/update license headers
```

## Code Style and Formatting

1. **Go code** - Format with `gofumpt`
2. **TypeScript code** - Format with `prettier`
3. **YAML** - Format with `prettier`
4. **Markdown** - Format with `prettier`
5. **Shell scripts** - Format with `shfmt`
6. **Markdown TOCs** - Sync with `markdown-toc`
7. **License headers** - All code files must include copyright notice and Apache 2.0 license header

**Copyright:** SLSA Authors
**License:** Apache License 2.0

Run `make format` to format all code before committing.

## Git Conventions

### Commit Sign-off

All commits must be signed-off to establish Developer Certificate of Origin:

```bash
git commit -s
git merge --signoff main
```

### Conventional Commits

PR titles must follow [Conventional Commits](https://www.conventionalcommits.org/) format with these prefixes:

- `fix:` - Bug fixes
- `feat:` - New features
- `docs:` - Documentation changes
- `chore:` - Maintenance tasks (e.g., updating dependencies)
- `refactor:` - Code quality improvements
- `style:` - Coding style or format changes
- `build:` - Build system changes
- `ci:` - CI/CD configuration changes
- `perf:` - Performance improvements
- `revert:` - Reverting previous changes
- `test:` - Adding or correcting tests

See `.github/pr-title-checker-config.json` for full configuration.

### Semantic Versioning

Releases follow [Semantic Versioning](https://semver.org/):

- **MAJOR** - Incompatible API changes
- **MINOR** - Backward compatible new functionality
- **PATCH** - Backward compatible bug fixes

## Repository Structure

- `.github/actions/` - GitHub Actions written in TypeScript
- `.github/workflows/` - GitHub Actions workflows (YAML)
- `actions/` - Additional GitHub Actions
- `internal/` - Internal Go packages
- `slsa/` - SLSA-related Go code
- `e2e/` - End-to-end tests
- `third_party/` - Third-party dependencies

## Testing Strategy

### Unit Tests

- Pre-submit tests run on each PR and block merging if they fail
- Located in `.github/workflows/` with prefix `pre-submit`
- Go unit tests: `make go-test`
- TypeScript tests: `make ts-test` (uses Jest)

### End-to-End Tests

- E2E tests run daily
- Located in the [example-package](https://github.com/slsa-framework/example-package) repository
- See the e2e testing [README.md](https://github.com/slsa-framework/example-package/blob/main/.github/workflows/README.md)

### Test Requirements for PRs

New PRs with new functionality should include automated tests for that functionality.

## Important Files

- `Makefile` - All development commands
- `CONTRIBUTING.md` - Detailed contributor guide
- `SECURITY.md` - Security policy
- `RELEASE.md` - Release process
- `.golangci.yml` - Go linter configuration
- `.markdownlint.yaml` - Markdown linter configuration
- `.yamllint.yaml` - YAML linter configuration
- `package.json` - Node.js dependencies and scripts
- `renovate.json` - Renovate bot configuration

## Making Changes

1. **Create a fork** - Fork the repository (required for testing GitHub Actions workflows)
2. **Create a test repo** - Set up a test repository for testing workflows
3. **Create a branch** - `git checkout -b my-feature-branch`
4. **Make changes** - Implement your changes
5. **Format code** - Run `make format`
6. **Run tests** - Run `make unit-test` and `make lint`
7. **Commit with sign-off** - `git commit -s`
8. **Submit PR** - Create PR with Conventional Commits title

## GitHub Actions Dependencies

When `renovate-bot` updates `package.json`/`package-lock.json`, you must recompile packages into `.js` files using the [Update actions dist post-commit](../.github/workflows/update-actions-dist-post-commit.yml) workflow:

```bash
gh workflow run update-actions-dist-post-commit.yml -F pr_number=<pull request number>
```

## Security Considerations

- DO NOT introduce memory-unsafe languages
- DO NOT use memory-unsafe features (like Go's `unsafe` package)
- All code files must include license headers
- Follow security best practices for supply chain security
- See `SECURITY.md` for full security policy

## Communication

- **Slack:** [`#slsa-tooling`](https://slack.com/app_redirect?team=T019QHUBYQ3&channel=slsa-tooling) in [OpenSSF Slack](https://slack.openssf.org/)
- **Issues:** [GitHub Issues](https://github.com/slsa-framework/slsa-github-generator/issues)

## Quick Reference

```bash
# List all available make targets
make

# Format all code
make format

# Run all linters
make lint

# Run all unit tests
make unit-test

# Clean temporary files
make clean
```

## Code Quality Standards

- All code must pass linters before merging
- All code must be properly formatted
- All code must include appropriate tests
- All commits must be signed-off
- All PR titles must follow Conventional Commits format
- All code files must include copyright and license headers
