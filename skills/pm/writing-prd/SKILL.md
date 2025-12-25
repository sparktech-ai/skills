---
name: writing-prd
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

**Same-session handoff**: If user just completed `/pm:research` or `/pm:teardown` in this conversation, skip the file check—use those insights directly and proceed to pre-fill confirmation.

**New session**: Check for existing documents:

1. Check `docs/prd/research-*.md` (market research)
2. Check `docs/prd/teardown-*.md` (competitor teardown)

**Pre-fill logic based on available documents:**

| Document | Pre-fills |
|----------|-----------|
| Research "Target Users & Pain Points" | Questions 1 (problem) and 2 (users) |
| Research "Recommended Direction" | Question 3 (use case) |
| Teardown "Insights → Differentiation Opportunities" | Question 4 (MVP scope) - what to prioritize |
| Teardown "Insights → Table Stakes" | Question 4 (MVP scope) - what must exist |
| Teardown "Pain Points" | Feature ideas - problems to avoid |

**Flow:**
- **Documents exist** → Ask: "Found [research/teardown] for [topic]. Use this as the basis?" If yes, present pre-filled summary for confirmation.
- **No documents** → Ask user to describe their product idea

Based on clarity of user's input:
- **Clear direction** → Proceed to Step 2
- **Vague/uncertain** → Suggest using `/pm:research` for market research first

### Step 2: Product Definition

Guide through 4 core questions (one at a time):

1. **"What problem does this solve?"** - Core value proposition
2. **"Who specifically will use this?"** - Target user persona
3. **"Walk me through how a user would use this"** - Primary use case
4. **"What's essential for the first version?"** - MVP scope

When user is uncertain, provide recommendations based on:
- Research document insights (if available)
- Teardown insights: differentiation opportunities, competitor pain points to avoid
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

### Step 4: Output Documents

Generate two files:
1. `docs/prd/prd.md` - PRD main document
2. `docs/prd/user-flow.md` - User flow document

#### PRD Main Document

Generate `docs/prd/prd.md`:

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

#### User Flow Document

Also generate `docs/prd/user-flow.md`:

```markdown
# User Flow

## Primary Flow: [Main Use Case]

```
[Start] → [Step 1] → [Step 2] → [Step 3] → [End]
```

### Step 1: [Action]
- **Screen:** [Page name]
- **User action:** [What user does]
- **System response:** [What happens]
- **Next:** [Where to go]

### Step 2: [Action]
...

## Secondary Flows

### [Alternative Flow Name]
...

## Error Flows

### [Error Case]
- **Trigger:** [What causes this]
- **Screen:** [Error page/state]
- **Recovery:** [How to recover]
```

## Key Principles

- **Flexible input**: Work with research docs, teardown analysis, or raw ideas
- **Phased approach**: Always structure as validation → refinement → expansion
- **Proactive recommendations**: When user is uncertain, suggest based on research/best practices
- **Product focus**: Keep technical details minimal, only essential constraints
- **One question at a time**: Don't overwhelm with multiple questions
- **Match user's language**: Output in the same language the user uses in conversation

## Handling Edge Cases

- **User abandons mid-process**: Save progress to a draft file (`docs/prd/prd-draft.md`) so user can resume later.
- **Insufficient information**: If user can't answer a core question after clarification, note it as "TBD" in the PRD and suggest validating with user research.
- **Conflicting requirements**: Surface the conflict explicitly, present trade-offs, and let user decide.
