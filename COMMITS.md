# Commit messages

All Lectern repositories use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). The history then reads clearly, and the changelog can be generated from it.

## Format

```
type(scope): short description

Optional body: why the change was needed, in plain sentences.

Optional footer: Closes #12, BREAKING CHANGE: ...
```

- **type**: what kind of change it is (see the list below).
- **scope** (optional): the part of the project, for example `cookies`, `pipeline`, `app`, `release`, `payments`.
- **short description**: an instruction, in lower case, without a full stop, at most about 70 characters. Write "add", not "added" or "adds".

## Types

| Type | Use it for |
| --- | --- |
| `feat` | A new feature for users |
| `fix` | A bug fix |
| `docs` | Documentation only |
| `refactor` | A code change that neither adds a feature nor fixes a bug |
| `test` | Adding or fixing tests |
| `perf` | A change that makes something faster or lighter |
| `build` | Build system, dependencies, packaging |
| `ci` | GitHub Actions and other automation |
| `chore` | Anything else that does not change the product (tooling, cleanup) |

## Breaking changes

A change that breaks compatibility (for example the public API of `lectern-cookie-reader`) gets a `!` after the type and a footer explaining what breaks and what to do:

```
feat(cookies)!: return matching profiles sorted by last use

BREAKING CHANGE: find_logins now returns a Vec<ProfileMatch> instead of Option<ProfileMatch>.
```

## Examples

Good:

```
feat(cookies): read Firefox profiles on Windows
fix(pipeline): skip silence at the end of the file
docs: add CONTRIBUTING.md
ci: run tests on a Windows runner
```

Not good:

```
Updated stuff                      (no type, says nothing)
feat: Added Firefox support.       (past tense, capital letter, full stop)
fix(pipeline): fix bug             (which bug?)
```

## Pull requests

Pull requests into `dev` are squash merged, so **the pull request title becomes the commit message** on `dev`. Releases from `dev` into `main` use a merge commit. Give every pull request title the same format. The commits inside a branch can be less strict.

## Project rules

- No AI or assistant attribution in commits or pull requests (no co-author trailers, no "generated with" lines).
- No em dashes.
- Never put cookie values, passwords, keys or signed links in a commit, message or pull request.
