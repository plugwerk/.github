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

## Maintenance

Changes to `default.json` affect every repo in the org. Treat changes here as
cross-cutting and validate with the `renovate-config-validator` workflow before
merging.
