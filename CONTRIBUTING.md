# Contributing to Synapse

Thanks for your interest in Synapse! This guide explains how to propose changes.

By participating, you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).

## Before you start

- **Bugs:** search [existing issues](../../issues) first, then open a bug report using the template.
- **Features:** open a feature request and describe the problem before the solution. Larger changes
  should be discussed in an issue before any code is written.
- **Security issues:** never open a public issue. Follow [SECURITY.md](SECURITY.md).

## Development workflow

1. Fork the repository and create a branch from `main` for your feature or fix:
   ```sh
   git switch -c feat/short-description
   ```
   Branch prefixes: `feat/`, `fix/`, `docs/`, `test/`, `refactor/`, `chore/`, `ci/`.
2. Make your changes in small, focused commits (see [Commit messages](#commit-messages)).
3. Add or update tests. **Every change ships with tests**, and CI must pass.
4. Push your branch and open a pull request against `main` using the PR template.
5. Address review comments. PRs are merged with a merge commit once CI is green and all
   conversations are resolved.

Local setup instructions will be added here with the first release.

## Commit messages

Synapse uses [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). Every commit on a
branch is kept in history, so every commit message matters.

```
<type>(<optional scope>): <summary in the imperative, lower case, no period>

<optional body: what and why, wrapped at 72 characters>

<optional footer: BREAKING CHANGE: ..., Closes #123>
```

| Type       | Use for                                             |
| ---------- | --------------------------------------------------- |
| `feat`     | A new user-facing feature                           |
| `fix`      | A bug fix                                           |
| `docs`     | Documentation only                                  |
| `test`     | Adding or fixing tests                              |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf`     | Performance improvement                             |
| `build`    | Build system or dependencies                        |
| `ci`       | CI configuration                                    |
| `chore`    | Maintenance that doesn't touch source or tests      |

Examples:

```
feat(map): stream prerequisite nodes over server-sent events
fix(mastery): keep state at learning when a check is skipped
docs: add self-hosting guide
```

## Code standards

- **Python:** formatted and linted with Ruff, type-checked with mypy.
- **TypeScript:** ESLint and Prettier, strict TypeScript.
- **Line endings:** LF everywhere (enforced by `.gitattributes`).
- **Secrets:** never commit secrets. Use a local `.env` file; only `.env.example` is committed.
- **Deterministic core:** graph checks (cycles, learning-path ordering), mastery scoring and review
  scheduling are plain, tested code. Language models generate content and grade individual answers;
  they never decide state directly.

## License

By contributing, you agree that your contributions are licensed under the
[GNU Affero General Public License v3.0](LICENSE).
