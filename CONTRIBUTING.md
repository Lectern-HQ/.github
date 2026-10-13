# Contributing to Lectern

Every change follows the same path: **issue, branch, pull request, checks, review, merge.**

Work is planned on the [Lectern project board](https://github.com/orgs/Lectern-HQ/projects/1) in two-week sprints. Each sprint is also a milestone (`Sprint 1`, `Sprint 2`, ...).

## 1. Start from an issue

- Every change needs an issue. If there is none, open one first (use the templates).
- An issue says **why** and **what "done" means** (a checklist under "Done when").
- Before starting, set the issue's status to **In progress** on the board and assign yourself.

## 2. Create a branch

Branch from the latest `main`, named after the issue:

```bash
git switch main
git pull
git switch -c 42-short-description
```

`42` is the issue number. Keep the description to a few words, in lower case, with hyphens.

## 3. Commit

Follow [COMMITS.md](COMMITS.md) (Conventional Commits). Small commits are fine; they are squashed when merged.

Never commit cookie values, cookie files, browser databases, passwords, keys, signed links, lecture recordings or transcripts of real lectures.

## 4. Open a pull request

- One pull request per issue.
- **Title in Conventional Commits format**: it becomes the commit message on `main`.
- Fill in the template. The description must contain `Closes #42` (or `Closes Lectern-HQ/<repo>#42` for an issue in another repository), so the issue closes when the pull request is merged.
- Set the issue's status to **In review**.

## 5. Checks and review

- All automatic checks must pass (format, lint, tests).
- At least one review by a code owner (see `CODEOWNERS`) before merging.
- Answer every review comment, by changing the code or by explaining why not.

## 6. Merge

- **Squash and merge** only.
- Delete the branch after merging.
- The issue closes automatically and moves to **Done** on the board.

## Project rules

- No AI or assistant attribution anywhere: commits, pull requests, comments, documentation.
- No em dashes in documentation, comments, commit messages or interface text.
- Write plainly: short sentences, ordinary words. Many readers do not have English as their first language.
- Ask before adding a large dependency or one that needs a global install.
- When something is uncertain (an API, a tool option, a platform behaviour), check the documentation or test it, and say in the pull request what was verified and what was assumed.

## Security

Never report a security problem in a public issue. See [SECURITY.md](SECURITY.md).
