<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-github-status/v4.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-github-status/v4.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across all workflow files use mutable tag refs (@v4, @v3) instead of full 40-character SHA commit digests. This exposes the workflow to supply-chain attacks if a referenced action's tag is moved or compromised. Affected references: ci.yml — actions/checkout@v4 (×2); labels.yml — actions/checkout@v4, crazy-max/ghaction-github-labeler@v4; test.yml — actions/checkout@v4, docker/bake-action@v3, codecov/codecov-action@v3; validate.yml — actions/checkout@v4, docker/bake-action@v3 (×2).

Locations:

- `.github/workflows/ci.yml:24`
- `.github/workflows/ci.yml:31`
- `.github/workflows/labels.yml:22`
- `.github/workflows/labels.yml:25`
- `.github/workflows/test.yml:17`
- `.github/workflows/test.yml:20`
- `.github/workflows/test.yml:23`
- `.github/workflows/validate.yml:22`
- `.github/workflows/validate.yml:38`
- `.github/workflows/validate.yml:41`

### missing-permissions (severity: medium)

None of the workflow files define a top-level `permissions:` key, and no individual job within any of these files defines a `permissions:` key. Without explicit permissions, workflows run with the default token permissions (which may be read-write depending on repository settings), granting broader access than necessary. Each workflow should declare minimal required permissions.

Locations:

- `.github/workflows/ci.yml:1`
- `.github/workflows/labels.yml:1`
- `.github/workflows/test.yml:1`
- `.github/workflows/validate.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 10 unpinned action references across 4 workflow files by replacing mutable tags with full 40-character SHA digests (preserving tags as comments). Added top-level permissions blocks to all 4 workflow files: ci.yml and test.yml and validate.yml get 'contents: read'; labels.yml gets 'contents: read', 'issues: write', and 'pull-requests: write' since the labeler action needs to manage labels on issues and PRs.

