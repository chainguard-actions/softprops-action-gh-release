<!-- markdownlint-disable -->

# Hardening Report: softprops--action-gh-release/v2.6.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **softprops--action-gh-release/v2.6.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level `permissions:` key, and the single `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow runs with the default GitHub token permissions, which may be broader than necessary (e.g., write access to contents, packages, etc. depending on repository settings). A minimal explicit permissions block such as `permissions: read-all` or specific scopes like `contents: read` should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions

**Notes:**

Added a top-level `permissions: contents: read` block to `.github/workflows/main.yml`. This is the minimum permission required for the build/test workflow — `actions/checkout` needs read access to repository contents, and no other permissions are needed for the npm install, build, test, and format check steps.

