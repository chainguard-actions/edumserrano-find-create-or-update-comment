<!-- markdownlint-disable -->

# Hardening Report: edumserrano--find-create-or-update-comment/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **edumserrano--find-create-or-update-comment/v1.0.3** was hardened automatically. 3 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml references third-party actions using mutable version tags instead of full 40-character commit SHAs. Failing references: `peter-evans/find-comment@v2.4.0` and `peter-evans/create-or-update-comment@v3.0.1` (used twice). These tags can be moved by the upstream repository owner, enabling supply-chain attacks.

Locations:

- `action.yml:37`
- `action.yml:43`
- `action.yml:52`

### unpinned-uses (severity: high)

Workflow files reference actions using mutable version tags instead of full 40-character commit SHAs. Failing references in test-action-gh-marketplace.yml: `actions/checkout@v3` (3 occurrences) and `edumserrano/find-create-or-update-comment@v1` (3 occurrences). Failing references in test-action.yml: `actions/checkout@v3` (3 occurrences). These tags can be moved by upstream maintainers, enabling supply-chain attacks.

Locations:

- `.github/workflows/test-action-gh-marketplace.yml:22`
- `.github/workflows/test-action-gh-marketplace.yml:34`
- `.github/workflows/test-action-gh-marketplace.yml:47`
- `.github/workflows/test-action-gh-marketplace.yml:59`
- `.github/workflows/test-action-gh-marketplace.yml:73`
- `.github/workflows/test-action-gh-marketplace.yml:76`
- `.github/workflows/test-action.yml:23`
- `.github/workflows/test-action.yml:46`
- `.github/workflows/test-action.yml:70`

### script-injection (severity: high)

Rule (a) violation: A `${{ }}` expression is interpolated directly inside a `run:` shell script. In both workflow files, the step 'The action should fail the step if it encounters an error' contains: `$errorOutcome = '${{ steps.action-bad-input.outcome }}'`. The `steps.*.outputs.*` context value is injected directly into the PowerShell script string before the shell processes it, allowing an attacker who can influence the step outcome value to inject arbitrary PowerShell commands.

Locations:

- `.github/workflows/test-action-gh-marketplace.yml:87`
- `.github/workflows/test-action.yml:81`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, script-injection

**Notes:**

Fixed all three findings:

1. action.yml: Pinned peter-evans/find-comment@v2.4.0 → SHA a54c31d7fa095754bfef525c0c8e5e5674c4b4b1 and peter-evans/create-or-update-comment@v3.0.1 → SHA ca08ebd5dc95aa0cd97021e9708fcd6b87138c9b (both occurrences).

2. test-action-gh-marketplace.yml: Pinned actions/checkout@v3 → SHA a37ce9120846195fa4ece8f58b268e6043cb2f26 (3 occurrences) and edumserrano/find-create-or-update-comment@v1 → SHA 60a62b88d02efeb2c405e578d3a2b47ea0b230b1 (3 occurrences).

3. test-action.yml: Pinned actions/checkout@v3 → SHA a37ce9120846195fa4ece8f58b268e6043cb2f26 (3 occurrences).

4. Script injection in both workflow files: Moved ${{ steps.action-bad-input.outcome }} out of the PowerShell run script into the step's env: block as ERROR_OUTCOME, then referenced it as $env:ERROR_OUTCOME in the PowerShell script.

