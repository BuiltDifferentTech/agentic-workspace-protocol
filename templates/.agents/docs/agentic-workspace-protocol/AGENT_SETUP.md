# Agent-Driven AWP Setup

## Purpose

This document is a procedure for an AI agent to adopt the Agentic Workspace Protocol (AWP) into a target repository directly — creating and populating the workspace itself, rather than a human copying the blank files in [`templates/`](../../../templates/).

## When to use this instead of `templates/`

| | `templates/` | This document |
|---|---|---|
| Who performs the setup | A human, by copying files | An agent, by generating them |
| Initial file content | Blank, filled in later | Populated from the real project during setup |
| Best for | Projects that want to review the skeleton before using it | Projects that want an agent to bootstrap AWP in one pass |

Both paths produce the same structure described in [`../design-document.md`](../design-document.md) (section 3). Neither is more "correct" than the other — choose based on who is doing the setup.

## Preconditions

Before starting, confirm:

- The target repository does not already have `AGENTS.md`, `CLAUDE.md`, or a `.agents/` directory. If it does, this is an update, not a fresh setup — read the existing files first and extend them rather than overwrite them.
- You have enough access to the target repository to inspect its source, dependencies, and history, since several steps below require this.

## Procedure

1. **Read the specification.** Read [`../design-document.md`](../design-document.md) in full before creating anything. It is the source of truth for structure and semantics; this document only sequences the work.
2. **Create the root entry points.**
   - `AGENTS.md` — canonical agent operating instructions. Base it on the example in design-document.md section 4, adjusted for the target project's actual layout and conventions.
   - `CLAUDE.md` — adapter that redirects to `AGENTS.md`. Use the exact text in design-document.md section 5; do not duplicate instructions into it.
3. **Create the `.agents/` skeleton:**
   ```text
   .agents/
   ├── PROJECT_STATE.md
   ├── memory/
   ├── implementations/
   ├── capabilities/
   ├── workspace/
   └── docs/
   ```
4. **Populate `PROJECT_STATE.md` from the real project, not blank.** Inspect the target repository (language/runtime, frameworks, major dependencies, architecture, existing systems, known issues) and fill in every section from design-document.md section 8. This is the key difference from `templates/`: the file should already be true on first commit, not a form waiting to be filled in. Mark anything the human explicitly told you (as opposed to what you inferred from reading the code) per design-document.md section 25.
5. **Create an initial implementation document** under `.agents/implementations/` (for example `00-bootstrap-repository.md`) recording this setup as a piece of work in its own right, using the structure in design-document.md section 14. Set its `Status` to `IN PROGRESS` while setup is underway — this is how the setup itself is tracked as active work, per section 9, since AWP has no separate `CURRENT.md`.
6. **Populate `capabilities/`** with whatever tools and capabilities are actually available to agents in this repository, or an honest "none configured yet" (design-document.md section 32) — not generic placeholder text. Start with at least a `README.md` index.
7. **Leave `memory/` and `workspace/` empty** (add a `.gitkeep` if the project needs Git to track the empty directory). They fill in as real work happens; do not pre-populate them with speculative content.
8. **Leave `docs/` for the human.** Do not add files to it unless the human has supplied material for the agent to place there.
9. **Verify** the result against design-document.md section 3 and section 41 (minimal workspace) before reporting the setup complete.
10. **Set the implementation document's `Status` to `COMPLETE`** once the above holds, and **stop here — do not treat setup as finished yet.** This is a hard gate, not a suggestion: a human must review and correct `PROJECT_STATE.md` (and the new implementation document) before they are trusted as "current truth" by future agents, per design-document.md section 6. Report back to the human what was created and which parts may need correction — an agent's read of "what's true about the project" is a starting point, not a guarantee. Setup is only complete once that review has happened.

## Result

A repository bootstrapped this way ends up structurally identical to one set up from `templates/`, but with `PROJECT_STATE.md`, `capabilities/`, and an initial implementation document already reflecting the real project instead of being blank — and with a human review of that generated content as the final step, not an optional afterthought.
