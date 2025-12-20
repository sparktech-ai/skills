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
