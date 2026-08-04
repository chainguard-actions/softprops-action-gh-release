<!-- markdownlint-disable -->

# Hardening Report: softprops--action-gh-release/v2.4.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--action-gh-release/v2.4.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key, and the single job (`build`) also has no job-level `permissions:` key. This means the workflow runs with GitHub's default token permissions, which include write access to repository contents and other scopes. A minimal explicit permissions block (e.g. `permissions: contents: read`) should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions: contents: read` block to `.github/workflows/main.yml`. The workflow only performs a checkout and runs npm build/test/format steps, so `contents: read` is the minimal permission required. This replaces the implicit default token permissions (which include write access) with an explicit minimal set.

