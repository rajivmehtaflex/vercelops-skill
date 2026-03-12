---
name: vercelops
description: "Use when working with Vercel cloud platform - deploying applications, managing projects, handling environment variables, configuring domains, monitoring logs, or any Vercel CLI operations. TRIGGER when user mentions: Vercel deployment, vercel deploy, vercel env, vercel domains, preview deployments, production deployments, edge functions, serverless functions on Vercel, vercel project setup, vercel CLI commands, or when deploying Next.js/Nuxt/SvelteKit/Astro apps to Vercel."
---

# Vercel Operations

This skill helps you work with the Vercel cloud platform and CLI. Use it whenever the user needs to deploy applications, manage projects, configure environments, handle domains, or perform any Vercel-related operations.

## Prerequisites

- User should be logged into Vercel CLI (`vercel login`)
- For first-time setup, ensure Vercel CLI is installed: `npm i -g vercel`

## Core Concepts

Vercel is a frontend cloud platform that provides:
- **Git-based deployments**: Automatic preview deployments on every push
- **Edge compute**: Serverless functions and edge middleware running globally
- **Multi-framework support**: Next.js, Nuxt, SvelteKit, Astro, Remix, and more
- **Built-in observability**: Logs, analytics, and performance monitoring
- **Team collaboration**: Role-based access, SSO, audit logs

## Command Reference by Use Case

### 1. Project Setup and Initialization

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel init <template>` | Create new project from template | `vercel init nextjs my-app` |
| `vercel link [path]` | Link local directory to existing project | `vercel link` |
| `vercel pull [path]` | Pull project settings from cloud | `vercel pull` |

### 2. Deployment Operations

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel` or `vercel deploy` | Deploy to preview (default) | `vercel` |
| `vercel --prod` | Deploy to production | `vercel --prod` |
| `vercel --prebuilt` | Deploy pre-built assets | `vercel --prebuilt` |
| `vercel build` | Build locally for inspection | `vercel build` |
| `vercel ls` | List all deployments | `vercel ls` |
| `vercel inspect <id>` | View deployment details | `vercel inspect abc123` |
| `vercel rm <id>` | Delete a deployment | `vercel rm abc123` |
| `vercel redeploy <id>` | Rebuild and redeploy | `vercel redeploy abc123` |
| `vercel rollback <id>` | Revert to previous deployment | `vercel rollback abc123` |
| `vercel promote <url>` | Promote preview to production | `vercel promote my-app.vercel.app` |

### 3. Local Development

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel dev` | Start local dev server with edge emulation | `vercel dev` |
| `vercel dev --listen 3001` | Run on custom port | `vercel dev --listen 3001` |
| `vercel curl <path>` | Test local deployment | `vercel curl /api/users` |

### 4. Environment Variables and Secrets

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel env add <name> <env>` | Add environment variable | `vercel env add API_KEY production` |
| `vercel env ls` | List all environment variables | `vercel env ls` |
| `vercel env rm <name> <env>` | Remove environment variable | `vercel env rm API_KEY preview` |
| `vercel secrets add <name>` | Add secret (encrypted) | `vercel secrets add stripe-key` |
| `vercel secrets ls` | List all secrets | `vercel secrets ls` |
| `vercel secrets rm <name>` | Remove secret | `vercel secrets rm stripe-key` |

### 5. Domain and DNS Management

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel domains add <domain>` | Add custom domain | `vercel domains add example.com` |
| `vercel domains ls` | List all domains | `vercel domains ls` |
| `vercel domains rm <domain>` | Remove domain | `vercel domains rm example.com` |
| `vercel alias set <url> <domain>` | Set alias for deployment | `vercel alias set abc123 app.example.com` |
| `vercel dns add <domain> <type> <value>` | Add DNS record | `vercel dns add example.com A 1.2.3.4` |
| `vercel certs add <domain>` | Add SSL certificate | `vercel certs add example.com` |

### 6. Logs and Monitoring

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel logs <url>` | Stream deployment logs | `vercel logs my-app.vercel.app` |
| `vercel logs --since 1h` | Logs from last hour | `vercel logs --since 1h` |
| `vercel logs --follow` | Follow logs in real-time | `vercel logs --follow` |
| `vercel open` | Open project in dashboard | `vercel open` |

### 7. Project and Team Management

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel projects ls` | List all projects | `vercel projects ls` |
| `vercel projects add <name>` | Create new project | `vercel projects add my-app` |
| `vercel projects rm <id>` | Delete project | `vercel projects rm abc123` |
| `vercel switch <scope>` | Switch team/scope | `vercel switch my-team` |
| `vercel teams ls` | List teams | `vercel teams ls` |
| `vercel whoami` | Show current user | `vercel whoami` |
| `vercel login` | Authenticate | `vercel login` |
| `vercel logout` | Log out | `vercel logout` |

### 8. Git Integration

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel git connect` | Connect Git repository | `vercel git connect` |
| `vercel git disconnect` | Disconnect Git repository | `vercel git disconnect` |
| `vercel git ls` | List connected repos | `vercel git ls` |

