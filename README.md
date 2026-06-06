# Zed Config

My [Zed](https://zed.dev) editor configuration.

## Structure

```
~/.config/zed/
├── settings.json                # Editor settings
├── update-anthropic-models.py   # Sync proxy models into settings.json
├── snippets/                    # Custom snippets
└── themes/
    └── obsidian-prism.json
```

## Theme

**Obsidian Prism** - a dark theme built on a near-black `#080909` base with translucent backgrounds and VS Code–inspired syntax highlighting.

## Highlights

- **AI** - Claude Opus 4 (thinking) as the default agent model, with [Context7](https://context7.com) MCP tools auto-allowed
- **Appearance** - Bar cursor, comfortable project panel spacing, no horizontal scrollbar, Base Charmed Icons
- **Privacy** - Telemetry fully disabled

## Rules

Three agent rules in the prompt library:

- **Git Commit** - Modified built-in rule enforcing [Conventional Commits](https://www.conventionalcommits.org) format (`type(scope): Subject`), imperative mood, 50-char subject limit, and minimal body usage
- **Context7** - Caps `maxTokens` at 5000 when calling the `query-docs` MCP tool to avoid flooding the context window
- **Writing Style** - UK English spelling, no em dashes or emojis, minimal inline comments, and proper documentation standards per language (JSDoc, docstrings, etc.)

## Anthropic model sync

`update-anthropic-models.py` repopulates the Anthropic model picker when Claude is routed through the [CLIProxyAPI](https://github.com/router-for-me/CLIProxyAPI) proxy.

Since [zed#56397](https://github.com/zed-industries/zed/pull/56397) Zed discovers Anthropic models by fetching `GET {api_url}/v1/models` and expects each entry to carry `display_name`, `max_input_tokens` and `max_tokens`. The proxy returns an OpenAI-style list without those fields, so the parse fails and the dropdown is left empty (see [zed#56880](https://github.com/zed-industries/zed/issues/56880)). Only model discovery breaks; the inference path (`/v1/messages`) is unaffected.

The script reads the model ids from the proxy and writes a `language_models.anthropic.available_models` block into `settings.json`, supplying the context and output token limits from a `MODEL_DEFAULTS` table at the top of the file. Run it whenever the proxy exposes new models.

```sh
python3 update-anthropic-models.py            # apply
python3 update-anthropic-models.py --dry-run  # preview without writing
```

The proxy URL is read from the existing `api_url` in `settings.json` (override with `--base-url`; pass `--api-key` if the proxy needs auth). The generated block is fenced with marker comments, so re-runs replace it in place and leave the rest of the file untouched. A timestamped `settings.json.*.bak` backup is written before each change and is gitignored.

## Setup

```sh
git clone git@github.com:dcrdev/zed-config.git ~/.config/zed
```
