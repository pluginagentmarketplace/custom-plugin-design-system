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

**Status**: 🟢 Ready | **Updated**: 2025
