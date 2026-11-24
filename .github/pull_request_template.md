<!--
Thanks for contributing to the Backproof runner.

Found a security problem? Please don't open a pull request. Report it privately as described in SECURITY.md.

Use a Conventional Commits title in plain language, for example:
fix(docker): remove orphaned volumes after a killed job
-->

## Problem

<!-- What is wrong or missing, in a sentence or two? Link the issue if there is one, for example: Fixes #123 -->

## Solution

<!-- How does this change solve it? Point out anything reviewers should look at closely. -->

## Testing

<!-- What did you run, and what happened? Never paste real keys, tokens, row contents or SQL from a dump. -->

## Checklist

- [ ] Every commit is signed off with `git commit -s`
- [ ] Code, logs, errors and fixtures contain no real secrets, customer data, row contents or SQL from a dump
- [ ] `CHANGELOG.md` is updated under "Unreleased" if users will notice this change

### If your change touches these areas

<!-- Tick the ones that apply and delete the rest. -->

- [ ] **Data sent to Backproof:** `docs/payload.md` is updated and `schema_version` is bumped
- [ ] **API:** `api/v1/openapi.yaml` changed first, with additions only, and the client is regenerated
- [ ] **Settings:** `docs/config.md` is updated
- [ ] **Restores or checks:** a fixture test reproduces the bug, and results use `fail` for a bad backup and `error` when the runner couldn't do its job
- [ ] **Containers or volumes:** they carry the runner labels, Postgres runs with network `none` and no published ports, and every code path cleans up
- [ ] **Install script:** it is POSIX `sh`, clean under `shellcheck`, and every prompt has a `--yes` path and a `--dry-run` description
- [ ] **Dependencies:** the Solution section explains why the standard library or an existing dependency can't do the job
