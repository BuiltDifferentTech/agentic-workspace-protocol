# Agent Instructions

This repository uses the Agentic Workspace Protocol.

Persistent agent context is stored under `.agents/`.

Before performing meaningful work:

1. Read `.agents/PROJECT_STATE.md`.
2. Find the relevant document under `.agents/implementations/`, including any already `IN PROGRESS`, to see what is currently active.
3. If no implementation exists for the requested work, create one.
4. Search `.agents/memory/` for relevant topics.
5. Inspect relevant files under `.agents/docs/`.
6. Check `.agents/capabilities/` before using external agent capabilities.

Keep the relevant implementation document updated throughout the task, including its `Status`.

Use `.agents/workspace/` freely for temporary work.

If project documentation, memory, or implementation records disagree with each other or with observed project behaviour, do not resolve the conflict silently. Flag it in the implementation document (and directly to the user, if significant) and prefer human-provided content over AI-generated content when a default is required.

Before finishing:

1. Verify the implementation.
2. Update its implementation document, including a final `Status`.
3. Update `PROJECT_STATE.md` where project truth changed.
4. Persist durable discoveries into topical memory files.
5. Persist newly learned capability/tool usage into `.agents/capabilities/`.
6. Remove or leave clearly disposable temporary workspace artifacts.
