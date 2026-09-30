<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three `uses:` references in action.yml are pinned to mutable version tags instead of immutable 40-character commit SHAs. This exposes the action to supply-chain attacks if the upstream repositories are compromised or the tags are moved.

Failing references:
- `peter-evans/find-comment@v3.0.0` (line 57)
- `peter-evans/create-or-update-comment@v4.0.0` (line 70)
- `peter-evans/create-or-update-comment@v4.0.0` (line 82)

Each should be replaced with the full 40-character commit SHA, e.g.:
  `uses: peter-evans/find-comment@<40-char-sha> # v3.0.0`

Locations:

- `action.yml:57`
- `action.yml:70`
- `action.yml:82`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced all three mutable tag references in hardened/action/action.yml with full 40-character commit SHAs:
- `peter-evans/find-comment@v3.0.0` → `peter-evans/find-comment@d5fe37641ad8451bdd80312415672ba26c86575e # v3.0.0` (line 57)
- `peter-evans/create-or-update-comment@v4.0.0` → `peter-evans/create-or-update-comment@71345be0265236311c031f5c7866368bd1eff043 # v4.0.0` (lines 70 and 82, both occurrences updated)

