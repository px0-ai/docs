# px[0] Docs

The documentation site for [px0](https://px0.ai), the local-first CLI that turns a sentence into a workflow you can run, schedule, and edit. Published at [docs.px0.ai](https://docs.px0.ai).

The product source of truth is the [px0 CLI repository](https://github.com/px0-ai/px0).

## Running the docs locally

The Mintlify CLI is a dev dependency, so one install gets you everything (Node.js 18 or newer):

```bash
npm install
npm run dev          # serves http://localhost:3000
```

Pages are MDX files and navigation lives in `docs.json`; both hot-reload while the dev server is running.

Before opening a pull request:

```bash
npm run validate       # strict build check; fails on warnings
npm run broken-links   # every internal link resolves
npm run format         # format MDX files
```

## Structure

| Path | Contents |
| :--- | :--- |
| `index.mdx` | Introduction |
| `get-started/` | Installation, quickstart, core concepts |
| `workflows/` | Building, running, the file format, scheduling |
| `tools/` | Connections and the tool catalogue |
| `knowledge/` | The library, search and ask, retrieval backends |
| `guidelines/` | Guidelines, proposals, provenance and history |
| `runs/` | Browsing run records |
| `skills/` | Agent skills and compiled guideline bundles |
| `reference/` | CLI, configuration, store, troubleshooting, updating |

Conventions for writing these pages — terminology, voice, and accuracy rules — are in [AGENTS.md](AGENTS.md).

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
