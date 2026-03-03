---
name: market-research
description: 'Use when user explicitly wants market research, competitor analysis, or needs help deciding what product to build. Triggers: "do market research", "analyze competitors", "what should I build", "validate this idea", "is there a market for". Do NOT trigger for casual product discussions or when user already has clear requirements.'
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

### Step 1: Understand Starting Point

**Gather three pieces of context before researching:**

1. **Direction**: Does user have a product idea, or exploring options?
2. **Goal**: Monetization, learning, or solving personal pain point?
3. **Market**: Target region/audience?

**How to gather**: Check what's already clear from user's message, then ask about missing pieces in a single question. Example: user says "I want to build a subscription manager to make money" → direction and goal are clear, only ask about target market.

**DO NOT proceed to research until all three are confirmed.** Goal and Market determine which competitors to analyze, what pricing to reference, and which trends are relevant.

Based on whether user has a direction:
- **Clear direction** → Proceed to Step 3 (Deep Dive)
- **Vague/uncertain** → Proceed to Step 2 (Trend Exploration)

### Step 2: Trend Exploration (when direction unclear)

**Purpose**: Discover potential directions (breadth). This step identifies options—detailed validation happens in Step 3.

Help user find direction through trend research:

1. Use WebSearch to discover:
   - Trending products on Product Hunt, GitHub trending
   - Emerging pain points in developer/productivity tools
   - Hot topics and underserved niches

2. Present 2-3 potential directions with:
   - **Recommended option first** with reasoning
   - Specific pain point being solved
   - Target niche and why it fits their goals
   - Pros/cons for each

3. **Wait for user to confirm direction**, then proceed to Step 3 (Deep Dive).

### Step 3: Deep Dive (after direction confirmed)

**Purpose**: Validate the chosen direction (depth). This step provides thorough analysis to inform the PRD.

Research the selected direction thoroughly:

**Competitor Analysis:**
- Identify 3-5 main players
- Analyze pricing, features, positioning
- Find gaps and weaknesses
- **Research competitor pain points**: Search for user complaints, negative reviews, feature requests (e.g., "[competitor] frustrating", "[competitor] missing feature", "[competitor] alternative" on Reddit, HackerNews, Twitter)
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

### User Pain Points with Competitors
- [Competitor A]: [common complaints, missing features]
- [Competitor B]: [common complaints, missing features]

## Target Users & Pain Points
- Primary persona
- Core pain points
- Current workarounds

## Recommended Direction
- Suggested approach
- Differentiation strategy
- Rationale
```

After generating the document, suggest: "Want to dive deeper into competitor features? Use `/pm:teardown` for detailed analysis. Or skip to `/pm:prd` if ready to define requirements."

## Key Principles

- **Proactive research**: Don't just ask questions—actively search and analyze
- **Opinionated recommendations**: Lead with recommendations, explain reasoning
- **One question at a time**: Keep dialogue focused, don't overwhelm
- **User decides**: Present options, let user choose direction
- **Match user's language**: Output in the same language the user uses in conversation

## Handling Edge Cases

- **User abandons mid-process**: Save any partial insights gathered so far. Offer to resume later.
- **Insufficient information**: If user's responses are too vague to proceed, ask one clarifying question. If still unclear after 2 attempts, suggest starting with a more concrete pain point or use case.
- **WebSearch/WebFetch fails**: Note the gap in research, proceed with available data, and flag limitations in the output document.
