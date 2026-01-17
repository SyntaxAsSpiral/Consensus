---
id: recipe-agent-antigravity
created: 2026-01-17
modified: 2026-01-17
status: active
type:
  - agent
---

```yaml
name: Antigravity
output_format: agent  # Simple concatenation, no template

target_locations:
  - path: ~/.antigravity/AGENTS.md

sources:
  - slice: agent=antigravity
    slice-file: agents/agent-roles.md
  - file: agents/steering-global-operator.md
  - file: agents/steering-global-principles.md
```
