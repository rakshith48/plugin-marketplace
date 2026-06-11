# Firecrawl

Turn any website into clean, LLM-ready markdown or structured data — search,
scrape, crawl, map, and extract live web data directly from Grok Build.

This plugin offers **two interchangeable paths** to Firecrawl:

1. **CLI skills** — wrap the [Firecrawl CLI](https://github.com/firecrawl/cli)
   (`firecrawl search|scrape|map|crawl|interact|monitor|download|parse`). Best
   for large or long-running jobs and for writing results to `.firecrawl/`
   files to keep the context window clean.
2. **MCP server** — the bundled `firecrawl` MCP server (`.mcp.json`) exposes
   `firecrawl_search`, `firecrawl_scrape`, `firecrawl_map`, `firecrawl_crawl`,
   and `firecrawl_extract` as native tools. Best for single, in-context
   operations with zero shell-out.

The agent picks the right path automatically (see the `firecrawl-mcp` skill).

## Setup

Get a free API key at <https://firecrawl.dev/app/api-keys>, then:

```bash
export FIRECRAWL_API_KEY=fc-YOUR-API-KEY
```

### MCP server

The MCP server runs via `npx -y firecrawl-mcp` and reads `FIRECRAWL_API_KEY`
from the environment (see `.mcp.json`). No separate install step is required.

To use the **hosted remote** server instead of a local process (key in URL, no
install):

```
https://mcp.firecrawl.dev/YOUR_API_KEY_HERE/v2/mcp
```

### CLI

The CLI skills require the Firecrawl CLI installed globally:

```bash
npm install -g firecrawl-cli
firecrawl login --browser        # or: firecrawl login --api-key "fc-YOUR-API-KEY"
firecrawl --status               # verify auth, concurrency, credits
```

## Components

- **Skills:** `firecrawl`, `firecrawl-mcp`, plus per-capability skills
  (search, scrape, map, crawl, agent, interact, monitor, parse, download).
- **MCP server:** `firecrawl` (stdio via `npx -y firecrawl-mcp`).
- **Command:** `/skill-gen <docs-url>` — generate an Agent Skill from docs.

## Links

- Docs: <https://docs.firecrawl.dev/>
- CLI: <https://github.com/firecrawl/cli>
- MCP server: <https://github.com/firecrawl/firecrawl-mcp-server>
- Claude Code plugin (upstream source for these skills):
  <https://github.com/firecrawl/firecrawl-claude-plugin>

Licensed under AGPL-3.0, consistent with Firecrawl's open-source license.
