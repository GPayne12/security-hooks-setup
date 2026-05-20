# 🔐 Security Hooks Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/GPayne12/security-hooks-setup.svg)](https://github.com/GPayne12/security-hooks-setup/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/GPayne12/security-hooks-setup.svg)](https://github.com/GPayne12/security-hooks-setup/network/members)
[![Documentation](https://img.shields.io/badge/docs-GitHub%20Pages-blue)](https://github.com/GPayne12/security-hooks-setup/blob/main/docs/SETUP.md)

Repo for security and safety in AI-assisted coding operations

## What it does
The `pre-push` hook blocks pushes that contain:
- `.env` files or credentials
- `node_modules/` or `dist/` build artifacts
- Secrets detected by `git-secrets` (API keys, tokens)
- High/critical npm vulnerabilities (if `package.json` present)

## Install into a project
```bash
cp hooks/pre-push /path/to/your-project/.git/hooks/pre-push
chmod +x /path/to/your-project/.git/hooks/pre-push
```

## Requirements
- [`git-secrets`](https://github.com/awslabs/git-secrets): `brew install git-secrets`
