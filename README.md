# scala-lsp

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/claude-plugin-orange.svg)](https://docs.anthropic.com/en/docs/claude-code/plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-zircote--lsp-purple.svg)](https://github.com/zircote/lsp-marketplace)
[![Scala](https://img.shields.io/badge/Scala-DC322F?logo=scala&logoColor=white)](https://www.scala-lang.org/)

A Claude Code plugin providing comprehensive Scala development support through:

- **Metals** LSP integration for IDE-like features
- **Automated hooks** for formatting, linting, and building
- **Scala ecosystem** integration (Scalafmt, Scalafix, SBT)

## Quick Setup

```bash
# Run the setup command (after installing the plugin)
/setup
```

Or manually:

```bash
# Install Metals via Coursier
cs install metals

# Install development tools
cs install scalafmt scalafix
```

## Features

### LSP Integration

The plugin configures Metals for Claude Code via `.lsp.json`:

```json
{
    "scala": {
        "command": "metals",
        "args": [],
        "extensionToLanguage": {
            ".scala": "scala",
            ".sc": "scala",
            ".sbt": "sbt"
        },
        "transport": "stdio"
    }
}
```

**Capabilities:**
- Go to definition / references
- Hover documentation
- Code completion
- Refactoring support
- Real-time diagnostics

### Automated Hooks

| Hook | Trigger | Description |
|------|---------|-------------|
| `scalafmt` | `**/*.scala` | Code formatting |
| `scalafix` | `**/*.scala` | Linting and refactoring |
| `scala-todo-fixme` | `**/*.scala` | Surface TODO/FIXME comments |

## Required Tools

| Tool | Installation | Purpose |
|------|--------------|---------|
| `metals` | `cs install metals` | LSP server |
| `scalafmt` | `cs install scalafmt` | Formatting |
| `scalafix` | `cs install scalafix` | Linting |

## Project Structure

```
scala-lsp/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── .lsp.json                  # Metals configuration
├── commands/
│   └── setup.md              # /setup command
├── hooks/
│   └── scripts/
│       └── scala-hooks.sh
├── tests/
│   └── SampleTest.scala      # Test file
├── CLAUDE.md                  # Project instructions
└── README.md                  # This file
```

## License

MIT
