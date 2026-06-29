# SPARK

**S**pec **P**owered **A**gent-**R**eady **K**it

A project bootstrapping template for AI-assisted development.

## What This Is

SPARK is a structured approach to starting new software projects with AI assistance. Instead of diving straight into code, you build up a specification through conversation—then implement against that spec.

The core idea: **discuss before writing, update as you build**.

## Usage

1. Clone this repo (or use as a GitHub template)
2. Open a conversation with your AI Agent
3. Tell the AI Agent what you're building

That's it. The AI Agent takes it from there.

## How It Works

### The Bootstrap Process

The repo ships with a minimal `AGENTS.md` that exists only to bootstrap the process. When the AI Agent reads it:

1. **Agent learns the methodology** - The bootstrap file points the Agent to `docs/spec-strategy.md`, which teaches the spec-driven approach and the "discussion first, implementation later" mindset

2. **Agent asks what you're building** - Simple open-ended question to get started

3. **You discuss the big picture** - What problem you're solving, who it's for, how it should work. The Agent asks questions and explores the problem space with you.

4. **Agent creates the real `AGENTS.md`** - Using `AGENTS.md.template`, the Agent replaces the bootstrap file with a proper project guide containing your stack, architecture, constraints, etc.

5. **Specs get filled out through conversation** - As decisions are made, The Agent populates specs from the templates in `docs/spec/templates/`. Platform specs go in `docs/spec/`, subsystem specs go in `docs/<subsystem>/spec/`. Each spec cross-references related specs so context stays connected.

6. **Implementation only when ready** - The Agent won't suggest coding until specs meet readiness criteria: no open questions, dependencies defined, UX/UI clear, user has approved.

### What's In The Box

```
AGENTS.md                 # Bootstrap file (gets replaced)
AGENTS.md.template        # Template for real project guide
docs/
├── spec-strategy.md      # The methodology
└── spec/
    └── templates/            # Templates for bootstrapping specs
        ├── index.md.template     # Spec overview (platform or subsystem)
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
- **Platform + subsystems** - Shared specs at the platform level, feature specs organized per subsystem/vertical
- **Capture decisions** - Record what you chose, what you considered, and why
