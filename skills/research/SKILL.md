---
name: research
description: Market research skill for indie developers. Use when exploring product ideas, analyzing markets, or finding opportunities. Helps go from vague ideas (or none) to clear product direction through research and analysis.
---

# Market Research

Help indie developers discover and validate product opportunities through market research.

## When to Use

- Starting a new project but unsure what to build
- Have a vague idea and want to validate it
- Need to understand market landscape before committing

## Process

### Phase 1: Understand Goals

Start by understanding what the user wants to achieve:

1. **Ask about purpose** (one question at a time):
   - Monetization (SaaS, one-time purchase, freemium)
   - Learning/portfolio building
   - Solving personal pain point
   - Other

2. **Ask about existing ideas**:
   - Do they have a specific direction in mind?
   - Or starting from blank?

3. **Constraints** (only if relevant, don't push):
   - Time availability
   - Technical preferences

### Phase 2: Market Exploration

When the user's idea is vague or blank, actively research opportunities:

1. Use WebSearch to find:
   - Trending markets suitable for indie developers
   - Emerging pain points in developer/productivity tools
   - Underserved niches with monetization potential

2. Filter opportunities by:
   - User's stated purpose (monetization vs learning)
   - Feasibility for solo developer
   - Competition level

3. Present 2-3 directions with:
   - **Recommended option first** with reasoning
   - Pros/cons for each
   - Why it fits their goals

### Phase 3: Deep Dive (after user selects direction)

Research the selected direction thoroughly:

**Competitor Analysis:**
- Identify 3-5 main players
- Analyze pricing, features, positioning
- Find gaps and weaknesses
- Use WebSearch and WebFetch for data

**User Research:**
- Define target user persona
- Identify core pain points
- Understand current solutions and frustrations

**Market Opportunity:**
- Entry points for a new player
- Differentiation opportunities
- Risk factors

### Phase 4: Output Document

Generate `docs/prd/research-<topic>.md`:

```markdown
# <Topic> Market Research

## Goals & Background
- Purpose: [user's goal]
- Constraints: [if any]

## Market Opportunity
- Market overview
- Trends and timing
- Why now

## Competitor Analysis

| Competitor | Strengths | Weaknesses | Pricing |
|------------|-----------|------------|---------|
| ...        | ...       | ...        | ...     |

## Target Users & Pain Points
- Primary persona
- Core pain points
- Current workarounds

## Recommended Direction
- Suggested approach
- Differentiation strategy
- Rationale
```

## Key Principles

- **Proactive research**: Don't just ask questions—actively search and analyze
- **Opinionated recommendations**: Lead with recommendations, explain reasoning
- **One question at a time**: Keep dialogue focused, don't overwhelm
- **User decides**: Present options, let user choose direction
