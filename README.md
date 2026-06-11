# hvilkenAI MCP Server

[![Glama Quality Score](https://glama.ai/mcp/servers/erorund/hvilkenai-mcp/badge)](https://glama.ai/mcp/servers/erorund/hvilkenai-mcp)

Daily Scandinavian AI language quality benchmark — Norwegian, Swedish, Danish.

## What this does

hvilkenAI benchmarks AI models daily on practical Scandinavian language tasks.
12+ models are tested every day, selected from a pool of over 350 AI models
available through OpenRouter. This MCP server lets AI assistants access
fresh benchmark data directly.

**Use cases:**
- "Which AI is best at Norwegian right now?"
- "Compare GPT-4o vs Claude on Swedish"
- "What's the cheapest model that handles Danish well?"
- "Show me how Gemini has performed this week"

## Available tools

### get_daily_benchmark
Get today's benchmark results for AI models on Scandinavian languages.

| Parameter | Type | Values | Default |
|-----------|------|--------|---------|
| `language` | string | `no`, `sv`, `da` | `no` |
| `tier` | string | `all`, `premium`, `midrange`, `budget` | `all` |

**Returns:** Model rankings with scores, pricing, and speed. Free tier returns yesterday's top 3; Pro returns today's full list.

### get_model_history
Track a specific model's performance over time.

| Parameter | Type | Values | Default |
|-----------|------|--------|---------|
| `model_name` | string | Model name or partial match, e.g. `"Claude Sonnet"`, `"GPT-4o"`, `"gemini"` | *(required)* |
| `language` | string | `no`, `sv`, `da` | `no` |
| `days` | number | 1–30 (free tier: max 3) | `7` |

**Returns:** Daily scores and trends for the specified model.

### get_orchestrator_ranking
Find the best model for AI agent orchestration and multi-agent systems.

| Parameter | Type | Values | Default |
|-----------|------|--------|---------|
| `language` | string | `no`, `sv`, `da` | `no` |

**Returns:** Models ranked by combined language quality and instruction-following ability.

### get_recommendation
Get a model recommendation tailored to your specific needs and budget.

| Parameter | Type | Values | Default |
|-----------|------|--------|---------|
| `use_case` | string | `writing`, `coding`, `research`, `agent`, `general` | `general` |
| `language` | string | `no`, `sv`, `da` | `no` |
| `budget` | string | `free`, `cheap`, `any` | `any` |

**Returns:** Best model match with reasoning. Pro tier returns top 3 with full details.

### get_weekly_summary
Get the weekly benchmark summary with trends and reliability analysis.

| Parameter | Type | Values | Default |
|-----------|------|--------|---------|
| `language` | string | `no`, `sv`, `da` | `no` |
| `week` | string | Format `YYYY-WW`, e.g. `"2026-21"` | current week |

**Returns:** Winner, most reliable model, and key observations for the week.

## Quick start

### Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "hvilkenai": {
      "type": "streamablehttp",
      "url": "https://mcp.hvilkenai.no/mcp"
    }
  }
}
```

Claude Desktop supports OAuth 2.1 — you will be prompted to connect with free or Pro access when you first use the server.

### Claude Code (CLI)

```bash
claude mcp add --transport http hvilkenai https://mcp.hvilkenai.no/mcp
```

### Cursor / VS Code

```json
{
  "mcpServers": {
    "hvilkenai": {
      "url": "https://mcp.hvilkenai.no/mcp"
    }
  }
}
```

### Direct API

```bash
curl -X POST https://mcp.hvilkenai.no/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","method":"tools/list","id":1}'
```

## Authentication

**Free tier** — no API key required:
- 24-hour delayed data
- Top 3 models per language
- 100 requests/hour

**Pro** — requires API key (Bearer token):
- Real-time data (updated daily at 07:30 CET)
- All models, all languages
- Historical data up to 30 days
- Higher rate limits

Get an API key at [hvilkenai.no/priser/](https://hvilkenai.no/priser/)

For Pro access, add your API key as a Bearer token:

```json
{
  "mcpServers": {
    "hvilkenai": {
      "type": "streamablehttp",
      "url": "https://mcp.hvilkenai.no/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## Example interaction

> **You:** Which AI model is best at Norwegian today?
>
> **Claude (using hvilkenAI):** Based on today's benchmark from hvilkenai.no,
> [model name] leads with a score of X.X, followed by...

## About the benchmark

- **Updated daily** at 07:30 CET
- **Three languages:** Norwegian (Bokmål), Swedish, Danish
- **Practical tasks:** Real-world language use, not academic tests
- **Broad coverage:** 12+ models selected daily from over 350 AI models
- **Independent:** No sponsorships, no affiliate deals
- **Proprietary methodology:** Scoring uses a proprietary weighting system

Data source: [hvilkenai.no](https://hvilkenai.no)

## Links

- **Website:** [hvilkenai.no](https://hvilkenai.no)
- **Glama:** [glama.ai/mcp/servers/erorund/hvilkenai-mcp](https://glama.ai/mcp/servers/erorund/hvilkenai-mcp)
- **Integrations page:** [hvilkenai.no/integrasjoner/](https://hvilkenai.no/integrasjoner/)
- **Server URL:** `https://mcp.hvilkenai.no/mcp`
- **Health check:** `https://mcp.hvilkenai.no/health`

## License

MIT
