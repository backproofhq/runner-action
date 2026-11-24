# Security policy

Backproof handles database backups and the keys to open them, so we take security reports seriously. Thank you for helping keep Backproof and its users safe.

## Reporting a vulnerability

Please don't open a public issue for security problems. Report them privately in one of these ways:

- **GitHub:** use "Report a vulnerability" on the [Security tab](https://github.com/backproofhq/runner-action/security) of this repository.
- **Email:** support@backproof.dev, with "Security" at the start of the subject line.

Please include:

- What you found and what an attacker could do with it.
- Steps to reproduce, or a proof of concept.
- The action version you use (for example `@v1` or a commit SHA) and the runner it ran on.
- Whether you'd like to be credited, and under what name.

Don't include real customer data, keys or tokens in a report. If a reproduction needs secrets, generate test ones.

A problem in the runner itself rather than in this action is welcome here too, or in the [runner repository](https://github.com/backproofhq/runner/security). Both reach the same team.

## What happens next

Backproof is run by a small team, so these are honest targets, not guarantees:

| Step | Target |
| --- | --- |
| We confirm we received your report | Within 3 working days |
| We share our first assessment and severity | Within 10 working days |
| We release a fix for a critical issue | As fast as possible, aiming for 14 days |
| We release a fix for other issues | In a following release, and we'll tell you when |

We'll keep you updated on progress, and we'll agree with you on when details are made public. We ask that you wait until a fix is released, or 90 days after your report, whichever comes first.

Once fixed, the issue is described in the release notes and `CHANGELOG.md`, with credit to you if you want it. We don't run a paid bug bounty at this time.

## Supported versions

| Version | Security fixes |
| --- | --- |
| The latest release of the current major version (`v1`) | Yes |
| Older releases and older major versions | No; please update |

Workflows that use `@v1` get every fix in the current major version automatically. If you pin the action to a commit SHA, update the SHA when a fix is released.

## Scope

In scope:

- The action in this repository (`action.yml`)
- The runner Docker image it runs (`backproofhq/runner`)
- The Backproof API and dashboard at `app.backproof.dev`, even though their code isn't public

Out of scope:

- Denial of service, spam or volume testing against our servers
- Social engineering or phishing of Backproof staff or users
- Issues that require an already compromised runner, workflow or user device, or a leaked repository secret
- Bugs in third-party services such as storage providers, Docker Hub or GitHub, which should go to those vendors
- Missing security headers or best practices with no demonstrated impact

## Testing guidelines

- Test only against your own account, runners and storage.
- Don't access, change or delete other users' data. If you come across it by accident, stop and tell us.
- Don't degrade the service for other users.

If you act in good faith and follow this policy, we won't pursue legal action against you for your research.

## More

How the runner protects your data, and where its limits are, is described in the runner's [docs/security.md](https://github.com/backproofhq/runner/blob/main/docs/security.md).
