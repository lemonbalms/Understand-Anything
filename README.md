# Understand Anything

An open-source tool that combines LLM intelligence with static analysis to help anyone understand any codebase — from junior developers to product managers.

## Current Status

**Phase 2 complete.** The core analysis engine, web dashboard, and Claude Code skill are all functional. The project includes fuzzy search, schema validation, staleness detection, layer auto-detection, and an interactive chat interface.

## Features

### Phase 1 — Foundation
- **Knowledge Graph** — Automatically maps your codebase into an interactive graph of files, functions, classes, and their relationships
- **Multi-Panel Dashboard** — Graph view, code viewer, chat, and learn panels in a workspace layout
- **Natural Language Search** — Search your codebase with plain English: "which parts handle authentication?"
- **Tree-sitter Analysis** — Accurate structural analysis for TypeScript, JavaScript (more languages coming)
- **LLM-Powered Summaries** — Every node gets a plain-English description of what it does and why

### Phase 2 — Intelligence
- **Fuzzy Search** — Fast, typo-tolerant search across all graph nodes via Fuse.js (SearchEngine in core)
- **Schema Validation** — Zod-based runtime validation when loading knowledge graphs, with detailed error messages
- **Staleness Detection** — Detects changed files via git diff and incrementally merges graph updates
- **Layer Auto-Detection** — Heuristic-based layer grouping (API, Service, Data, UI, Utility) with LLM refinement
- **`/understand-chat` Skill** — Ask questions about your codebase directly in the terminal via Claude Code
- **Dashboard Chat Panel** — Context-aware Q&A integrated into the web dashboard (Claude API)
- **Dagre Auto-Layout** — Automatic hierarchical graph layout for clean visualization
- **Layer Visualization** — Color-coded layer grouping with collapsible groups and a legend panel

## Quick Start

```bash
# Install dependencies
pnpm install

# Build the core package
pnpm --filter @understand-anything/core build

# Build the skill package
pnpm --filter @understand-anything/skill build

# Start the dashboard dev server
pnpm dev:dashboard
```

## Commands

| Command | Description |
|---------|-------------|
| `pnpm install` | Install all dependencies |
| `pnpm --filter @understand-anything/core build` | Build the core package |
| `pnpm --filter @understand-anything/core test` | Run core tests |
| `pnpm --filter @understand-anything/skill build` | Build the skill package |
| `pnpm --filter @understand-anything/skill test` | Run skill tests |
| `pnpm --filter @understand-anything/dashboard build` | Build the dashboard |
| `pnpm dev:dashboard` | Start dashboard dev server |

### Claude Code Skill

Once installed as a Claude Code skill, use the `/understand-chat` command to ask questions about your codebase directly in the terminal:

```
/understand-chat How does authentication work in this project?
/understand-chat What files are related to the payment system?
```

## Project Structure

```
packages/
  core/        — Analysis engine: types, persistence, tree-sitter, search, schema, staleness, layers
  dashboard/   — React + TypeScript web dashboard with chat panel
  skill/       — Claude Code skill (/understand-chat command)
```

## Tech Stack

- TypeScript, pnpm workspaces
- React 18, Vite, TailwindCSS
- React Flow (graph visualization)
- Monaco Editor (code viewer)
- Zustand (state management)
- tree-sitter (static analysis)
- Fuse.js (fuzzy search)
- Zod (schema validation)
- Dagre (graph layout)

## License

MIT
