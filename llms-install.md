# Installing the AlphaYou MCP server

AlphaYou is a hosted, keyless, read-only MCP server. Nothing needs to be cloned, built or run locally, and no API key is required.

Add this entry to the MCP settings file (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "alphayou": {
      "type": "streamableHttp",
      "url": "https://alphayou.net/api/mcp/market?utm_source=claude",
      "disabled": false
    }
  }
}
```

For clients that use the standard remote format:

```json
{
  "mcpServers": {
    "alphayou": {
      "type": "http",
      "url": "https://alphayou.net/api/mcp/market?utm_source=claude"
    }
  }
}
```

Check it works by asking: "Using AlphaYou, who is buying NVDA?" The answer should list dated rows with SEC or House Clerk source links.
