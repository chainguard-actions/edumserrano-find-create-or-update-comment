<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All three `uses:` references in action.yml are pinned to mutable version tags rather than immutable 40-character SHA commit hashes. This exposes the action to supply-chain attacks if the upstream repositories are compromised or the tags are moved.

Failing references:
- `peter-evans/find-comment@v3.0.0` (line 57)
- `peter-evans/create-or-update-comment@v4.0.0` (line 67, Create comment step)
- `peter-evans/create-or-update-comment@v4.0.0` (line 78, Update comment step)

Each should be replaced with a full SHA pin, e.g.:
  `uses: peter-evans/find-comment@<40-char-sha> # v3.0.0`

Locations:

- `action.yml:57`
- `action.yml:67`
- `action.yml:78`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable tag references in hardened/action/action.yml to immutable SHA hashes:
- `peter-evans/find-comment@v3.0.0` → `peter-evans/find-comment@d5fe37641ad8451bdd80312415672ba26c86575e # v3.0.0` (line 57)
- `peter-evans/create-or-update-comment@v4.0.0` → `peter-evans/create-or-update-comment@71345be0265236311c031f5c7866368bd1eff043 # v4.0.0` (lines 67 and 78, both Create and Update comment steps)

### Iteration 2

**Fixes applied:** script-injection, unpinned-uses

**Notes:**

Fixed all script-injection findings by moving ${{ }} expressions into env: variables and referencing them as PowerShell env vars ($env:VAR_NAME) in run: blocks. Fixed all unpinned-uses findings by pinning: actions/checkout@v4 → SHA 11d5960a326750d5838078e36cf38b85af677262, gaurav-nelson/github-action-markdown-link-check@1.0.15 → SHA d53a906aa6b22b8979d33bc86170567e619495ec, edumserrano/find-create-or-update-comment@v2 → SHA 3d340543af6d2743c70ab2d525deeb0f12e290de. Changes applied across pr-dependabot-auto-merge.yml, markdown-link-check.yml, test-action-gh-marketplace.yml, and test-action.yml.

