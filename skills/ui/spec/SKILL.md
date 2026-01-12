---
name: ui-spec
description: Use to generate page specifications and Stitch AI prompts. Triggers: "design pages", "UI spec", "page breakdown", "Stitch prompts". Requires PRD and user-flow.
---

# UI Specification

Generate page specifications and Stitch AI prompts (English) for each screen.

## When to Use

- PRD and user flow are complete
- Ready to design individual pages
- Need prompts for Stitch AI to generate UI

## Output Structure

```
docs/ui/
├── design-concept.md # Design philosophy, mood, and visual strategy
├── style.md          # Technical style guide (colors, radius, libraries)
├── pages/            # Page specs (user's language), numbered by priority
│   ├── 01-landing.md
│   ├── 02-error.md
│   ├── 03-login.md
│   └── 04-dashboard.md
└── prompts/          # Stitch AI prompts (English, for AI), numbered by priority
    ├── 01-landing.md
    ├── 02-error.md
    ├── 03-login.md
    └── 04-dashboard.md
```

## Process

### Step 1: Check Prerequisites

**Same-session handoff**: If user just completed `/tech:stack` or `/pm:prd` in this conversation, use that context directly.

**New session**: Check for existing documents:
- `docs/prd/prd.md` - **Required**
- `docs/prd/user-flow.md` - **Required**
- `docs/prd/research-*.md` - **Optional** (highly recommended for design inspiration)
- `docs/tech/stack.md` - **Optional** (provides UI component library and constraints)

Missing prerequisites → Suggest completing them first

### Step 2: Define Design Concept

Before defining technical parameters, establish the "soul" of the design based on the product's goals and market positioning.

**Input:**
- Analysis of `docs/prd/prd.md` (Target audience, Core value)
- Analysis of `docs/prd/research-*.md` (Competitor visual distinctiveness)

**Action:**
Propose a professional design concept. Don't ask the user to design it; acting as a Design Director, **present a recommended direction** that fits the product.

**Output to `docs/ui/design-concept.md`:**
```markdown
# Design Concept

## Design Philosophy
[e.g., "Radical Simplicity," "Data-Dense Professionalism," "Playful Exploration"]
[Brief explanation of why this philosophy fits the PRD]

## Mood & Atmosphere
[Keywords describing the feeling, e.g., Trustworthy, Energetic, Calm, Futuristic]
[Description of emotional response intended for the user]

## Visual Strategy
- **Color Psychology:** [Strategy for color usage, e.g., "Deep blues for trust with electric neon accents for action"]
- **Typography & Hierarchy:** [e.g., "Clean sans-serifs with high-contrast sizing for readability"]
- **Spacing & Layout:** [e.g., "Generous white space to reduce cognitive load"]

## Interaction Principles
[e.g., "Instant feedback, minimal motion," "Fluid transitions, playful micro-interactions"]
```

**Flow:**
1. Analyze PRD/Research.
2. Present the proposed Design Concept: "Based on the product goals, I recommend a [Philosophy Name] approach..."
3. Ask for confirmation or adjustment.
4. Save to `docs/ui/design-concept.md`.

### Step 3: Confirm Technical Preferences

Translate the **Design Concept** into concrete technical constraints.

Collect preferences from `docs/tech/stack.md` or existing `docs/ui/style.md`. If creating new, **recommend values that match the Step 2 Design Concept**.

| Preference | Description | Example Values |
|------------|-------------|----------------|
| **UI Component Library** | Framework components to use | HeroUI, shadcn/ui, Ant Design |
| **Icon Library** | Icon package to use (SVG format) | Lucide, Heroicons, Phosphor, Tabler |
| **Primary Color** | Brand primary color | #3B82F6, blue-500 |
| **Theme Support** | Light/dark mode support | light-only, dark-only, both (default: light), both (default: dark) |
| **Border Radius** | Corner roundness style | none, sm, md, lg, full |
| **Visual Style** | Overall aesthetic direction | minimal, modern, playful, corporate |

**Flow:**
1. Recommend settings that align with `design-concept.md`.
   *   *Example: If concept is "Playful", recommend Rounded (lg/full) and Vibrant colors.*
   *   *Example: If concept is "Professional/Data", recommend Square/Small radius and Muted colors.*
2. Present summary: "Based on the Design Concept, here are the recommended technical specs: [list]. Confirm?"
3. Save confirmed preferences to `docs/ui/style.md`

**style.md format:**
```markdown
# UI Style Guide

- **UI Library:** [library]
- **Icon Library:** [icon package, e.g., Lucide]
- **Primary Color:** [color]
- **Theme:** [theme support and default]
- **Border Radius:** [radius]
- **Visual Style:** [style]
```

### Step 4: Identify and Prioritize Pages

From user-flow.md, extract all unique screens and sort by implementation priority:

