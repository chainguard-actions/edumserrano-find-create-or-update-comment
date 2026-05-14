# Hardening Report: edumserrano--find-create-or-update-comment/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **edumserrano--find-create-or-update-comment/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references three external actions using mutable version tags instead of pinned 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream tags are moved or compromised. Failing references:
- `peter-evans/find-comment@v3.0.0` (Find Comment step)
- `peter-evans/create-or-update-comment@v4.0.0` (Create comment step)
- `peter-evans/create-or-update-comment@v4.0.0` (Update comment step)

Each should be replaced with a full SHA digest, e.g. `peter-evans/find-comment@<40-char-sha> # v3.0.0`.

Locations:

- `action.yml:68`
- `action.yml:78`
- `action.yml:88`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in action.yml to their full 40-character commit SHAs: peter-evans/find-comment@v3.0.0 → SHA d5fe37641ad8451bdd80312415672ba26c86575e, and both peter-evans/create-or-update-comment@v4.0.0 references → SHA 71345be0265236311c031f5c7866368bd1eff043. Original version tags preserved as inline comments.

