# Documentation project instructions

## About this project

- This is the documentation site for [px0](https://px0.ai), built on [Mintlify](https://mintlify.com) and published at [docs.px0.ai](https://docs.px0.ai).
- Pages are MDX files with YAML frontmatter (`title`, `description`).
- Navigation and site configuration live in `docs.json`.
- The product source of truth is the [px0 repository](https://github.com/px0-ai/px0). When behaviour is ambiguous, read the CLI's `px0/` modules (`parser.py` for the command surface, `config.py` for settings, `workflow.py` for the file format, `doctor.py` for health checks) rather than guessing.
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP.
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP.

## What px0 is

px0 is a **local-first CLI**. You describe a recurring job in plain English and px0 writes it as a workflow you can run, schedule, and edit. Everything lives in one directory the user owns (`~/.px0` by default) as plain Markdown and TOML. There is no server, no account, and no hosted state.

Two things follow from that, and both matter when writing docs:

- **Never document a hosted service, an API endpoint, a dashboard, or a web console.** px0 has none. There is no SDK, no access key, and no HTTP API.
- **px0 has no model of its own.** It shells out to a coding agent CLI (`claude`, `gemini`, `pi`, `opencode`) and reuses that CLI's login. Never suggest that px0 stores a provider API key.

## Terminology

Use these terms consistently. They match the CLI's own vocabulary, where commands read as entity then verb (`px0 workflows new`, `px0 brain search`).

| Use | Not |
| :--- | :--- |
| store (the `~/.px0` directory) | project, workspace, database |
| workflow | job, task, automation, recipe |
| guideline | rule, instruction, style guide, memory |
| brain (the library, `brain/`) | knowledge, docs, corpus, notes, RAG store |
| run (one execution, with a record) | execution, invocation, job run |
| tool | connector, integration, action |
| toolkit / app (a Composio provider) | service, vendor |
| harness / model backend | LLM provider, model API |
| daemon (`px0d`, the scheduler) | cron job, worker, service |
| change (an atomic store-wide write, `px0 changes`) | commit, transaction |
| claim (an addressable guideline section, `<file>#<slug>`) | rule id, section |

Write `px0` in lowercase, including at the start of a sentence. `px[0]` is the brand mark and is used only in the site name and navigation.

## Style preferences

- Use active voice and second person ("you").
- Keep sentences concise - one idea per sentence.
- Use sentence case for headings.
- Bold for UI elements: Click **Settings**.
- Code formatting for file names, commands, paths, and code references.
- **Explain why, not just how.** px0 makes opinionated choices (guidelines are matched by name and never retrieved; write tools are surfaced everywhere; nothing is written to `guidelines/` without consent). A page that lists commands without the reasoning behind them is incomplete.
- **Be empathetic about failure.** Document what a failure looks like on screen and the concrete next step, not just the happy path. Prefer showing real CLI output over describing it.
- Use `<Note>` for useful asides, `<Tip>` for optional improvements, and `<Warning>` only for things that risk data or privacy.
- Do not use emoji. The CLI does not, and neither should the docs.

## Accuracy rules

- Every command, flag, config key, and default in the docs must exist in the CLI. Check `px0/parser.py` and `px0/config.py` before adding one.
- Sample CLI output should match the real thing, including its restrained formatting.
- In MDX, wrap template syntax and anything containing braces or angle brackets in backticks, or the parser will treat it as JSX.

## Content boundaries

- Do not document internal `.state/` file formats beyond what a user needs to interpret `px0 doctor` output.
- Do not document unreleased or half-wired settings as if they work. Where a config key exists but is not enforced (for example `connectors.provider`, `retrieval.rerank`), say so plainly.
- Do not invent Composio tool slugs. Curated tools are listed in `px0/tools.py`; discovered tools come from a live catalogue search and should be shown as examples only.