### 9. Advanced Operations

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel bisect` | Find deployment that introduced bug | `vercel bisect` |
| `vercel cache ls` | List cached items | `vercel cache ls` |
| `vercel cache rm <path>` | Clear cache | `vercel cache rm /api/users` |
| `vercel webhooks add <url>` | Add webhook | `vercel webhooks add https://...` |
| `vercel blob add <name>` | Create blob store | `vercel blob add my-store` |
| `vercel api <endpoint>` | Make authenticated API request | `vercel api /v2/deployments` |
| `vercel upgrade` | Upgrade CLI to latest | `vercel upgrade` |

### 10. Redirects and Routing

| Command | Purpose | Example |
|---------|---------|---------|
| `vercel redirects ls` | List redirects | `vercel redirects ls` |
| `vercel redirects add <src> <dst>` | Add redirect | `vercel redirects add /old /new` |

## Common Workflows

### New Project Workflow

```bash
# 1. Initialize new project
vercel init nextjs my-app
cd my-app

# 2. Run locally
vercel dev

# 3. Add environment variables (if needed)
vercel env add DATABASE_URL production

# 4. Deploy to preview
vercel

# 5. Deploy to production when ready
vercel --prod
```

### Existing Project Workflow

```bash
# 1. Link to existing project
vercel link

# 2. Pull latest settings
vercel pull

# 3. Run locally
vercel dev

# 4. Deploy changes
vercel

# 5. Promote to production
vercel promote <preview-url>
```

### Debugging Workflow

```bash
# 1. List recent deployments
vercel ls

# 2. Inspect specific deployment
vercel inspect <deployment-id>

# 3. View logs
vercel logs <deployment-url> --since 1h

# 4. If needed, rollback
vercel rollback <deployment-id>
```

### Domain Setup Workflow

```bash
# 1. Add custom domain
vercel domains add example.com

# 2. Configure DNS (follow instructions)
# Vercel will provide DNS records to add

# 3. Add/verify SSL certificate
vercel certs add example.com

# 4. Set alias for production
vercel alias set <production-url> example.com
```

## Global Options

- `--yes` / `-y`: Skip confirmation prompts
- `--debug`: Enable debug output
- `--token`: Use specific authentication token
- `--scope`: Set custom scope (team)
- `--cwd`: Set current working directory
- `--local-config`: Path to vercel.json
- `--force`: Force operation

## Environment Variable Scopes

Environment variables can be scoped to:
- **production**: Production deployments
- **preview**: Preview/PR deployments
- **development**: Local development with `vercel dev`

## Configuration Files

### vercel.json

Common configuration file for project settings:

```json
{
  "name": "my-app",
  "version": 2,
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "framework": "nextjs",
  "regions": ["iad1"],
  "env": {
    "MY_VAR": "@my-secret"
  },
  "build": {
    "env": {
      "BUILD_VAR": "value"
    }
  },
  "routes": [
    {
      "src": "/api/(.*)",
      "dest": "/api/$1"
    }
  ],
  "rewrites": [
    {
      "source": "/old/:path*",
      "destination": "/new/:path*"
    }
  ],
  "redirects": [
    {
      "source": "/old",
      "destination": "/new",
      "statusCode": 301
    }
  ]
}
```

## Framework-Specific Notes

### Next.js
- Automatic framework detection
- Image optimization enabled by default
- ISR (Incremental Static Regeneration) supported

### Nuxt/SvelteKit/Astro
- Requires appropriate build configuration
- May need `vercel.json` for output directory
- Edge middleware supported

### Static Sites
- Set `version: 2` in vercel.json
- Specify `outputDirectory`
- Can use `vercel --prebuilt` for CI/CD

## Troubleshooting

### Build Failures
1. Check logs: `vercel logs <url> --since 1h`
2. Verify build command in vercel.json
3. Check environment variables: `vercel env ls`
4. Try local build: `vercel build`

### Deployment Issues
1. Verify authentication: `vercel whoami`
2. Check project link: `cat .vercel/project.json`
3. Inspect deployment: `vercel inspect <id>`
4. Check quota limits in dashboard

### Domain Problems
1. Verify DNS: `vercel dns ls <domain>`
2. Check certificate: `vercel certs ls`
3. Use `vercel domains inspect <domain>`

## Best Practices

1. **Use environment-specific variables**: Scope variables properly (production/preview/development)
2. **Link before deploying**: Always `vercel link` existing projects
3. **Test with preview**: Always deploy to preview before `--prod`
4. **Monitor logs**: Use `vercel logs --follow` during debugging
5. **Use vercel.json**: Keep configuration in version control
6. **Leverage edge functions**: Use `vercel dev` to test edge behavior locally
7. **Set aliases**: Use descriptive aliases for production deployments

## Integration with Git Hooks

For CI/CD integration, use:
```bash
# Non-interactive mode for CI
vercel --prod --yes --token $VERCEL_TOKEN
```

For preview deployments from PRs:
```bash
vercel --yes --token $VERCEL_TOKEN
```

## When to Use Vercel CLI vs Dashboard

- **Use CLI for**: Deployment, environment management, local development, CI/CD automation
- **Use Dashboard for**: Visual analytics, team management, spending overview, complex project settings
