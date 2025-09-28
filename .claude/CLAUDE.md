# Universal Coding Guidelines for Claude Code

## Available Subagents and Workflow

### ⚠️ MANDATORY: Use Subagents for ALL Code Changes - NO EXCEPTIONS

**Pre-implementation agents:**
- `@spec-writer`: Clarify requirements (even if they seem clear)
- `@architect`: Design system architecture before coding
- `@task-planner`: Break down into actionable tasks

**Domain specialists:** Consult BEFORE @architect when using:
- `@azure-speech-specialist`: Azure Speech SDK (checks official docs)

**Implementation agents:**
- `@test-runner`: Execute tests and update test code
- `@debugger`: Fix production code bugs
- `@code-reviewer`: Review code quality

**Required workflows:**

1. **Standard (ALL code changes):**
   User request → `@spec-writer` → [Specialist if needed] → `@architect` → `@task-planner` → You implement → `@test-runner` → `@code-reviewer`

2. **Documentation-only:**
   Changes to README/comments → You implement → `@code-reviewer`

**Rules:**
- ANY code changes require FULL workflow
- ALL agents: Max 4000 tokens per response (break large tasks into subtasks)
- Skipping subagents = Rule violation
- Test failures → `@debugger` → `@test-runner` → continue

---

## Core Principles (All Projects)

**MUST** rules are enforced by CI; **SHOULD** rules are strongly recommended.

### 0 — Communication
- **COMM-1 (MUST)** Think and reason in English for technical accuracy, but respond in Japanese for explanations
- **COMM-2 (MUST)** Use English for variable names and function names, but Japanese for code comments and technical documentation

### 1 — Before Coding
- **BP-1 (MUST)** Ask clarifying questions before starting
- **BP-2 (SHOULD)** Draft approach for complex features
- **BP-3 (MUST)** Avoid self-contradictions in recommendations

### 2 — Universal Code Quality
- **C-1 (MUST)** Follow TDD: write failing test → implement → refactor
- **C-2 (MUST)** Use descriptive function names explaining WHAT it does (e.g., `calculate_cost()` not `improved_calc()` or `new_handler()`)
- **C-3 (MUST)** Use strict type hints/annotations - avoid `any` in TS, use type hints in Python
- **C-4 (SHOULD)** Prefer pure functions when possible
- **C-5 (MUST)** Keep functions/components under 50 lines (Python) / 200 lines (React); extract if longer
- **C-6 (MUST)** ONLY modify code explicitly requested - do NOT refactor unrelated code, change formatting, or "improve" existing working code
- **C-7 (MUST)** Do NOT add debug logging to production code - use proper error logging with exception details instead

### 3 — Universal Testing
- **T-1 (MUST)** Write tests for every new function/endpoint/component
- **T-2 (MUST)** Use descriptive test names: `test_should_[expected_behavior]_when_[condition]`
- **T-3 (SHOULD)** Test user interactions and behavior, not implementation details
- **T-4 (MUST)** Mock external dependencies (databases, APIs, file systems)
- **T-5 (MUST)** When modifying existing code, ALWAYS update corresponding tests and documentation
- **T-6 (MUST)** Use existing test files - add tests to them, never create duplicates

### 4 — Code Organization
- **O-1 (MUST)** Use absolute imports
- **O-2 (SHOULD)** Keep business logic separate from framework-specific code
- **O-3 (MUST)** Group related functionality in feature folders

### 5 — Security & Performance
- **P-1 (MUST)** Validate and sanitize all user inputs
- **P-2 (SHOULD)** Use environment variables for configuration
- **P-3 (MUST)** Never commit secrets or API keys

---

## Common Error Patterns to Avoid

### Universal Anti-Patterns
- Using vague function names like `newHandler()` or `improvedLogic()`
- Mixing business logic with framework code
- Missing error handling
- Hardcoded values instead of configuration
- Writing comments for self (do NOT include self-reminders, TODOs, implementation notes in parentheses, or obvious code explanations) - write meaningful comments for human readers only
