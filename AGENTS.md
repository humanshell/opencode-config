# AGENTS.md

## What this directory is

This is the **OpenCode user configuration directory** (`~/.config/opencode`), not a software project.
There is no source code, no git repo, and no build/test/lint commands. Do not look for them or invent them.

## Files

- `opencode.jsonc` — main OpenCode config: primary model (`opencode/big-pickle`), title-agent model,
  a local Ollama provider, commented-out plugins, and MCP servers (`context7`, `searchcode`).
  This file is **JSONC**: `//` comments are intentional — preserve them when editing.
- `cli.json` — TUI/UI preferences only (theme, diff wrapping, session sidebar, animations).
  Plain JSON (no comments).
- `service.json` — contains the local OpenCode service password; excluded from git via `.gitignore`.
  **Sensitive: never print its contents, include them in prompts/responses, or modify this file.**
- `.gitignore` — keeps `service.json` (and `.DS_Store`) out of version control.
- `README.md` — human-facing overview of this config; setup details live there.

## Editing conventions

- Match each file's existing style: `opencode.jsonc` is tab-indented; `cli.json` and `service.json`
  use 2-space indentation.
- Config is read by OpenCode at startup — after changing `opencode.jsonc` or `cli.json`, changes apply
  to new sessions, not the current one.
- Keep JSON valid: removing a `//` line that actually documents a value (e.g. a commented-out
  `disabled_providers`) changes behavior only if uncommented; do not enable commented-out options
  unless asked.

## Model / provider notes

- The primary model is `opencode/big-pickle` (OpenCode's built-in free model); the `agents.title`
  model is a lightweight free model. Don't "fix" these to OpenAI/Anthropic IDs.
- The `ollama` provider points at `http://localhost:11434/v1` and defines a single model
  (`gemma4:12b-mlx`); it only works if Ollama is running locally.

## MCP servers

- `context7` (remote): up-to-date library/framework docs — prefer it over web search for
  library questions.
- `searchcode` (remote): searches public git repos; requires a full repo URL (no global search).
