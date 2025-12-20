---
name: market-research
description: Use when user explicitly wants market research, competitor analysis, or needs help deciding what product to build. Triggers: "do market research", "analyze competitors", "what should I build", "validate this idea", "is there a market for". Do NOT trigger for casual product discussions or when user already has clear requirements.
---

# Market Research

Help product builders discover and validate product opportunities through market research.

## Research Methods

Use WebSearch and WebFetch based on what you need:

| Need | Method | Example |
|------|--------|---------|
| Find pain points | WebSearch | "frustrated with X" reddit, "I wish there was" HackerNews |
| Discover trends | WebSearch | trending products on Product Hunt, GitHub trending |
| Analyze competitors | WebFetch | competitor pricing pages, feature lists |
| Understand users | WebSearch | user discussions, reviews, complaints |
| Validate market | WebSearch + WebFetch | market reports, industry analysis |

**Note:** All research uses publicly available web sources.

## Product Philosophy

**Focus on small and beautiful, not large and comprehensive:**

- **Start with specific pain points** - Solve one problem exceptionally well, not many problems poorly
- **Target niche users** - Better to be essential to 100 users than nice-to-have for 10,000
- **Minimum viable scope** - Ship the smallest version that delivers real value
- **Iterate based on feedback** - Let users guide expansion, don't predict features

**Why this matters:**
- Large teams build platforms; small teams win with focused solutions
- Users choose specialists over generalists for critical pain points
- Faster to market = faster to learn what actually matters
- Less to build = less to maintain = more sustainable

**Use brainstorming skill** when exploring ideas to ensure focus on user pain points and small-beautiful approach.

## When to Use

- Starting a new project but unsure what to build
- Have a vague idea and want to validate it
- Need to understand market landscape before committing

## Process

### Step 1: Understand Goals

Ask two questions (one at a time):

1. **"What type of product do you want to build? Any initial ideas?"**
2. **"What's your main goal—monetization, learning, or solving a personal pain point?"**

Let constraints emerge naturally through conversation. Don't interrogate.

### Step 2: Market Exploration

When the user's idea is vague or blank, actively research opportunities:

1. Use WebSearch to find:
   - **Specific user pain points** - Look for "I wish there was..." "frustrated with..." discussions
   - Emerging pain points in developer/productivity tools
   - Underserved niches with clear, focused needs
   - Trending markets and opportunities

2. Filter opportunities by:
   - **Pain point specificity** - Is it a clear, focused problem?
   - **Niche definition** - Can you serve 100 users exceptionally well?
   - User's stated purpose (monetization vs learning)
   - Feasibility for the team/individual
   - Competition level (large competitors often ignore niches)

3. Present 2-3 directions with:
   - **Recommended option first** with reasoning (prioritize small-beautiful over large-comprehensive)
   - Specific pain point being solved
   - Target niche and size
   - Minimum viable scope
   - Pros/cons for each
   - Why it fits their goals

### Step 3: Deep Dive (after user selects direction)

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

### Step 4: Output Document

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

After generating the document, suggest: "When ready to define requirements, use `/sparkai:prd` to create a PRD based on this research."

## Key Principles

- **Proactive research**: Don't just ask questions—actively search and analyze
- **Opinionated recommendations**: Lead with recommendations, explain reasoning
- **One question at a time**: Keep dialogue focused, don't overwhelm
- **User decides**: Present options, let user choose direction
- **Match user's language**: Output in the same language the user uses in conversation
