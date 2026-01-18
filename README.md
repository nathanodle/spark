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

### The Bootstrap Process

The repo ships with a minimal `CLAUDE.md` that exists only to bootstrap the process. When Claude reads it:

1. **Claude learns the methodology** - The bootstrap file points Claude to `docs/spec-strategy.md`, which teaches the spec-driven approach and the "discussion first, implementation later" mindset

2. **Claude asks what you're building** - Simple open-ended question to get started

3. **You discuss the big picture** - What problem you're solving, who it's for, how it should work. Claude asks questions and explores the problem space with you.

4. **Claude creates the real `CLAUDE.md`** - Using `CLAUDE.md.template`, Claude replaces the bootstrap file with a proper project guide containing your stack, architecture, constraints, etc.

5. **Specs get filled out through conversation** - As decisions are made, Claude populates the spec templates in `docs/spec/`. Each spec cross-references related specs so context stays connected.

6. **Implementation only when ready** - Claude won't suggest coding until specs meet readiness criteria: no open questions, dependencies defined, UX/UI clear, user has approved.

### What's In The Box

```
CLAUDE.md                 # Bootstrap file (gets replaced)
CLAUDE.md.template        # Template for real project guide
docs/
├── spec-strategy.md      # The methodology
└── spec/
    ├── index.md.template     # Spec overview
    ├── stack.md.template     # Tech stack
    ├── build-order.md.template
    ├── backend.md.template
    ├── ui.md.template
    └── feature.md.template   # Copy per feature
```

## The Methodology

See `docs/spec-strategy.md` for the full approach. Key principles:

- **Discuss before writing** - Specs emerge from conversation, not isolation
- **Living documents** - Update specs as you build and learn
- **Separate concerns** - Stack, backend, UI, and features in separate docs
- **Cross-reference** - Feature specs link to relevant shared specs
- **Build order** - Know what to build first and why
