# Vercel Operations Skill

A portable agent skill for working with the Vercel cloud platform and CLI. It is packaged in the universal `.agents/skills` layout so it can be reused by tools that follow the emerging shared skill convention, including `skills.sh`-compatible tooling.

## What This Skill Does

The **vercelops** skill provides complete command reference and workflow guidance for:

- **Project Setup**: Initialize new projects, link existing projects, pull settings
- **Deployment Operations**: Preview and production deployments, rollback, promote, inspect
- **Local Development**: Run dev server with edge emulation, test deployments locally
- **Environment Variables**: Manage secrets and scoped environment variables
- **Domain & DNS**: Add custom domains, configure SSL, manage DNS records
- **Logs & Monitoring**: Stream deployment logs, debug issues
- **Project Management**: List projects, switch teams, manage Git integrations
- **Advanced Operations**: Cache management, webhooks, blob storage, API calls

## Repository Layout

```text
.agents/
  skills/
    vercelops/
      SKILL.md
      evals/
```

The canonical installable skill folder in this repo is `.agents/skills/vercelops/`.

## Installation

### skills.sh install

If you use the `skills.sh` ecosystem, install directly from GitHub:

```bash
npx skills add https://github.com/rajivmehtaflex/vercelops-skill --skill vercelops
```

This resolves the skill from `.agents/skills/vercelops` in this repository.

### Universal install

Copy `.agents/skills/vercelops` into your agent's skills directory.

Examples:

- Claude Code: `~/.claude/skills/vercelops`
- Codex: `~/.codex/skills/vercelops`
- Any `skills.sh`-compatible tool: its configured skills directory

### Option 1: Clone the Repository

```bash
git clone https://github.com/rajivmehtaflex/vercelops-skill.git
mkdir -p ~/.claude/skills
cp -r vercelops-skill/.agents/skills/vercelops ~/.claude/skills/
```

### Option 2: Manual Installation

1. Download the `.agents/skills/vercelops` folder from this repository.
2. Place it in your tool's skills directory as `vercelops/`.
3. Restart the tool if it loads skills only at startup.

## Prerequisites

Installing the skill into an agent is separate from having the OS tools required to execute the commands the skill recommends.

- `Node.js` and `npm`: required to install and update the Vercel CLI.
- `Vercel CLI` (`vercel`): install with `npm i -g vercel`.
- `Vercel account`: required for project, deployment, env, and domain operations.
- Authenticated Vercel session: run `vercel login` before remote operations.
- `Git`: recommended for clone-based workflows and common Vercel Git integrations.
- Project-specific runtime tools: your app may still need its own framework/runtime dependencies for local development and builds.

## Requirements

- **Vercel CLI installed**: `npm i -g vercel`
- **Logged into Vercel**: Run `vercel login` before using deployment commands

## Usage Examples

### Deploy a Next.js Application

```bash
# Initialize a new project
vercel init nextjs my-app
cd my-app

# Run locally
vercel dev

# Deploy to preview
vercel

# Deploy to production
vercel --prod
```

### Debug a Broken Deployment

```bash
# List recent deployments
vercel ls

# Inspect specific deployment
vercel inspect <deployment-id>

# View logs
vercel logs <deployment-url> --since 1h

# Rollback if needed
vercel rollback <deployment-id>
```

### Add Environment Variables

```bash
# Add production-only variable
vercel env add DATABASE_URL production

# Add preview variable
vercel env add API_KEY preview

# Add development variable
vercel env add DEBUG development

# List all variables
vercel env ls
```

### Configure Custom Domain

```bash
# Add custom domain
vercel domains add example.com

# Add SSL certificate
vercel certs add example.com

# Set alias for production
vercel alias set <production-url> example.com
```

## Skill Content

The skill includes:

- **Complete command reference** organized by use case
- **Common workflows** for new projects, existing projects, debugging, and domain setup
- **vercel.json configuration** examples
- **Framework-specific notes** for Next.js, Nuxt, SvelteKit, Astro, and static sites
- **Troubleshooting guides** for build failures, deployment issues, and domain problems
- **Best practices** for production deployments
- **Git hooks integration** for CI/CD

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## Author

Created for the Claude Code community to simplify Vercel platform operations.

---

**Note**: This skill requires the Vercel CLI to be installed and configured. Make sure to run `vercel login` before performing any deployment operations.
