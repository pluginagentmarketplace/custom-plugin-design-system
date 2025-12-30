---
name: test-plugin
description: Run comprehensive tests on plugin including structure, content, functionality, and performance validation
sasmp_version: "1.3.0"
allowed-tools: Read

# Exit Codes
exit_codes:
  0: all_tests_pass
  1: invalid_input
  2: plugin_not_found
  3: structure_tests_failed
  4: content_tests_failed
  5: functionality_tests_failed
  6: performance_tests_failed
  7: integration_tests_failed

# Input Validation
validation:
  plugin_name:
    pattern: "^[a-z][a-z0-9-]{2,49}$"
    required: true
  test_type:
    type: string
    enum: [full, structure, content, functionality, performance, integration]

# Retry Configuration
retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# /test-plugin - Test & Validate Plugin

## What This Does

Runs comprehensive tests on your plugin. Validates structure, content, functionality, and performance. Ensures quality before deployment.

## Usage

```
/test-plugin my-plugin
/test-plugin my-plugin --full
/test-plugin my-plugin --report
/test-plugin my-plugin --fix-issues
```

## Options

| Option | Description |
|--------|-------------|
| `--full` | Run all tests (comprehensive) |
| `--report` | Generate detailed report |
| `--fix-issues` | Auto-fix common issues |
| `--verbose` | Show all details |
| `--performance` | Performance testing |

## Example

```
$ /test-plugin my-awesome-plugin

PLUGIN TEST REPORT
═══════════════════════════════════════

Plugin: my-awesome-plugin
Version: 1.0.0

RUNNING TESTS...

Structure Tests
  ✅ Manifest valid JSON
  ✅ All files exist
  ✅ Naming conventions
  ✅ References valid
  └─ 4/4 PASS

Content Tests
  ✅ Agents valid (3/3)
  ✅ Skills valid (5/5)
  ✅ Commands valid (3/3)
  └─ 11/11 PASS

Functionality Tests
  ✅ Agents invoke
  ✅ Skills load
  ✅ Commands execute
  └─ 8/8 PASS

Performance Tests
  ✅ Load time < 500ms
  ✅ Command response < 2s
  ✅ File sizes optimal
  └─ 3/3 PASS

Integration Tests
  ✅ Agent collaboration
  ✅ Skill linking
  ✅ Command workflow
  └─ 3/3 PASS

═══════════════════════════════════════
TOTAL: 29/29 PASS ✅

Quality Score: 98/100 ✅
Status: PRODUCTION READY ✅

📍 Next: /optimize-plugin my-awesome-plugin
```

## Test Categories

### Structure Tests
```
✅ plugin.json valid
✅ All referenced files exist
✅ Naming conventions followed
✅ No circular references
✅ Required files present
```

### Content Tests
```
✅ Agent descriptions valid
✅ Agent capabilities specified
✅ Skill content complete
✅ Command documentation clear
✅ All links valid
```

### Functionality Tests
```
✅ Agents load without error
✅ Skills accessible
✅ Commands execute
✅ Output as expected
✅ Error handling works
```

### Performance Tests
```
✅ Agent load < 500ms
✅ Skill load < 300ms
✅ Command response < 2s
✅ File sizes acceptable
✅ Memory usage reasonable
```

## Detailed Report Example

