# Changelog

All notable changes to the Backproof Runner action are documented here. The project follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## Unreleased

### Added

- A composite action that runs due Backproof backup tests on a GitHub-hosted runner with `backproofhq/runner:latest run --once`.
- A required `token` input for the CI token from the Backproof dashboard.
- The action exits with `0` when every due test passed or nothing was due, `1` when a backup failed and `2` when the runner couldn't do its job.
- Clear errors with exit code `2` when the token is empty, the runner isn't Linux or Docker isn't available.
- `BACKPROOF_*` and `BP_SRC_*` variables set on the step are forwarded to the runner by name, so local secrets can take precedence over sealed keys.
