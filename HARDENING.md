<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-github-status/v5.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-github-status/v5.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in the workflow files use mutable version tags instead of pinned 40-character SHA commit hashes. This exposes the workflow to supply-chain attacks where a compromised or malicious tag update could execute arbitrary code in the runner. Failing references:
- `actions/checkout@v6` (appears in ci.yml, labels.yml, test.yml, validate.yml)
- `crazy-max/ghaction-github-labeler@v5` (labels.yml)
- `docker/bake-action@v6` (test.yml, validate.yml)
- `docker/bake-action/subaction/list-targets@v6` (validate.yml)
- `codecov/codecov-action@v5` (test.yml)

All should be replaced with their full 40-character SHA commit digest, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/ci.yml:33`
- `.github/workflows/ci.yml:41`
- `.github/workflows/labels.yml:33`
- `.github/workflows/labels.yml:36`
- `.github/workflows/test.yml:22`
- `.github/workflows/test.yml:25`
- `.github/workflows/test.yml:29`
- `.github/workflows/validate.yml:24`
- `.github/workflows/validate.yml:28`
- `.github/workflows/validate.yml:43`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable `uses:` references to full 40-character SHA commit hashes across four workflow files:
- ci.yml: `actions/checkout@v6` → `@d23441a48e516b6c34aea4fa41551a30e30af803 # v6` (2 occurrences)
- labels.yml: `actions/checkout@v6` → `@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`; `crazy-max/ghaction-github-labeler@v5` → `@24d110aa46a59976b8a7f35518cb7f14f434c916 # v5`
- test.yml: `actions/checkout@v6` → `@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`; `docker/bake-action@v6` → `@5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 # v6`; `codecov/codecov-action@v5` → `@0fb7174895f61a3b6b78fc075e0cd60383518dac # v5`
- validate.yml: `actions/checkout@v6` → `@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`; `docker/bake-action/subaction/list-targets@v6` → `@5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 # v6`; `docker/bake-action@v6` → `@5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 # v6`
All original tag names preserved as inline comments for readability.

