# Coding Agent Configs

Team-shared configuration repository for coding agents.

## Directory Structure

```
├── opencode/                  # opencode agent configuration
│   ├── opencode.json          # opencode main config file
│   ├── .opencode/             # opencode specific directory
│   │   └── rules/             # coding rules for opencode
│   │       └── code-style.md
├── trae/                      # future: trae cli configuration
│   └── ...
└── README.md                  # this file
```

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

### Update Team Config

```bash
npx @tothemax/agent-config-cli update --repo https://github.com/tothemax/coding-agent-configs.git -a opencode
```

### Custom Config Directory

```bash
npx @tothemax/agent-config-cli setup --repo https://github.com/tothemax/coding-agent-configs.git -a opencode --config-dir ~/custom-dir
```

### Uninstall

Remove the `OPENCODE_CONFIG_DIR` line from your shell profile (marked with `agent-config-cli` comments), then delete the config directory.

## Adding a New Agent

1. Create a `<agent-name>/` directory in this repo following the agent's config structure
2. Implement an `Agent` class in `agent-config-cli` (see `packages/agent-config-cli/src/agents/`)
3. Register it in the CLI's agent registry

## Notes

- Each agent's config is maintained in its own directory
- The config repo URL is provided by the user at setup time
- opencode uses `OPENCODE_CONFIG_DIR` env var to avoid overwriting personal config