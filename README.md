<!--
  README.md optimized for Gemini CLI usage:
  - Renamed .claude to .gemini
  - Updated CLI commands to use `gemini context` prefix
  - Changed file references from CLAUDE.md to GEMINI.md
  - Adjusted examples and terminology from Claude Code to Gemini CLI
-->

# Context Engineering Template for Gemini CLI

A comprehensive template to jumpstart Context Engineering with Gemini CLI—ensuring your AI coding assistant has all the context needed for end-to-end feature implementation.

> **Context Engineering with Gemini CLI is 10x smarter than prompt engineering and 100x more reliable than vibe coding.**

## 🚀 Quick Start

```bash
# 1. Clone this template
git clone https://github.com/coleam00/context-engineering-intro-GeminiCLI.git
cd context-engineering-intro

# 2. Customize project guidelines (optional)
# Edit GEMINI.md to add your project-specific conventions

# 3. Add illustrative examples (highly recommended)
# Place relevant code samples in the examples/ folder

# 4. Define your initial feature request
# Edit INITIAL.md with detailed requirements

# 5. Generate a comprehensive PRP (Product Requirements Prompt)
# Using Gemini CLI, run:

gemini context generate-prp INITIAL.md

# 6. Execute the PRP to implement your feature
# Using Gemini CLI, run:

gemini context execute-prp PRPs/your-feature-name.md
```  

## 📚 Table of Contents

- [What is Context Engineering?](#what-is-context-engineering)
- [Template Structure](#template-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Writing Effective INITIAL.md Files](#writing-effective-initialmd-files)
- [The PRP Workflow](#the-prp-workflow)
- [Using Examples Effectively](#using-examples-effectively)
- [Best Practices](#best-practices)

## What is Context Engineering?

Context Engineering shifts the focus from single-shot prompts to a structured system of rules, examples, and validations:

### Prompt Engineering vs Context Engineering

**Prompt Engineering:**
- Crafting clever wording
- Limited to phrasing
- Like leaving a sticky note

**Context Engineering with Gemini CLI:**
- Full framework: docs, examples, rules, tests
- End-to-end feature pipelines
- Like directing a full movie production

### Why It Matters
1. **Fewer AI Failures**: Most issues stem from missing context, not model errors.
2. **Consistent Results**: Enforce your code style and patterns.
3. **Supports Complex Flows**: Multi-step features handled seamlessly.
4. **Automated Validation**: Built‑in tests and linting loops ensure quality.

## Template Structure

```text
context-engineering-intro/
├── .gemini/
│   ├── commands/
│   │   ├── generate-prp.md    # PRP generation logic
│   │   └── execute-prp.md     # PRP execution logic
│   └── settings.local.json    # Gemini CLI permissions
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md        # Base PRP template
│   └── EXAMPLE_multi_agent_prp.md  # Sample complete PRP
├── examples/                   # Your code examples (critical!)
├── GEMINI.md                   # Global project rules for Gemini CLI
├── INITIAL.md                  # Template for new feature requests
├── INITIAL_EXAMPLE.md          # Example feature request
└── README.md                   # This file (updated for Gemini CLI)
```  

<!-- Updated directory names and filenames to use Gemini CLI conventions -->

## Step-by-Step Guide

### 1. Define Global Rules (GEMINI.md)

`GEMINI.md` holds project‑wide conventions for your AI assistant:

- **Awareness**: Task and planning docs
- **Structure**: Module splits, file size limits
- **Testing**: Unit test templates, coverage thresholds
- **Style**: Language and formatting rules
- **Docs**: Docstring and commenting practices

Customize or use the template as‑is for your project needs.

### 2. Draft Your INITIAL.md

Describe your new feature:

```markdown
## FEATURE:
[Clear, detailed description]

## EXAMPLES:
[List example files and patterns]

## DOCUMENTATION:
[Links to API docs, schemas, guides]

## OTHER CONSIDERATIONS:
[Auth, rate limits, gotchas]
```

See `INITIAL_EXAMPLE.md` for guidance.

### 3. Generate the PRP

PRPs (Product Requirements Prompts) combine context, implementation steps, validation gates, and tests.

Run:
```bash
gemini context generate-prp INITIAL.md
```

The CLI will:
1. Parse your request
2. Analyze code patterns
3. Gather docs
4. Create `PRPs/your-feature-name.md`

### 4. Execute the PRP

After reviewing the generated PRP, implement it:
```bash
gemini context execute-prp PRPs/your-feature-name.md
```

The assistant will:
1. Load the PRP context
2. Plan steps
3. Implement code with validation
4. Run tests and linting
5. Iterate until success

## Writing Effective INITIAL.md Files

- **Be Explicit**: Include all requirements.
- **Reference Examples**: Show what to emulate.
- **Link Docs**: Provide URLs and resources.
- **Note Gotchas**: Auth, quotas, edge cases.

## The PRP Workflow

### generate-prp
1. Research codebase patterns
2. Fetch docs and quirks
3. Draft implementation blueprint
4. Embed validation gates

### execute-prp
1. Load PRP context
2. Create task list
3. Write and test code
4. Iterate on failures
5. Finalize feature

## Using Examples Effectively

Examples in `examples/` are critical:

- **Structure Patterns**: Modules, classes, functions
- **Testing**: Test file layouts, mocks, assertions
- **Integration**: API clients, DB connections
- **CLI**: Arg parsing, outputs, errors

## Best Practices

1. **INIT.md Clarity**: No assumptions—spell it out.
2. **Rich Examples**: More = better.
3. **Validation Gates**: Tests in PRPs.
4. **Leverage Docs**: Include all relevant links.
5. **Customize GEMINI.md**: Enforce standards.

## Resources

- [Gemini CLI Docs](https://developers.google.com/ai/gemini/cli)
- [Context Engineering Guide](https://www.philschmid.de/context-engineering)
