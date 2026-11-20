---
name: conventional-commit
description: 'Creates a Conventional Commits–compliant message from staged changes. It is used when the user wants to commit or says "conventional commit".'
---

Run `git diff --staged` + `git status`. If nothing is staged, output exactly `Nothing staged.` — nothing else — and stop.

Inspect the last 50 commit subjects with `git log --format='%s' -n 50` (treat an unborn repository as having no commits). Detect ticket usage with the `ABC-123`/`ABCD-1234` pattern:
- Existing commits include a ticket: tickets are required. Run `git branch --show-current`; use its ticket silently if found, otherwise ask `No ticket detected — enter ticket number or "none":` and wait. "none" → omit ticket.
- Existing commits include no ticket: omit the ticket and do not ask.
- No commits: ask `No ticket detected — enter ticket number or "none":` and wait. "none" → omit ticket.

Inspect repository conventions before choosing the message: run `git log --oneline -n 30` and `git log --format='%h %s' -n 20 -- <staged-files>`. Look for commits that touch the same area or address similar work. When a clearly relevant precedent exists, reuse its type and scope where they fit the staged change; do not copy a type or scope blindly. If no relevant precedent exists, infer them from the staged diff.

Craft a Conventional Commits message:
- **Type:** `feat` · `fix` · `docs` · `style` · `refactor` · `perf` · `test` · `build` · `ci` · `chore`
- **Scope:** optional noun in parens — omit if cross-cutting
- **Breaking:** append `!` + `BREAKING CHANGE: <desc>` footer
- **Description:** imperative, lowercase, no period — ticket appended as `[TICKET]`, ≤72 chars total
- **Body:** blank line, *why* not *what*, wrap 72 chars
- **Footers:** `Token: value`, multi-word tokens hyphenated

Split unrelated concerns: if the staged files form clearly separate groups (e.g. a feature plus a version or build-number bump, IDE/editor config, or formatting-only churn), use one commit per group, main change first. Split by whole files only, and only if none of the split-off files also has unstaged changes (`git diff --name-only`); otherwise keep one commit. Sequence: `git restore --staged <split-off paths>`, commit the main group, then per group `git add <paths>` + its own `git commit`.

Output: fenced commit message + `git commit` command (heredoc if multi-line), per commit in order, with the restore/add commands when split. No commit, no explanation.

Exception: if the arguments explicitly ask to commit or push (any language, e.g. `commit`, `and push`), run the `git commit`(s) yourself, then `git push` if asked. Never push to a branch other than the current one, never force-push. Output: each commit message + short hash, and the push result.
