---
name: refine-ticket
description: 'Refines a vague ticket (bug or feature) by researching the codebase and producing a structured, actionable ticket. Use when the user asks to refine a ticket or invokes the skill manually.'
---

Ask the user for the ticket input if not already provided.

Research the codebase for relevant files, patterns, and context related to the ticket.

Output two blocks separated by a blank line:

First block:
- **Title** — rewrite if the original is vague
- **Description** — brief, functional summary
- **User story** — "As a [role], I want [goal], so that [benefit]"
- **Acceptance criteria** — Given/When/Then format
- **Subtasks** — only if needed; keep minimal; use `[ ]` checkboxes

Second block:
**Estimates:**
- Junior: X points, Xh
- Medior: X points, Xh
- Senior: X points, Xh

**Business value:** X/10

Constraints:
- Scope must be completable by 1 person in 1 sprint
- If any estimate exceeds 4 hours, flag as too large and suggest how to split
- Focus on functionality, not technical implementation depth

No explanation outside the two sections above.
