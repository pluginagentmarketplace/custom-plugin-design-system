---
name: optimize-plugin
description: Optimize plugin for performance, quality, and marketplace readiness with automated improvements
sasmp_version: "1.3.0"
allowed-tools: Read

# Exit Codes
exit_codes:
  0: optimization_complete
  1: invalid_input
  2: plugin_not_found
  3: optimization_failed
  4: marketplace_check_failed
  5: pre_submit_failed
  6: version_bump_failed

# Input Validation
validation:
  plugin_name:
    pattern: "^[a-z][a-z0-9-]{2,49}$"
    required: true
  optimization_type:
    type: string
    enum: [performance, marketplace, pre-submit, auto-apply, report]
  version_bump:
    type: string
    enum: [patch, minor, major]

# Retry Configuration
retry_config:
  max_attempts: 3
  backoff_type: exponential
  initial_delay_ms: 500
---

# /optimize-plugin - Optimize & Deploy Plugin

## What This Does

Optimizes your plugin for performance, quality, and marketplace readiness. Applies best practices, optimizes content, and prepares for deployment.

## Usage

```
/optimize-plugin my-plugin
/optimize-plugin my-plugin --performance
/optimize-plugin my-plugin --marketplace
/optimize-plugin my-plugin --pre-submit
```

## Options

| Option | Description |
|--------|-------------|
| `--performance` | Optimize speed and size |
| `--marketplace` | Prepare for marketplace |
| `--pre-submit` | Final pre-submission check |
| `--auto-apply` | Auto-apply optimizations |
| `--report` | Generate optimization report |

## Example

```
$ /optimize-plugin my-awesome-plugin

PLUGIN OPTIMIZATION
═══════════════════════════════════════

Plugin: my-awesome-plugin
Current Score: 85/100
Target Score: 95/100

ANALYZING...

Performance Optimization
  ✅ Agent load time: 0.42s (optimal)
  ✅ Skill load time: 0.28s (optimal)
  ✅ File sizes: 15.2KB (optimal)
  ✅ Content efficiency: 92%
  └─ Performance: GOOD

Content Optimization
  ⚠️  Agent descriptions could be clearer
  ⚠️  Add more real-world examples
  ⚠️  Enhance error messages
  └─ Recommendations: 3

Best Practices
  ✅ YAML frontmatter valid
  ✅ Naming conventions correct
  ✅ Documentation complete
  ✅ Integration documented
  └─ Practices: EXCELLENT

Marketplace Readiness
  ✅ README comprehensive
  ✅ Examples working
  ✅ License included
  ✅ Repository valid
  └─ Marketplace: READY

═══════════════════════════════════════

Applying Optimizations...
  ✅ Trimmed verbose sections
  ✅ Enhanced examples
  ✅ Improved error messages
  ✅ Updated documentation

New Score: 94/100 ✅

OPTIMIZATIONS COMPLETE
═══════════════════════════════════════

Changes:
  ├─ 5 files improved
  ├─ 42 lines trimmed
  ├─ 18 examples enhanced
  └─ 7 messages clarified

Before: 85/100
After:  94/100
Improvement: +9 points ✅

📍 Ready for deployment!
   Next: Push to marketplace
```

## Optimization Checklist

### Performance ✅
```
[ ] Agent load time < 500ms
[ ] Skill load time < 300ms
[ ] Command response < 2s
[ ] File sizes optimized
[ ] Memory usage reasonable
```

### Quality ✅
```
[ ] All tests passing
[ ] No console errors
[ ] Error handling complete
[ ] Documentation accurate
[ ] Examples working
```

### Best Practices ✅
```
[ ] Single responsibility agents
[ ] Clear agent integrations
[ ] Working skill examples
[ ] Intuitive commands
[ ] Helpful error messages
```

### Documentation ✅
```
[ ] README comprehensive
[ ] CHANGELOG updated
[ ] Examples clear
[ ] Links verified
[ ] Instructions followed
```

## Marketplace Preparation

```
$ /optimize-plugin my-plugin --marketplace

MARKETPLACE PREPARATION
═══════════════════════════════════════

Manifest Verification
  ✅ Name: clear, descriptive
  ✅ Version: semantic (1.0.0)
  ✅ Description: complete
  ✅ Author: specified
  ✅ License: MIT
  ✅ Repository: active

Documentation Review
  ✅ README: comprehensive
  ✅ Examples: working
  ✅ Installation: clear
  ✅ Usage: documented
  ✅ Support: included

Quality Assessment
  ✅ Test coverage: 95%
  ✅ Error rate: < 1%
  ✅ Performance: baseline met
  ✅ Best practices: 98%

Marketplace Checklist
  ✅ Structure: valid
  ✅ Content: quality
  ✅ Features: complete
  ✅ Documentation: thorough
  ✅ Ready to submit: YES

Submission Details:
  Plugin Name: my-awesome-plugin
  Version: 1.0.0
  Category: Development Tools
  Tags: plugin, architecture, design

Ready for marketplace submission ✅
```

## Pre-Submission Check

