<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-github-status/v4.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-github-status/v4.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in the workflow files are pinned to mutable version tags (e.g. @v4, @v5, @v6) rather than immutable 40-character SHA commit hashes. This means a compromised or malicious update to any of these actions could silently affect this workflow without any change to the workflow file itself.

Affected references:
- .github/workflows/ci.yml: `actions/checkout@v4` (×2)
- .github/workflows/labels.yml: `actions/checkout@v4`, `crazy-max/ghaction-github-labeler@v5`
- .github/workflows/test.yml: `actions/checkout@v4`, `docker/bake-action@v6`, `codecov/codecov-action@v5`
- .github/workflows/validate.yml: `actions/checkout@v4`, `docker/bake-action/subaction/list-targets@v6`, `docker/bake-action@v6`

Each should be replaced with a full 40-character SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/ci.yml:33`
- `.github/workflows/ci.yml:43`
- `.github/workflows/labels.yml:33`
- `.github/workflows/labels.yml:35`
- `.github/workflows/test.yml:21`
- `.github/workflows/test.yml:24`
- `.github/workflows/test.yml:28`
- `.github/workflows/validate.yml:24`
- `.github/workflows/validate.yml:27`
- `.github/workflows/validate.yml:43`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 10 unpinned `uses:` references across 4 workflow files:
- actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262 # v4 (used in ci.yml ×2, labels.yml, test.yml, validate.yml)
- crazy-max/ghaction-github-labeler@v5 → @24d110aa46a59976b8a7f35518cb7f14f434c916 # v5 (labels.yml)
- docker/bake-action@v6 → @5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 # v6 (test.yml, validate.yml ×2)
- docker/bake-action/subaction/list-targets@v6 → @5be5f02ff8819ecd3092ea6b2e6261c31774f2b4 # v6 (validate.yml)
- codecov/codecov-action@v5 → @0fb7174895f61a3b6b78fc075e0cd60383518dac # v5 (test.yml)
All SHAs were resolved via lookup_action_sha and are immutable commit hashes.

