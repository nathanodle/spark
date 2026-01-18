# Spec Strategy

A reusable approach to project specification. Applicable to any project.

---

## Philosophy

### Discuss Before Writing
Specs emerge from conversation, not isolation. Start broad, narrow gradually through discussion. The spec is a record of decisions made, not a document written in a vacuum.

### Specs Are Living Documents
Specs change as understanding deepens and implementation reveals reality. Update them continuously. A stale spec is worse than no spec - it actively misleads.

### Separate Concerns, Link Liberally
Split specs by concern (stack, backend, UI, features) but cross-reference heavily. When working on a feature, you should know exactly which shared specs are relevant.

### Capture Decisions, Not Just Outcomes

Don't just write down *what* was decided—write down *why*.

Specs should capture:
- **What you chose** - The decision itself
- **What you considered** - Alternatives that were on the table
- **Why you chose it** - The reasoning, tradeoffs, constraints that led to this choice

Why this matters:
- Conversations get lost (session ends, context compacts, memory fades)
- Future you (or future contributors) will wonder "why did we do it this way?"
- Knowing what was *rejected* prevents revisiting the same debates
- The reasoning often matters more than the decision itself

Don't let important decisions live only in conversation. Write them down promptly.

---

## Document Structure

### Three Layers

```
┌─────────────────────────────────────────────┐
│  Planning                                   │
│  - Critical path, implementation order      │
│  - What to build first and why              │
└─────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────┐
│  Shared Specs                               │
│  - Stack (technologies, infrastructure)     │
│  - Backend (architecture, services, schema) │
│  - UI (layout, design system, components)   │
└─────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────┐
│  Feature Specs                              │
│  - One per major feature                    │
│  - References shared specs                  │
│  - Contains feature-specific details        │
└─────────────────────────────────────────────┘
```

### Recommended Files

```
docs/spec/
├── index.md          # Entry point - links to everything, shows status
├── stack.md          # Tech choices, infrastructure, data flow
├── backend.md        # Project structure, services, schema, API conventions
├── ui.md             # Shared UI patterns, design system
└── [feature].md      # One per feature (e.g., chatbot.md, billing.md)
```

### Index Structure

The index is the entry point. It should show:
1. What the project is (one paragraph)
2. All spec documents with status
3. High-level scope/phases

```markdown
## Spec Components

### Planning
| Document | Status | Description |
|----------|--------|-------------|
| [Critical Path](critical-path.md) | ✅ Complete | Implementation order |

### Shared Specs
| Document | Status | Description |
|----------|--------|-------------|
| [Stack](stack.md) | ✅ Complete | Tech stack |
| [Backend](backend.md) | 🔲 Pending | Architecture |
| [UI](ui.md) | 🔲 Pending | Design system |

### Feature Specs
| Document | Status | Description |
|----------|--------|-------------|
| [Feature A](feature-a.md) | 🔲 Pending | Description |
```

---

## Cross-Referencing

Every feature spec should start with a "Related Specs" table:

```markdown
## Related Specs

| Spec | Relevance |
|------|-----------|
| [Stack](stack.md) | Technologies used by this feature |
| [Backend](backend.md) | Shared services, API conventions |
| [UI](ui.md) | Shared components, design system |
```

This tells the reader (human or AI) where to look for context before diving into feature-specific details.

---

## Status Tracking

Use consistent status indicators:

| Status | Meaning |
|--------|---------|
| ✅ Complete | Spec written and approved, ready to implement |
| 🔲 Pending | Placeholder exists, content not written |
| 🔲 Partial | Some sections done, others TODO |
| 🔲 Draft | Written but not reviewed/approved |

Mark sections within docs too:

```markdown
## Authentication

*TODO: Define auth flow*

## Database Schema

✅ **Complete**

Tables defined and approved.
```

---

## Build Order

Every project should have a build order document that answers:
1. What do we build first?
2. Why that order? (dependencies)
3. What spec sections need to be done for each step?

Format:

```
Step 1: [Name]
  What: Brief description
  Why first: Dependency explanation
  Spec: Which doc/section
  Status: ✅/🔲
      ↓
Step 2: [Name]
  ...
```

---

## Stack Spec

The stack spec should cover:

