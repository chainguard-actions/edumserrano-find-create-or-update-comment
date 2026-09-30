<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references external actions using mutable version tags instead of pinned full-length commit SHAs. This exposes the action to supply-chain attacks where a tag could be moved to point to malicious code. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 38)
- `peter-evans/create-or-update-comment@v3.0.1` (line 44)
- `peter-evans/create-or-update-comment@v3.0.1` (line 51)

Each should be replaced with the full 40-character commit SHA, e.g. `peter-evans/find-comment@<sha> # v2.4.0`.

Locations:

- `action.yml:38`
- `action.yml:44`
- `action.yml:51`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in hardened/action/action.yml:
- `peter-evans/find-comment@v2.4.0` (line 38) → `peter-evans/find-comment@a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0`
- `peter-evans/create-or-update-comment@v3.0.1` (lines 44 & 51) → `peter-evans/create-or-update-comment@ca08ebd5dc95aa0cd97021e9708fcd6b87138c9b # v3.0.1`

SHAs were resolved via lookup_action_sha and the original version tags are preserved as inline comments.

