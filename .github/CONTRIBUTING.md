# Contributing to Plugwerk

Plugwerk welcomes contributions from humans and AI agents alike. This file
covers org-wide expectations. **For repository-specific build, test, and
style instructions, read the per-repo `CONTRIBUTING.md`, `AGENTS.md`, or
`CLAUDE.md` first** — those override anything written here when a conflict
exists.

## Before You Start

1. **Look for an existing issue** describing what you want to change. If
   none exists, open one first for non-trivial work, so we can align on
   the approach before code is written.
2. **Read the repo's `AGENTS.md`** (or `CLAUDE.md`) if present. It
   captures conventions, build commands, and the project's
   architecture in one place.
3. **Check open PRs** to avoid duplicate work.

## Branch Naming

Use a short, type-prefixed branch name that references the issue when
applicable:

- `feat/123-short-description` for new features
- `fix/456-bug-description` for bug fixes
- `refactor/<area>-<purpose>` for refactors without a tracking issue
- `docs/<area>` for docs-only changes

## Commits

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>: <imperative description>

<optional body explaining why, not what>
```

Common types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`,
`perf`, `ci`. Keep subject lines under 72 characters.

## Pull Requests

- Reference the issue you are closing (`Closes #123`).
- Keep PRs focused — one logical change per PR.
- Include a test for any behaviour change unless the affected file is
  covered by an explicit "no test needed" rule in the repo's docs.
- Wait for CI to be green before requesting review.

## Contributor License Agreement

Plugwerk is licensed under [AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0)
with a parallel commercial-licensing track. To keep both options open
for the project, **first-time contributors must sign a CLA** before
their first PR can be merged. The current CLA text and signing
instructions live in [`plugwerk/plugwerk/CLA.md`](https://github.com/plugwerk/plugwerk/blob/main/CLA.md);
the signing process is the same for contributions to any repo in this
org.

If you are unsure whether you have already signed, ask in the PR — the
maintainers will check and let you know.

## Code of Conduct

Participation in this org is governed by the
[Code of Conduct](./CODE_OF_CONDUCT.md). Be respectful in issues, PRs,
discussions, and any other channel where you interact with the
community.

## Reporting Security Issues

Do not open public issues for security problems. See the
[Security Policy](./SECURITY.md) for the private reporting channels.

## Questions

Open a [GitHub Discussion](https://github.com/orgs/plugwerk/discussions)
on the relevant repository, or check the [Support guide](./SUPPORT.md).