```
$ /optimize-plugin my-plugin --pre-submit

FINAL PRE-SUBMISSION CHECK
═══════════════════════════════════════

REQUIREMENTS ✅
  [✅] plugin.json exists
  [✅] All agents present
  [✅] All skills present
  [✅] All commands present
  [✅] Hooks configured

QUALITY ✅
  [✅] All tests pass
  [✅] No warnings
  [✅] No errors
  [✅] Performance ok
  [✅] Documentation complete

STANDARDS ✅
  [✅] YAML frontmatter valid
  [✅] Markdown proper
  [✅] JSON valid
  [✅] Naming conventions
  [✅] References valid

MARKETPLACE ✅
  [✅] README ready
  [✅] Examples working
  [✅] Links active
  [✅] License included
  [✅] Repository active

═══════════════════════════════════════
✅ ALL CHECKS PASSED

Status: READY FOR SUBMISSION
Next: Submit to marketplace

Submission Steps:
1. git push to main
2. Create GitHub release
3. Submit marketplace form
4. Wait for approval (24-48 hours)
```

## Optimization Report

```
$ /optimize-plugin my-plugin --report

OPTIMIZATION REPORT
═══════════════════════════════════════

Performance Metrics:
  Load time:          0.42s (< 500ms) ✅
  Skill load:         0.28s (< 300ms) ✅
  Command response:   1.64s (< 2s) ✅
  File size:          15.2KB (< 50KB) ✅

Quality Metrics:
  Test pass rate:     100% ✅
  Error rate:         0% ✅
  Documentation:      100% ✅
  Best practices:     98% ✅

Content Metrics:
  Agent quality:      95/100 ✅
  Skill quality:      94/100 ✅
  Command quality:    96/100 ✅

Overall Score: 94/100 ✅

Recommendations:
  ✅ Production ready
  ✅ Marketplace ready
  ✅ No issues found

Status: OPTIMIZED & READY
```

## Version Management

### Bump Version
```
/optimize-plugin my-plugin --bump-version

Current: 1.0.0
Type: patch | minor | major
New: 1.0.1

Changes:
  ✅ Updated plugin.json
  ✅ Updated CHANGELOG.md
  ✅ Tagged git commit
```

### Release Checklist
```
Before Release:
  [✅] Version bumped
  [✅] CHANGELOG updated
  [✅] All tests pass
  [✅] Documentation complete
  [✅] Changes committed
  [✅] Git tagged

After Release:
  [✅] Push to main
  [✅] Create GitHub release
  [✅] Submit to marketplace
  [✅] Monitor for issues
```

## Tips

- Optimize content before performance
- Review suggestions before applying
- Test after each optimization
- Version bump before deployment
- Document all changes
- Monitor metrics post-deployment

## Related Commands

- `/create-plugin` - Create plugin
- `/design-plugin` - Design architecture
- `/test-plugin` - Test plugin

---

## 🔧 TROUBLESHOOTING

### Error Messages

| Error | Code | Cause | Solution |
|-------|------|-------|----------|
| `Invalid plugin name` | 1 | Name format wrong | Use lowercase-hyphen format |
| `Plugin not found` | 2 | Directory missing | Run /create-plugin first |
| `Optimization failed` | 3 | Cannot apply changes | Check file permissions |
| `Marketplace check failed` | 4 | Missing requirements | Complete checklist items |
| `Pre-submit failed` | 5 | Quality below threshold | Run /test-plugin, fix issues |
| `Version bump failed` | 6 | Invalid version | Use semantic versioning |

### Debug Checklist

```markdown
□ Step 1: Check current state
  → Run /test-plugin first
  → All tests passing?

□ Step 2: Review requirements
  → Marketplace checklist complete?
  → Documentation present?
  → Examples working?

□ Step 3: Verify quality
  → Score above 80%?
  → No critical issues?
  → Performance within limits?

□ Step 4: Pre-submit check
  → All files valid?
  → References resolved?
  → License included?
```

### Optimization Failures

| Failure | Cause | Solution |
|---------|-------|----------|
| Score won't improve | Fundamental issues | Address architecture first |
| Auto-apply rejected | Risky changes | Review manually |
| Marketplace blocked | Missing metadata | Complete plugin.json |
| Version conflict | Already exists | Increment version |

### Marketplace Rejection Reasons

| Reason | Fix |
|--------|-----|
| Invalid manifest | Validate plugin.json |
| Missing README | Add comprehensive README |
| No license | Add MIT/Apache/GPL license |
| Quality too low | Score must be 80%+ |
| Security issues | Run security scan |

### Version Bump Guide

```markdown
PATCH (1.0.0 → 1.0.1)
├─ Bug fixes
├─ Minor improvements
└─ No API changes

MINOR (1.0.0 → 1.1.0)
├─ New features
├─ New agents/skills
└─ Backwards compatible

MAJOR (1.0.0 → 2.0.0)
├─ Breaking changes
├─ Major refactoring
└─ API changes
```

### Exit Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| 0 | Complete | Ready to deploy |
| 1 | Invalid input | Check plugin name |
| 2 | Not found | Create plugin first |
| 3 | Optimization failed | Check permissions/files |
| 4 | Marketplace failed | Complete requirements |
| 5 | Pre-submit failed | Fix quality issues |
| 6 | Version failed | Use valid semver |

---

**Status**: 🟢 Ready | **Updated**: 2025
