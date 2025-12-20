# Sparking AI Skills

Claude Code skills for product builders.

## Product Management Skills

### `/sparkai:market-research` - Market Research
Explore product opportunities through market research and competitor analysis.

**Use when:**
- Starting a new project but unsure what to build
- Have a vague idea and want to validate it
- Need to understand market landscape

**Output:** `docs/prd/research-<topic>.md`

### `/sparkai:prd` - PRD Writing
Transform ideas into structured PRD documents with phased implementation.

**Use when:**
- Have a clear product idea ready to document
- Completed market research
- Need to structure thoughts into actionable requirements

**Output:** `docs/prd/<product-name>.md`

## Installation

### Option 1: Direct Plugin Installation (Recommended)

Install directly from GitHub as a standalone plugin:

```bash
/plugin marketplace add sparktech-ai/skills
/plugin install sparkai
```

Then restart Claude Code to activate the skills.

### Option 2: Via Marketplace

If you're using a marketplace that includes this plugin:

```bash
/plugin marketplace add <marketplace-repo>
/plugin install sparkai@<marketplace-name>
```

### Development Installation

For local development and testing:

```bash
# Add local directory as marketplace
/plugin marketplace add /path/to/skills

# Install from local marketplace
/plugin install sparkai@sparkai-dev

# Restart Claude Code
```
