# Adaption Docs

An agent skill for answering questions and implementing workflows with Adaptive Data, AutoScientist, and the Adaption API.

The skill uses the open Agent Skills format. It has no dependency on a specific coding agent or editor.

## Install

Install interactively. The CLI detects supported coding agents on your machine and lets you choose the targets:

```bash
npx skills add huyxdang/Adaption-Docs
```

Inspect the repository without installing:

```bash
npx skills add huyxdang/Adaption-Docs --list
```

Install the skill globally for a specific agent:

```bash
npx skills add huyxdang/Adaption-Docs \
  --skill adaption-docs \
  --agent claude-code \
  --global
```

Replace `claude-code` with any name from the supported-agent list. To install the repository's skill for every detected agent:

```bash
npx skills add huyxdang/Adaption-Docs --all --global
```

The CLI supports Codex, Claude Code, Cursor, OpenCode, GitHub Copilot, Gemini CLI, Windsurf, and many other agents. See the [current supported-agent list](https://github.com/vercel-labs/skills#supported-agents) for agent names and install locations.

## Use

Invoke the skill explicitly as `$adaption-docs`, or ask your agent a question about Adaption, Adaptive Data, AutoScientist, or the Adaption API. Agents that support automatic skill selection can load it based on its description.

Examples:

```text
Use $adaption-docs to show me how to upload a local JSONL dataset and wait for ingestion.
```

```text
Use $adaption-docs to check the current AutoScientist parameters before writing this integration.
```

## What it does

- Starts with current official Adaption documentation instead of recalled API details.
- Routes Adaptive Data, AutoScientist, SDK, REST API, and documentation-source questions to the right source.
- Preserves API keys and requires authorization before launching credit-consuming jobs.
- Handles asynchronous ingestion, adaptation, training, and artifact downloads correctly.

## Repository layout

```text
skills/adaption-docs/
├── SKILL.md
├── ATTRIBUTION.md
└── references/
    └── official-docs.md
```

## License

This project is licensed under [CC BY 4.0](LICENSE). See the skill's [attribution notice](skills/adaption-docs/ATTRIBUTION.md) for the official Adaption sources used to create it.

Copyright © 2026 Adaption Docs contributors.

This is an unofficial community project. It is not affiliated with or endorsed by Adaption Labs.
