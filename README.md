# Sparking AI Skills

Claude Code skills for product builders.

## Commands

| Command | Description | Output |
|---------|-------------|--------|
| `/spark:pm-research` | Market research and opportunity discovery | `docs/prd/research-*.md` |
| `/spark:pm-teardown` | Competitor feature analysis (optional) | `docs/prd/teardown-*.md` |
| `/spark:pm-prd` | PRD with user flow | `docs/prd/prd.md`, `docs/prd/user-flow.md` |
| `/spark:tech-stack` | Technology stack decisions | `docs/tech/stack.md` |
| `/spark:tech-arch` | Top-level system architecture | `docs/tech/architecture.md` |
| `/spark:ui-spec` | Page specs and Stitch AI prompts | `docs/ui/pages/*.md`, `docs/ui/prompts/*.md` |

## Workflow

```
/spark:pm-research → /spark:pm-prd → /spark:tech-stack → /spark:ui-spec
         ↓                                  ↘ /spark:tech-arch
/spark:pm-teardown (optional)
```

## Installation

```bash
/plugin marketplace add sparking-ai/skills
/plugin install spark@sparkai-skills
```

Then restart Claude Code to activate the skills.
