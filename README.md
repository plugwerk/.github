# plugwerk/.github

Org-wide defaults for the [plugwerk](https://github.com/plugwerk) GitHub
organization. The contents of this repo are loaded automatically by GitHub for
every repository under `plugwerk/*` that does not provide its own override.

## Layout

| Path | Purpose |
| --- | --- |
| `default.json` | Renovate config consumed via `extends: ["github>plugwerk/.github"]`. |
| `profile/README.md` | Rendered as the public org landing page at <https://github.com/plugwerk>. |
| `.github/SECURITY.md` | Security policy fallback for repos without their own. |
| `.github/CODE_OF_CONDUCT.md` | Community standards across all org repos. |
| `.github/CONTRIBUTING.md` | Generic contribution guide; per-repo `CONTRIBUTING.md` overrides. |
| `.github/SUPPORT.md` | Where to ask for help. |
| `.github/FUNDING.yml` | Sponsor button (currently empty — see file for rationale). |
| `.github/ISSUE_TEMPLATE/` | YAML issue forms (bug, feature, config). |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR template. |
| `.github/workflows/renovate-config-validator.yml` | Validates `default.json` on every PR. |
| `.github/workflows/renovate.yml` | Reusable Renovate trigger; consumer repos call it via `uses:` with their own schedule. |

## Override Behavior

A file in a specific repo's `.github/` directory always overrides the
corresponding file here. For example:

- `plugwerk/plugwerk/CONTRIBUTING.md` (project-specific build/test/style
  instructions) overrides `plugwerk/.github/.github/CONTRIBUTING.md` when
  contributors view it on the `plugwerk/plugwerk` repo.
- `plugwerk/plugwerk/.github/PULL_REQUEST_TEMPLATE.md` overrides this repo's
  generic template, because that project carries Liquibase-rollback rules
  that other repos in the org do not need.

For Renovate, per-repo `renovate.json` files extend `github>plugwerk/.github`
and add their own `packageRules` for project-specific stacks (e.g. Java/Kotlin
groupings live in `plugwerk/plugwerk/.github/renovate.json`, not here).

## Reusable Renovate Workflow

Consumer repos call the reusable trigger from this repo so the
`renovatebot/github-action` SHA pin and run conventions live in one
place. Minimal stub for a consumer repo's
`.github/workflows/renovate.yml`:

```yaml
name: Renovate

on:
  schedule:
    - cron: "0 4 * * 1-5"
  workflow_dispatch:
    inputs:
      logLevel:
        description: "Log level"
        type: choice
        default: info
        options: [info, debug]

jobs:
  renovate:
    uses: plugwerk/.github/.github/workflows/renovate.yml@main
    permissions:
      contents: write
      pull-requests: write
      issues: write
    with:
      logLevel: ${{ inputs.logLevel || 'info' }}
```

Each caller's `GITHUB_TOKEN` is scoped to its own repo, so the call is
single-repo by design — the reusable workflow does not add cross-repo
write access.

## Maintenance

Changes to `default.json` affect every repo in the org. Treat changes here as
cross-cutting and validate with the `renovate-config-validator` workflow before
merging.
