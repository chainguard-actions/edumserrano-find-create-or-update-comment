# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **edumserrano--find-create-or-update-comment/v1.0.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml contains three `uses:` references pinned to mutable version tags instead of immutable 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream tags are moved or the repositories are compromised. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 40)
- `peter-evans/create-or-update-comment@v3.0.2` (line 46)
- `peter-evans/create-or-update-comment@v3.0.2` (line 55)

Each should be replaced with a full SHA pin, e.g. `peter-evans/find-comment@<40-char-sha> # v2.4.0`.

Locations:

- `action.yml:40`
- `action.yml:46`
- `action.yml:55`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references in action.yml to full 40-character commit SHAs:
- peter-evans/find-comment@v2.4.0 → @a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0
- peter-evans/create-or-update-comment@v3.0.2 (×2) → @c6c9a1a66007646a28c153e2a8580a5bad27bcfa # v3.0.2
SHAs were resolved using lookup_action_sha against the upstream repositories.

