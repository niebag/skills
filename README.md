# niebag-skills

[![skills.sh](https://skills.sh/b/niebag/skills)](https://skills.sh/niebag/skills)

Personal skills by Niels Baggerman.

## Install via Claude Code

```
/plugin marketplace add niebag/skills
/plugin install niebag-skills@niebag-skills
```

## Install via skills.sh

```bash
npx skills add niebag/skills
```

## Skills

### Product workflow

Four skills that cover the full lifecycle from idea to sprint-ready tickets. They are designed to chain together but each works standalone too.

```
/drill-me  →  /to-prd  →  /to-tickets
                               ↓
                         individual tickets
                               ↑
                        /refine-ticket  ←  tickets from elsewhere
```

| Skill | Purpose | Input |
|---|---|---|
| `/drill-me` | Stress-test an idea or design through structured questioning | A rough idea or plan |
| `/to-prd` | Capture the conversation into a structured PRD | Conversation context (typically after `/drill-me`) |
| `/to-tickets` | Break the PRD into detailed, actionable tickets | Conversation context with a PRD |
| `/refine-ticket` | Refine a vague or externally created ticket | A single ticket (Jira, Linear, written by hand) |

**Happy path:** start a new feature with `/drill-me`, then run `/to-prd` to lock in the spec, then `/to-tickets` to generate sprint-ready work items.

**Standalone use:** skip straight to `/to-prd` if you already know what you want to build. Use `/refine-ticket` independently on any ticket that needs more clarity, whether it came from the workflow above or from someone else entirely.

### Dev workflow

| Skill | Purpose |
|---|---|
| `/conventional-commit` | Inspect staged changes and craft a Conventional Commits–compliant message, auto-detects ticket numbers from the branch name |
| `/create-skill` | Scaffold a new skill following best practices |
