---
name: plugin-testing
description: Master plugin testing, quality assurance, and validation. Learn unit testing, integration testing, and how to ensure plugin quality.
sasmp_version: "1.3.0"
bonded_agent: 04-plugin-tester
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

# Plugin Testing

## Quick Start

Test your plugin:

```bash
# Validate structure
/test-plugin my-plugin

# Run all tests
/test-plugin my-plugin --all

# Detailed report
/test-plugin my-plugin --report
```

## Core Concepts

### Testing Pyramid

```
       ╱╲
      ╱  ╲       E2E (10%)
     ╱────╲
    ╱      ╲     Integration (30%)
   ╱────────╲
  ╱          ╲   Unit (60%)
 ╱────────────╲
```

### Unit Tests

**Agent Testing:**
```markdown
Test A001: Validation
├─ YAML valid: PASS/FAIL
├─ Schema defined: PASS/FAIL
├─ Error handling: PASS/FAIL
└─ Troubleshooting: PASS/FAIL
```

**Skill Testing:**
```markdown
Test S001: Validation
├─ Name lowercase: PASS/FAIL
├─ bonded_agent: PASS/FAIL
├─ Quick Start: PASS/FAIL
└─ Troubleshooting: PASS/FAIL
```

**Command Testing:**
```markdown
Test C001: Validation
├─ exit_codes: PASS/FAIL
├─ Options table: PASS/FAIL
├─ Error messages: PASS/FAIL
└─ Next steps: PASS/FAIL
```

### Integration Tests

**Bond Testing:**
```markdown
For each skill:
├─ bonded_agent exists: PASS/FAIL
├─ Agent references skill: PASS/FAIL
└─ Bond type valid: PASS/FAIL

Orphan Detection:
├─ Skills without agent: [list]
└─ Circular deps: [list]
```

**Workflow Testing:**
```markdown
/create → /design → /test

Step 1: /create-plugin test
├─ Executes: PASS/FAIL
├─ Suggests next: PASS/FAIL
└─ Files created: PASS/FAIL
```

### Performance Benchmarks

| Component | Target | Acceptable | Critical |
|-----------|--------|------------|----------|
| Agent init | < 500ms | < 1000ms | > 2000ms |
| Skill load | < 300ms | < 500ms | > 1000ms |
| Command | < 1000ms | < 2000ms | > 5000ms |

### Size Limits

| Component | Min | Max | Optimal |
|-----------|-----|-----|---------|
| Agent | 200 | 400 | 280-320 |
| Skill | 150 | 300 | 200-250 |
| Command | 80 | 150 | 100-120 |

## Advanced Topics

### Security Testing

```markdown
SEC001: Input Validation
├─ All inputs validated: PASS/FAIL
├─ No eval/exec: PASS/FAIL
└─ Path traversal blocked: PASS/FAIL

SEC002: Data Handling
├─ No hardcoded secrets: PASS/FAIL
├─ No sensitive logging: PASS/FAIL
└─ Proper escaping: PASS/FAIL
```

### Test Report Format

```
╔════════════════════════════════════╗
║        PLUGIN TEST REPORT          ║
╠════════════════════════════════════╣
║ Plugin: my-plugin                  ║
║ Version: 1.0.0                     ║
╠════════════════════════════════════╣
║ STRUCTURE     ✅ 5/5              ║
║ COMPONENTS    ✅ 14/14            ║
║ INTEGRATION   ✅ 5/5              ║
║ PERFORMANCE   ✅ 4/4              ║
╠════════════════════════════════════╣
║ QUALITY SCORE: 98%                 ║
║ VERDICT: ✅ PRODUCTION READY      ║
╚════════════════════════════════════╝
```

## Real-World Projects

### Project 1: Unit Test Suite
```markdown
Test Suite: Agent Validation
═══════════════════════════════

Test 1: Schema
├─ input_schema: ✅
├─ output_schema: ✅
└─ error_handling: ✅

Test 2: Content
├─ Troubleshooting: ✅
└─ Integration: ✅

Result: 5/5 PASS ✅
```

### Project 2: Integration Test
```markdown
Test Suite: Workflow
═══════════════════════════════

Step 1: Create
├─ Command exists: ✅
└─ Output correct: ✅

Step 2: Test
├─ Runs validation: ✅
└─ Reports results: ✅

Result: WORKFLOW VALID ✅
```

---

## 🔧 TROUBLESHOOTING

### Common Test Failures

| Failure | Cause | Solution |
|---------|-------|----------|
| YAML error | Bad indent | 2-space, no tabs |
| Bond missing | No bonded_agent | Add to frontmatter |
| Performance | Large content | Trim to limits |
| Security | Hardcoded value | Use env vars |

### Debug Checklist

```markdown
□ Step 1: Read error message
  → Note test ID (A001, S002)

□ Step 2: Locate issue
  → Open file, find line

□ Step 3: Understand
  → Expected vs actual?

□ Step 4: Fix
  → Minimal change
  → Re-run test

□ Step 5: Verify
  → Full suite passes?
```

### Flaky Test Detection

**Indicators:**
- Passes sometimes, fails other times
- Depends on timing
- Uses random data
- External dependencies

**Fixes:**
- Add explicit waits
- Use deterministic data
- Mock external services
- Add retry with backoff

### Exit Codes

| Code | Meaning | Action |
|------|---------|--------|
| 0 | All pass | Proceed |
| 1 | Some fail | Fix failures |
| 2 | Setup fail | Check environment |
| 3 | Timeout | Optimize or increase |
| 4 | Coverage low | Add more tests |

---

**Use this skill when:**
- Testing plugin components
- Validating structure
- Checking quality
- Before deployment
- Finding and fixing issues
