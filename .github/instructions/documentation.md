---
applyTo: "**/*.md"
excludeAgent: "code-review"
---

# Documentation and Markdown Instructions

## Formatting

### Formatting Tools

- **prettier**: Formats Markdown files
- **markdownlint**: Lints Markdown for style and consistency
- Configuration in `.markdownlint.yaml`
- Run `make format` to format all Markdown
- Run `npm run markdownlint-fix` to auto-fix linting issues

### Linting Rules

Key markdownlint rules (from `.markdownlint.yaml`):

- Use dash (`-`) style for unordered lists (MD004)
- 2-space indentation for lists (MD007)
- No line length limit (MD013: false)
- Ordered lists use sequential numbering (MD029)
- Use fenced code blocks with backticks (MD046, MD048)
- Files must end with single newline (MD047)
- Inline HTML is allowed (MD033)
- Bare URLs are allowed (MD034)

## Table of Contents

### Updating TOC

- Use `markdown-toc` for maintaining tables of contents
- Command: `npm run markdown-toc -- -i <file.md>`
- TOC markers: `<!-- toc -->` and `<!-- tocstop -->`
- Use dash bullets: `--bullets='-'`

### TOC Conventions

- Include TOC in longer documents (README, CONTRIBUTING, etc.)
- Keep TOC up to date when changing headings
- Use relative links in TOC

## Documentation Files

### Key Documentation

- `README.md` - Project overview and quick start
- `CONTRIBUTING.md` - Contributor guide
- `SECURITY.md` - Security policy and reporting
- `RELEASE.md` - Release process
- `SPECIFICATIONS.md` - Technical specifications
- `BYOB.md` - Build Your Own Builder guide

### Documentation Structure

- Start with clear purpose/overview
- Use descriptive headings
- Include code examples where helpful
- Link to related documentation
- Keep language clear and concise

## Code Examples in Documentation

### Code Blocks

- Use fenced code blocks with language specifiers:

  ```yaml
  name: Example Workflow
  ```

- Common languages: `yaml`, `bash`, `go`, `typescript`, `shell`
- Ensure examples are accurate and tested

### Command Examples

- Show both commands and expected output when helpful
- Use `$` prompt for shell commands
- Include context for commands

## Links

### Link Conventions

- Use relative links for internal documentation
- Prefer reference-style links for readability: `[text][ref]`
- Keep URLs up to date
- Check for broken links

## Copyright and License

### Headers

- Major documentation files should include copyright notice
- Reference LICENSE file when appropriate
- Use Apache 2.0 license header format

## Writing Style

### Tone and Language

- Write in clear, professional English
- Be concise but thorough
- Use second person ("you") when addressing users
- Use active voice
- Define acronyms on first use

### Technical Accuracy

- Ensure technical details are correct
- Test commands and examples before documenting
- Keep documentation in sync with code changes
- Update docs when functionality changes

## Special Documentation

### Issue Templates

- Located in `.github/ISSUE_TEMPLATE/`
- Use YAML frontmatter for GitHub issue forms
- Keep templates clear and focused

### Pull Request Template

- Located in `.github/pull_request_template.md`
- Provides structure for PR descriptions
- Include checklist items

## Maintenance

### Regular Updates

- Review documentation with code changes
- Update version references
- Check for outdated information
- Fix broken links and references

### Documentation Tests

- Some documentation may be validated in CI
- Ensure markdownlint passes
- Verify TOC is up to date
- Check that code examples work
