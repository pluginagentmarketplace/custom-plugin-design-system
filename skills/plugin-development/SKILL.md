---
name: plugin-development
description: Master writing plugins including agent implementation, skill creation, command development, and hook scripting. Learn best practices for plugin coding.
sasmp_version: "1.3.0"
bonded_agent: 02-plugin-developer
bond_type: PRIMARY_BOND

# Production-Grade Configuration
validation:
  required_sections:
    - quick_start
    - core_concepts
    - troubleshooting
  min_examples: 5

retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# Plugin Development

## Quick Start

Create a production-grade agent:

```yaml
---
name: my-agent
description: Expert in X domain (max 1024 chars)
model: sonnet
sasmp_version: "1.3.0"

input_schema:
  type: object
  required: [task]
  properties:
    task: { type: string }

output_schema:
  type: object
  properties:
    result: { type: string }

error_handling:
  strategy: graceful_degradation
  max_retries: 3
  retry_delay_ms: [500, 1000, 2000]
---

# Agent Name

## Overview
Expert specializing in X domain.

## Expert Areas
### Area 1
[Content]

## Troubleshooting
| Issue | Solution |
|-------|----------|
| Error X | Fix Y |

## Integration
Works with: agent-2, skill-common
```

## Core Concepts

### Agent Implementation

**YAML Frontmatter (Production):**
```yaml
---
name: agent-id
description: "What + When (max 1024 chars)"
model: sonnet
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string }

output_schema:
  type: object
  properties:
    result: { type: string }

error_handling:
  strategy: graceful_degradation
  max_retries: 3
---
```

**Content Structure:**
```markdown
# Agent Name

## Overview
[1-2 sentences]

## Expert Areas
### Area 1
[Detailed content]

## When to Use
- Task 1
- Task 2

## Troubleshooting
[Issue table]

## Integration
Works with: [agents], [skills]
```

### Skill Implementation

**SKILL.md Template:**
```yaml
---
name: skill-id
description: "What it teaches (max 1024 chars)"
sasmp_version: "1.3.0"
bonded_agent: agent-id
bond_type: PRIMARY_BOND
---

# Skill Name

## Quick Start
[Working code]

## Core Concepts
[3+ sections]

## Troubleshooting
[Issue table]

## Real-World Projects
[2+ examples]
```

### Command Implementation

**Command Template:**
```yaml
---
name: command-name
description: Brief description
exit_codes:
  0: success
  1: invalid_input
  2: execution_error
---

# /command-name - Description

## What This Does
[Explanation]

## Usage
/command-name [options]

## Options
| Option | Type | Default | Description |
|--------|------|---------|-------------|
| --opt | string | null | What it does |

## Error Messages
| Error | Solution |
|-------|----------|
| ERR001 | Check X |

## Next Steps
[Suggestions]
```

### Hook Implementation

```json
{
  "version": "1.0.0",
  "hooks": [
    {
      "id": "hook-id",
      "name": "Hook Name",
      "event": "command-executed",
      "condition": "command == 'create'",
      "action": "log_usage",
      "enabled": true,
      "retry": {
        "max_attempts": 3,
        "backoff_ms": [500, 1000, 2000]
      },
      "timeout_ms": 5000
    }
  ]
}
```

### Hook Event Types

| Event | Trigger | Use Case |
|-------|---------|----------|
| `command-executed` | Command runs | Logging |
| `agent-invoked` | Agent used | Analytics |
| `skill-loaded` | Skill accessed | Progress |
| `error-occurred` | Any error | Alerting |

## Advanced Topics

### Code Quality Checklists

**Agent Quality:**
```
✅ input_schema defined
✅ output_schema defined
✅ error_handling configured
✅ Troubleshooting section
✅ 250-400 lines total
```

**Skill Quality:**
```
✅ bonded_agent defined
✅ Quick Start with code
✅ Troubleshooting table
✅ 200-300 lines total
```

**Command Quality:**
```
✅ exit_codes defined
✅ Options table
✅ Error messages
✅ 100-150 lines total
```

### Implementation Patterns

**Error Recovery Pattern:**
```
Try action
  ↓ (fails)
Retry [500ms, 1s, 2s]
  ↓ (still fails)
Fallback to alternative
  ↓ (still fails)
Graceful degradation + notify
```

## Real-World Projects

### Project 1: Simple Agent
```yaml
---
name: helper
description: General helper agent
model: sonnet
sasmp_version: "1.3.0"

error_handling:
  strategy: graceful_degradation
  max_retries: 2
---

# Helper Agent

## Overview
Assists with common tasks.

## Expert Areas
### Task Automation
[Content]

## Troubleshooting
| Issue | Solution |
|-------|----------|
| Slow response | Reduce content |
```

### Project 2: Complete Skill
```yaml
---
name: guide
description: Step-by-step guide skill
sasmp_version: "1.3.0"
bonded_agent: helper
bond_type: PRIMARY_BOND
---

# Guide Skill

## Quick Start
[Working example]

## Troubleshooting
| Issue | Solution |
|-------|----------|
| Load error | Check YAML |
```

---

## 🔧 TROUBLESHOOTING

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| YAML parse error | Bad indentation | Use 2-space indent, no tabs |
| Agent won't load | Missing field | Add name, description |
| Skill not bonded | Missing bonded_agent | Add to frontmatter |
| Hook not firing | Wrong event | Check event type |
| Command timeout | Too much content | Trim to size limits |

### Debug Checklist

```markdown
□ Validate YAML syntax
  → npx yaml-lint file.md

□ Check required fields
  → name, description present?

□ Verify error handling
  → strategy defined?
  → max_retries set?

□ Test integrations
  → bonded_agent exists?
```

### Log Interpretation

| Level | Example | Action |
|-------|---------|--------|
| INFO | Agent loaded | None |
| WARN | Retry 2/3 | Monitor |
| ERROR | Parse failed | Fix immediately |
| FATAL | Circuit open | Investigate |

### Exit Codes

| Code | Meaning | Action |
|------|---------|--------|
| 0 | Success | Continue |
| 1 | Invalid input | Check schema |
| 2 | File error | Check paths |
| 3 | YAML error | Fix syntax |
| 4 | Schema error | Match types |

---

**Use this skill when:**
- Writing agent content
- Creating new skills
- Implementing commands
- Setting up hooks
- Debugging implementation