```
$ /test-plugin my-plugin --report --verbose

COMPREHENSIVE TEST REPORT
═══════════════════════════════════════
Plugin: my-awesome-plugin
Date: 2025-01-18
Duration: 2.34 seconds

STRUCTURE VALIDATION
├─ plugin.json
│  ├─ Valid JSON: ✅
│  ├─ Required fields: ✅
│  ├─ Agent count: 3 ✅
│  ├─ Skill count: 5 ✅
│  └─ Command count: 3 ✅
│
├─ File Organization
│  ├─ agents/ exists: ✅
│  ├─ skills/ exists: ✅
│  ├─ commands/ exists: ✅
│  └─ hooks/ exists: ✅
│
└─ References
   ├─ All agents exist: ✅
   ├─ All skills exist: ✅
   ├─ All commands exist: ✅
   └─ No broken links: ✅

CONTENT VALIDATION
├─ Agent Files (3)
│  ├─ 01-architect.md: ✅ (320 lines)
│  ├─ 02-developer.md: ✅ (300 lines)
│  └─ 03-designer.md: ✅ (310 lines)
│
├─ Skill Files (5)
│  ├─ plugin-architecture: ✅ (240 lines)
│  ├─ plugin-development: ✅ (220 lines)
│  ├─ plugin-design: ✅ (210 lines)
│  ├─ plugin-testing: ✅ (230 lines)
│  └─ plugin-optimization: ✅ (250 lines)
│
└─ Command Files (3)
   ├─ create-plugin.md: ✅ (120 lines)
   ├─ design-plugin.md: ✅ (140 lines)
   └─ test-plugin.md: ✅ (130 lines)

QUALITY METRICS
├─ Documentation: 100% ✅
├─ Examples: 100% ✅
├─ Links: 100% functional ✅
├─ Error messages: Clear ✅
└─ Best practices: 98% ✅

PERFORMANCE METRICS
├─ Agent init time: 0.42s ✅
├─ Skill load time: 0.28s ✅
├─ Command execution: 1.64s ✅
├─ Total plugin: 2.34s ✅
└─ File size: 15.2KB ✅

═══════════════════════════════════════
SUMMARY
Quality Score: 98/100 ✅
Tests Passed: 29/29
Status: PRODUCTION READY ✅

Recommendations:
✅ No issues found
✅ Ready for deployment
✅ Ready for marketplace
```

## Performance Baseline

```
Load time:       < 500ms  ✅
Skill load:      < 300ms  ✅
Command exec:    < 2s     ✅
File size:       < 50KB   ✅
```

## Auto-Fix Issues

```
$ /test-plugin my-plugin --fix-issues

Auto-fixing issues...

✅ Fixed: YAML formatting in agents/agent.md
✅ Fixed: Agent description too long (trimmed)
✅ Fixed: Skill name invalid (updated)
✅ Fixed: Missing required field in plugin.json
⚠️  Warning: Manual review needed for complex changes

Fixed: 4 issues
Review needed: 1 issue

Run: /test-plugin my-plugin again to verify
```

## Tips

- Test early and often
- Fix issues immediately
- Review detailed report before deployment
- Use auto-fix for simple issues
- Manually review complex problems
- Test integrations thoroughly

## Related Commands

- `/create-plugin` - Create new plugin
- `/design-plugin` - Design architecture
- `/optimize-plugin` - Optimize and deploy

---

## 🔧 TROUBLESHOOTING

### Error Messages

| Error | Code | Cause | Solution |
|-------|------|-------|----------|
| `Invalid plugin name` | 1 | Name format wrong | Use lowercase-hyphen format |
| `Plugin not found` | 2 | Directory missing | Run /create-plugin first |
| `Structure tests failed` | 3 | Missing/invalid files | Check plugin.json, folders |
| `Content tests failed` | 4 | Invalid YAML/content | Validate frontmatter |
| `Functionality tests failed` | 5 | Runtime errors | Check agent/skill loading |
| `Performance tests failed` | 6 | Exceeds limits | Optimize file sizes |
| `Integration tests failed` | 7 | Broken references | Fix bonded_agent links |

### Debug Checklist

```markdown
□ Step 1: Identify failing test
  → Note test ID (A001, S002, etc.)
  → Read error message

□ Step 2: Locate issue
  → Open referenced file
  → Find problematic line

□ Step 3: Understand expected
  → Check test criteria
  → Compare with passing examples

□ Step 4: Fix and verify
  → Make minimal change
  → Re-run specific test
  → Run full suite
```

### Test Failure Patterns

| Pattern | Cause | Fix |
|---------|-------|-----|
| All structure fail | Invalid plugin.json | Validate JSON syntax |
| All content fail | YAML errors | Check indentation |
| Random failures | Flaky tests | Add retry, check timing |
| Performance fail | Large files | Trim to size limits |

### Auto-Fix Capabilities

```markdown
Can auto-fix:
✅ YAML formatting
✅ Trim long descriptions
✅ Fix naming conventions
✅ Add missing fields

Cannot auto-fix:
❌ Logic errors
❌ Complex refactoring
❌ Security issues
❌ Architecture problems
```

### Exit Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| 0 | All pass | Proceed to /optimize-plugin |
| 1 | Invalid input | Check plugin name |
| 2 | Not found | Create plugin first |
| 3 | Structure fail | Fix manifest/folders |
| 4 | Content fail | Fix YAML/markdown |
| 5 | Functionality fail | Debug runtime errors |
| 6 | Performance fail | Optimize sizes |
| 7 | Integration fail | Fix references |

---

**Status**: 🟢 Ready | **Updated**: 2025
