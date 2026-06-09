---
name: create-skill
description: 'Scaffold a new skill following best practices. Use when the user wants to create a new skill.'
---

Ask the user these 3 questions in a single message:

1. **Name** — lowercase hyphenated slug (e.g. `my-skill`)
2. **Trigger** — when should Claude invoke this? The description is the *only* thing Claude sees when deciding which skill to load — be specific: first sentence says what it does, second says "Use when [triggers/keywords]". Max 1024 chars.
3. **Behavior** — describe what the skill does, step by step. Include: any early-exit conditions and what to output, the expected output format (if any), and any exact strings the skill should produce (use quotes).

After receiving answers:

1. Create `skills/<name>/SKILL.md` with frontmatter (`name` + `description`) and a compact body derived from the behavior description. Use backticks for exact output strings. End with `No explanation.` only if the skill produces a specific output.
2. Add `"./skills/<name>"` to the `skills` array in `.claude-plugin/plugin.json`
3. Verify against checklist (fix silently if needed):
   - [ ] Description includes "Use when [triggers]"
   - [ ] No time-sensitive information
   - [ ] SKILL.md under 100 lines
   - [ ] Exact output strings in backticks
4. Output exactly `Created skills/<name>/SKILL.md — run /reload-plugins to activate.` — then, on a new line, optionally suggest a better name or description if the given ones are suboptimal (e.g. `` `better-name` might be more descriptive than `given-name` ``). Skip if both are already good.
