<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references external actions using mutable version tags instead of pinned 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream tag is moved or the repository is compromised.

Failing references:
- `peter-evans/find-comment@v2.4.0` (line 36) — should be pinned to a full SHA, e.g. `peter-evans/find-comment@<40-char-sha> # v2.4.0`
- `peter-evans/create-or-update-comment@v3.0.1` (line 43) — should be pinned to a full SHA
- `peter-evans/create-or-update-comment@v3.0.1` (line 50) — should be pinned to a full SHA

Locations:

- `action.yml:36`
- `action.yml:43`
- `action.yml:50`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in hardened/action/action.yml to full 40-character commit SHAs: peter-evans/find-comment@v2.4.0 → a54c31d7fa095754bfef525c0c8e5e5674c4b4b1, and both instances of peter-evans/create-or-update-comment@v3.0.1 → ca08ebd5dc95aa0cd97021e9708fcd6b87138c9b. Version tags are preserved as inline comments.

