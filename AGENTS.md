# Backproof Runner action

Instructions for coding agents working in `backproofhq/runner-action`. Read this file fully before every task.

## What this repo is

The GitHub Action that runs the open-source [Backproof runner](https://github.com/backproofhq/runner) (`backproofhq/runner`) in a GitHub workflow. It is a composite action that checks the runner environment and starts the runner image with `run --once`. It lives in its own repo so it can be listed on GitHub Marketplace. People trust us with their backups, so correctness and safety come before speed.

License: Apache 2.0.

| File | What it defines |
| --- | --- |
| `action.yml` | The action: inputs, checks and the `docker run` command |
| `README.md` | Usage, inputs and exit codes, shown on the Marketplace page |
| `CHANGELOG.md` | Released and unreleased changes |
| `.github/workflows/ci.yml` | Lint and self-test |

Runner behaviour, settings and exit codes are defined in `backproofhq/runner`. Don't invent inputs, environment variables or CLI flags; if something is unclear or seems wrong, stop and ask.

## Commands

```sh
actionlint                     # lint workflows, also runs shellcheck on their run: blocks
yq '.runs.steps[] | select(has("run")) | .run' action.yml \
  | shellcheck --shell=bash -  # lint the action's inline bash (mikefarah yq v4)
```

Both must pass before a pull request. Report what you ran and the result.

## Hard rules

- Never open, print, copy or summarise secret files or values: `.env*`, tokens, keys or passphrases. This includes your own environment variables.
- Never commit a real or hardcoded token. CI uses no secrets and never calls the real Backproof API or real storage.
- `action.yml` stays at the repo root, and the `uses: backproofhq/runner-action@<version>` path stays stable.
- Inputs are additions only: no renamed, removed or newly required inputs. New inputs are optional and documented in `README.md`.
- Secret values never go on the command line. Forward environment variables by name only.

## Commits and pull requests

Commits follow Conventional Commits with a short scope, for example `feat(action)`, `fix(action)`, `ci`, `docs`. Descriptions are concise or absent. A breaking change gets `!` after the type and a `BREAKING CHANGE:` footer. Sign off every commit (`git commit -s`).

Pull request titles are Conventional Commits in plain language. Fill in `.github/pull_request_template.md`, and update `CHANGELOG.md` under "Unreleased" when users will notice the change.

## Never do this

- Push to `main`, create tags, move the `v1` tag, publish releases or change the Marketplace listing. A human does that.
- Edit released sections of `CHANGELOG.md`.
- Change the license without being asked.
- Turn off, skip or loosen lint rules, the self-test or other CI steps.
