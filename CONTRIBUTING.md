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

## Code quality

Every pull request is reviewed against these rules.

### Modular
- One module, one responsibility. A file that does two unrelated things is split.
- Keep pure logic (parsing, decryption, matching, formatting) separate from input and output (files, network, operating system calls). Pure logic is then testable without a computer set up in a special way.
- Platform-specific code (macOS, Windows) sits behind one module per platform, with the same interface.
- Small public API: expose only what callers need. Everything else stays private.

### Clean
- Clear names over comments. A comment explains *why*, never *what*.
- No duplicated logic: if the same rule appears in two places, it moves to one function.
- No dead code, no commented-out code, no leftover debug output.
- Errors are explicit and say what to do. Never ignore an error silently.
- Formatter and linter pass with no warnings (`cargo fmt`, `cargo clippy -D warnings`; the equivalents for TypeScript and Python).

### Optimised
- Optimise what users wait for: download, audio extraction, transcription, app start. Measure before and after, and write the numbers in the pull request.
- No needless copies of large data (recordings, audio, models): stream or borrow instead.
- Do not make code harder to read for a gain nobody can measure.

### Tests
- Every bug fix gets a test that fails before the fix.
- Rust: unit tests in the same file, in a `#[cfg(test)] mod tests` block at the bottom (they can test private functions and are not part of the release). Tests of the public API go in the `tests/` folder. When a file's tests grow long, they move to their own file next to it.
- TypeScript and Python: tests in a separate `tests/` folder.
- Tests never use real cookies, real recordings or real transcripts. Use generated test data.

## Project rules

- No AI or assistant attribution anywhere: commits, pull requests, comments, documentation.
- No em dashes in documentation, comments, commit messages or interface text.
- Write plainly: short sentences, ordinary words. Many readers do not have English as their first language.
- Ask before adding a large dependency or one that needs a global install.
- When something is uncertain (an API, a tool option, a platform behaviour), check the documentation or test it, and say in the pull request what was verified and what was assumed.

## Security

Never report a security problem in a public issue. See [SECURITY.md](SECURITY.md).
