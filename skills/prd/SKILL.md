---
name: prd
description: Use when user explicitly wants to write or create a PRD/product requirements document. Triggers: "write PRD", "create PRD", "document requirements", "define the product". Requires user to have a product direction—if unclear, suggest market-research first.
---

# PRD Writing

Transform product ideas into structured PRD documents with phased implementation plans.

## When to Use

- Have a clear product idea ready to document
- Completed market research and ready to define requirements
- Need to structure scattered thoughts into actionable PRD

## Process

### Step 1: Assess Readiness

Check for `docs/prd/research-*.md` files first:

- **Research exists** → Ask: "Found research for [topic]. Use this as the basis?" If yes, extract key insights (target users, pain points, recommended direction) to pre-fill Step 2 answers—only confirm or refine with user instead of asking from scratch.
- **No research** → Ask user to describe their product idea

Based on clarity of user's input:
- **Clear direction** → Proceed to Step 2
- **Vague/uncertain** → Suggest using `/sparkai:market-research` for market research first

### Step 2: Product Definition

Guide through 4 core questions (one at a time):

1. **"What problem does this solve?"** - Core value proposition
2. **"Who specifically will use this?"** - Target user persona
3. **"Walk me through how a user would use this"** - Primary use case
4. **"What's essential for the first version?"** - MVP scope

When user is uncertain, provide recommendations based on:
- Research document insights (if available)
- Market best practices
- Indie developer constraints (lean, fast validation)

### Step 3: Refine Requirements

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

### Step 4: Output Document

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
- **Match user's language**: Output in the same language the user uses in conversation
