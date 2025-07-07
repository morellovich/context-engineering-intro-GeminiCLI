<!--
  GEMINI.md: Project Guidelines optimized for Gemini CLI
  - Streamlined for direct use with `gemini context` commands
  - Base examples in Python; adapt via comments for other languages
-->

```yaml
# Project language setting (change as needed)
language: Python  # e.g., C++, C, Lua
```

### 🔄 Project Awareness & Context

- **Bootstrapping**: On each CLI session, run:
  ```bash
  gemini context load PLANNING.md
  ```
  to import architecture, goals, style, and constraints.
- **Task Registration**: Before starting work:
  ```bash
  gemini context list-tasks
  ```
  If missing, add with:
  ```bash
  gemini context add-task "YYYY-MM-DD: Brief task description"
  ```
- **Consistency**: Enforce naming, folder structure, and patterns from `PLANNING.md`.
- **Environment**: Activate project environment:
  - Python: `source venv_linux/bin/activate`
  - <!-- C++: `source env_cpp.sh` -->

---

### 🧱 Code Structure & Modularity

- **File Size Limit**: Keep files under 500 lines; refactor into modules if exceeded.

- **Module Layout (Python)**:
  ```text
  src/
    agent.py      # agent logic
    tools.py      # utility functions
    prompts.py    # system prompts
  tests/
    test_agent.py # unit tests
  ```
  <!-- Adapt for Lua: use `.lua` files; for C++: `.hpp`/`.cpp` pairs -->

- **Imports/Includes**:
  - Python: relative imports, e.g., `from .tools import helper`
  - <!-- C++: `#include "Tools.hpp"` and `#pragma once` guards -->

- **Configuration Loading**:
  ```python
  from dotenv import load_dotenv
  load_dotenv()
  ```
  <!-- C: use `getenv` from `<stdlib.h>` -->

---

### 🧪 Testing & Reliability

- **Test Creation**: For new features, add unit tests:
  ```bash
  gemini context run pytest
  ```
- **Structure**: Mirror `src/` in `tests/`:
  - 1 normal case
  - 1 edge case
  - 1 failure case

- **Post-change Validation**:
  ```bash
  pytest --maxfail=1 -q
  ```
  <!-- C++: `cmake --build build && ctest` -->

---

### ✅ Task Completion

- **Mark Done**:
  ```bash
  gemini context complete-task <task-id>
  ```
- **Discovered Work**: Append new subtasks:
  ```bash
  gemini context add-subtask "Description of discovered task"
  ```

---

### 📎 Style & Conventions

- **Python**:
  - Enforce PEP8 with `black` and `flake8`:
    ```bash
    black . && flake8 .
    ```
  - Type hints on all public functions.
  - Use `pydantic` for data validation.
- **Frameworks**:
  - API: FastAPI; ORM: SQLAlchemy or SQLModel.

- **Docstrings**: Google style:
  ```python
  def func(x: int) -> str:
      """
      Description.

      Args:
          x (int): input value.

      Returns:
          str: result.
      """
  ```
  <!-- C++: use Doxygen (`/** ... */`) -->

---

### 📚 Documentation & Explainability

- **README Updates**: After adding features or changing deps, run:
  ```bash
  gemini context update-readme
  ```
- **Inline Reasoning**:
  ```python
  # Reason: handle null input to prevent crash
  if data is None:
      return default
  ```

---

### 🧠 AI Behavior Rules

1. **Clarify**: Ask if context is missing.
2. **No Hallucinations**: Only use documented packages/APIs.
3. **Verify Paths**: Confirm files/modules exist before coding.
4. **Safe Edits**: Do not overwrite code without explicit `TASK.md` instruction.

---

### ⚡ Key Gemini CLI Commands

```bash
# Load planning context
gemini context load PLANNING.md

# Generate and execute PRPs
gemini context generate-prp INITIAL.md
gemini context execute-prp PRPs/your-feature.md

# Manage tasks
gemini context list-tasks
gemini context add-task "..."
gemini context complete-task <id>
```
