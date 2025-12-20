---
name: market-research
description: Use when user explicitly wants market research, competitor analysis, or needs help deciding what product to build. Triggers: "do market research", "analyze competitors", "what should I build", "validate this idea", "is there a market for". Do NOT trigger for casual product discussions or when user already has clear requirements.
---

# Market Research

Help product builders discover and validate product opportunities through market research.

## CRITICAL: Do Not Skip

**Before ANY research, you MUST know:**
1. **Goal** - monetization, learning, or solving a personal pain point?
2. **Market** - local (e.g., China) or global?

If the user's initial message doesn't provide both, **STOP and ask** before doing any WebSearch or WebFetch. These determine which competitors to analyze, what pricing to reference, and which distribution channels matter.

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

First, ask one open question:

**"Do you have a product direction in mind, or are you looking for ideas?"**

Based on response:

- **Clear direction** → **MUST confirm both context items before any research**:
  1. **Goal**: monetization, learning, or solving a personal pain point?
  2. **Market**: local (e.g., China) or global?

  Only ask what's missing. Example: user says "subscription manager to monetize" → goal is clear, ask about market. **DO NOT proceed to Step 3 until both are explicitly confirmed.** These shape competitor selection, pricing strategy, and distribution recommendations.

- **Vague/uncertain** → Proceed to Step 2 (Trend Exploration) first. Context questions will be asked after user picks a direction.

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

3. **Wait for user to confirm direction**, then ask the context questions:
   - **"What's your main goal—monetization, learning, or solving a personal pain point?"**
   - **"Who's your target market—local (e.g., China) or global?"**

4. Proceed to Step 3 (Deep Dive) after context is confirmed.

### Step 3: Deep Dive (after direction confirmed)

**Purpose**: Validate the chosen direction (depth). This step provides thorough analysis to inform the PRD.

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

After generating the document, suggest: "When ready to define requirements, use `/pm:prd` to create a PRD based on this research."

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
