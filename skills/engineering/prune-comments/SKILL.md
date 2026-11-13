---
name: prune-comments
description: 'Removes code comments that do not earn their place, keeping only comments that explain what the code cannot. It is used when the user asks to minimize, trim or clean up comments in a diff, branch, PR/MR or files.'
---

Scope: the files, branch or PR/MR the user names (work on its source branch locally). Otherwise the current branch's changes against its base: `git diff $(git merge-base HEAD origin/HEAD)`, plus uncommitted changes. Touch only comments on changed lines unless the user asks for whole files.

A comment stays only if a reader could not get it from the code below it:
- **Why:** intent, trade-off, rejected alternative
- **Constraint:** external API or backend contract, spec, legal or compliance requirement
- **Quirk:** platform or library bug, workaround (keep the upstream link)
- **Invariant:** units, ordering, threading, non-obvious edge case
- **Marker:** `TODO`/`FIXME` with a ticket or owner

Remove:
- Comments that restate the code (`// increment retry count`, `/// Returns the name` on `name()`)
- History or provenance: "ported from…", "mirrors the other implementation", "changed for ABC-123", "no design yet"
- Commented-out code
- Section banners and dividers
- Doc comments that only repeat the signature, unless the project generates API docs or lints for them

Never touch tool directives (`// swiftlint:disable`, `# noqa`, `// @ts-expect-error`, `#pragma`), license headers or generated files. Comments the user names to keep stay verbatim.

Shorten a useful but wordy comment to one line instead of deleting it. A comment that contradicts the code: fix or remove it and report it. Information that belongs in the PR/MR description or commit body: report it, don't keep it in code.

Change comments only, never code, formatting or imports. Verify with `git diff` that only comment lines changed. No commit unless asked.

Output: per file, the number of comments removed and shortened, plus any comment you were unsure about.
