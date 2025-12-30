---
name: plugin-design
description: Master plugin user experience design, command workflows, and interaction patterns. Create intuitive, user-friendly plugin interfaces.
sasmp_version: "1.3.0"
bonded_agent: 03-plugin-designer
bond_type: PRIMARY_BOND

# Production-Grade Configuration
validation:
  required_sections:
    - quick_start
    - core_concepts
    - troubleshooting
  min_examples: 4

retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# Plugin Design

## Quick Start

Design user-friendly commands:

```markdown
# /create-plugin - Create new plugin

## What This Does
Creates a new plugin with guided setup.

## Usage
/create-plugin [name] [--type agent|command]

## Example
$ /create-plugin my-plugin --type agent
✅ Plugin created!
Next: /design-plugin my-plugin
```

## Core Concepts

### Command Naming Convention

| Pattern | Example | Why |
|---------|---------|-----|
| verb-noun | `/create-plugin` | Clear action |
| consistent | `/test-plugin` | Predictable |
| descriptive | `/optimize-plugin` | Self-explanatory |

❌ Bad: `/plugin`, `/do-stuff`, `/plgn-crt`
✅ Good: `/create-plugin`, `/test-plugin`

### Interactive Workflow

```
/create-plugin

┌────────────────────────────────┐
│ PLUGIN CREATION WIZARD         │
├────────────────────────────────┤
│ Step 1/3: Plugin name          │
│ > my-plugin ✅                 │
│                                │
│ Step 2/3: Plugin type          │
│ [1] Agent-based                │
│ [2] Command-based              │
│ > 1 ✅                         │
│                                │
│ ✅ Created!                    │
│ Next → /design-plugin          │
└────────────────────────────────┘
```

### Error Message Design

**Structure:**
```
❌ [ERROR_CODE] Brief title

What happened:
  [Description]

How to fix:
  1. [Step 1]
  2. [Step 2]

Help: /help error-code
```

**Good vs Bad:**

| Bad ❌ | Good ✅ |
|--------|---------|
| `Invalid input` | `Name must be 3-50 chars, lowercase` |
| `Error 500` | `File not found: skills/my-skill/SKILL.md` |
| `Failed` | `Missing --type option` |

### Visual Consistency

| Symbol | Meaning | Usage |
|--------|---------|-------|
| ✅ | Success | Completed |
| ❌ | Error | Failed |
| ⚠️ | Warning | Caution |
| ℹ️ | Info | Note |
| → | Next | Suggestion |

### Feedback Patterns

**Progress:**
```
Creating plugin...
  [1/4] Creating folders    ✅
  [2/4] Writing files       ✅
  [3/4] Validating          ⏳
  [4/4] Complete            ○
```

**Success:**
```
✅ Plugin created!

Summary:
├─ Name: my-plugin
├─ Type: Agent-based
└─ Location: ./my-plugin/

Next: /design-plugin my-plugin
```

## Advanced Topics

### Progressive Disclosure

| Level | Example | Users |
|-------|---------|-------|
| Basic | `/create-plugin` | Beginners |
| Options | `/create-plugin --type agent` | Intermediate |
| Full | `/create-plugin --config cfg.json` | Advanced |

### Accessibility Standards

```
✅ DO:
- Simple, clear words
- Active voice
- Specific instructions
- Explain acronyms

❌ DON'T:
- Jargon without explanation
- Passive voice
- Vague instructions
```

### Workflow Patterns

**Linear:**
```
/create → /design → /test → /deploy
```

**Branching:**
```
/test
  ├─ Pass → /deploy
  └─ Fail → Fix → /test
```

## Real-World Projects

### Project 1: Simple Command
```markdown
# /greet - Say hello

## What This Does
Displays a greeting message.

## Usage
/greet [name]

## Example
$ /greet World
Hello, World! 👋

## Next Steps
Try: /help for more commands
```

### Project 2: Interactive Command
```markdown
# /setup - Setup wizard

## Usage
/setup

## Flow
1. Ask project name
2. Select template
3. Configure options
4. Generate files
5. Show next steps
```

---

## 🔧 TROUBLESHOOTING

### Common UX Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Confusing command | Unclear naming | Use verb-noun |
| Too many options | Feature creep | Progressive disclosure |
| No feedback | Missing status | Add progress |
| Unclear error | Technical jargon | Plain language |
| Stuck workflow | No next step | Always suggest |

### UX Audit Checklist

```markdown
□ Command Naming
  → Verb-noun pattern?
  → Self-explanatory?

□ Error Handling
  → Clear messages?
  → Solutions provided?

□ Feedback
  → Progress shown?
  → Next steps suggested?

□ Accessibility
  → Works without color?
  → Clear language?
```

### UX Scoring Rubric

| Category | Weight | Criteria |
|----------|--------|----------|
| Clarity | 25% | Self-explanatory |
| Feedback | 25% | Progress shown |
| Errors | 20% | Helpful messages |
| Consistency | 15% | Uniform patterns |
| Accessibility | 15% | Universal design |

**Target Score: 85%+**

### Recovery Procedures

**Unclear Command:**
```
1. Rename to verb-noun
2. Add description
3. Include examples
4. Test with users
```

**Confusing Error:**
```
1. Identify actual cause
2. Write plain language
3. Add fix steps
4. Link to help
```

---

**Use this skill when:**
- Designing commands
- Planning workflows
- Creating help systems
- Improving user experience
- Designing error messages
