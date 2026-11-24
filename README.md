# Backproof Runner action

Proves that your latest Postgres backup actually restores. The action runs the open-source [Backproof runner](https://github.com/backproofhq/runner) on your GitHub-hosted runner, restores the backup into a throwaway container, runs your checks and reports metadata to [Backproof](https://app.backproof.dev). Your data never leaves the job.

## Usage

1. Create a CI token on the **Add runner** page in the Backproof dashboard.
2. Save it as a repository secret named `BACKPROOF_TOKEN`.
3. Add this workflow as `.github/workflows/backproof.yml`:

```yaml
name: Backproof
on:
  schedule:
    - cron: "17 * * * *"
  workflow_dispatch:
jobs:
  backproof:
    runs-on: ubuntu-latest
    steps:
      - uses: backproofhq/runner-action@v1
        with:
          token: ${{ secrets.BACKPROOF_TOKEN }}
```

The dashboard decides which tests are due. The schedule only has to run at least as often as your most frequent backup test.

## Inputs

| Input | Required | Purpose |
| --- | --- | --- |
| `token` | Yes | CI token from the Backproof dashboard |

## Results

| Exit code | Meaning |
| --- | --- |
| `0` | Every due test passed, or nothing was due |
| `1` | At least one backup failed |
| `2` | The runner couldn't do its job, for example because of wrong credentials |

A failed backup outranks a runner error, and both fail the workflow.

## Keep keys out of Backproof

Keys you seal in the dashboard are only opened inside this job. To keep them out of Backproof entirely, pass them as secrets on the step. They take precedence over sealed keys:

```yaml
      - uses: backproofhq/runner-action@v1
        with:
          token: ${{ secrets.BACKPROOF_TOKEN }}
        env:
          BP_SRC_PROD_DB_S3_ACCESS_KEY: ${{ secrets.PROD_DB_S3_ACCESS_KEY }}
          BP_SRC_PROD_DB_S3_SECRET_KEY: ${{ secrets.PROD_DB_S3_SECRET_KEY }}
```

The action forwards `BACKPROOF_*` and `BP_SRC_*` variables to the runner. The [configuration docs](https://github.com/backproofhq/runner/blob/main/docs/config.md) list every setting.

## Requirements

A Linux runner with Docker, such as `ubuntu-latest`.

## License

[Apache 2.0](LICENSE)
