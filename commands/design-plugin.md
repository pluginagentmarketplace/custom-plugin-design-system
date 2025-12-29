---
name: design-plugin
description: plugin - Design Plugin Architecture
allowed-tools: Read
---

# /design-plugin - Design Plugin Architecture

## What This Does

Designs and optimizes your plugin architecture. Analyzes structure, agents, skills, and commands. Provides recommendations for best practices and improvements.

## Usage

```
/design-plugin my-plugin
/design-plugin my-plugin --review
/design-plugin my-plugin --restructure
/design-plugin my-plugin --report
```

## Options

| Option | Description |
|--------|-------------|
| `--review` | Review current design |
| `--restructure` | Suggest restructuring |
| `--report` | Generate design report |
| `--architecture` | Show architecture diagram |
| `--integrations` | Analyze agent integrations |

## Example

```
$ /design-plugin my-awesome-plugin --review

PLUGIN DESIGN REVIEW
═══════════════════════════════════════

Plugin: my-awesome-plugin
Status: Initial Structure ⏳

ARCHITECTURE ANALYSIS
├─ Agents: 3 ✅
│  ├─ Agent 1: Primary domain ✅
│  ├─ Agent 2: Secondary domain ✅
│  └─ Agent 3: Supporting role ✅
├─ Skills: 5 ✅
│  └─ All referenced ✅
├─ Commands: 3 ✅
│  └─ Properly documented ✅
└─ Hooks: 2 ✅

RECOMMENDATIONS
⚠️  Document agent integrations
⚠️  Add more concrete examples
⚠️  Enhance command help text

DESIGN SCORE: 78/100
Next step: Implement recommendations

📍 Next: /test-plugin my-awesome-plugin
```

## Design Review Criteria

```
Structure:
  ✅ Logical folder organization
  ✅ Clear file naming
  ✅ Proper manifest

Agents:
  ✅ Single responsibility
  ✅ Clear integrations
  ✅ Complete documentation

Skills:
  ✅ Reusable knowledge
  ✅ Working examples
  ✅ Clear descriptions

Commands:
  ✅ Intuitive workflow
  ✅ Clear options
  ✅ Helpful output

Hooks:
  ✅ Automation configured
  ✅ Events well-defined
  ✅ Actions clear
```

## Architecture Visualization

```
$ /design-plugin my-plugin --architecture

YOUR PLUGIN ARCHITECTURE
═══════════════════════════════════════

    Commands
    ├─ /create
    ├─ /design
    └─ /test
       ↓
    Agents
    ├─ architect (primary)
    ├─ developer (secondary)
    └─ designer (support)
       ↓
    Skills
    ├─ architecture
    ├─ development
    ├─ design
    ├─ testing
    └─ optimization
       ↓
    Hooks
    ├─ structure validation
    └─ quality checking
```

## Integration Analysis

```
$ /design-plugin my-plugin --integrations

AGENT INTEGRATIONS
═══════════════════

Architect Agent
  ├─ Works with: Developer, Designer
  ├─ Skills: architecture, design-patterns
  └─ Commands: /design-plugin

Developer Agent
  ├─ Works with: Architect, Tester
  ├─ Skills: development, optimization
  └─ Commands: /create-plugin

Designer Agent
  ├─ Works with: Architect, Tester
  ├─ Skills: design, testing
  └─ Commands: /design-plugin

Integration Score: 92/100 ✅
```

## Design Report

```
$ /design-plugin my-plugin --report

COMPREHENSIVE DESIGN REPORT
═══════════════════════════════════════
Plugin: my-awesome-plugin
Date: 2025-01-18

STRUCTURE ANALYSIS
  Score: 90/100
  ✅ Well organized
  ✅ Clear naming
  ✅ Proper documentation

AGENT ANALYSIS
  Score: 85/100
  ✅ Good separation
  ⚠️  Could improve integrations

SKILL ANALYSIS
  Score: 88/100
  ✅ Comprehensive
  ✅ Well documented

COMMAND ANALYSIS
  Score: 92/100
  ✅ Intuitive
  ✅ Clear workflow

OVERALL SCORE: 89/100
Recommendation: Good design, implement suggestions

Areas to Improve:
1. Agent collaboration documentation
2. Additional real-world examples
3. Enhanced error messages
```

## Common Design Issues

### Too Many Agents
```
Problem: 10+ agents
Issue: Hard to understand relationships

Fix: Consolidate related domains
     Keep 3-5 primary agents
```

### Unclear Agent Roles
```
Problem: Overlapping responsibilities
Issue: Users don't know which agent to ask

Fix: Clear single responsibility per agent
     Document integration points
```

### Missing Skills
```
Problem: Agents mentioned but skills don't exist
Issue: Users can't access knowledge

Fix: Create missing skills
     Link in agent capabilities
```

### Confusing Commands
```
Problem: Inconsistent naming
Issue: Users can't discover commands

Fix: Use verb-noun pattern consistently
     Document all options
```

## Tips

- Start with clear agent domains
- Plan integrations before implementing
- Document as you design
- Review with colleagues
- Test the workflow
- Iterate based on feedback

## Related Commands

- `/create-plugin` - Create new plugin
- `/test-plugin` - Test architecture
- `/optimize-plugin` - Optimize design

---

**Status**: 🟢 Ready | **Updated**: 2025
