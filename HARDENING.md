<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character SHA commit hashes. This exposes the action to supply-chain attacks if the referenced tags are moved or the upstream repositories are compromised.

Failing references:
- `uses: peter-evans/find-comment@v2.4.0` (line 40)
- `uses: peter-evans/create-or-update-comment@v3.0.2` (line 48, Create comment step)
- `uses: peter-evans/create-or-update-comment@v3.0.2` (line 56, Update comment step)

Each should be replaced with the full 40-character SHA of the intended commit, e.g.:
`uses: peter-evans/find-comment@<40-char-sha> # v2.4.0`

Locations:

- `action.yml:40`
- `action.yml:48`
- `action.yml:56`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references in hardened/action/action.yml to immutable 40-character SHA commit hashes:
- peter-evans/find-comment@v2.4.0 → @a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 # v2.4.0
- peter-evans/create-or-update-comment@v3.0.2 (both Create and Update comment steps) → @c6c9a1a66007646a28c153e2a8580a5bad27bcfa # v3.0.2
Original version tags preserved as inline comments for readability.

