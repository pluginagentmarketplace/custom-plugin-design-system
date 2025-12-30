---
name: plugin-architecture
description: Master plugin folder structure, manifest design, and architectural patterns. Learn to organize plugins for scalability and maintainability.
sasmp_version: "1.3.0"
bonded_agent: 01-plugin-architect
bond_type: PRIMARY_BOND

# Production-Grade Configuration
validation:
  required_sections:
    - quick_start
    - core_concepts
    - troubleshooting
  min_examples: 3
  max_lines: 350

retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# Plugin Architecture

## Quick Start

A well-structured plugin follows this layout:

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json              # Required manifest
├── agents/
│   └── 01-agent.md              # Agent definition
├── skills/
│   └── skill-name/SKILL.md      # Skill definition
├── commands/
│   └── command.md               # Command definition
├── hooks/
│   └── hooks.json               # Automation hooks
└── README.md
```

## Core Concepts

### Plugin Manifest (plugin.json)

```json
{
  "name": "my-plugin",
  "version": "1.0.0",
  "description": "What my plugin does (max 256 chars)",
  "author": "Your Name",
  "license": "MIT",
  "repository": "https://github.com/user/repo",
  "agents": [
    {
      "name": "agent-id",
      "description": "What it does",
      "file": "agents/01-agent.md"
    }
  ],
  "commands": [
    {
      "name": "command",
      "file": "commands/command.md",
      "description": "What it does"
    }
  ],
  "skills": [
    {
      "name": "skill-id",
      "file": "skills/skill-id/SKILL.md"
    }
  ],
  "hooks": {
    "file": "hooks/hooks.json"
  }
}
```

### Manifest Validation Rules

| Field | Rule | Example |
|-------|------|---------|
| name | lowercase-hyphens, 10-50 chars | `my-plugin` |
| version | semantic (MAJOR.MINOR.PATCH) | `1.0.0` |
| description | 50-256 characters | `Plugin for X` |
| agents | array of agent definitions | `[{...}]` |
| skills | array of skill definitions | `[{...}]` |

### Agent Structure (Production-Grade)

```yaml
---
name: agent-id
description: What this agent does (max 1024 chars)
model: sonnet
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    # Define inputs

output_schema:
  type: object
  properties:
    # Define outputs

error_handling:
  strategy: graceful_degradation
  max_retries: 3
---
```

### Skill Structure

```
skills/
├── skill-one/
│   ├── SKILL.md              # Always named SKILL.md
│   └── resources/            # Optional: additional files
└── skill-two/
    └── SKILL.md
```

### Architectural Patterns

**Single Responsibility:**
```
Agent 1: Domain A only
Agent 2: Domain B only
Agent 3: Domain C only
```

**Layered Architecture:**
```
Commands (User interface)
    ↓
Agents (Logic & guidance)
    ↓
Skills (Knowledge & examples)
    ↓
Hooks (Automation)
```

**Orchestrator Pattern:**
```
Orchestrator Agent
├── Subagent A (Specialized)
├── Subagent B (Specialized)
└── Subagent C (Specialized)
```

## Advanced Topics

### Scaling Your Plugin

| Stage | Agents | Skills | Commands | Description |
|-------|--------|--------|----------|-------------|
| MVP | 1 | 2 | 1 | Minimal viable |
| Standard | 3 | 5 | 3 | Feature-rich |
| Enterprise | 5-7 | 10+ | 5+ | Full-featured |

### File Naming Conventions

| Component | Pattern | Example |
|-----------|---------|---------|
| Agents | `00-name.md` | `01-architect.md` |
| Skills | `skill-name/SKILL.md` | `plugin-dev/SKILL.md` |
| Commands | `verb-noun.md` | `create-plugin.md` |
| Hooks | `hooks.json` | `hooks.json` |

## Real-World Projects

### Project 1: Simple Plugin
```
simple-plugin/
├── .claude-plugin/plugin.json
├── agents/01-main.md
├── skills/core/SKILL.md
├── commands/run.md
└── README.md
```

### Project 2: Enterprise Plugin
```
enterprise-plugin/
├── .claude-plugin/plugin.json
├── agents/
│   ├── 01-orchestrator.md
│   ├── 02-analyzer.md
│   └── 03-reporter.md
├── skills/
│   ├── analysis/SKILL.md
│   └── reporting/SKILL.md
├── commands/
│   ├── analyze.md
│   └── report.md
├── hooks/hooks.json
├── docs/
│   └── ARCHITECTURE.md
├── README.md
└── CHANGELOG.md
```

---

## 🔧 TROUBLESHOOTING

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Agent not found | Missing manifest entry | Add to `agents` array in plugin.json |
| Skill won't load | Invalid YAML | Validate YAML syntax, check indentation |
| Command fails | Missing file | Ensure file exists at path specified |
| Plugin rejected | Invalid manifest | Validate JSON syntax |
| Circular dependency | Agents reference each other | Use orchestrator pattern |

### Debug Checklist

```markdown
□ Validate plugin.json syntax
  → npx jsonlint .claude-plugin/plugin.json

□ Check file references
  → All agents[].file paths exist?
  → All skills[].file paths exist?

□ Validate YAML frontmatter
  → Each file has valid --- block?

□ Check naming conventions
  → Lowercase-hyphens only?
  → No spaces or underscores?
```

### Recovery Procedures

**Invalid Manifest:**
```bash
# Validate JSON
npx jsonlint .claude-plugin/plugin.json

# Common fixes:
# - Add missing commas
# - Fix quote mismatches
# - Check array brackets
```

**Missing File Reference:**
```bash
# List referenced files
grep -r "file\":" .claude-plugin/plugin.json

# Create missing file or remove reference
```

---

**Use this skill when:**
- Designing plugin structure
- Creating plugin.json
- Organizing agents and skills
- Planning plugin growth
- Troubleshooting structure issues
