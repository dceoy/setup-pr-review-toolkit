---
allowed-tools: Bash(gh pr comment:*),Bash(gh pr diff:*),Bash(gh pr view:*)
description: Comprehensive PR review using specialized agents
argument-hint: "[review-aspects]"
---

# Comprehensive PR Review

Perform a comprehensive code review using specialized subagents, each focusing on a different aspect of code quality.

**Review Aspects (optional):** "$ARGUMENTS"

## Available Review Agents:

**Core Quality Agents (Original):**
- code-quality-reviewer - Clean code, DRY, readability, best practices
- performance-reviewer - Algorithmic complexity, bottlenecks, resource management
- test-coverage-reviewer - Test coverage ratios, test quality, missing scenarios
- documentation-accuracy-reviewer - Documentation accuracy, README validation
- security-code-reviewer - Security vulnerabilities, OWASP Top 10, input validation

**Specialized Analysis Agents (Extended):**
- code-reviewer - Project guidelines compliance, bug detection, style violations
- code-simplifier - Code clarity, simplification, maintainability improvements
- comment-analyzer - Comment accuracy, documentation quality, comment rot
- pr-test-analyzer - PR-specific test coverage, behavioral coverage gaps
- silent-failure-hunter - Silent failures, error handling, swallowed exceptions
- type-design-analyzer - Type design, encapsulation, invariant analysis

## Review Workflow:

1. **Determine Review Scope**
   - Check git status and diff to identify changed files
   - Parse arguments to select specific review aspects (if provided)
   - Default: Run all applicable reviews

2. **Select Agents Based on Arguments:**
   - `all` or no args - Run all applicable agents (default)
   - `quality` - code-quality-reviewer, code-reviewer
   - `tests` - test-coverage-reviewer, pr-test-analyzer
   - `docs` - documentation-accuracy-reviewer, comment-analyzer
   - `errors` - silent-failure-hunter
   - `security` - security-code-reviewer
   - `types` - type-design-analyzer
   - `simplify` - code-simplifier
   - `performance` - performance-reviewer

3. **Launch Review Agents**
   - Instruct each agent to only provide noteworthy feedback
   - Run agents sequentially for interactive review
   - User can request parallel execution for speed

4. **Aggregate and Filter Results**
   - Review feedback from all agents
   - Post only feedback you also deem noteworthy
   - Organize by severity: Critical > Important > Suggestions

5. **Provide Feedback**
   - Use inline comments for specific issues with file:line references
   - Use top-level comments for general observations
   - Keep feedback concise and actionable

## Output Format:

```markdown
# PR Review Summary

## Critical Issues (Must Fix)
- [agent-name]: Issue description [file:line]

## Important Issues (Should Fix)
- [agent-name]: Issue description [file:line]

## Suggestions (Nice to Have)
- [agent-name]: Suggestion [file:line]

## Strengths
- What's well-done in this PR
```

---
