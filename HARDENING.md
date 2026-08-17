<!-- markdownlint-disable -->

# Hardening Report: crazy-max--ghaction-github-status/v4.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **crazy-max--ghaction-github-status/v4.1.0** was hardened automatically. 8 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in ci.yml are pinned to mutable version tags instead of immutable 40-character SHA digests, making the workflow vulnerable to supply-chain attacks if the referenced action is compromised or the tag is moved. Failing references: `actions/checkout@v4` (appears twice).

Locations:

- `.github/workflows/ci.yml:24`
- `.github/workflows/ci.yml:33`

### unpinned-uses (severity: high)

All `uses:` references in labels.yml are pinned to mutable version tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4`, `crazy-max/ghaction-github-labeler@v5`.

Locations:

- `.github/workflows/labels.yml:22`
- `.github/workflows/labels.yml:26`

### unpinned-uses (severity: high)

All `uses:` references in test.yml are pinned to mutable version tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4`, `docker/bake-action@v5`, `codecov/codecov-action@v4`.

Locations:

- `.github/workflows/test.yml:16`
- `.github/workflows/test.yml:19`
- `.github/workflows/test.yml:23`

### unpinned-uses (severity: high)

All `uses:` references in validate.yml are pinned to mutable version tags instead of immutable 40-character SHA digests. Failing references: `actions/checkout@v4` (appears twice), `docker/bake-action@v5`.

Locations:

- `.github/workflows/validate.yml:22`
- `.github/workflows/validate.yml:35`
- `.github/workflows/validate.yml:41`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g., write access to contents). Explicit minimal permissions should be declared.

Locations:

- `.github/workflows/ci.yml:1`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad. Explicit minimal permissions should be declared.

Locations:

- `.github/workflows/labels.yml:1`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad. Explicit minimal permissions should be declared.

Locations:

- `.github/workflows/test.yml:1`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and no job-level `permissions:` key on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad. Explicit minimal permissions should be declared.

Locations:

- `.github/workflows/validate.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 4 workflow files:

1. ci.yml: Pinned actions/checkout@v4 to SHA 34e114876b0b11c390a56381ad16ebd13914f8d5 (appears twice), added top-level `permissions: contents: read`.

2. labels.yml: Pinned actions/checkout@v4 to SHA 34e114876b0b11c390a56381ad16ebd13914f8d5 and crazy-max/ghaction-github-labeler@v5 to SHA 24d110aa46a59976b8a7f35518cb7f14f434c916, added top-level `permissions: contents: read`.

3. test.yml: Pinned actions/checkout@v4 to SHA 34e114876b0b11c390a56381ad16ebd13914f8d5, docker/bake-action@v5 to SHA 4a9a8d494466d37134e2bfca2d3a8de8fb2681ad, and codecov/codecov-action@v4 to SHA b9fd7d16f6d7d1b5d2bec1a2887e65ceed900238, added top-level `permissions: contents: read`.

4. validate.yml: Pinned actions/checkout@v4 to SHA 34e114876b0b11c390a56381ad16ebd13914f8d5 (appears twice) and docker/bake-action@v5 to SHA 4a9a8d494466d37134e2bfca2d3a8de8fb2681ad, added top-level `permissions: contents: read`.

All original tags are preserved as inline comments for readability.

