# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **edumserrano--find-create-or-update-comment/v1.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references external actions using mutable version tags instead of immutable 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream tags are moved or compromised. Failing references:
- `peter-evans/find-comment@v2.2.1` (line 36)
- `peter-evans/create-or-update-comment@v2.1.1` (line 43)
- `peter-evans/create-or-update-comment@v2.1.1` (line 51)
Each should be pinned to a full SHA, e.g. `peter-evans/find-comment@<40-char-sha> # v2.2.1`.

Locations:

- `action.yml:36`
- `action.yml:43`
- `action.yml:51`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in action.yml to their full 40-character commit SHAs: peter-evans/find-comment@v2.2.1 → @85a676a52594b4481e0532825a2d8906ef96dac2, and both occurrences of peter-evans/create-or-update-comment@v2.1.1 → @67dcc547d311b736a8e6c5c236542148a47adc3d. Original version tags are preserved as inline comments for readability.

