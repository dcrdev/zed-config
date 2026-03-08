# Zed Config

My [Zed](https://zed.dev) editor configuration.

## Structure

```
~/.config/zed/
├── settings.json     # Editor settings
├── snippets/         # Custom snippets
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

## Setup

```sh
git clone git@github.com:dcrdev/zed-config.git ~/.config/zed
```
