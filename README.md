# hvilkenAI MCP Server

Daily Scandinavian AI language quality benchmark — Norwegian, Swedish, Danish.

## What this does

hvilkenAI benchmarks 12+ AI models daily on practical Norwegian, Swedish,
and Danish tasks. This MCP server lets AI assistants query our data directly.

## Connect

Add to your MCP client config:

```json
{
  "mcpServers": {
    "hvilkenai": {
      "url": "https://mcp.hvilkenai.no/mcp"
    }
  }
}
```

Or use with Claude Code:

```bash
claude mcp add hvilkenai --transport streamable-http https://mcp.hvilkenai.no/mcp
```

## Available tools

| Tool | Description |
|------|-------------|
| `get_daily_benchmark` | Today's benchmark results by language and tier |
| `get_weekly_summary` | Weekly winner, most reliable, key stats |
| `get_model_history` | Historical scores for a specific model |
| `get_orchestrator_ranking` | Combined ranking across all metrics |
| `get_recommendation` | Best model for your use case and budget |

## Example queries

Ask your AI assistant:
- "Which AI is best for Norwegian right now?"
- "Compare budget vs premium models on Scandinavian languages"
- "Show me GPT-5.4 Pro's history over the last 7 days"
- "What's the best free model for Danish customer service?"

## Data

- 12+ models tested daily at 07:30 CET
- Languages: Norwegian (bokmål), Swedish, Danish
- Metrics: language quality, instruction following, speed, cost
- Free tier: today's top 3 + weekly summary
- Pro tier: full history, all models, raw data (API key required)

## Links

- Website: [hvilkenai.no](https://hvilkenai.no)
- API docs: [hvilkenai.no/api](https://hvilkenai.no/api)
- Contact: erik@hvilkenai.no
