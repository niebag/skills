---
name: to-prd
description: 'Creates a Product Requirements Document (PRD) from the current conversation context. Use when the user wants to create a PRD, document a feature discussion, or turn a conversation into a structured product spec.'
---

Synthesize the current conversation into a PRD. Do not ask for additional input unless critical context is missing.

Output the following sections in order:

---

# PRD: [Feature/Project Name]

## Overview
One paragraph summarising what is being built and why.

## Decisions
Bullet list of key decisions made during the conversation. Each entry: **Decision:** what was decided — **Rationale:** why.

## Out of Scope
Bullet list of things explicitly excluded or deferred. If none were discussed, infer obvious exclusions from the scope.

## User Stories
One line per story: `As a [role], I want [goal], so that [benefit].`
Group related stories under a bold heading if helpful.

## Test Plan
Bulleted checklist of scenarios to verify. Cover: happy path, edge cases, and any explicit concerns raised in the conversation.

---

No explanation outside the sections above.
