# Claude Code Guidelines for Python/FastAPI & TypeScript/Next.js

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
- **C-2 (MUST)** Use descriptive function names that explain WHAT the function does
  ```
  # ✅ Good - describes the action
  calculate_user_subscription_cost()
  validateEmailFormat()
  fetchUserProfile()
  
  # ❌ Bad - describes changes or improvements  
  faster_calculation()
  improved_validation()
  new_user_handler()  // too vague
  ```
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

### 4 — Code Organization
- **O-1 (MUST)** Use absolute imports
- **O-2 (SHOULD)** Keep business logic separate from framework-specific code
- **O-3 (MUST)** Group related functionality in feature folders

### 5 — Security & Performance
- **P-1 (MUST)** Validate and sanitize all user inputs
- **P-2 (SHOULD)** Use environment variables for configuration
- **P-3 (MUST)** Never commit secrets or API keys

---

## Python/FastAPI Specific Rules

### FastAPI Framework
- **PY-F1 (MUST)** Use Pydantic models for request/response validation
- **PY-F2 (SHOULD)** Include proper HTTP status codes and error responses
- **PY-F3 (MUST)** Add docstrings to all endpoints for auto-generated docs
- **PY-F4 (SHOULD)** Use dependency injection for database sessions and auth
- **PY-F5 (MUST)** Design RESTful APIs: use resource-based URLs (/users, not /get-users) and proper HTTP methods

### Python Code Style
- **PY-C1 (MUST)** Use type hints for all function parameters and return values
- **PY-C2 (SHOULD)** Use async/await for I/O operations
- **PY-C3 (MUST)** Use specific exception types, not generic `Exception`

### Python Project Structure
```
app/
├── api/v1/routers/
├── core/
├── crud/            # Database operations
├── models/          # SQLAlchemy models
├── schemas/         # Pydantic models
├── services/        # Business logic
├── utils/           # Helper functions
├── tests/
└── main.py
```

### Python Tools
- **Testing**: `pytest --cov=app`
- **Formatting**: `black .`
- **Import sorting**: `isort .`
- **Type checking**: `mypy .`
- **Linting**: `ruff check .`

---

## TypeScript/Next.js Specific Rules

### React Patterns
- **TS-R1 (MUST)** Use functional components with hooks, not class components
- **TS-R2 (MUST)** Extract custom hooks for reusable logic
- **TS-R3 (SHOULD)** Use `useCallback` and `useMemo` for performance optimization
- **TS-R4 (MUST)** Handle loading and error states in components

### Next.js Framework
- **TS-N1 (MUST)** Use App Router (not Pages Router) for new features
- **TS-N2 (SHOULD)** Use Server Components by default, Client Components when needed
- **TS-N3 (MUST)** Implement proper SEO with metadata API
- **TS-N4 (SHOULD)** Use Next.js Image component for optimized images

### TypeScript Code Style
- **TS-C1 (SHOULD)** Use branded types for IDs: `type UserId = Brand<string, 'UserId'>`
- **TS-C2 (MUST)** Use `import type { … }` for type-only imports
- **TS-C3 (SHOULD)** Use Zod for runtime validation

### TypeScript Project Structure
```
src/
├── app/             # Next.js App Router
├── components/
│   ├── ui/         # Reusable UI components
│   └── features/   # Feature-specific components
├── hooks/          # Custom React hooks
├── lib/            # Utility libraries
├── types/          # TypeScript definitions
├── utils/          # Helper functions
└── __tests__/
```

### TypeScript Tools
- **Package Manager**: `pnpm` or `npm`
- **Testing**: `jest --watchAll` or `vitest`
- **Linting**: `eslint --fix .`
- **Formatting**: `prettier --write .`
- **Type Checking**: `tsc --noEmit`

---

## Common Error Patterns to Avoid

### Universal Anti-Patterns
- Using vague function names like `newHandler()` or `improvedLogic()`
- Mixing business logic with framework code
- Missing error handling
- Hardcoded values instead of configuration
- Writing comments for self (do NOT include self-reminders, TODOs, or implementation notes in parentheses) - write comments for human readers only

### Python Anti-Patterns
- Using `any` type annotations
- Not using async for I/O operations
- Missing Pydantic validation

### TypeScript Anti-Patterns
- Using `any` type
- Not handling loading/error states
- Mixing Server and Client Component patterns incorrectly
