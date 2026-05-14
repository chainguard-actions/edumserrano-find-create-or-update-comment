# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **edumserrano--find-create-or-update-comment/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references three external actions using mutable version tags instead of pinned full-length SHA commit hashes. This exposes the action to supply-chain attacks where a tag could be silently moved to point to malicious code. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 36)
- `peter-evans/create-or-update-comment@v3.0.1` (line 43)
- `peter-evans/create-or-update-comment@v3.0.1` (line 51)
Each should be replaced with the corresponding full 40-character commit SHA, e.g. `peter-evans/find-comment@<sha> # v2.4.0`.

Locations:

- `action.yml:36`
- `action.yml:43`
- `action.yml:51`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in action.yml to their full 40-character commit SHAs: (1) peter-evans/find-comment@v2.4.0 → @a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0; (2) and (3) peter-evans/create-or-update-comment@v3.0.1 → @ca08ebd5dc95aa0cd97021e9708fcd6b87138c9b # v3.0.1. Original version tags preserved as inline comments for readability.

