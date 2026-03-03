---
name: tech-arch
description: 'Use for top-level system architecture after stack decision. Triggers: "system architecture", "module design", "technical architecture". Requires stack.md to exist.'
---

# System Architecture

Create top-level architecture design including module breakdown, key decisions, and integration points.

## When to Use

- Tech stack is decided
- Need to define system boundaries and module structure
- Want architectural decisions documented before implementation

## Process

### Step 1: Check Prerequisites

**Same-session handoff**: If user just completed `/tech-stack` in this conversation, use that context directly.

**New session**: Check for existing documents:
- `docs/tech/stack.md` - **Required**
- `docs/prd/prd.md` - **Required**
- `docs/prd/user-flow.md` - **Optional** (helps understand system scope)

Missing prerequisites → Suggest completing them first

### Step 2: Design Architecture

Based on PRD features, user flows, and tech stack:

**Core Modules:**
- List major system components
- Define responsibilities for each
- Identify boundaries between modules

**Key Decisions:**
- What choice was made and why
- Alternatives considered
- Impact on scalability, maintainability, development speed

**External Dependencies:**
- Third-party services and APIs
- Integration points and data flow

Present proposed architecture for confirmation before generating document.

### Step 3: Output Document

Generate `docs/tech/architecture.md`:

```markdown
# System Architecture

## Overview
[One sentence describing what the system does]

## Architecture Diagram
```
[Module diagram using ASCII or Mermaid]
```

## Core Modules

| Module | Responsibility | Key Interfaces |
|--------|----------------|----------------|
| ... | ... | ... |

## Key Decisions

| Decision | Choice | Alternatives | Rationale |
|----------|--------|--------------|-----------|
| ... | ... | ... | ... |

## External Dependencies

| Dependency | Purpose | Integration Point |
|------------|---------|-------------------|
| ... | ... | ... |

## Constraints & Risks
- [Technical constraint]
- [Known risk and mitigation]
```

After generating, suggest: "Architecture defined. Ready to start implementation."

## Key Principles

- **Top-level only**: Focus on modules and boundaries, not implementation details
- **Match PRD scope**: Don't over-architect beyond Phase 1
- **Decision rationale**: Always document why, not just what
- **YAGNI**: Simplest architecture that meets requirements

## Handling Edge Cases

- **Scope creep**: If architecture discussion reveals PRD gaps, note them and suggest revisiting PRD before proceeding.
- **Over-engineering tendency**: Push back on unnecessary abstractions; remind that Phase 1 architecture can evolve.
- **Unclear boundaries**: When module responsibilities overlap, propose the simpler option and note it can be split later if needed.
