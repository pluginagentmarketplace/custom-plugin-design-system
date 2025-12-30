---
name: plugin-optimization
description: Master plugin performance optimization, best practices, and marketplace readiness. Learn to optimize for speed, efficiency, and user satisfaction.
sasmp_version: "1.3.0"
bonded_agent: 05-plugin-optimizer
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

# Plugin Optimization

## Quick Start

Optimize your plugin:

```bash
# Get recommendations
/optimize-plugin my-plugin

# Auto-fix issues
/optimize-plugin my-plugin --auto-fix

# Full report
/optimize-plugin my-plugin --report
```

## Core Concepts

### Performance Targets

| Component | Target | Acceptable | Critical |
|-----------|--------|------------|----------|
| Agent init | < 500ms | < 1000ms | > 2000ms |
| Skill load | < 300ms | < 500ms | > 1000ms |
| Command | < 1000ms | < 2000ms | > 5000ms |
| Hook | < 50ms | < 100ms | > 500ms |
| Workflow | < 3000ms | < 5000ms | > 10000ms |

### Content Optimization

**Before (Verbose):**
```markdown
This agent specializes in various aspects of the field,
including many different topics that are related to the
general area of expertise.
```

**After (Optimized):**
```markdown
Expert in X, Y, Z. Focuses on production-grade solutions.
```

**Impact:** 70% size reduction

### Size Limits

| Component | Min | Max | Optimal |
|-----------|-----|-----|---------|
| Agent | 200 | 400 | 280-320 |
| Skill | 150 | 300 | 200-250 |
| Command | 80 | 150 | 100-120 |
| Plugin | - | 50KB | < 40KB |

### Quality Score

```
Score = Weighted Average:
├─ Structure (30%)
│  ├─ Manifest valid
│  ├─ Files organized
│  └─ Naming correct
├─ Content (30%)
│  ├─ Completeness
│  └─ Clarity
├─ Functionality (20%)
│  ├─ Error handling
│  └─ Integration
├─ Performance (10%)
└─ Documentation (10%)

Target: 95%+ for production
Minimum: 80% for marketplace
```

### Marketplace Readiness

```markdown
SUBMISSION CHECKLIST
═══════════════════════════════

METADATA
□ name: 20-50 chars
□ version: semantic
□ description: 100-256 chars
□ license: MIT/Apache/GPL

DOCUMENTATION
□ README comprehensive
□ CHANGELOG current
□ Examples working

QUALITY
□ All tests pass
□ No errors
□ Performance met
□ Security scan passed
```

## Advanced Topics

### Optimization Priorities

| Impact | Effort | Priority | Action |
|--------|--------|----------|--------|
| High | Low | P0 | Do now |
| High | High | P1 | Plan |
| Low | Low | P2 | Quick win |
| Low | High | P3 | Later |

### Release Workflow

```markdown
Pre-Release:
├─ Version bump
├─ Update CHANGELOG
├─ Run test suite
├─ Performance check
└─ Security scan

Release:
├─ Create git tag
├─ Push to main
├─ Submit to marketplace
└─ Announce

Post-Release:
├─ Monitor metrics
├─ Respond to issues
└─ Plan next iteration
```

### Semantic Versioning

| Version | When | Example |
|---------|------|---------|
| PATCH | Bug fixes | 1.0.0 → 1.0.1 |
| MINOR | New features | 1.0.0 → 1.1.0 |
| MAJOR | Breaking changes | 1.0.0 → 2.0.0 |

## Real-World Projects

### Project 1: Performance Report
```
╔════════════════════════════════════╗
║     PERFORMANCE DASHBOARD          ║
╠════════════════════════════════════╣
║ LOAD TIMES          Target  Actual ║
║ ├─ Plugin init:     500ms   320ms ✅║
║ ├─ Agent call:      1000ms  650ms ✅║
║ └─ Command:         2000ms  890ms ✅║
╠════════════════════════════════════╣
║ QUALITY             Target  Actual ║
║ ├─ Test coverage:   90%     95%   ✅║
║ └─ Best practices:  95%     98%   ✅║
╚════════════════════════════════════╝
```

### Project 2: Optimization Plan
```markdown
OPTIMIZATION PLAN: my-plugin
═══════════════════════════════

P0 - CRITICAL (This Week)
├─ Fix broken manifest
└─ Add missing error handling

P1 - HIGH (Next Sprint)
├─ Reduce agent size
└─ Add input validation

P2 - MEDIUM (Backlog)
├─ Improve docs
└─ Add more examples
```

---

## 🔧 TROUBLESHOOTING

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Slow load | Large content | Trim to limits |
| Low score | Missing sections | Add required content |
| Rejection | Invalid metadata | Fix manifest |
| Regression | Recent changes | Revert, investigate |
| High errors | Missing validation | Add input checks |

### Debug Flow

```markdown
□ Step 1: Identify problem
  → Check quality score
  → Review metrics
  → Read errors

□ Step 2: Analyze cause
  → Compare baseline
  → Check changes
  → Review tests

□ Step 3: Plan fix
  → Estimate impact
  → Assess effort
  → Prioritize

□ Step 4: Implement
  → Minimal change
  → Test thoroughly
  → Verify improvement

□ Step 5: Validate
  → Re-run benchmarks
  → Confirm score
  → Monitor
```

### Marketplace Rejections

| Reason | Fix |
|--------|-----|
| Invalid manifest | Validate JSON |
| Missing docs | Add README |
| Quality low | Run /test-plugin |
| Security issue | Security scan |

### Exit Codes

| Code | Meaning | Action |
|------|---------|--------|
| 0 | Complete | Deploy |
| 1 | Minor issues | Review |
| 2 | Major issues | Fix first |
| 3 | Critical | Do not deploy |
| 4 | Not ready | Address checklist |

---

**Use this skill when:**
- Optimizing performance
- Preparing for deployment
- Improving quality
- Following best practices
- Before marketplace submission
