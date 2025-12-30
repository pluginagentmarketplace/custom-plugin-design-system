---
name: create-plugin
description: Create a new Claude Code plugin with guided setup, generating all files and configuration
sasmp_version: "1.3.0"
allowed-tools: Read

# Exit Codes
exit_codes:
  0: success
  1: invalid_input
  2: file_exists
  3: permission_denied
  4: template_error
  5: validation_failed

# Input Validation
validation:
  name:
    pattern: "^[a-z][a-z0-9-]{2,49}$"
    min_length: 3
    max_length: 50
  agents:
    type: integer
    min: 1
    max: 7
  skills:
    type: integer
    min: 1
    max: 10
  commands:
    type: integer
    min: 1
    max: 5

# Retry Configuration
retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# /create-plugin - Create New Plugin

## What This Does

Creates a new Claude Code plugin from scratch with guided setup. Generates all necessary files, folder structure, and configuration.

## Usage

```
/create-plugin
/create-plugin my-plugin
/create-plugin my-plugin --type agent
/create-plugin my-plugin --agents 3 --skills 5
```

## Options

| Option | Type | Description |
|--------|------|-------------|
| `--type` | agent\|command\|skill | Plugin focus type |
| `--agents` | number | Number of agents (1-7) |
| `--skills` | number | Number of skills (1-10) |
| `--commands` | number | Number of commands (1-5) |
| `--template` | name | Use template (minimal, standard, full) |
| `--include-tests` | boolean | Include test files |
| `--include-docs` | boolean | Include documentation |

## Example

```
$ /create-plugin my-awesome-plugin

┌─────────────────────────────────────┐
│  PLUGIN CREATION WIZARD             │
├─────────────────────────────────────┤

1. Plugin Name: my-awesome-plugin ✅

2. Plugin Type?
   [1] Agent-based
   [2] Command-based
   [3] Skill library
   > 1

3. Number of Agents?
   (recommended: 1-5)
   > 3

4. Number of Skills?
   (recommended: 1-5)
   > 5

5. Include tests?
   > yes

Creating plugin...
  ✅ Folders created
  ✅ Files generated
  ✅ Manifest created
  ✅ Validation passed

✅ Plugin created successfully!

Location: ./my-awesome-plugin/
Files: 18
Lines of code: 2,500+

📍 Next Steps:
1. /design-plugin my-awesome-plugin
2. /test-plugin my-awesome-plugin
3. /optimize-plugin my-awesome-plugin
```

## Generated Structure

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json
├── agents/
│   ├── 01-primary.md
│   ├── 02-secondary.md
│   └── 03-tertiary.md
├── skills/
│   ├── skill-one/SKILL.md
│   ├── skill-two/SKILL.md
│   └── skill-three/SKILL.md
├── commands/
│   ├── create.md
│   ├── design.md
│   └── test.md
├── hooks/
│   └── hooks.json
├── README.md
├── CHANGELOG.md
└── LICENSE
```

## Templates

### Minimal
```
1 agent, 1 skill, 1 command
Fastest setup, extend from there
```

### Standard (Default)
```
3 agents, 5 skills, 3 commands
Good starting point
```

### Full
```
5 agents, 10 skills, 5 commands
Complete plugin framework
```

## Tips

- Use clear, descriptive plugin name (my-awesome-plugin)
- Choose agent-based for complex systems
- Start with standard template, customize later
- Include tests from the beginning
- Document as you build

## Related Commands

- `/design-plugin my-plugin` - Design architecture
- `/test-plugin my-plugin` - Validate plugin
- `/optimize-plugin my-plugin` - Optimize and deploy

---

## 🔧 TROUBLESHOOTING

### Error Messages

| Error | Code | Cause | Solution |
|-------|------|-------|----------|
| `Invalid plugin name` | 1 | Name doesn't match pattern | Use lowercase letters, numbers, hyphens only (3-50 chars) |
| `Plugin already exists` | 2 | Directory exists | Choose different name or delete existing |
| `Permission denied` | 3 | No write access | Check directory permissions |
| `Template not found` | 4 | Invalid template name | Use: minimal, standard, or full |
| `Validation failed` | 5 | Generated files invalid | Check disk space, retry |

### Debug Checklist

```markdown
□ Step 1: Verify name format
  → Starts with letter?
  → Only lowercase, numbers, hyphens?
  → 3-50 characters?

□ Step 2: Check directory
  → Parent directory exists?
  → Write permissions?
  → Enough disk space?

□ Step 3: Validate options
  → --agents between 1-7?
  → --skills between 1-10?
  → --template valid?

□ Step 4: Retry with verbose
  → Run with --verbose flag
  → Check error details
```

### Common Issues

| Issue | Fix |
|-------|-----|
| Name rejected | Use `my-plugin` format, not `My Plugin` |
| Too many agents | Reduce to max 7 |
| Template fails | Try `--template standard` |
| Slow creation | Check disk I/O, network |

### Exit Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| 0 | Success | Proceed to /design-plugin |
| 1 | Invalid input | Check name/options format |
| 2 | File exists | Remove or rename existing |
| 3 | Permission denied | Check write access |
| 4 | Template error | Verify template name |
| 5 | Validation failed | Retry, check logs |

---

**Status**: 🟢 Ready | **Updated**: 2025
