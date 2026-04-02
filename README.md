# Security Workflows

Reusable GitHub Actions security workflows for **BlackAsteroid**, **Cloutfit**, and **pablofmorales** repos.

## Usage

Add this to your repo at `.github/workflows/security.yml`:

```yaml
name: Security
on:
  pull_request:
  push:
    branches: [main]

jobs:
  security:
    uses: pablofmorales/security-workflows/.github/workflows/security.yml@main
    secrets: inherit
```

## What It Does

| Check | Job | What it catches |
|---|---|---|
| Socket Firewall | `supply-chain` | Malicious packages at install time |
| npm audit | `audit` | Known CVEs in dependency tree |
| Gitleaks | `secrets` | Accidentally committed secrets/tokens |

## Options

```yaml
jobs:
  security:
    uses: pablofmorales/security-workflows/.github/workflows/security.yml@main
    secrets: inherit
    with:
      node-version: "20"        # default: "20"
      package-manager: "pnpm"   # default: "npm" (npm, yarn, pnpm)
      audit-level: "critical"   # default: "high" (low, moderate, high, critical)
      skip-gitleaks: false      # default: false
      skip-audit: false         # default: false
```
