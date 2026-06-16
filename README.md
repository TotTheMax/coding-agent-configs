# Coding Agent Configs

Team-shared configuration repository for coding agents.

## Directory Structure

```
├── opencode/                  # opencode agent configuration
│   ├── opencode.json          # opencode main config (model, provider, mcp)
│   └── rules/                 # coding rules (flat structure for OPENCODE_CONFIG_DIR)
│       ├── code-style.md
│       ├── testing-conventions.md
│       └── git-conventions.md
├── skills/                    # shared skills (universal format, cross-agent)
│   ├── code-review/SKILL.md
│   └── api-design/SKILL.md
└── README.md                  # this file
```

## Contents

### MCP Servers

`opencode.json` includes MCP server configurations:

- **filesystem**: Read-only access to project files via `@modelcontextprotocol/server-filesystem`
- **fetch**: Web content fetching via `@modelcontextprotocol/server-fetch`

### Skills

Skills in `skills/` are in universal format with YAML frontmatter (`name`, `description`). They are installed to the config directory's `skills/` subdirectory, matching the `.opencode` format used by `OPENCODE_CONFIG_DIR`.

- **code-review**: Review code for quality, security, and best practices
- **api-design**: Design, plan, or review REST/GraphQL APIs

### Rules

Coding rules in `opencode/rules/` are installed to the config directory's `rules/` subdirectory:

- **code-style**: Follow existing conventions, include error handling, minimal changes
- **testing-conventions**: Descriptive test names, beforeEach/afterEach, mock external deps
- **git-conventions**: Conventional commits format, branch naming, PR practices

## How to Use

### Install Team Config (via Skill)

1. Install the skill:
   ```bash
   npx skills add <skill-gitlab-url>
   ```

2. Invoke the skill in opencode and provide your team's config repo URL.

### Install Team Config (via CLI directly)

```bash
npx @tothemax/agent-config-cli setup --repo https://github.com/tothemax/coding-agent-configs.git -a opencode
```

### Specify Shell Type

```bash
npx @tothemax/agent-config-cli setup --repo https://github.com/tothemax/coding-agent-configs.git -a opencode --shell zsh
npx @tothemax/agent-config-cli setup --repo https://github.com/tothemax/coding-agent-configs.git -a opencode --shell fish
```

If `--shell` is not specified, the CLI detects the running shell automatically. When detection is ambiguous, it writes env vars to both `.bashrc` and `.zshrc`.

### Custom Config Directory

```bash
npx @tothemax/agent-config-cli setup --repo https://github.com/tothemax/coding-agent-configs.git -a opencode --config-dir ~/custom-dir
```

### Update Team Config

```bash
npx @tothemax/agent-config-cli update --repo https://github.com/tothemax/coding-agent-configs.git -a opencode
```

### Uninstall

Remove the `OPENCODE_CONFIG_DIR` marker block from your shell profile (marked with `# >>> agent-config-cli:opencode >>>` comments). Both `.bashrc` and `.zshrc` may contain the env var if detection was ambiguous. Then delete the config directory.

## Adding a New Agent

1. Create a `<agent-name>/` directory in this repo following the agent's config structure
2. Implement an `Agent` class in `agent-config-cli` (see `packages/agent-config-cli/src/agents/`)
3. Register it in the CLI's agent registry

## Notes

- Each agent's config is maintained in its own directory
- Skills are in `skills/` at repo root (universal format, shared across agents)
- The installed config directory follows `.opencode` format: `rules/` and `skills/` at top level
- The config repo URL is provided by the user at setup time
- opencode uses `OPENCODE_CONFIG_DIR` env var to avoid overwriting personal config
