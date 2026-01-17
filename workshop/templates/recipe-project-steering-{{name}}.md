---
id: recipe-project-steering-{{name}}
created: {{date}}
modified: {{date}}
status: draft
type:
  - "agent"
  - "project"
---

```yaml
name: {{name}}
output_format: agent

# Project steering: repack a single vault file (or slice) into AGENTS.md for a repo.
#
# Target options:
# - Repo root (relative): path: .
#   - Auto-generates AGENTS.md in current repo root
# - Directory form (absolute): ends with `/` or `\` → auto-filename
#   - Claude targets become CLAUDE.md (only under ~/.claude)
#   - everything else becomes AGENTS.md
# - File form (absolute): point directly at .../AGENTS.md to force the name

target_locations:
  - path: .  # Current repo root (only supported relative path)

sources:
  # Whole-file inclusion (simplest)
  - file: agents/steering-project-{{name}}.md

  # Or slice extraction
  # - slice: project={{name}}
  #   slice-file: agents/steering-projects.md

# Optional wrapper template
# template: |
#   # Project Steering ({{name}})
#   {content}
```
