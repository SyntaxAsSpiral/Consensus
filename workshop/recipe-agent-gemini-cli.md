---
id: recipe-agent-gemini-cli
created: 2026-01-17
modified: 2026-01-17
status: active
type:
  - agent
---

```yaml
name: Gemini CLI
output_format: agent  # Simple concatenation, no template

target_locations:
  - path: ~/.gemini/AGENTS.md

sources:
  - slice: agent=gemini-cli
    slice-file: agents/agent-roles.md
  - file: agents/steering-global-operator.md
  - file: agents/steering-global-principles.md
```
