# Context Vault Template

A template for building AI agent context systems using Obsidian and a recipe-based assembly workflow.

> **Reference Implementation**: See [zk-context-vault](https://github.com/SyntaxAsSpiral/zk-context-vault) for a working example with real content.

## Quick Start

### 1. Clone and Open

```bash
git clone <your-repo-url>
cd context-vault-template
```

Open the folder in Obsidian:
- Launch Obsidian
- Click "Open folder as vault"
- Select the `context-vault-template` directory

### 2. What's Inside

```
agents/          # Agent configurations and steering rules
skills/          # Reusable agent skills (Agent Skills standard)
prompts/         # Prompt templates for different cognitive modes
artifacts/       # Visual models (Obsidian Canvas files)
workshop/        # Assembly system for deploying context
  src/           # Python scripts (assemble.py, sync.py)
  templates/     # Recipe templates
  recipe-*.md    # Active recipes
```

### 3. How It Works

**Write once, deploy everywhere:**

1. **Create content** in `agents/`, `skills/`, `prompts/`
2. **Write recipes** in `workshop/` to define what goes where
3. **Run assembly** to generate outputs in `workshop/staging/`
4. **Run sync** to deploy to target locations (like `~/.kiro/`, `~/.claude/`)

### 4. Basic Workflow

```bash
# Assemble recipes into staging
python workshop/src/assemble.py

# Deploy staging to targets
python workshop/src/sync.py
```

## Key Concepts

### Recipes

Recipes are Obsidian notes with embedded YAML that define:
- What content to assemble
- Where to deploy it
- What format to use (agent, skill, power, command)

Example recipe:
```yaml
name: my-agent
output_format: agent
target_locations:
  - path: ~/.claude/CLAUDE.md
sources:
  - file: agents/my-config.md
```

### Skills

Skills follow the [Agent Skills standard](https://agentskills.io):
- Flat directory structure
- `SKILL.md` with YAML frontmatter
- Optional `scripts/`, `references/`, `assets/` folders

### Powers

Kiro Powers package skills with steering files:
- `POWER.md` - Main documentation
- `steering/` - Additional guides
- `mcp.json` - Optional MCP server config

## Customization

1. **Replace example content** with your own
2. **Update paths** in `workshop/src/assemble.py` and `sync.py`
3. **Create recipes** for your deployment targets
4. **Run the workflow** to deploy

## Requirements

- Python 3.8+
- Obsidian (optional, but recommended)
- Git

## Learn More

- Check `workshop/templates/` for recipe examples
- See `skills/spec-agent-skill.md` for skill format
- See `skills/spec-kiro-power.md` for power format
