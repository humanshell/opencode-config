# OpenCode configuration

Personal [OpenCode](https://opencode.ai) user configuration (`~/.config/opencode`). Not a software
project — editing these files changes the behavior of the OpenCode CLI/TUI and its agents.
Version-controlled here and pushed to <https://github.com/humanshell/opencode-config> (branch `main`).

## Files

| File | Purpose |
| --- | --- |
| `opencode.jsonc` | Main config: models, providers, plugins, MCP servers (JSONC — comments allowed) |
| `cli.json` | TUI preferences: theme, diff wrapping, session sidebar, animations |
| `service.json` | Local service password — **secret**, ignored by git, never commit |
| `AGENTS.md` | Instructions for AI agents working in this directory |
| `.gitignore` | Keeps `service.json` and `.DS_Store` out of version control |

## Current setup

- **Model:** `opencode/big-pickle` (OpenCode's built-in free model); titles use the lightweight
  `opencode/deepseek-v4.1-flash-free`.
- **Provider:** local [Ollama](https://ollama.com) at `http://localhost:11434/v1` exposing
  `gemma4:12b-mlx`. Only usable while Ollama is running locally.
- **MCP servers:**
  - [context7](https://context7.com) — up-to-date library docs for agents
  - [searchcode](https://searchcode.com) — public git repository search
- **Plugins:** none active; `context-mode` and `@dietrichgebert/ponytail` are listed in
  `opencode.jsonc` as commented-out options.

## Making changes

- Config is read at startup — restart the OpenCode session/CLI to pick up changes.
- `opencode.jsonc` is tab-indented; `cli.json` uses 2 spaces. Match the surrounding style.
- Keep secrets out of `opencode.jsonc`; use `{env:VAR}` or `{file:path}` placeholders instead.
- See <https://opencode.ai/v2/docs/config> for the full config schema and precedence rules
  (global < project < `.opencode/` < system).
