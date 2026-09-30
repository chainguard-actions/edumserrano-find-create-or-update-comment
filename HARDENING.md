<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream repositories are compromised or the tags are moved. Failing references:
- `peter-evans/find-comment@v2.2.1` (line 36)
- `peter-evans/create-or-update-comment@v2.1.1` (line 43)
- `peter-evans/create-or-update-comment@v2.1.1` (line 50)

Each should be replaced with the full 40-character commit SHA, e.g. `peter-evans/find-comment@<sha> # v2.2.1`.

Locations:

- `action.yml:36`
- `action.yml:43`
- `action.yml:50`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references in hardened/action/action.yml to immutable commit SHAs:
- `peter-evans/find-comment@v2.2.1` → `peter-evans/find-comment@85a676a52594b4481e0532825a2d8906ef96dac2 # v2.2.1` (line 36)
- `peter-evans/create-or-update-comment@v2.1.1` → `peter-evans/create-or-update-comment@67dcc547d311b736a8e6c5c236542148a47adc3d # v2.1.1` (lines 43 and 50)
Original version tags are preserved as inline comments for readability.

