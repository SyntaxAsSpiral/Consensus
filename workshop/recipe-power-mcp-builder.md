---
id: recipe-power-mcp-builder
created: 2026-01-16
modified: 2026-01-16
status: active
type:
  - "power"
---

```yaml
name: mcp-builder
output_format: power  # Creates power folder structure

# Power folder structure:
# mcp-builder/
# ├── POWER.md (from power_md source)
# ├── mcp.json (from mcp_config source)
# └── steering/ (all steering_files go here as .md)

target_locations:
  - path: ~/.kiro/powers/installed/mcp-builder/

# Source mapping to power structure
sources:
  power_md:
    - file: skills/mcp-builder/POWER.md
  
  mcp_config:
    - file: skills/mcp-builder/mcp.json
      output_name: mcp.json
  
  steering_files:  # All go to steering/ folder as .md
    - file: skills/mcp-builder/python_mcp_server.md
      output_name: python_mcp_server.md
    - file: skills/mcp-builder/node_mcp_server.md
      output_name: node_mcp_server.md
    - file: skills/mcp-builder/mcp_best_practices.md
      output_name: mcp_best_practices.md
    - file: skills/mcp-builder/evaluation.md
      output_name: evaluation.md
    - file: skills/mcp-builder/evaluation.py.md
      output_name: evaluation.py.md
    - file: skills/mcp-builder/connections.py.md
      output_name: connections.py.md
    - file: skills/mcp-builder/example-evaluation.xml.md
      output_name: example-evaluation.xml.md
```
