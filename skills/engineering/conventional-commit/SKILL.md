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

Output: fenced commit message + `git commit` command (heredoc if multi-line). No commit, no explanation.
