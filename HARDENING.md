<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.2** was hardened automatically. 5 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references three external actions by mutable version tags instead of full 40-character SHA commit hashes, making the action vulnerable to supply-chain attacks if the upstream tag is moved: `peter-evans/find-comment@v2.2.1` (line 37), `peter-evans/create-or-update-comment@v2.1.1` (line 46), and `peter-evans/create-or-update-comment@v2.1.1` (line 55).

Locations:

- `action.yml:37`
- `action.yml:46`
- `action.yml:55`

### unpinned-uses (severity: high)

`.github/workflows/test-action.yml` references `actions/checkout@v3` (a mutable tag) in all three jobs instead of a pinned SHA digest.

Locations:

- `.github/workflows/test-action.yml:26`
- `.github/workflows/test-action.yml:55`
- `.github/workflows/test-action.yml:80`

### unpinned-uses (severity: high)

`.github/workflows/test-action-gh-marketplace.yml` references `actions/checkout@v3` and `edumserrano/find-create-or-update-comment@v1` (both mutable tags) in all three jobs instead of pinned SHA digests.

Locations:

- `.github/workflows/test-action-gh-marketplace.yml:26`
- `.github/workflows/test-action-gh-marketplace.yml:33`
- `.github/workflows/test-action-gh-marketplace.yml:55`
- `.github/workflows/test-action-gh-marketplace.yml:62`
- `.github/workflows/test-action-gh-marketplace.yml:80`
- `.github/workflows/test-action-gh-marketplace.yml:85`

### script-injection (severity: high)

Rule (a) violation: A `${{ ... }}` expression is interpolated directly inside a `run:` shell block. The line `$errorOutcome = '${{ steps.action-bad-input.outcome }}'` embeds the step output directly into the PowerShell script string before the shell executes it. An attacker who can influence the step outcome label could inject arbitrary PowerShell commands.

Locations:

- `.github/workflows/test-action.yml:91`

### script-injection (severity: high)

Rule (a) violation: A `${{ ... }}` expression is interpolated directly inside a `run:` shell block. The line `$errorOutcome = '${{ steps.action-bad-input.outcome }}'` embeds the step output directly into the PowerShell script string before the shell executes it. An attacker who can influence the step outcome label could inject arbitrary PowerShell commands.

Locations:

- `.github/workflows/test-action-gh-marketplace.yml:96`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, script-injection

**Notes:**

Fixed all unpinned action references by resolving real commit SHAs via lookup_action_sha:
- action.yml: peter-evans/find-comment@v2.2.1 → @85a676a52594b4481e0532825a2d8906ef96dac2, peter-evans/create-or-update-comment@v2.1.1 → @67dcc547d311b736a8e6c5c236542148a47adc3d (both occurrences)
- test-action.yml: actions/checkout@v3 → @a37ce9120846195fa4ece8f58b268e6043cb2f26 (all 3 jobs)
- test-action-gh-marketplace.yml: actions/checkout@v3 → @a37ce9120846195fa4ece8f58b268e6043cb2f26 (all 3 jobs), edumserrano/find-create-or-update-comment@v1 → @60a62b88d02efeb2c405e578d3a2b47ea0b230b1 (all 3 jobs)

Fixed script injection in both test workflow files: moved ${{ steps.action-bad-input.outcome }} out of the PowerShell run: block into an env: block as ERROR_OUTCOME, then referenced it as $env:ERROR_OUTCOME in the shell script. This prevents attacker-controlled step outcome values from being interpolated directly into the shell string.

