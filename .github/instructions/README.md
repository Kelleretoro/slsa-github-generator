# GitHub Copilot Instructions

This directory contains custom instructions for the GitHub Copilot coding agent, as documented in [Best practices for Copilot coding agent in your repository](https://docs.github.com/en/copilot/tutorials/coding-agent/get-the-best-results).

## Purpose

These instructions help the Copilot coding agent understand the specific conventions, requirements, and best practices for this repository when working on tasks.

## Instruction Files

Each `.instructions.md` file includes:

- **YAML frontmatter**: Specifies which files the instructions apply to using `applyTo` patterns
- **Markdown content**: Detailed guidelines and conventions for that file type

### Current Instructions

- **general.md** - Applies to all files (`**/*`)
  - Project overview and key principles
  - Repository structure
  - Development commands
  - Commit conventions
  - Code review process

- **go-code.md** - Applies to Go files (`**/*.go`)
  - Go language version and tools
  - Code style and formatting
  - Testing conventions
  - Security requirements
  - Common patterns

- **typescript-code.md** - Applies to TypeScript files (`**/*.ts`)
  - TypeScript development for GitHub Actions
  - Formatting and linting
  - Testing with Jest
  - Building and distributing actions

- **yaml-workflows.md** - Applies to YAML files (`**/*.yml`, `**/*.yaml`)
  - YAML formatting and linting
  - GitHub Actions workflow conventions
  - Security considerations
  - Configuration file patterns

- **documentation.md** - Applies to Markdown files (`**/*.md`)
  - Markdown formatting and linting
  - Table of contents maintenance
  - Documentation structure
  - Writing style and tone

- **shell-scripts.md** - Applies to shell scripts (`**/*.sh`)
  - Shell script formatting and linting
  - Error handling conventions
  - Security considerations
  - Workflow script integration

## Agent-Specific Instructions

Most instruction files use `excludeAgent: "code-review"` to ensure these instructions are used by the coding agent but not the code review agent, which has different needs.

## Maintaining Instructions

When updating these instructions:

1. Ensure YAML frontmatter is valid
2. Keep markdown formatting consistent
3. Run `npm run markdownlint-fix` to auto-fix formatting issues
4. Verify instructions match current repository practices
5. Update as tooling or conventions change

## Learn More

- [GitHub Copilot coding agent documentation](https://docs.github.com/en/copilot/tutorials/coding-agent)
- [Custom instructions guide](https://docs.github.com/en/copilot/tutorials/coding-agent/add-custom-instructions)
