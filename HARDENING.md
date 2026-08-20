<!-- markdownlint-disable -->

# Hardening Report: softprops--action-gh-release/v2.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--action-gh-release/v2.5.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key and the `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (write access to contents, etc.). A minimal permissions block (e.g. `permissions: read-all` or specific scopes like `contents: read`) should be added at the top level or on each job.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions: contents: read` block to `.github/workflows/main.yml`. The workflow only checks out code and runs npm build/test/format commands, so `contents: read` is the minimal permission required. No job-level permissions override was needed since the single `build` job inherits the top-level permissions.

