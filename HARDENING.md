# Hardening Report: edumserrano--find-create-or-update-comment/v2.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **edumserrano--find-create-or-update-comment/v2.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character SHA commit hashes. This exposes the action to supply-chain attacks if the referenced tags are moved or the upstream repositories are compromised. Failing references: `peter-evans/find-comment@v2.4.0` (line 57), `peter-evans/create-or-update-comment@v3.1.0` (line 65), `peter-evans/create-or-update-comment@v3.1.0` (line 76). Each should be replaced with the full commit SHA, e.g. `peter-evans/find-comment@<40-char-sha> # v2.4.0`.

Locations:

- `action.yml:57`
- `action.yml:65`
- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned `uses:` references in action.yml:
- `peter-evans/find-comment@v2.4.0` → `peter-evans/find-comment@a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0` (line 57)
- `peter-evans/create-or-update-comment@v3.1.0` → `peter-evans/create-or-update-comment@23ff15729ef2fc348714a3bb66d2f655ca9066f2 # v3.1.0` (lines 65 and 76, both occurrences replaced)
SHAs were resolved using lookup_action_sha against the upstream repositories.

