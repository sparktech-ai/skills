# Sparking AI Skills

Claude Code skills for product builders.

## Skills

| Skill | Description | Output |
|-------|-------------|--------|
| `/pm-market-research` | Market research and opportunity discovery | `docs/prd/research-*.md` |
| `/pm-competitor-analysis` | Competitor feature analysis (optional) | `docs/prd/competitor-*.md` |
| `/pm-prd` | PRD with user flow | `docs/prd/prd.md`, `docs/prd/user-flow.md` |
| `/tech-stack` | Technology stack decisions | `docs/tech/stack.md` |
| `/tech-arch` | Top-level system architecture | `docs/tech/architecture.md` |
| `/ui-spec` | Page specs and Stitch AI prompts | `docs/ui/pages/*.md`, `docs/ui/prompts/*.md` |

## Workflow

```
/pm-market-research → /pm-prd → /tech-stack → /ui-spec
              ↓                                    ↘ /tech-arch
/pm-competitor-analysis (optional)
```

## Installation

```bash
/plugin marketplace add sparktech-ai/skills
/plugin install product-builder@sparktech-ai
```

Then restart Claude Code to activate the skills.
