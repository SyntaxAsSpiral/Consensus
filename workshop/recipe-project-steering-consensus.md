---
id: recipe-project-steering-consensus
created: 2026-01-16
modified: 2026-01-16
status: active
type:
  - agent
  - project
---

```yaml
name: Consensus
output_format: agent

# Project-scoped steering → repo-root AGENTS.md.
# In real projects, use: path: .
target_locations:
  - path: .  # Current repo root (relative path)

sources:
  - file: agents/steering-project-consensus.md
```
