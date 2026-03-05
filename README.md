# Vercel Operations Skill

A comprehensive Claude Code skill for working with the Vercel cloud platform and CLI. This skill helps you deploy applications, manage projects, configure environments, handle domains, and perform all Vercel-related operations.

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

## Installation

### Option 1: Clone the Repository

```bash
# Clone this repository
git clone https://github.com/rajivmehtaflex/vercelops-skill.git

# Copy the skill to your Claude skills directory
mkdir -p ~/.claude/skills
cp -r vercelops-skill/vercelops ~/.claude/skills/
```

### Option 2: Manual Installation

1. Download the `vercelops` folder from this repository
2. Place it in your Claude skills directory (`~/.claude/skills/`)
3. Restart Claude Code

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
