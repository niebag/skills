---
name: to-tickets
description: 'Breaks down the current conversation into detailed, actionable tickets using the refine-ticket methodology (acceptance criteria, estimates, business value). Use when the user wants to turn a conversation or PRD into sprint-ready tickets.'
---

Research the codebase for relevant files and patterns before writing tickets. Infer logical units of work from the conversation.

For each ticket, output two blocks separated by a blank line:

First block:
- **Title** — clear, actionable
- **Description** — brief, functional summary
- **User story** — "As a [role], I want [goal], so that [benefit]"
- **Acceptance criteria** — Given/When/Then format
- **Subtasks** — only if needed; use `[ ]` checkboxes

Second block:
**Estimates:**
- Junior: X points, Xh
- Medior: X points, Xh
- Senior: X points, Xh

**Business value:** X/10

Separate tickets with `---`.

Constraints:
- Each ticket must be completable by 1 person in 1 sprint
- If any estimate exceeds 4 hours, flag as too large and suggest how to split
- Focus on functionality, not technical implementation depth

No explanation outside the ticket blocks above.