1. **Summary table** - Quick reference of all tech choices
2. **Backend details** - Framework, ORM, database, etc.
3. **Frontend details** - Framework, styling, components
4. **AI/ML details** - Models, inference, embeddings (if applicable)
5. **Infrastructure** - Deployment, networking, process management
6. **External services** - APIs, third-party integrations
7. **Data flow diagram** - How pieces connect
8. **Future considerations** - Known areas for later expansion

---

## Backend Spec

The backend spec should cover:

1. **Project structure** - Folder layout, where code goes
2. **Database schema** - Tables, relationships
3. **Authentication** - Auth strategy, session handling
4. **Shared services** - Reusable components (API clients, etc.)
5. **API conventions** - Response formats, error handling
6. **WebSocket protocol** - If real-time features exist

---

## Feature Specs

Each feature spec should cover:

1. **Related specs** - Links to relevant shared specs
2. **Overview** - What the feature does, user perspective
3. **Detailed requirements** - Specific functionality
4. **Feature-specific UI** - Screens, interactions unique to this feature
5. **Feature-specific backend** - Endpoints, logic unique to this feature
6. **Error handling** - Feature-specific error cases

---

## AI/Agent Instructions

If using AI assistants (Claude, etc.), create a `CLAUDE.md` or `AGENTS.md` in project root:

1. **Project description** - What is this?
2. **Spec organization** - How specs are structured
3. **Key files** - Where to find important docs
4. **Constraints** - Important rules (no Docker, read-only APIs, etc.)
5. **Keep docs in sync** - Remind AI to update docs as it works

```markdown
## Keep Docs in Sync

**IMPORTANT:** Always update documentation as you work.

- When you implement something, update the relevant spec
- When you make architecture decisions, document them
- Mark spec sections as ✅ Complete when done

The user may start new sessions and relies on docs being accurate.
```

---

## Workflow

### Starting a New Project

1. Create `docs/spec/` directory
2. Create `index.md` with project overview
3. Discuss stack choices → write `stack.md`
4. Identify features → create placeholder `[feature].md` files
5. Discuss build-order → write `build-order.md`
6. Work through build-order, filling in specs as you go

### During Development

1. Before implementing: check relevant specs
2. During implementing: note any spec changes needed
3. After implementing: update specs to reflect reality
4. Mark sections complete as you go

### New Session / New Contributor

1. Read `CLAUDE.md` or `AGENTS.md` (if AI) or `README.md` (if human)
2. Read `docs/spec/index.md` for overview
3. Check `critical-path.md` for current focus
4. Read relevant feature spec + its related specs
5. Continue work

---

## Spec Before Implementation

### Default Mode: Discussion

The default mode is **discussion**, not implementation. Spec first, code second.

Don't suggest starting implementation until the relevant spec sections are solid. It's tempting to jump into code early, but premature implementation leads to rework, inconsistencies, and wasted effort.

### Implementation Readiness Criteria

A spec section is ready for implementation when:

1. **No unresolved TODOs** - No "TODO", "TBD", or placeholders in that section
2. **No open questions** - Questions about that section have been discussed and answered
3. **User has approved** - Not just written, but reviewed and agreed to by the user
4. **Status is ✅ Complete** - Explicitly marked complete, not 🔲 Pending or Draft
5. **Dependencies ready** - Anything it depends on is either:
   - Already implemented, OR
   - Well enough defined that you know how to use it (what it takes in, what it gives back, how to call it)
6. **UX/UI defined (if user-facing)** - User flows, layouts, key interactions, error states
7. **Big picture understood** - How this fits into overall architecture, no conflicts with other specs

### Dependencies and Build Order

Be mindful of what depends on what. Before implementing feature X:

- Are its dependencies specced?
- Are they implemented, or at least defined well enough to code against?
- Do you understand how X fits into the bigger picture?

"Well enough defined" means:
- Data models/schemas are clear
- API endpoints are defined (method, path, what goes in, what comes back)
- For internal pieces: what it does, what you pass it, what you get back
- Enough that you could write code that *uses* it, even if the implementation doesn't exist yet

### What's NOT Required

