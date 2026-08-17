<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-github-status/v3.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-github-status/v3.2.0** was hardened automatically. 8 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in ci.yml use mutable version tags instead of pinned 40-character SHA commits: `actions/checkout@v3` (appears twice). These are vulnerable to supply-chain attacks if the tag is moved.

Locations:

- `.github/workflows/ci.yml:23`
- `.github/workflows/ci.yml:31`

### unpinned-uses (severity: high)

All `uses:` references in labels.yml use mutable version tags instead of pinned 40-character SHA commits: `actions/checkout@v3` and `crazy-max/ghaction-github-labeler@v4`.

Locations:

- `.github/workflows/labels.yml:14`
- `.github/workflows/labels.yml:17`

### unpinned-uses (severity: high)

All `uses:` references in test.yml use mutable version tags instead of pinned 40-character SHA commits: `actions/checkout@v3`, `docker/bake-action@v3`, and `codecov/codecov-action@v3`.

Locations:

- `.github/workflows/test.yml:13`
- `.github/workflows/test.yml:16`
- `.github/workflows/test.yml:20`

### unpinned-uses (severity: high)

All `uses:` references in validate.yml use mutable version tags instead of pinned 40-character SHA commits: `actions/checkout@v3` (appears twice) and `docker/bake-action@v3`.

Locations:

- `.github/workflows/validate.yml:18`
- `.github/workflows/validate.yml:33`
- `.github/workflows/validate.yml:40`

### missing-permissions (severity: medium)

ci.yml has no top-level `permissions:` key and no job-level `permissions:` key on any of its jobs (`ci`, `ci-fail`). Without explicit permissions, the workflow inherits the default (potentially write) token permissions.

Locations:

- `.github/workflows/ci.yml:1`

### missing-permissions (severity: medium)

labels.yml has no top-level `permissions:` key and no job-level `permissions:` key on its `labeler` job. Without explicit permissions, the workflow inherits the default (potentially write) token permissions.

Locations:

- `.github/workflows/labels.yml:1`

### missing-permissions (severity: medium)

test.yml has no top-level `permissions:` key and no job-level `permissions:` key on its `test` job. Without explicit permissions, the workflow inherits the default (potentially write) token permissions.

Locations:

- `.github/workflows/test.yml:1`

### missing-permissions (severity: medium)

validate.yml has no top-level `permissions:` key and no job-level `permissions:` key on either of its jobs (`prepare`, `validate`). Without explicit permissions, the workflow inherits the default (potentially write) token permissions.

Locations:

- `.github/workflows/validate.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 4 workflow files: (1) ci.yml - pinned actions/checkout@v3 to SHA a37ce9120846195fa4ece8f58b268e6043cb2f26 in both jobs, added `permissions: {}`; (2) labels.yml - pinned actions/checkout@v3 and crazy-max/ghaction-github-labeler@v4 to their full SHAs (f4f6b96e7e747b5416cd470f3cfecf26abaa811e), added `permissions: {}`; (3) test.yml - pinned actions/checkout@v3, docker/bake-action@v3 (45c4bed4f4f232fb1466194a6cbdd7a18bcf0639), and codecov/codecov-action@v3 (ab904c41d6ece82784817410c45d8b8c02684457) to full SHAs, added `permissions: {}`; (4) validate.yml - pinned actions/checkout@v3 (twice) and docker/bake-action@v3 to full SHAs, added `permissions: {}`. All SHAs were resolved via lookup_action_sha.

