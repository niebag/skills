---
name: conventional-commit
description: 'Inspect staged changes and craft a Conventional Commits–compliant commit message (type, scope, description, body, footer). Use when the user wants to commit or says "conventional commit".'
---

Run `git diff --staged` + `git status`. If nothing is staged, output exactly `Nothing staged.` — nothing else — and stop.

Run `git branch --show-current`. Extract ticket (`ABC-123`/`ABCD-1234` pattern) — use silently if found; if not, ask `No ticket detected — enter ticket number or "none":` and wait. "none" → omit ticket.

Craft a Conventional Commits message:
- **Type:** `feat` · `fix` · `docs` · `style` · `refactor` · `perf` · `test` · `build` · `ci` · `chore`
- **Scope:** optional noun in parens — omit if cross-cutting
- **Breaking:** append `!` + `BREAKING CHANGE: <desc>` footer
- **Description:** imperative, lowercase, no period — ticket appended as `[TICKET]`, ≤72 chars total
- **Body:** blank line, *why* not *what*, wrap 72 chars
- **Footers:** `Token: value`, multi-word tokens hyphenated

Output: fenced commit message + `git commit` command (heredoc if multi-line). No commit, no explanation.
