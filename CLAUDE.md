# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **skill definition repository** for the Vercel Operations skill. It follows the universal `.agents/skills` layout, making it compatible with tools like Claude Code, Codex, and any `skills.sh`-compatible tooling.

The skill provides comprehensive guidance on using the Vercel CLI and cloud platform for deployments, environment management, domain configuration, and monitoring.

## Architecture and Structure

### Main Components

- **`.agents/skills/vercelops/SKILL.md`** - The core skill definition containing:
  - Prerequisites and core concepts
  - Command reference organized by use case (10 main categories)
  - Common workflows (new project, existing project, debugging, domain setup)
  - Global options and environment variable scopes
  - Configuration file examples (vercel.json)
  - Framework-specific notes
  - Troubleshooting guides
  - Best practices

- **`.agents/skills/vercelops/evals/evals.json`** - Evaluation tests with 5 test cases covering:
  - Next.js deployment workflow
  - Production debugging
  - Custom domain and SSL setup
  - Environment variable management
  - Linking existing projects

- **`README.md`** - Installation instructions and overview for end users

- **`LICENSE`** - MIT license

### Installation Layout

The skill is installed by copying `.agents/skills/vercelops/` to an agent's skills directory:
- Claude Code: `~/.claude/skills/vercelops/`
- Codex: `~/.codex/skills/vercelops/`
- Other tools: their configured skills directory

## Development Commands

This is a documentation-focused repository, so there are no build, test, or lint commands. Development involves:

### Editing the Skill Definition
```bash
# Edit the main skill content
vi .agents/skills/vercelops/SKILL.md

# Edit evaluation tests
vi .agents/skills/vercelops/evals/evals.json
```

### Validating Changes
- **Manual testing**: Install the skill and test with agents to ensure guidance is accurate
- **JSON validation**: Verify `evals.json` has valid JSON syntax
- **Markdown**: Ensure `SKILL.md` renders correctly

### Distributing Updates
The skill can be installed via:
```bash
# skills.sh install from GitHub
npx skills add https://github.com/rajivmehtaflex/vercelops-skill --skill vercelops

# Manual installation
cp -r .agents/skills/vercelops ~/.claude/skills/
```

## Key Development Notes

### SKILL.md Content Structure
The SKILL.md file is the complete skill definition. It should include:
1. **Metadata** (YAML frontmatter with name, description, and trigger conditions)
2. **Prerequisites** - what users need installed/configured
3. **Core Concepts** - overview of Vercel platform capabilities
4. **Command Reference** - organized tables by use case
5. **Common Workflows** - step-by-step guides for typical tasks
6. **Global Options** - CLI flags that apply broadly
7. **Configuration** - vercel.json file format and examples
8. **Framework Notes** - specific guidance for Next.js, Nuxt, SvelteKit, Astro
9. **Troubleshooting** - common issues and solutions
10. **Best Practices** - recommended approaches

### Evaluation Tests
The `evals.json` file contains test cases with:
- `id` - unique identifier
- `prompt` - user query the skill should handle
- `expected_output` - description of what the skill should guide the user to do
- `files` - (empty array, not currently used)

These serve as validation that the skill provides appropriate guidance for key use cases.

### Key Trigger Conditions
The skill triggers when users mention:
- Vercel deployment, `vercel` CLI commands
- Environment variables, domains, preview/production deployments
- Edge/serverless functions on Vercel
- Next.js, Nuxt, SvelteKit, Astro deployments to Vercel

## Design Principles

1. **Command-Driven Guidance**: Provide exact CLI commands with examples
2. **Use-Case Organization**: Group commands by real-world workflows
3. **Multi-Level Guidance**: From new project setup through advanced operations
4. **Practical Examples**: Every command reference includes usage examples
5. **Troubleshooting Focus**: Include debugging workflows and common pitfalls
6. **Framework Awareness**: Acknowledge differences between Next.js, Nuxt, SvelteKit, etc.

## Git Workflow

This repository uses Git LFS for potential large file support. The `.git/hooks` directory contains pre-push and post-commit hooks for LFS integration.

Standard git workflow:
```bash
# Create feature branch
git checkout -b feature/improve-docs

# Make changes to SKILL.md or evals.json
# Commit changes
git add .agents/skills/vercelops/

# Test the skill locally before pushing
# Create pull request to master
```

## Testing the Skill

While this repository doesn't have automated tests, you should:

1. **Validate JSON syntax**: Ensure `evals.json` is valid JSON
2. **Verify markdown rendering**: Check that SKILL.md renders correctly
3. **Manual smoke tests**: Install the skill in an agent and test key workflows
4. **Review command accuracy**: Verify commands match the current Vercel CLI version
5. **Test trigger conditions**: Ensure the skill activates for appropriate user queries
