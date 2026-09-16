# Contributing to the Agentic Workspace Protocol

AWP is a young draft specification (v0.2). Feedback from real use is the most valuable contribution right now.

## Proposing a spec change

1. Open an issue describing the problem you hit while using AWP, not just the change you want — the reasoning matters more than the wording.
2. If you have a concrete proposal, edit `templates/.agents/docs/design-document.md` in a pull request and explain what changed and why.
3. If the change affects the on-disk layout (new file, renamed section, changed convention), update the rest of `templates/` to match in the same pull request.

## Proposing a template change

Templates under `templates/` must stay consistent with `templates/.agents/docs/design-document.md`. If they diverge, the spec is the source of truth — fix the template, or propose a spec change first.

## Scope

This repository does not currently include tooling (linters, generators, CLIs) for AWP. Proposals for such tooling are welcome as issues for discussion before implementation.
