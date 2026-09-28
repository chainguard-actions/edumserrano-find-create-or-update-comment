<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references composite action steps using mutable version tags instead of full 40-character commit SHA digests. This exposes the action to supply-chain attacks where a tag can be silently moved to point to malicious code. Failing references:
- `peter-evans/find-comment@v2.2.1`
- `peter-evans/create-or-update-comment@v2.1.1` (used twice)

Each should be pinned to a full SHA, e.g. `peter-evans/find-comment@<40-hex-sha> # v2.2.1`.

Locations:

- `action.yml:38`
- `action.yml:44`
- `action.yml:52`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in hardened/action/action.yml to full 40-character commit SHAs: peter-evans/find-comment@v2.2.1 → SHA 85a676a52594b4481e0532825a2d8906ef96dac2, and both occurrences of peter-evans/create-or-update-comment@v2.1.1 → SHA 67dcc547d311b736a8e6c5c236542148a47adc3d. Original version tags preserved as inline comments.

