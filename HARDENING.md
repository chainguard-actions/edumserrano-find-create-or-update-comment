<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character SHA digests. This exposes the action to supply-chain attacks if the upstream action tags are moved or overwritten. Failing references:
- `peter-evans/find-comment@v2.4.0` (line 40)
- `peter-evans/create-or-update-comment@v3.0.2` (line 47)
- `peter-evans/create-or-update-comment@v3.0.2` (line 56)
Each should be replaced with the full commit SHA, e.g. `peter-evans/find-comment@<40-char-sha> # v2.4.0`.

Locations:

- `action.yml:40`
- `action.yml:47`
- `action.yml:56`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three uses references in hardened/action/action.yml to immutable commit SHAs:
- peter-evans/find-comment@v2.4.0 → @a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0 (line 40)
- peter-evans/create-or-update-comment@v3.0.2 → @c6c9a1a66007646a28c153e2a8580a5bad27bcfa # v3.0.2 (lines 47 and 56)
Original version tags preserved as inline comments for readability.

