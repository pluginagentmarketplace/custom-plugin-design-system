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

**Status**: 🟢 Ready | **Updated**: 2025
