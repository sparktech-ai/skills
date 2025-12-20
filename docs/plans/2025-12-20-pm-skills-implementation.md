# PM Skills Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Create two Claude Code skills (`/research` and `/prd`) to help indie developers go from vague ideas to structured PRD documents.

**Architecture:** Each skill is a standalone SKILL.md file following Claude Code skill conventions. Skills use collaborative dialogue + WebSearch for research, producing markdown documents in `docs/prd/`.

**Tech Stack:** Claude Code Skills (YAML frontmatter + Markdown instructions)

---

## Task 1: Create skill directory structure

**Files:**
- Create: `skills/research/SKILL.md`
- Create: `skills/prd/SKILL.md`

**Step 1: Create directories**

```bash
mkdir -p skills/research skills/prd
```

**Step 2: Verify directory structure**

Run: `ls -la skills/`
Expected: `research/` and `prd/` directories exist

**Step 3: Commit**

```bash
git add skills/
git commit -m "chore: create skill directories for research and prd"
```

---

## Task 2: Implement `/research` skill

**Files:**
- Create: `skills/research/SKILL.md`

**Step 1: Write the SKILL.md file**

```markdown
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
```

**Step 2: Verify file created**

Run: `cat skills/research/SKILL.md | head -20`
Expected: YAML frontmatter with name and description visible

**Step 3: Commit**

```bash
git add skills/research/SKILL.md
git commit -m "feat: add /research skill for market research workflow"
```

---

## Task 3: Implement `/prd` skill

**Files:**
- Create: `skills/prd/SKILL.md`

**Step 1: Write the SKILL.md file**

```markdown
---
name: prd
description: PRD writing skill for indie developers. Use when ready to define product requirements. Transforms ideas or research into structured PRD with phased feature rollout (validation → refinement → expansion).
---

# PRD Writing

Transform product ideas into structured PRD documents with phased implementation plans.

## When to Use

- Have a clear product idea ready to document
- Completed market research and ready to define requirements
- Need to structure scattered thoughts into actionable PRD

## Process

### Phase 1: Determine Input

Check for existing research:

1. Look for `docs/prd/research-*.md` files
2. If found, ask: "Found research document for [topic]. Base PRD on this research?"
3. If none, ask user to describe their product idea

### Phase 2: Product Definition

Guide through core product decisions (one question at a time):

**Core Value:**
- What problem does this solve?
- What's the one-sentence pitch?

**Target Users:**
- Who specifically will use this?
- What's their current situation?

**Core Scenarios:**
- Walk through primary use case
- What does success look like for the user?

**MVP Scope:**
- What's absolutely essential for first version?
- What can wait?

When user is uncertain, provide recommendations based on:
- Research document insights (if available)
- Market best practices
- Indie developer constraints (lean, fast validation)

### Phase 3: Refine Requirements

Structure features into phases:

**Phase 1 - Validation:**
- Minimum features to test core hypothesis
- How to validate (metrics, user feedback)
- Success criteria (what proves/disproves the idea)

**Phase 2 - Refinement:**
- Features to add after validation succeeds
- Improvements based on learnings

**Phase 3 - Expansion (optional):**
- Growth features
- Nice-to-haves

Also capture:
- Non-functional requirements (performance, security basics)
- Constraints (technical limitations, resource limits)

### Phase 4: Output Document

Generate `docs/prd/<product-name>.md`:

```markdown
# <Product Name> PRD

## Product Overview
- **One-liner:** [elevator pitch]
- **Target Users:** [who]
- **Core Value:** [why they care]

## User Stories

### Primary Scenario
As a [user], I want to [action] so that [outcome].

### Secondary Scenarios
...

## Feature Requirements

### Phase 1: Validation
| Feature | Description | Validation Method | Success Criteria |
|---------|-------------|-------------------|------------------|
| ...     | ...         | ...               | ...              |

### Phase 2: Refinement
| Feature | Description | Priority |
|---------|-------------|----------|
| ...     | ...         | ...      |

### Phase 3: Expansion (Optional)
| Feature | Description |
|---------|-------------|
| ...     | ...         |

## Non-Functional Requirements
- Performance: ...
- Security: ...

## Constraints
- Technical: ...
- Resources: ...

## Success Metrics
- Validation: [how to know if Phase 1 worked]
- Growth: [longer-term metrics]
```

## Key Principles

- **Flexible input**: Work with research docs or raw ideas
- **Phased approach**: Always structure as validation → refinement → expansion
- **Proactive recommendations**: When user is uncertain, suggest based on research/best practices
- **Product focus**: Keep technical details minimal, only essential constraints
- **One question at a time**: Don't overwhelm with multiple questions
```

**Step 2: Verify file created**

Run: `cat skills/prd/SKILL.md | head -20`
Expected: YAML frontmatter with name and description visible

**Step 3: Commit**

```bash
git add skills/prd/SKILL.md
git commit -m "feat: add /prd skill for PRD writing workflow"
```

---

## Task 4: Create docs/prd directory placeholder

**Files:**
- Create: `docs/prd/.gitkeep`

**Step 1: Create directory with placeholder**

```bash
mkdir -p docs/prd
touch docs/prd/.gitkeep
```

**Step 2: Verify**

Run: `ls -la docs/prd/`
Expected: `.gitkeep` file exists

**Step 3: Commit**

```bash
git add docs/prd/.gitkeep
git commit -m "chore: add docs/prd directory for skill outputs"
```

---

## Task 5: Update README

**Files:**
- Modify: `README.md`

**Step 1: Update README with skill documentation**

Replace contents with:

```markdown
# Skills

Claude Code skills for indie developer workflows.

## Available Skills

### `/research` - Market Research
Explore product opportunities through market research and competitor analysis.

**Use when:**
- Starting a new project but unsure what to build
- Have a vague idea and want to validate it
- Need to understand market landscape

**Output:** `docs/prd/research-<topic>.md`

### `/prd` - PRD Writing
Transform ideas into structured PRD documents with phased implementation.

**Use when:**
- Have a clear product idea ready to document
- Completed market research
- Need to structure thoughts into actionable requirements

**Output:** `docs/prd/<product-name>.md`

## Installation

Add this repository as a Claude Code plugin or copy the `skills/` directory to your project.
```

**Step 2: Verify**

Run: `cat README.md`
Expected: Updated content with skill documentation

**Step 3: Commit**

```bash
git add README.md
git commit -m "docs: update README with skill documentation"
```

---

## Task 6: Final verification

**Step 1: Verify complete file structure**

Run: `find . -type f -name "*.md" | grep -v node_modules | sort`

Expected output:
```
./README.md
./docs/plans/2024-12-20-pm-skills-design.md
./docs/plans/2024-12-20-pm-skills-implementation.md
./docs/prd/.gitkeep
./skills/prd/SKILL.md
./skills/research/SKILL.md
```

**Step 2: Verify git status is clean**

Run: `git status`
Expected: "nothing to commit, working tree clean"

**Step 3: View commit history**

Run: `git log --oneline -5`
Expected: 4 new commits for skill implementation
