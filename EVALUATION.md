# AlphaYou MCP evaluation

Verified November 5, 2026. No credentials, customer records or live research payloads are included here.

## Connect

- Public research: `https://alphayou.net/api/mcp/market`, no key; 19 tools. Claude-tagged requests add one fund scoreboard and six starter prompts.
- Keyed API: `https://api.alphayou.net/api/v1/mcp`, `Authorization: Bearer YOUR_KEY`. Create your own key at the developer page linked in README. Free has 4 tools; API Pro has 9. API Pro is separate from the consumer plan.
- Streamable HTTP; protocol negotiation verified at `2025-11-25`. Discover inputs with `tools/list`; do not guess tool arguments.

## Positive checks

1. Initialize and list tools. Expect 4 for a Free key, 9 for Pro. The public connector has a different catalog.
2. Ask the keyed `alphayou_search_datasets` tool for paths, costs and coverage. Discovery costs zero daily units.
3. Read company disclosures for NVDA with a bounded time window. Expect dated records with original links when available, or an explicit empty result. Do not invent filings.
4. Read reported insider trades. Preserve transaction dates, filing dates and source links; a reported sale is not evidence of a short position.
5. With Pro, read a fund book, changes and ticker holders. Preserve quarter-end and filing dates. These are reported holdings, not live trades.
6. With Pro, read the tracked Hyperliquid trader cohort. Preserve venue, observation time, coverage and methodology. A trader return is not a follower return.
7. Check HTTP quota headers after a hosted tool call. `X-RateLimit-*` describes daily request units; `X-BurstLimit-*` describes the transport ceiling. Detailed fund reads cost 3 units.
8. Ask `GET /api/mcp/whoami` on `api.alphayou.net` for effective plan, catalog, costs, scope and concurrency. Free is 100 units/day across account keys; Pro is 50,000/day/key. Reset: midnight UTC.

## Negative checks

- A Free key calling a Pro REST dataset returns 403. Its MCP catalog omits Pro tools.
- A revoked key returns 401. Never use another user's key for this test.
- A minute-limit refusal returns 429 with retry guidance and does not consume daily units. Respect Retry-After; do not load-test the public service.
- Unsupported inputs should return validation errors or clear coverage limits, never fabricated data.
- Execution, signing, funding, copy trading, alert creation and personalized investment advice are outside these MCP surfaces.

## Evidence and limits

The owner audit passed 39 SDK tool calls across hosted MCP, npm 0.1.1 and the 0.1.2 candidate. After release, Free/Pro catalogs, daily quota headers, 1/3-unit costs and key revocation passed again. Local regression fixtures cover credential redirects, stalled requests, quota errors and billing state transitions.

Native Perplexity, Cursor and Antigravity installation has not been verified. A real paid Stripe checkout was not performed. Functional tests establish neither a latency SLA nor load capacity. Public data may be delayed, amended, empty or unavailable.
