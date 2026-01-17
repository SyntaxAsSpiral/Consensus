# Workshop Quickstart

Recipe-based context assembly system. Create recipes → assemble → sync.

## Three Steps

### 1. Create Recipe from Template

Use Obsidian templates or copy from `templates/`:

```bash
# Agent system prompt
templates/recipe-agent-{{name}}.md

# Agent Skills standard (SKILL.md + folders)
templates/recipe-skill-{{name}}.md

# Kiro Power (POWER.md + steering/)
templates/recipe-power-{{name}}.md

# Commands/prompts/hooks
templates/recipe-command-{{name}}.md

# Project steering (AGENTS.md in repo root)
templates/recipe-project-steering-{{name}}.md
```

### 2. Assemble to Staging

```bash
python workshop/src/assemble.py          # Generate artifacts
python workshop/src/assemble.py --dry-run --verbose  # Preview
```

Outputs to `workshop/staging/` with structure:
- `agent/<name>/*.md` - Simple markdown files
- `skill/<name>/` - SKILL.md + scripts/ + references/ + assets/
- `power/<name>/` - POWER.md + steering/ + optional mcp.json
- `command/<name>/` - *.md + optional *.kiro.hook

### 3. Sync to Targets

```bash
python workshop/src/sync.py              # Deploy to targets
python workshop/src/sync.py --dry-run --verbose  # Preview
```

Copies staging → target locations, cleans orphans, auto-commits + pushes.

## Recipe Anatomy

```yaml
name: example
output_format: agent  # or skill, power, command

target_locations:
  - path: ~/.claude/CLAUDE.md
  - path: ~/.kiro/modular/

sources:
  # Whole file
  - file: agents/example.md
  
  # Slice extraction
  - slice: id=example
    slice-file: agents/multi.md
```

## Source Types

- `file: path/to/file.md` - Include entire file
- `slice: id=name` + `slice-file: path` - Extract `<!-- slice:id=name -->` content
- `inline: "text"` - Embed literal text

## Output Formats

- **agent** - Simple markdown concatenation
- **skill** - Agent Skills standard (SKILL.md + folders)
- **power** - Kiro Power (POWER.md + steering/)
- **command** - Platform commands/prompts/hooks

## Path Conventions

- `~/` expands to home directory
- Trailing `/` or `\` = directory target (auto-filename)
- Claude targets → `CLAUDE.md`, others → `AGENTS.md`
- Kiro hooks → `.kiro.hook` JSON wrapper

## Multi-Section Recipes

Separate YAML documents with `---` inside the YAML block:

```yaml
name: shared-name
output_format: agent
---
target_locations:
  - path: ~/.claude/
sources:
  - file: agents/section1.md
---
target_locations:
  - path: ~/.kiro/
sources:
  - file: agents/section2.md
```

## Tracking

- `recipe-manifest.md` - Assembly/sync logs
- Staging artifacts - Inspect before sync
- Auto-commit/push - After successful sync

## Common Patterns

**Agent prompt for multiple platforms:**
```yaml
name: MyAgent
output_format: agent
target_locations:
  - path: ~/.claude/
  - path: ~/.kiro/modular/
sources:
  - file: agents/my-agent.md
```

**Skill with power variant:**
```yaml
name: my-skill
output_format: skill
also_output_as_power: true
target_locations:
  - path: ~/.claude/skills/my-skill/
  - path: ~/.kiro/powers/installed/my-skill/
sources:
  skill_md:
    frontmatter:
      name: my-skill
      description: What it does
    body:
      - file: skills/my-skill/SKILL.md
```

**Project steering (repo root):**
```yaml
name: MyProject
output_format: agent
target_locations:
  - path: .  # Current repo root (only supported relative path)
sources:
  - file: agents/steering-project-myproject.md
```

---

*For full details see [README.md](README.md)*
