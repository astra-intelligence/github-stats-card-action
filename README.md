# GitHub Stats Card Action 🔥

Replace your broken `github-readme-stats` card with a beautiful, live-updating alternative. Zero setup, no API keys needed.

## Why this exists

The original `github-readme-stats.vercel.app` is **permanently deprecated** (503 SERVICE_UNAVAILABLE). This action gives you a working replacement in 2 minutes.

## How it works

1. This action fetches a stats SVG from the GitHub Stats Card API every time it runs
2. The SVG shows your **total stars, followers, repos, top language, and gists**
3. It gets committed to your profile repo automatically
4. Your README references the SVG directly — no external service dependency

## Usage

### 1. Create a workflow file

In your profile repo (username/username), create `.github/workflows/stats-card.yml`:

```yaml
name: Update GitHub Stats Card

on:
  schedule:
    - cron: '0 */6 * * *'   # every 6 hours
  workflow_dispatch:         # manual trigger

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: astra-intelligence/github-stats-card-action@v1
        with:
          username: ${{ github.repository_owner }}
          theme: dark
```

### 2. Reference the SVG in your README

```markdown
![GitHub Stats](github-stats-card.svg)
```

That's it. After the first workflow run, the SVG appears in your repo and renders on your profile.

## Options

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `username` | ✅ | — | Your GitHub username |
| `theme` | ❌ | `dark` | Theme: dark, light, ocean, sunset, forest, midnight, copper, plasma |
| `filename` | ❌ | `github-stats-card.svg` | Output SVG filename |
| `license_key` | ❌ | — | Gumroad license key for premium themes & no watermark |

## Themes

| Theme | Free/Pro |
|-------|----------|
| `dark` | Free |
| `light` | Free |
| `ocean` | Pro ($1) |
| `sunset` | Pro ($1) |
| `forest` | Pro ($1) |
| `midnight` | Pro ($1) |
| `copper` | Pro ($1) |
| `plasma` | Pro ($1) |

## Premium ($1)

Remove the watermark and unlock 6 exclusive themes. Get a lifetime license:

[https://grantshatz.gumroad.com/l/github-stats-card-pro](https://grantshatz.gumroad.com/l/github-stats-card-pro)

## License

MIT — free for any use.