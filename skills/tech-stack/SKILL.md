---
name: tech-stack
description: 'Use when ready to decide on technology stack after PRD. Triggers: "choose tech stack", "what technology", "technical decisions". Requires PRD to exist.'
---

# Tech Stack Decision

Guide technology choices based on product requirements and constraints.

## When to Use

- PRD is complete and ready to start design
- Need to decide on frameworks, languages, infrastructure
- Want to document technical constraints for UI design

## Process

### Step 1: Check Prerequisites

**Same-session handoff**: If user just completed `/pm-prd` in this conversation, use that context directly and proceed to Step 2.

**New session**: Check for existing documents:
- `docs/prd/prd.md` - **Required**
- `docs/prd/user-flow.md` - **Optional** (helps understand flow complexity)

Missing PRD → Suggest using `/pm-prd` first

### Step 2: Gather Constraints

**Gather these four constraints:**

1. **Platform**: Web, mobile, or both?
2. **Preferences**: Any existing tech stack or strong preferences?
3. **Team**: Solo developer or team?
4. **Experience**: Comfort level with different technologies?

**How to gather**: Check what's inferable from PRD and context, then ask about remaining unknowns in a single question. For solo indie projects, default to simpler stacks unless user indicates otherwise.

### Step 3: Recommend Stack

Based on constraints, recommend stack with reasoning:

Present 2-3 options with:
- **Recommended option first** with reasoning
- Pros/cons for each
- Why it fits their constraints

Categories to cover:
- Frontend framework
- UI component library
- Backend/API approach
- Database
- Hosting/deployment
- Key libraries

### Step 4: Output Document

Generate `docs/tech/stack.md`:

```markdown
# Technology Stack

## Platform
- **Target:** [Web/Mobile/Both]
- **Primary:** [Main platform]

## Frontend
- **Framework:** [Choice]
- **UI Components:** [Choice - e.g., shadcn/ui, Ant Design, Material UI]
- **Reasoning:** [Why]
- **Key libraries:** [List]

## Backend
- **Approach:** [Choice - e.g., serverless, traditional, BaaS]
- **Reasoning:** [Why]
- **Key services:** [List]

## Database
- **Type:** [Choice]
- **Reasoning:** [Why]

## Infrastructure
- **Hosting:** [Choice]
- **CI/CD:** [Choice]

## Constraints for UI Design
- [Technical constraint that affects UI]
- [Another constraint]

## Not Using (and Why)
- [Technology]: [Reason for exclusion]
```

After generating, suggest: "Stack decided. Ready for `/ui-spec` to design pages or `/tech-arch` for system architecture."

## Key Principles

- **Opinionated recommendations**: Lead with your recommendation
- **Match skill level**: Don't suggest complex stacks for solo beginners
- **YAGNI**: Simplest stack that meets requirements
- **Document constraints**: UI designers need to know technical limits

## Handling Edge Cases

- **User insists on unfamiliar stack**: Note risks in the document, suggest learning resources, but respect user's choice.
- **Conflicting requirements**: Surface the trade-off explicitly (e.g., "React Native for speed vs native for performance"), let user decide.
- **No clear platform target**: Default to web-first for faster iteration, note mobile as Phase 2 option.
