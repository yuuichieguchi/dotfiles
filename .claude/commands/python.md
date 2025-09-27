Read CLAUDE.md for universal coding rules, then apply the following Python/FastAPI specific patterns.

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

### Python Anti-Patterns
- Using `any` type annotations
- Not using async for I/O operations
- Missing Pydantic validation
