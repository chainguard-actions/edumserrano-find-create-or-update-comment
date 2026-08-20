<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v2.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v2.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All three `uses:` references in action.yml are pinned to mutable version tags rather than immutable full 40-character SHA commit hashes. This exposes the action to supply-chain attacks if the upstream repositories are compromised or tags are moved. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 57)
- `peter-evans/create-or-update-comment@v3.1.0` (line 66)
- `peter-evans/create-or-update-comment@v3.1.0` (line 77)

Each should be replaced with the corresponding full SHA, e.g. `peter-evans/find-comment@<40-char-sha> # v2.4.0`.

Locations:

- `action.yml:57`
- `action.yml:66`
- `action.yml:77`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned `uses:` references in hardened/action/action.yml to their full 40-character SHA commit hashes: `peter-evans/find-comment@v2.4.0` → SHA `a54c31d7fa095754bfef525c0c8e5e5674c4b4b1`, and both `peter-evans/create-or-update-comment@v3.1.0` references → SHA `23ff15729ef2fc348714a3bb66d2f655ca9066f2`. Original version tags are preserved as inline comments for readability.

