# Squad Skills Marketplace

Personal/team skill library for [Squad](https://github.com/bradygaster/squad) AI agent teams.

## What is this?

This repository serves as a **self-hosted skills marketplace** for Squad. Instead of depending on external skill sources, you can maintain your own curated collection of skills that evolve with your team.

## Repository Structure

```
squad-skills/
 README.md             # This file
 marketplace.json      # Index of all skills (auto-updated)
 skills/               # One folder per skill
    windows-compatibility/
       SKILL.md
    git-workflow/
       SKILL.md
    ...
 .github/
     workflows/
         update-marketplace.yml  # Auto-updates marketplace.json
```

## Using This Marketplace

Configure your Squad project to use this marketplace by updating `.squad/plugins/marketplaces.json`:

```json
{
  "version": "1",
  "sources": [
    {
      "name": "personal",
      "description": "Personal Squad skills marketplace",
      "url": "https://github.com/luckyjohnb/squad-skills/tree/main/skills",
      "type": "github",
      "owner": "luckyjohnb",
      "repo": "squad-skills",
      "path": "skills",
      "branch": "main",
      "primary": true
    }
  ]
}
```

## Adding a New Skill

1. Create a folder under `skills/` with your skill name (kebab-case)
2. Add a `SKILL.md` file with YAML frontmatter:

```markdown
---
name: "my-skill-name"
description: "Brief description of the skill"
domain: "category"
confidence: "high|medium|low"
---

## Context
What problem does this skill solve?

## Patterns
How to apply this skill...
```

3. Commit and push  the marketplace.json index updates automatically

## Available Skills

| Skill | Domain | Description |
|-------|--------|-------------|
| [windows-compatibility](skills/windows-compatibility/SKILL.md) | platform | Cross-platform path handling and command patterns |
| [git-workflow](skills/git-workflow/SKILL.md) | version-control | Squad branching model: dev-first workflow |
| [error-recovery](skills/error-recovery/SKILL.md) | reliability | Standard recovery patterns for all agents |
| [secret-handling](skills/secret-handling/SKILL.md) | security | Never read .env files or write secrets |
| [test-discipline](skills/test-discipline/SKILL.md) | quality | Update tests when changing APIs |
| [model-selection](skills/model-selection/SKILL.md) | orchestration | Determines which LLM model to use |
| [reviewer-protocol](skills/reviewer-protocol/SKILL.md) | orchestration | Reviewer rejection workflow and lockout |
| [docs-standards](skills/docs-standards/SKILL.md) | documentation | Microsoft Style Guide + Squad patterns |
| [agent-conduct](skills/agent-conduct/SKILL.md) | team-governance | Shared hard rules across all agents |
| [history-hygiene](skills/history-hygiene/SKILL.md) | documentation | Record final outcomes, not intermediate |
| [release-process](skills/release-process/SKILL.md) | releases | Pre-release validation checks |
| [squad-conventions](skills/squad-conventions/SKILL.md) | project-conventions | Core Squad codebase conventions |

## License

MIT
