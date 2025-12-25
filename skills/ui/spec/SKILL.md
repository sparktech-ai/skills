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

### Step 2: Identify Pages

From user-flow.md, extract all unique screens:

1. List all pages mentioned in flows
2. Categorize by flow (primary, secondary, error)
3. Present list for confirmation

Ask: "I identified these pages from the user flow: [list]. Any to add or remove?"

### Step 3: Generate Page Specs

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

### Step 4: Generate Stitch AI Prompts

For each page, create `docs/ui/prompts/{page-name}.md`:

```markdown
Design a [page type] for a [platform] app.

**Context:**
[Brief description of the app and this page's purpose]

**Elements:**
- [Element with behavior]
- [Element with behavior]

**States:**
- Default: [description]
- Loading: [description]
- Empty: [description]
- Error: [description]

**Style:**
[Design direction - colors, theme, style]

**Constraints:**
- Use [UI component library from stack.md] components
- [Other technical constraints from stack.md]
```

### Step 5: Batch Review

After generating all pages:
- Present a summary of all specs and prompts
- Ask if any need adjustments
- Iterate on specific pages as needed

### Step 6: Summary

After all pages complete:
- List all generated files
- Suggest: "Ready to use prompts with Stitch AI. Copy content from `docs/ui/prompts/` files."

## Key Principles

- **Match user's language**: Specs follow conversation language, prompts always in English
- **Derive from user flow**: Every page should map to a flow step
- **Include all states**: Default, loading, empty, error for each page

## Handling Edge Cases

- **Missing tech stack**: Proceed without component library constraints, note that prompts may need updating after `/tech:stack`.
- **Complex page with many states**: Break into sub-pages or components if a single prompt would be too long for Stitch AI.
- **User wants different design direction**: Update Style section in both spec and prompt; maintain consistency across all pages.
