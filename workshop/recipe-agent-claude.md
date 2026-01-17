---
id: recipe-agent-claude
created: 2026-01-15
modified: 2026-01-15
status: active
type:
  - agent
---

```yaml
name: Claude
output_format: agent  # Simple concatenation, no template

target_locations:
  - path: ~/.claude/CLAUDE.md

sources:
  - slice: agent=claudi-claude-code 
    slice-file: agents/agent-roles.md
  - file: agents/steering-global-operator.md
  - file: agents/steering-global-principles.md
```