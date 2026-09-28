<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references three external actions using mutable version tags instead of immutable full-length SHA commit digests. This exposes the action to supply-chain attacks if the upstream tag is moved or the repository is compromised.

Failing references:
- `peter-evans/find-comment@v3.0.0` (line 63)
- `peter-evans/create-or-update-comment@v4.0.0` (line 72, Create comment step)
- `peter-evans/create-or-update-comment@v4.0.0` (line 83, Update comment step)

Each should be replaced with the full 40-character commit SHA, e.g.:
  `uses: peter-evans/find-comment@<40-char-sha> # v3.0.0`

Locations:

- `action.yml:63`
- `action.yml:72`
- `action.yml:83`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three unpinned action references in hardened/action/action.yml:
- `peter-evans/find-comment@v3.0.0` → `peter-evans/find-comment@d5fe37641ad8451bdd80312415672ba26c86575e # v3.0.0` (line 63)
- `peter-evans/create-or-update-comment@v4.0.0` → `peter-evans/create-or-update-comment@71345be0265236311c031f5c7866368bd1eff043 # v4.0.0` (lines 72 and 83, both the Create comment and Update comment steps)

