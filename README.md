# Cyberuni Marketplace

Plugin catalog for Claude Code. Install curated plugins with a single command.

## Usage

Add the marketplace:

```sh
claude plugin marketplace add cyberuni/marketplace
```

Then install any plugin:

```sh
claude plugin install <plugin-name>@cyberuni
```

## Plugins

### Research

| Plugin | Description |
|--------|-------------|
| `research-workbench` | Durable research workflows and community post authoring for AI coding agents. |

### Skills

| Plugin | Description |
|--------|-------------|
| `skill-discovery` | Find and evaluate skills before installing. Prefer global install (`-g`). |
| `skill-authoring` | Create, generalize, patch, persona, and audit skills. Prefer global install (`-g`). |

### Setup

| Plugin | Description |
|--------|-------------|
| `agent-initialization` | One-time repo setup. `init` and `init-commit-discipline`: global (`-g`); `commit`: project. |

### Productivity

| Plugin | Description |
|--------|-------------|
| `awesome-list-maintenance` | Manage curated awesome-list sources and entries. `configure-awesome-sources`: global; `update-awesome-list`: project. |

### Plugin Authoring

| Plugin | Description |
|--------|-------------|
| `universal-agent-plugin` | Scaffold a universal AI coding agent plugin targeting Claude Code, Cursor, Codex, and GitHub Copilot CLI from a single source. |

## Contributing

To add or update a plugin, edit `.claude-plugin/marketplace.json` and follow the schema documented in [`AGENTS.md`](AGENTS.md).