**Priority order:**
1. Landing page - establishes visual foundation
2. Error pages - 404, 500, generic error (simple but can be triggered anytime)
3. Auth pages - login, register, forgot password
4. Core feature pages - main functionality (by user-flow order)
5. Secondary pages - settings, profile, etc.

**Flow:**
1. List all pages mentioned in flows
2. Auto-sort by priority order above
3. Present numbered list for confirmation
4. Ask: "Pages sorted by implementation priority: [numbered list]. Adjust order?"

File naming: `{nn}-{page-name}.md` (e.g., `01-landing.md`, `02-404.md`)

### Step 5: Generate Page Specs

For each page, create `docs/ui/pages/{nn}-{page-name}.md`:

```markdown
# [Page Name]

## Purpose
[What this page does, its position in the flow]

## Navigation
- **From:** [Which pages lead here]
- **To:** [Which pages can be reached]

## Elements
- [Element description]
- [Element description]

## States
- **Default:** [Default state description]
- **Loading:** [Loading state description]
- **Empty:** [Empty state description]
- **Error:** [Error state description]

## Design Style
[Specific design notes for this page, referencing design-concept.md]
```

Use the user's conversation language for page specs.

### Step 6: Generate Stitch AI Prompts

For each page, create `docs/ui/prompts/{nn}-{page-name}.md`. **Crucially, inject the Design Concept to guide the AI's aesthetic generation.**

```markdown
Design a [page type] for a [platform] application.

**Context:**
[Product name] - [One-liner from PRD]
Target users: [Target users from PRD]
This page: [Brief description of this page's purpose and position in user flow]

**Design Philosophy:**
[Insert content from design-concept.md > Design Philosophy]
Mood: [Insert content from design-concept.md > Mood]
Visual Strategy: [Insert content from design-concept.md > Visual Strategy]

**Elements:**
- [Element with behavior]
- [Element with behavior]

**States:**
- Loading: [description]
- Empty: [description]
- Error: [description]

**Style:**
- Visual style: [from style.md]
- Primary color: [from style.md]
- Border radius: [from style.md]
- Theme: Support light/dark theme following the established pattern from landing page

**Constraints:**
- Use [UI component library from style.md] components
- Use [Icon library from style.md] icons (SVG format)
- [Other technical constraints from stack.md]
```

**Important:** Always extract product name, one-liner, and target users from `docs/prd/prd.md` and include them in the Context section. This ensures Stitch AI generates contextually appropriate content instead of placeholder text.

### Step 7: Batch Review

After generating all pages:
- Present a summary of all specs and prompts
- Ask if any need adjustments
- Iterate on specific pages as needed

### Step 8: Summary

After all pages complete:
- List all generated files
- Suggest: "Ready to use prompts with Stitch AI. Copy content from `docs/ui/prompts/` files."

## Key Principles

- **Concept First**: Design parameters flow from the Concept, they are not arbitrary choices.
- **Match user's language**: Specs follow conversation language, prompts always in English
- **Derive from user flow**: Every page should map to a flow step
- **Inject product context**: Include product name, one-liner, and target users from PRD in prompts
- **Apply design preferences**: Include all style preferences (color, radius, theme, visual style) in every prompt

## Handling Edge Cases

- **Missing tech stack**: Proceed without component library constraints, note that prompts may need updating after `/tech:stack`.
- **Complex page with many states**: Break into sub-pages or components if a single prompt would be too long for Stitch AI.
- **User wants different design direction**: Update `design-concept.md` first, then let that flow down to `style.md` and prompts.

## Landing Page Special Handling

When generating a landing page prompt, ask user to confirm Hero section details before generating:

| Element | Options |
|---------|---------|
| **Background** | solid / gradient / pattern (grid, dots) / animated (particles, waves) |
| **CTA Buttons** | single (Get Started) / dual (Get Started + Learn More) / with demo (Get Started + Watch Demo) |
| **Hero Visual** | none / product screenshot / mockup / 3D illustration / floating shapes |
| **Social Proof** | none / metrics below hero / trust badges / client logos |

Present defaults based on **Design Concept** and Visual Style:
- `minimal`: solid background, single CTA, none visual, none social proof
- `modern`: gradient background, dual CTA, product screenshot, metrics below hero
- `playful`: animated background, dual CTA, 3D illustration, trust badges
- `corporate`: pattern background, with demo CTA, mockup, client logos

Ask: "Hero section for landing page - [defaults based on style]. Adjust?"

Include confirmed choices in the landing page prompt's Elements section.

**Theme generation strategy:**
- Landing page: MUST generate both light and dark theme versions explicitly (two separate designs establishing the pattern)
- Other pages: Reference landing page pattern with "Support light/dark theme following the established pattern from landing page"

This reduces generation overhead while ensuring theme consistency across all pages.
