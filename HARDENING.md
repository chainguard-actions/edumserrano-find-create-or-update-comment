<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v2.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v2.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character SHA digests. This exposes the action to supply-chain attacks: if the upstream repository is compromised, a malicious tag update would automatically be picked up. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 63)
- `peter-evans/create-or-update-comment@v3.1.0` (line 72, Create comment step)
- `peter-evans/create-or-update-comment@v3.1.0` (line 83, Update comment step)

Each should be replaced with the full 40-character commit SHA, e.g. `peter-evans/find-comment@<sha> # v2.4.0`.

Locations:

- `action.yml:63`
- `action.yml:72`
- `action.yml:83`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned `uses:` references in hardened/action/action.yml:
- `peter-evans/find-comment@v2.4.0` → `@a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0`
- `peter-evans/create-or-update-comment@v3.1.0` (Create comment step) → `@23ff15729ef2fc348714a3bb66d2f655ca9066f2 # v3.1.0`
- `peter-evans/create-or-update-comment@v3.1.0` (Update comment step) → `@23ff15729ef2fc348714a3bb66d2f655ca9066f2 # v3.1.0`

SHAs were resolved using lookup_action_sha and the original version tags are preserved as comments.

