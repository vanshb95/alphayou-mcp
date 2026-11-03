# AlphaYou MCP server

Smart money research for AI assistants and agents: insider trades (SEC Form 4), Congress stock trades, hedge fund 13F holdings, government contracts, financial creators and Hyperliquid top traders, plus SEC financials, earnings, US macro and CFTC positioning. Every answer carries its source link and date.

- **Server URL:** `https://alphayou.net/api/mcp/market?utm_source=claude`
- **Transport:** Streamable HTTP
- **Sign-in:** none. No account, no API key
- **Access:** read-only. It never signs, trades, copies a trader or sets alerts

<img src="logo.png" width="96" alt="AlphaYou logo">

## Add it

| Client | How |
|---|---|
| Claude | Install the [AlphaYou plugin](https://alphayou.net/connectors) from the Claude directory, or Settings > Connectors > Add custom connector and paste the URL |
| ChatGPT | Install [AlphaYou: Smart Money Intel](https://chatgpt.com/plugins/plugin_asdk_app_6aca22e01fd081918dde85b14c78f16d) from the plugin directory |
| Claude Code | `claude mcp add --transport http alphayou "https://alphayou.net/api/mcp/market?utm_source=claude"` |
| Gemini CLI | `gemini extensions install https://github.com/vanshb95/alphayou-mcp` |
| Cursor, VS Code, Windsurf, Cline | Add a remote server with the URL above (see `llms-install.md`) |
| Grok, Perplexity, Mistral Le Chat, Manus | Add a custom connector and paste the URL |

## What you can ask

- Who is buying NVDA, and what did insiders do this quarter?
- What did Pelosi buy?
- Which hedge funds hold TSLA, and what changed last quarter?
- Rank the top Hyperliquid traders by Sharpe and show what the best three hold.
- Brief me on NVDA's latest earnings, guidance and recent 8-K filings.
- What changed for NVDA and TSLA in the last 24 hours?

## Tools

Twenty read-only tools: `get_smart_money`, `get_smart_money_overlap`, `get_fund_scoreboard`, `get_stock_fundamentals`, `get_financial_quality`, `get_company_disclosures`, `get_company_earnings`, `get_earnings_calendar`, `get_macro_context`, `get_futures_positioning`, `search_hyperliquid_traders`, `analyze_hyperliquid_wallet`, `compare_hyperliquid_traders`, `get_hyperliquid_wallet_positions`, `get_hyperliquid_wallets_positions`, `get_hyperliquid_activity`, `get_hyperliquid_positioning`, `get_hyperliquid_market_state`, `resolve_hyperliquid_market`, `get_alphayou_capabilities`. Six starter prompts are served over MCP.

## How it answers

Missing data is reported as unknown, never as zero. A sale is a sale, not a short. Fund rows are quarter-end changes, not live trades. Stock-linked perpetuals are derivatives, not shares. Answers are the same for every user: no personal advice, sizing or buy and sell calls.

## Links

- Website: https://alphayou.net
- Connectors and support: https://alphayou.net/connectors
- Privacy: https://alphayou.net/legal/privacy
- Terms: https://alphayou.net/legal/terms
- Contact: info@alphayou.net

The files in this repository are MIT licensed. Use of the hosted server is governed by the AlphaYou terms.
