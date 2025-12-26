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
├── pages/           # Page specs (user's language)
│   ├── login.md
│   └── dashboard.md
└── prompts/         # Stitch AI prompts (English, for AI)
    ├── login.md
    └── dashboard.md
```

## Process

### Step 1: Check Prerequisites

**Same-session handoff**: If user just completed `/tech:stack` or `/pm:prd` in this conversation, use that context directly.

**New session**: Check for existing documents:
- `docs/prd/prd.md` - **Required**
- `docs/prd/user-flow.md` - **Required**
- `docs/tech/stack.md` - **Optional** (provides UI component library and constraints)

Missing prerequisites → Suggest completing them first

### Step 2: Confirm Design Preferences

Collect design preferences from `docs/tech/stack.md` or `docs/ui/style.md` if they exist. Present the following to user for confirmation:

| Preference | Description | Example Values |
|------------|-------------|----------------|
| **UI Component Library** | Framework components to use | HeroUI, shadcn/ui, Ant Design |
| **Icon Library** | Icon package to use (SVG format) | Lucide, Heroicons, Phosphor, Tabler |
| **Primary Color** | Brand primary color | #3B82F6, blue-500 |
| **Theme Support** | Light/dark mode support | light-only, dark-only, both (default: light), both (default: dark) |
| **Border Radius** | Corner roundness style | none, sm, md, lg, full |
| **Visual Style** | Overall aesthetic direction | minimal, modern, playful, corporate |

**Flow:**
1. Extract existing preferences from stack.md or style.md
2. Present summary: "Design preferences: [list]. Confirm or adjust?"
3. If no existing preferences, ask user to provide them
4. Save confirmed preferences to `docs/ui/style.md`

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

### Step 3: Identify Pages

From user-flow.md, extract all unique screens:

1. List all pages mentioned in flows
2. Categorize by flow (primary, secondary, error)
3. Present list for confirmation

Ask: "I identified these pages from the user flow: [list]. Any to add or remove?"

### Step 4: Generate Page Specs

For each page, create `docs/ui/pages/{page-name}.md`:

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
[Design constraints from tech stack or user input]
```

Use the user's conversation language for page specs.

### Step 5: Generate Stitch AI Prompts

For each page, create `docs/ui/prompts/{page-name}.md`:

```markdown
Design a [page type] for a [platform] application.

**Context:**
[Product name] - [One-liner from PRD]
Target users: [Target users from PRD]
This page: [Brief description of this page's purpose and position in user flow]

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

### Step 6: Batch Review

After generating all pages:
- Present a summary of all specs and prompts
- Ask if any need adjustments
- Iterate on specific pages as needed

### Step 7: Summary

After all pages complete:
- List all generated files
- Suggest: "Ready to use prompts with Stitch AI. Copy content from `docs/ui/prompts/` files."

## Key Principles

- **Match user's language**: Specs follow conversation language, prompts always in English
- **Derive from user flow**: Every page should map to a flow step
- **Confirm before generating**: Always confirm design preferences with user before generating prompts
- **Inject product context**: Include product name, one-liner, and target users from PRD in prompts
- **Apply design preferences**: Include all style preferences (color, radius, theme, visual style) in every prompt

## Handling Edge Cases

- **Missing tech stack**: Proceed without component library constraints, note that prompts may need updating after `/tech:stack`.
- **Complex page with many states**: Break into sub-pages or components if a single prompt would be too long for Stitch AI.
- **User wants different design direction**: Update Style section in both spec and prompt; maintain consistency across all pages.

## Landing Page Special Handling

When generating a landing page prompt, ask user to confirm Hero section details before generating:

| Element | Options |
|---------|---------|
| **Background** | solid / gradient / pattern (grid, dots) / animated (particles, waves) |
| **CTA Buttons** | single (Get Started) / dual (Get Started + Learn More) / with demo (Get Started + Watch Demo) |
| **Hero Visual** | none / product screenshot / mockup / 3D illustration / floating shapes |
| **Social Proof** | none / metrics below hero / trust badges / client logos |

Present defaults based on Visual Style from style.md:
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
