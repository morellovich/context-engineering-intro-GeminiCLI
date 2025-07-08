<!--
  GEMINI_PROJECT_GUIDELINES.md — Optimized for Gemini CLI
  This version keeps all original content and structure, but is annotated for Gemini CLI context awareness.
-->

### 🔄 Project Awareness & Context
- **Always read `PLANNING.md`** at the start of a new Gemini CLI session to load the project’s architecture, goals, style, and constraints.
  ```bash
  gemini context load PLANNING.md
  ```
- **Check `TASK.md`** before beginning a new task:
  ```bash
  gemini context list-tasks
  ```
  If the task isn’t listed, add it with:
  ```bash
  gemini context add-task "YYYY-MM-DD: Task description"
  ```
- **Maintain consistency** with naming conventions, file structure, and architecture from `PLANNING.md`.
- **Activate the virtual environment** before any Python execution:
  ```bash
  source venv_linux/bin/activate
  ```

### 🧱 Code Structure & Modularity
- **Never create a file longer than 500 lines of code.**
  - Use modularization to split logic into smaller, reusable components.
- **Organize code into clearly separated modules**, grouped by feature or responsibility. For AI agents:
  ```
  agent.py    # Main agent logic
  tools.py    # Reusable tools
  prompts.py  # System prompts and context
  ```
- **Use clear, consistent imports** — prefer relative imports within packages.
- **Load environment variables** using:
  ```python
  from dotenv import load_dotenv
  load_dotenv()
  ```

### 🧪 Testing & Reliability
- **Always write Pytest unit tests** for each new function, class, or route.
- **Check and update existing tests** when changing logic.
- **Tests must live in a `/tests` folder**, mirroring the structure of the main application:
  - Include:
    - ✅ 1 expected use case
    - ⚠️ 1 edge case
    - ❌ 1 failure case
- Run tests using:
  ```bash
  pytest tests/
  ```
  Or automate with:
  ```bash
  gemini context test-all
  ```

### ✅ Task Completion
- **Mark tasks as complete** in `TASK.md` when finished:
  ```bash
  gemini context complete-task <task-id>
  ```
- **Add sub-tasks** discovered during development to the "Discovered During Work" section:
  ```bash
  gemini context add-subtask "Subtask description"
  ```

### 📎 Style & Conventions
- **Language**: Python (default project language)
- **Style**: Follow PEP8, use type hints, and format with `black`:
  ```bash
  black . && flake8 .
  ```
- **Validation**: Use `pydantic` for defining schemas and validating inputs.
- **Frameworks**:
  - Use `FastAPI` for API routing.
  - Use `SQLAlchemy` or `SQLModel` for ORM.
- **Docstrings**: Use Google style for function documentation:
  ```python
  def example():
      """
      Brief summary.

      Args:
          param1 (type): Description.

      Returns:
          type: Description.
      """
  ```

### 📚 Documentation & Explainability
- **Update `README.md`** whenever new features are added, dependencies change, or setup instructions are modified:
  ```bash
  gemini context update-readme
  ```
- **Comment non-obvious code** to make it accessible to mid-level developers.
- **Add `# Reason:` comments** in complex logic to clarify why the logic exists.

### 🧠 AI Behavior Rules
- ✅ **Do not assume missing context. Ask questions when uncertain.**
- 🚫 **Do not hallucinate libraries or functions** — only use known, documented Python packages.
- 📂 **Confirm file paths and module names** exist before referencing.
- 🔒 **Do not delete or overwrite existing code** unless instructed via `TASK.md` or explicitly requested in a PRP.

---