Don't over-spec. These can emerge during implementation:
- Every edge case (some you'll discover as you build)
- Pixel-perfect designs (wireframes and descriptions are enough)
- Performance optimization details
- Implementation internals (spec the *what*, not the *how*)

---

## Project Structure

### When to Define It

Project structure (folder layout, file organization) is one of the **last things to define** before implementation begins. Don't jump to creating folders and files early.

Why wait?

- Structure follows from decisions, not the other way around
- You need to know your stack before you can structure the project
- You need to understand the major pieces before you know how to organize them
- Premature structure locks you into patterns that may not fit

**Define structure after:**
- Big picture is clear (what you're building, who it's for)
- Stack is decided (framework, database, frontend approach)
- Major features/modules are identified
- You understand how the pieces relate

**Define structure before:**
- Writing any implementation code
- It's part of the "last mile" of spec work

### Separation of Concerns

Good project structure reflects clean boundaries between different kinds of code. The goal: each layer can change independently without rippling through everything else.

**Core principle:** Code should be organized by *what it does*, not just *what feature it's part of*.

#### Common Layers

**Data / Models**
- Database schemas, data structures, types
- Should be independent—no knowledge of how data is served or displayed
- Other layers import from here, this layer imports from nothing (or very little)

**Backend / API**
- Business logic, API endpoints, services
- Knows about data layer, doesn't know about UI
- Handles validation, authorization, orchestration

**UI / Frontend**
- Presentation, user interaction, display logic
- Knows how to call the API, doesn't know how the API is implemented
- Doesn't contain business logic—that belongs in the backend

**Shared / Utilities**
- Code used across layers (helpers, constants, types)
- Should be minimal—if everything ends up here, your boundaries are unclear

#### Why This Matters

- **Testability** - Each layer can be tested in isolation
- **Flexibility** - Swap out the UI without touching the backend, change the database without rewriting the API
- **Clarity** - New contributors know where to find things and where to put new code
- **Maintainability** - Changes stay localized instead of cascading everywhere

#### Signs of Poor Separation

- UI components making direct database calls
- Business logic scattered across frontend components
- Backend code that knows about UI-specific concerns (how things are displayed)
- Circular dependencies between layers
- "Utils" folder that contains half the codebase

#### Practical Guidance

1. **Start with the obvious layers** - Most apps have data, backend, and frontend. Start there.

2. **Let features emerge within layers** - Within `backend/`, you might have `auth/`, `users/`, `billing/`. But those are subdivisions of the backend layer, not replacements for it.

3. **Shared code should be minimal** - If you're constantly reaching for shared utilities, ask if your boundaries are in the right place.

4. **Monorepo vs. separate repos** - For most projects, a monorepo with clear folder boundaries is simpler than multiple repos. Separate repos add coordination overhead.

5. **Match the framework's conventions** - If your framework has opinions about structure, follow them unless you have a strong reason not to. Fighting the framework creates friction.

---

## Anti-Patterns

### Don't Do This

- **Monolithic spec** - One giant document is hard to navigate and update
- **Orphan specs** - Feature specs with no links to shared specs
- **Write-once specs** - Specs written at start and never updated
- **Implementation details in stack spec** - Stack is *what*, not *how*
- **Vague TODOs** - "TODO: figure this out" - be specific about what's unknown

### Do This Instead

- **Split by concern** - Easier to find, easier to update
- **Cross-reference** - Related Specs table in every feature doc
- **Living documents** - Update as you learn and build
- **Stack = choices, Backend = architecture** - Clear separation
- **Specific unknowns** - "TODO: Define session expiration policy"

---

## Template Files

When starting a new project, copy these templates and replace `{{PLACEHOLDER}}` values:

| Template | Purpose |
|----------|---------|
| `CLAUDE.md.template` | AI assistant project guide - copy to `CLAUDE.md` |
| `docs/spec/index.md.template` | Spec overview and entry point |
| `docs/spec/stack.md.template` | Tech stack documentation |
| `docs/spec/build-order.md.template` | Implementation order |
| `docs/spec/backend.md.template` | Backend architecture (if applicable) |
| `docs/spec/ui.md.template` | UI patterns (if applicable) |
| `docs/spec/feature.md.template` | Feature spec - copy once per major feature |

### Quick Start

```bash
# Copy templates to start a new project
cp CLAUDE.md.template CLAUDE.md
cp docs/spec/index.md.template docs/spec/index.md
cp docs/spec/stack.md.template docs/spec/stack.md
cp docs/spec/build-order.md.template docs/spec/build-order.md

# Copy shared specs if applicable
cp docs/spec/backend.md.template docs/spec/backend.md
cp docs/spec/ui.md.template docs/spec/ui.md

# Copy feature template for each major feature
cp docs/spec/feature.md.template docs/spec/my-feature.md
```
