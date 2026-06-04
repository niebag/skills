---
name: conventional-commit
description: 'Inspect staged changes and craft a Conventional Commits–compliant commit message (type, scope, description, body, footer). Use when the user wants to commit or says "conventional commit".'
---

Run `git diff --staged` and `git status`. If nothing is staged, output only: "Nothing staged." and stop.

Otherwise craft a Conventional Commits message:

- **Type:** `feat` · `fix` · `docs` · `style` · `refactor` · `perf` · `test` · `build` · `ci` · `chore`
- **Scope:** optional noun in parens, e.g. `fix(parser):` — omit if cross-cutting
- **Breaking:** append `!` and add `BREAKING CHANGE: <desc>` footer
- **Description:** imperative, lowercase, no period, ≤72 chars total on line 1
- **Body:** blank line separator, explain *why* not *what*, wrap at 72 chars
- **Footers:** `Token: value` format, multi-word tokens hyphenated

Output exactly: a fenced code block with the message, then the ready-to-run `git commit` command (heredoc if multi-line). Do not commit, ask questions, or explain.
