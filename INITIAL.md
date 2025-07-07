
## FEATURE:

Describe the feature you want Gemini CLI to implement in a single, actionable sentence.
Be precise: name flags, expected behavior, edge cases, and success criteria.
Example:
"Add a `--verbose` flag to the CLI that logs HTTP request/response details,
redacting sensitive headers, and exits with code 0 on success or 1 on failure."

[Insert your concise feature description here remember to remove all the text above]

## EXAMPLES:

Reference code samples in the examples/ folder that illustrate patterns Gemini should follow.
Include file paths and a brief note on what to emulate.

- `examples/cli_pattern.py` — shows standard argparse setup and subcommand handling
- `examples/error_handling.py` — demonstrates structured exception catching and exit codes

[Insert your examples here remember to remove all the text above]


## DOCUMENTATION:

List URLs or internal docs Gemini CLI may need for context.
Include a one-line summary of each resource.

- https://developers.google.com/ai/gemini/cli#commands — Official Gemini CLI reference
- https://company.internal/rag/docs — Internal RAG server API documentation

[Insert your documentation description here remember to remove all the text above]


## OTHER CONSIDERATIONS:

Mention special requirements, configuration, or common pitfalls.
Examples: authentication, rate limits, environment variables, test fixtures, formatting constraints.

- Ensure `API_TOKEN` is loaded from a `.env` file via python-dotenv
- All CLI output must be valid JSON for downstream parsing
- Tip: use pytest's `monkeypatch` to mock filesystem and network calls in CLI tests

[Insert your Other Considerations here remember to remove all the text above]

