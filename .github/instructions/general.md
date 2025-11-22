---
applyTo: "**/*"
---

# SLSA GitHub Generator - General Instructions

## Project Overview

This repository contains free tools to generate and verify SLSA Build Level 3 provenance for native GitHub projects using GitHub Actions. The project helps developers build software using a secure process that protects against supply chain attacks.

## Key Principles

### Security First

- This is a security-focused project. All changes MUST maintain or improve security posture
- Never introduce memory-unsafe code or practices
- All new dependencies must be vetted for security vulnerabilities
- Follow secure coding practices as outlined in SECURITY.md

### Minimal Changes

- Make surgical, precise changes that accomplish the specific goal
- Do not refactor or modify working code unless absolutely necessary
- Preserve existing functionality and behavior

## Repository Structure

- `/actions` - GitHub Actions written in TypeScript
- `/internal` - Go packages for internal use
- `/slsa` - Core SLSA provenance functionality in Go
- `/github` - GitHub-specific utilities
- `/e2e` - End-to-end tests
- `.github/workflows` - Reusable GitHub Actions workflows

## Development Commands

### Building and Testing

- `make unit-test` - Run all unit tests (Go + TypeScript)
- `make go-test` - Run Go unit tests
- `make ts-test` - Run TypeScript tests with Jest
- `make lint` - Run all linters
- `make format` - Format all code

### Important Notes

- Always run tests before submitting changes
- Linters and tests must pass for PRs to be merged
- Use `make` to see all available targets

## Commit Conventions

All PR titles must use [Conventional Commits](https://www.conventionalcommits.org/) format:

- `fix:` - Bug fixes
- `feat:` - New features
- `docs:` - Documentation changes
- `chore:` - Maintenance tasks
- `refactor:` - Code improvements
- `style:` - Code formatting
- `build:` - Build system changes
- `ci:` - CI/CD changes
- `perf:` - Performance improvements
- `test:` - Test changes

## Code Review Process

1. All commits must be signed-off (Developer Certificate of Origin)
2. PRs require maintainer review and approval
3. All pre-submit tests must pass
4. Code must follow project formatting standards
