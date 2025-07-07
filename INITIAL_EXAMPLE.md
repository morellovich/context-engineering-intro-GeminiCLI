<!--
  INITIAL_EXAMPLE.md optimized for Gemini CLI:
  - Clear, user-friendly feature description with context
  - References to examples/ folder with guidance on usage
  - Documentation link formatted with summary
  - Detailed other considerations with setup tips
  - REMBER TO DELETE BEFORE RUNNING THE CLI
-->

## FEATURE:
Define a Pydantic-based AI agent system with the following capabilities:

- **Primary Agent (ResearchAgent):** Queries the Brave API to gather research data on user-specified topics.
- **Secondary Agent (EmailDraftAgent):** Uses the output of ResearchAgent to generate a Gmail-compatible draft email.
- **CLI Integration:** Provide commands to invoke each agent:
  - `gemini context execute-agent ResearchAgent --query "<topic>"`
  - `gemini context execute-agent EmailDraftAgent --template "<template_name>"`
- **API Integrations:** Authenticate with Gmail API for sending drafts and Brave API for research calls, using environment variables loaded via python-dotenv.

## EXAMPLES:
In the `examples/` folder, use these samples for inspiration (do **not** copy line-for-line):

- `examples/cli.py` — Demonstrates how to parse arguments with `argparse` and structure subcommands for agent execution.
- `examples/agent/` — Contains Pydantic agent definitions showing:
  - Provider and LLM abstractions
  - Tool registration on agents
  - Dependency injection for agent-to-agent communication

## DOCUMENTATION:
- **Pydantic AI Docs:** https://ai.pydantic.dev/ — Guides on defining Pydantic-based AI agents, tooling patterns, and model configuration.

## OTHER CONSIDERATIONS:
- **Environment Setup:**
  - Include a `.env.example` listing variables: `GMAIL_API_KEY`, `BRAVE_API_KEY`, and any OAuth settings.
  - Use `python-dotenv` with `load_env()` to load credentials.
- **README Instructions:**
  - Add a setup section explaining Gmail OAuth configuration and Brave API onboarding steps.
  - Document project structure and how to run each `gemini context execute-agent` command.
- **Testing Tips:**
  - Mock API calls in tests using pytest’s `monkeypatch` to simulate Gmail and Brave responses.
  - Ensure CLI outputs valid JSON for downstream parsers or logging systems.
