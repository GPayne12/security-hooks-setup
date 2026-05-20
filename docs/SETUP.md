# Setup Guide

## Prerequisites

- macOS or Linux
- Git installed
- [Homebrew](https://brew.sh) (macOS)

## 1. Install git-secrets

```bash
brew install git-secrets
```

## 2. Clone this repo

```bash
git clone git@github.com:GPayne12/security-hooks-setup.git
cd security-hooks-setup
```

## 3. Install the hook into your project

```bash
cp hooks/pre-push /path/to/your-project/.git/hooks/pre-push
chmod +x /path/to/your-project/.git/hooks/pre-push
```

## 4. Register secret patterns with git-secrets

Run these inside your project directory:

```bash
git secrets --add 'AKIA[0-9A-Z]{16}'          # AWS access keys
git secrets --add 'sk-[a-zA-Z0-9]{32,}'        # OpenAI / Stripe keys
git secrets --add 'ghp_[a-zA-Z0-9]{36}'        # GitHub personal tokens
git secrets --add 'xox[baprs]-[0-9a-zA-Z]{10,}' # Slack tokens
```

## 5. Verify the hook is active

```bash
ls -la /path/to/your-project/.git/hooks/pre-push
```

You should see `-rwxr-xr-x` permissions.

## What the hook blocks

| Check | What it catches |
|---|---|
| `.env` files | Credentials, API keys, secrets |
| `node_modules/` | Large dependency folders |
| `dist/` | Build artifacts |
| `git-secrets` scan | Key patterns in all committed files |
| `npm audit` | High/critical vulnerabilities |

## Troubleshooting

**Hook not running?** Confirm the file is executable:
```bash
chmod +x .git/hooks/pre-push
```

**git-secrets not found?**
```bash
brew install git-secrets
```

**False positive blocked your push?** Review the flagged file and remove any matching patterns, or add a git-secrets allowlist entry:
```bash
git secrets --add --allowed 'your-safe-pattern'
```
