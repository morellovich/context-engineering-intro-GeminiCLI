# PRP Template for Gemini CLI
name: base_prp_template_v2
version: 2
type: prp
author: Sathariels -- this is just and edited version of the template of coleam00 most credit goes to him. 
date_created: 07/7/2025
feature_name: [insert-a-feature-slug]
description: |
  Template optimized for AI agents to implement features with sufficient context and self-validation capabilities to achieve working code through iterative refinement.
```

## Purpose
A structured, context-rich PRP format for Gemini CLI with built-in validation loops and examples.

## Core Principles
1. **Context is King**: Include ALL necessary documentation, examples, and caveats
2. **Validation Loops**: Provide executable tests/lints the AI can run and fix
3. **Information Dense**: Use keywords and patterns from the codebase
4. **Progressive Success**: Start simple, validate, then enhance
5. **Global rules**: Follow all rules in GEMINI.md

---

## Goal
[What needs to be built - be specific about the end state and desires]

## Why
- [Business value and user impact]
- [Integration with existing features]
- [Problems this solves and for whom]

## What
[User-visible behavior and technical requirements]

### Success Criteria
```yaml
success_criteria:
  - description: [Specific measurable outcome 1]
  - description: [Specific measurable outcome 2]
```

## All Needed Context

### Documentation & References (list all context needed to implement the feature)
```yaml
# MUST READ - Include these in your context window
- url: [Official API docs URL]
  why: [Specific sections/methods you'll need]

- file: [path/to/example.py]
  why: [Pattern to follow, gotchas to avoid]

- doc: [Library documentation URL] 
  section: [Specific section about common pitfalls]
  critical: [Key insight that prevents common errors]

- docfile: [PRPs/ai_docs/file.md]
  why: [docs that the user has pasted in to the project]
```

### Current Codebase tree (run `tree` in the root of the project) to get an overview of the codebase
```bash
# paste tree output here
```

### Desired Codebase tree with files to be added and responsibility of file
```bash
# Show which files will be created/edited
```

### Known Gotchas of our codebase & Library Quirks
```python
# CRITICAL: [Library name] requires [specific setup]
# Example: FastAPI requires async functions for endpoints
# Example: This ORM doesn't support batch inserts over 1000 records
# Example: We use pydantic v2 and ...
```

## Implementation Blueprint

### Data models and structure
```python
# Examples: 
#  - orm models
#  - pydantic models
#  - pydantic schemas
#  - validators
```

### List of tasks to be completed to fulfill the PRP
```yaml
Task 1:
  MODIFY src/existing_module.py:
    - FIND pattern: "class OldImplementation"
    - INJECT after: "def __init__"
    - PRESERVE: method signatures

  CREATE src/new_feature.py:
    - MIRROR: src/similar_feature.py
    - MODIFY: class name and logic
    - KEEP: error handling pattern

# ... additional tasks ...
```

### Per task pseudocode
```python
# Task 1 pseudocode
async def new_feature(param: str) -> Result:
    # PATTERN: validate input (see src/validators.py)
    validated = validate_input(param)

    # GOTCHA: requires connection pooling
    async with get_connection() as conn:
        @retry(attempts=3, backoff=exponential)
        async def _inner():
            await rate_limiter.acquire()
            return await external_api.call(validated)

        result = await _inner()
    return format_response(result)  # see src/utils/responses.py
```

### Integration Points
```yaml
DATABASE:
  - migration: "Add column 'feature_enabled' to users table"
  - index: "CREATE INDEX idx_feature_lookup ON users(feature_id)"

CONFIG:
  - add to: config/settings.py
  - pattern: "FEATURE_TIMEOUT = int(os.getenv('FEATURE_TIMEOUT', '30'))"

ROUTES:
  - add to: src/api/routes.py
  - pattern: "router.include_router(feature_router, prefix='/feature')"
```

## Validation Loop

### Level 1: Syntax & Style
```bash
ruff check src/new_feature.py --fix
mypy src/new_feature.py
```

### Level 2: Unit Tests
```python
def test_happy_path():
    result = new_feature("valid")
    assert result.status == "success"

def test_validation_error():
    with pytest.raises(ValidationError):
        new_feature("")

def test_external_api_timeout():
    with mock.patch('external_api.call', side_effect=TimeoutError):
        result = new_feature("valid")
        assert result.status == "error"
        assert "timeout" in result.message
```
```bash
uv run pytest test_new_feature.py -v
```

### Level 3: Integration Test
```bash
uv run python -m src.main --dev

curl -X POST http://localhost:8000/feature \
  -H "Content-Type: application/json" \
  -d '{"param": "test_value"}'
```

## Final validation Checklist
```yaml
- [ ] All tests pass: uv run pytest tests/ -v
- [ ] No linting errors: uv run ruff check src/
- [ ] No type errors: uv run mypy src/
- [ ] Manual test successful: [insert curl/command]
- [ ] Error cases handled gracefully
- [ ] Logs are informative but not verbose
- [ ] Documentation updated if needed
```

---

## Anti-Patterns to Avoid
- ❌ Creating new patterns when existing ones suffice
- ❌ Skipping validation
- ❌ Ignoring test failures
- ❌ Using sync functions in async flows
- ❌ Hardcoding config values
- ❌ Catching all exceptions generically

---

```bash
# To generate this PRP:
gemini context generate-prp INITIAL.md

# To execute this PRP:
gemini context execute-prp PRPs/your-feature.md
