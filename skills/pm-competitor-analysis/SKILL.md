---
name: pm-competitor-analysis
description: 'Use when user wants deep competitor feature analysis. Triggers: "analyze competitor features", "teardown competitors", "what features do competitors have", "competitor deep dive". Requires knowing which competitors to analyze—if unclear, suggest market-research first.'
---

# Competitor Teardown

Deep dive into competitor features to inform product design decisions.

## When to Use

- Have identified competitors and want to understand their features in depth
- Need to find differentiation opportunities before writing PRD
- Want to understand what users love/hate about existing solutions

## What This Skill Does

Analyzes competitors on three dimensions:
- **Core Features** - What functionality do they offer
- **Highlight Features** - What users love, differentiators
- **Pain Points** - What users complain about, missing features

## Process

### Step 1: Identify Competitors

**Same-session handoff**: If user just completed `/pm:research` in this conversation, use the competitors identified there directly.

**New session**: Check for `docs/prd/research-*.md` files first:

- **Research exists** → Ask: "Found research for [topic] with competitors [list]. Analyze these?"
- **No research** → Ask: "Do you have specific competitors in mind, or should we use `/pm:research` to identify them first?"
  - User has competitors → Proceed with user-specified list (2-5 competitors)
  - User unsure → Guide to `/pm:research` first

### Step 2: Analyze Each Competitor

For each competitor, gather both features and sentiment in parallel:

**Features** (via WebFetch):
- Official website, docs, feature pages
- Build feature inventory: name, description, category

**User Sentiment** (via WebSearch):

| What to Find | Search Examples |
|--------------|-----------------|
| Positive reviews | "[competitor] review", "[competitor] best feature" |
| Comparisons | "[competitor] vs", "[competitor] alternative" |
| Complaints | "[competitor] frustrating" reddit, "[competitor] missing feature" |
| Feature requests | "[competitor] wish it had", "[competitor] feature request" |

Extract:
- **Highlight features**: Features users explicitly praise
- **Pain points**: Features users complain about or wish existed

Complete one competitor fully before moving to the next.

### Step 3: Output Document

Generate `docs/prd/competitor-<topic>.md`:

```markdown
# <Topic> Competitor Teardown

## Analysis Scope
- **Purpose**: [Why this analysis]
- **Competitors**: [List of analyzed competitors]

## Competitor Breakdown

### [Competitor A]

**Core Features:**
| Feature | Description | Notes |
|---------|-------------|-------|
| ... | ... | ... |

**Highlight Features:**
- [Feature]: [Why users love it, source]

**Pain Points:**
- [Feature/Gap]: [User complaints, source]

### [Competitor B]
...

## Feature Comparison Matrix
| Feature | Competitor A | Competitor B | Competitor C | Opportunity |
|---------|--------------|--------------|--------------|-------------|
| ... | ✅/❌/⚠️ | ✅/❌/⚠️ | ✅/❌/⚠️ | ... |

Legend: ✅ Well implemented | ⚠️ Partially/poorly implemented | ❌ Missing

## Insights

### Common Weaknesses
- [What all competitors do poorly or miss]

### Differentiation Opportunities
- [Where a new product could win]

### Table Stakes
- [Features that must exist to compete]
```

After generating the document, suggest: "Ready to define your product? Use `/pm:prd` to create a PRD based on this analysis."

## Key Principles

- **Deep over broad**: Focus on feature-level detail, not market-level analysis
- **User voice matters**: Prioritize real user feedback over marketing claims
- **Actionable insights**: Every finding should inform product decisions
- **Match user's language**: Output in the same language the user uses in conversation

## Handling Edge Cases

- **Competitor has no public info**: Note the gap, focus on user reviews and community discussions instead.
- **No user feedback found**: Note as "Limited user feedback available", rely more on feature comparison.
- **Too many competitors**: Recommend focusing on top 3-5 most relevant ones.
- **User abandons mid-process**: Save partial analysis to draft file for later resumption.
