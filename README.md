# SPARK

**S**pec **P**owered **A**gent-**R**eady **K**it

A project bootstrapping template for AI-assisted development.

## What This Is

SPARK is a structured approach to starting new software projects with AI assistance. Instead of diving straight into code, you build up a specification through conversation—then implement against that spec.

The core idea: **discuss before writing, update as you build**.

## Usage

1. Clone this repo (or use as a GitHub template)
2. Open a conversation with Claude
3. Tell Claude what you're building

That's it. Claude takes it from there.

## How It Works

The `CLAUDE.md` file bootstraps the process. When Claude reads it, Claude will:

- Ask what you're building
- Create project documentation through conversation
- Fill out specs iteratively as decisions are made
- Keep everything in sync as you build

## The Methodology

See `docs/spec-strategy.md` for the full approach. Key principles:

- **Discuss before writing** - Specs emerge from conversation, not isolation
- **Living documents** - Update specs as you build and learn
- **Separate concerns** - Stack, backend, UI, and features in separate docs
- **Cross-reference** - Feature specs link to relevant shared specs
- **Build order** - Know what to build first and why
