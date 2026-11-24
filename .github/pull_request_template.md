<!--
Thanks for contributing to the Backproof Runner action.

Found a security problem? Please don't open a pull request. Report it privately as described in SECURITY.md.

Use a Conventional Commits title in plain language, for example:
fix(action): explain how to start Docker when it isn't running
-->

## Problem

<!-- What is wrong or missing, in a sentence or two? Link the issue if there is one, for example: Fixes #123 -->

## Solution

<!-- How does this change solve it? Point out anything reviewers should look at closely. -->

## Testing

<!-- What did you run, and what happened? Never paste real tokens or keys. -->

## Checklist

- [ ] Every commit is signed off with `git commit -s`
- [ ] `actionlint` and `shellcheck` on the action's inline bash pass
- [ ] Code, logs and errors contain no real tokens, keys or other secrets
- [ ] `CHANGELOG.md` is updated under "Unreleased" if users will notice this change

### If your change touches these areas

<!-- Tick the ones that apply and delete the rest. -->

- [ ] **Inputs:** they are additions only, new inputs are optional, and `README.md` documents them
- [ ] **The action's bash:** secret values stay off the command line and are forwarded by name only
- [ ] **CI:** no step is loosened or skipped, no secrets are used, nothing calls the real Backproof API or storage, and actions are pinned to full commit SHAs
