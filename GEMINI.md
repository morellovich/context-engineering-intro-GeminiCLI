<!--
  GEMINI.md: Modular Context Engineering Rules (Base: Python)
  - Core guidelines use Python examples.
  - Side comments (HTML) show how to adapt for other languages (C++, C, Lua, JavaScript).
-->

```yaml
# LANGUAGE CONFIGURATION
# To switch base language, change this value (e.g., C++, C, Lua).
language: Python  # <-- Adapt for C++: set to "C++", then adjust naming and tools below
```

---

## 🔄 Project Awareness & Context

- **Always read `PLANNING.md`** at the beginning of your session to load architecture, project goals, style, and constraints.
- **Check and update `TASK.md`**:
  - If the task isn’t listed, add:
    ```markdown
    - [ ] YYYY-MM-DD: Brief task description
    ```
  - **Use CLI**: `gemini context list-tasks` to view current tasks.
- **Naming & Structure**:
  - Python: follow snake_case modules and packages.
  - <!-- Adapt for C++: use PascalCase for classes, snake_case for files -->
  - <!-- Adapt for Lua: use module_name.lua and table-based modules -->
- **Environment Setup**:
  - Python: activate `venv_linux` (or other venv) before running scripts.
  - <!-- Adapt for C++: source `env_cpp.sh` or set up `cmake` build dir -->

---

## 🧱 Code Structure & Modularity

- **Max file length**: 500 lines. Refactor into modules/packages if exceeded.

- **Base Layout (Python)**:
  ```
  src/
    agent.py       # Main agent class and logic
    tools.py       # Helper functions and tools
    prompts.py     # Prompt definitions and templates
  tests/
    test_agent.py  # Unit tests for agent behaviors
  ```

- <!-- Adapt for C++:
  src/
    Agent.hpp/Agent.cpp  // Class definitions and implementations
    Tools.hpp/Tools.cpp  // Utility functions
    Prompts.hpp          // Constants and templates
  tests/
    test_agent.cpp
  -->

- **Imports/Includes**:
  - Python: `from .tools import ToolClass`
  - <!-- C++: `#include "Tools.hpp"` and `#pragma once` guards -->

---

## 🧪 Testing & Reliability

- **Python (Base)**:
  - Write Pytest tests under `tests/` mirroring `src/` structure.
  - Example:
    ```python
    def test_agent_behavior():
        agent = Agent()
        assert agent.run("input") == "expected"
    ```
- <!-- Adapt for C++: use Google Test, e.g., TEST(AgentTest, Behavior) { ... } -->
- **Test Cases**:
  1. Expected behavior
  2. Edge cases
  3. Failure modes

- **Run tests via CLI**:
  ```bash
  pytest --maxfail=1 --disable-warnings -q
  ```
  - <!-- C++: `cmake --build build && ctest --output-on-failure` -->

---

## 📎 Style & Conventions

- **Python**:
  - Follow PEP8, use `black` and `flake8`.
  - Use type hints for all functions and classes.
- <!-- Adapt for C++: use `clang-format` and `clang-tidy` -->

- **Docstrings/Comments**:
  - Python: Google-style docstrings.
    ```python
    def example(param: int) -> str:
        """
        Brief summary.

        Args:
            param (int): Description.

        Returns:
            str: Description.
        """
    ```
  - <!-- C++: Doxygen comments (`/** ... */`) -->

- **Environment Variables**:
  - Base: load via `python-dotenv` and `load_env()`.
  - Example:
    ```python
    from dotenv import load_dotenv
    load_dotenv()
    ```
  - <!-- C: use `getenv` in `<stdlib.h>` -->

---

## ✅ Task Completion & CLI

- **Mark tasks in `TASK.md`** when done.
- **Add discovered subtasks** under a “Discovered During Work” header.

- **Gemini CLI Commands**:
  ```bash
  # Generate PRP
  gemini context generate-prp INITIAL.md

  # Execute PRP
  gemini context execute-prp PRPs/your-feature.md

  # List Tasks
  gemini context list-tasks
  ```

---

## 📚 Documentation & Explainability

- **Update `README.md`** whenever features or dependencies change.
- **Inline reasoning comments**:
  ```python
  # Reason: We apply X to handle edge-case Y
  result = compute_edge_case(data)
  ```
  - <!-- C++: `// Reason: ...` -->

---

## 🧠 AI Behavior Rules

1. Ask for clarification if context is missing.
2. Do not hallucinate packages or APIs.
3. Verify file paths and modules exist before code references.
4. Only overwrite code when following explicit `TASK.md` directives.
