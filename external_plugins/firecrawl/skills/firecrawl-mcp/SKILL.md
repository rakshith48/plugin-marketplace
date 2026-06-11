---
name: firecrawl-mcp
description: |
  Use the Firecrawl MCP server's native tools (firecrawl_search, firecrawl_scrape, firecrawl_map, firecrawl_crawl, firecrawl_extract) for live web data when they are available in this session. Prefer these MCP tools over the CLI when the result should come straight back into context (a single search, one page scrape, a quick extraction). Fall back to the firecrawl CLI skill for large or long-running jobs (bulk crawls, downloads to disk, scheduled monitors) and for output that should be written to .firecrawl/ files to keep context clean. Trigger whenever the user wants to search the web, scrape a URL, map a site, crawl docs, or extract structured data from pages.
---

# Firecrawl MCP

This plugin ships an MCP server (`firecrawl`) alongside the CLI skills. When the
MCP tools are connected, the agent has direct, in-context access to Firecrawl
without shelling out.

## Setup

The server is declared in this plugin's `.mcp.json` and runs via
`npx -y firecrawl-mcp`. It needs a Firecrawl API key in the environment:

```bash
export FIRECRAWL_API_KEY=fc-YOUR-API-KEY   # get one at https://firecrawl.dev/app/api-keys
```

Alternatively, point any MCP-capable client at the hosted remote server (no
local install, key in the URL):

```
https://mcp.firecrawl.dev/YOUR_API_KEY_HERE/v2/mcp
```

## MCP tools

| Tool | Use for |
| --- | --- |
| `firecrawl_search` | Web search with full-page content (web, news, images) |
| `firecrawl_scrape` | Clean markdown / structured data from one URL (JS-rendered) |
| `firecrawl_map` | Discover all URLs on a site |
| `firecrawl_crawl` | Bulk-extract a site section |
| `firecrawl_extract` | AI-powered structured extraction across pages |

## MCP vs CLI — which to use

- **MCP tools** — single search, one-page scrape, quick map/extract whose result
  should land directly in context. Lowest-friction path.
- **CLI skill (`firecrawl`)** — large or long-running work: full-site crawls,
  `download` to disk, scheduled `monitor`s, or any output you want saved under
  `.firecrawl/` to keep the context window clean. See the `firecrawl` skill.

Never run both for the same request. Pick one path and stay on it.
