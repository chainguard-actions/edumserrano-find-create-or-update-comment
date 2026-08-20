<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.4** was hardened automatically. 4 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references composite action steps using mutable version tags instead of full 40-character commit SHAs, making the action vulnerable to supply-chain attacks if those tags are moved. Failing references: `peter-evans/find-comment@v2.4.0` and `peter-evans/create-or-update-comment@v3.0.2` (appears twice).

Locations:

- `action.yml:37`
- `action.yml:44`
- `action.yml:51`

### unpinned-uses (severity: high)

Workflow files reference actions using mutable version tags instead of full 40-character commit SHAs. Failing references in pr-dependabot-auto-merge.yml: `actions/checkout@v3`. Failing references in test-action.yml: `actions/checkout@v3` (three times). Failing references in test-action-gh-marketplace.yml: `actions/checkout@v3` (three times) and `edumserrano/find-create-or-update-comment@v1` (three times).

Locations:

- `.github/workflows/pr-dependabot-auto-merge.yml:21`
- `.github/workflows/test-action.yml:27`
- `.github/workflows/test-action.yml:49`
- `.github/workflows/test-action.yml:68`
- `.github/workflows/test-action-gh-marketplace.yml:27`
- `.github/workflows/test-action-gh-marketplace.yml:49`
- `.github/workflows/test-action-gh-marketplace.yml:68`
- `.github/workflows/test-action-gh-marketplace.yml:30`
- `.github/workflows/test-action-gh-marketplace.yml:52`
- `.github/workflows/test-action-gh-marketplace.yml:71`

### script-injection (severity: high)

Sub-rule (a): A GitHub Actions expression is interpolated directly inside a `run:` shell command string. In pr-dependabot-auto-merge.yml, the value `${{ github.event.workflow_run.pull_requests[0].number }}` is embedded directly in a PowerShell run block: `$prNumber = "${{ github.event.workflow_run.pull_requests[0].number }}"`. An attacker who can control the PR number field (e.g. via a crafted event payload) could inject arbitrary shell commands. The value should be passed via an `env:` variable and the env var referenced as `$env:PR_NUMBER` instead.

Locations:

- `.github/workflows/pr-dependabot-auto-merge.yml:30`

### script-injection (severity: high)

Sub-rule (a): A GitHub Actions expression is interpolated directly inside a `run:` shell command string. The expression `${{ steps.action-bad-input.outcome }}` (a `steps.*` context value) is embedded directly in a PowerShell run block: `$errorOutcome = '${{ steps.action-bad-input.outcome }}'`. Any workflow-controllable value flowing through step outputs should be passed via an `env:` variable and referenced as `$env:ERROR_OUTCOME` instead.

Locations:

- `.github/workflows/test-action.yml:87`
- `.github/workflows/test-action-gh-marketplace.yml:87`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, script-injection

**Notes:**

Fixed all unpinned action references by resolving them to full 40-character commit SHAs: peter-evans/find-comment@v2.4.0 → a54c31d7fa095754bfef525c0c8e5e5674c4b4b1, peter-evans/create-or-update-comment@v3.0.2 → c6c9a1a66007646a28c153e2a8580a5bad27bcfa, actions/checkout@v3 → a37ce9120846195fa4ece8f58b268e6043cb2f26, edumserrano/find-create-or-update-comment@v1 → 60a62b88d02efeb2c405e578d3a2b47ea0b230b1. Fixed script injection in pr-dependabot-auto-merge.yml by moving github.event.workflow_run.pull_requests[0].number to env var PR_NUMBER. Fixed script injection in test-action.yml and test-action-gh-marketplace.yml by moving steps.action-bad-input.outcome to env var ERROR_OUTCOME and referencing it as $env:ERROR_OUTCOME in the PowerShell run blocks.

