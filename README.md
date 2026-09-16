# Agentic Workspace Protocol (AWP)

**Status:** Draft · **Version:** 0.3

AWP is an open, file-based architecture for giving AI development agents a persistent, structured workspace inside a software repository.

> Agent context should be project infrastructure, not transient conversation history.

## The problem

Conversations end. Context windows compress. Agents get swapped out. Without a durable place to put project truth, active work, and hard-won lessons, every new agent session starts from zero and repeats the same investigation.

## The idea

AWP separates concerns that are usually collapsed into ad-hoc chat history:

| Concern | Lives in |
|---|---|
| How agents should behave | `AGENTS.md` |
| What's true about the project right now | `.agents/PROJECT_STATE.md` |
| What work was done, why, and what's currently active | `.agents/implementations/` |
| What was learned, by topic | `.agents/memory/` |
| Temporary scratch work | `.agents/workspace/` |
| Human-supplied context (specs, screenshots, docs) | `.agents/docs/` |
| Available tools and capabilities, and how to use them | `.agents/capabilities/` |

It's built entirely from ordinary files and directories — no proprietary format, database, IDE, or model dependency.

## Read the spec

The full specification lives at [`templates/.agents/docs/design-document.md`](templates/.agents/docs/design-document.md).

## Adopt it in your project

There are two ways to adopt AWP, depending on who's doing the setup:

**By hand:** copy the starter kit in [`templates/`](templates/) into your repository root:

```text
your-project/
├── AGENTS.md
├── CLAUDE.md
└── .agents/
    ├── PROJECT_STATE.md
    ├── memory/
    ├── implementations/
    ├── capabilities/
    ├── workspace/
    └── docs/
```

Fill in `PROJECT_STATE.md` and `capabilities/` for your project, then point your agent at `AGENTS.md`.

**By agent:** point an AI agent at [`templates/.agents/docs/agentic-workspace-protocol/AGENT_SETUP.md`](templates/.agents/docs/agentic-workspace-protocol/AGENT_SETUP.md) and have it bootstrap the workspace directly in your repository. It creates the same structure, but populates `PROJECT_STATE.md`, `capabilities/`, and an initial implementation document from the real project instead of leaving them blank — subject to a human reviewing that generated content before setup counts as complete.

## Status

The specification is a draft (v0.3). It's being refined based on real use. Expect changes before a 1.0 is ratified.

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## License

MIT — see [`LICENSE`](LICENSE).
