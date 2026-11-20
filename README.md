<p align="center"><img src="assets/icon.svg" width="96" height="96" alt="Torhy"></p>

# Torhy

Search and analyze Ukrainian Prozorro and EU TED public tenders: notices, documents, award prices, alerts.

Torhy is a hosted [Model Context Protocol](https://modelcontextprotocol.io) server. There is nothing to
install: add the URL to your AI client and sign in.

```
https://torhy.com.ua/mcp
```

- Website: https://torhy.com.ua/en · Documentation: https://torhy.com.ua/en/docs
- Transport: Streamable HTTP · Authorization: OAuth 2.1 (dynamic client registration, PKCE)
- Sign-in: e-mail code, Google or GitHub. A free plan is available; plans and limits are on the website.

## Connect

**Claude (web, desktop, mobile).** Settings → Connectors → Add custom connector → paste the URL → Connect.
Step by step: https://torhy.com.ua/en/docs/connect-claude

**ChatGPT.** Settings → Apps & Connectors → add a connector with the URL (developer mode).
Step by step: https://torhy.com.ua/en/docs/connect-chatgpt

**Claude Code.**

```bash
claude mcp add --transport http torhy https://torhy.com.ua/mcp
```

**Cursor** (`~/.cursor/mcp.json` or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "torhy": { "url": "https://torhy.com.ua/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):

```json
{
  "servers": {
    "torhy": { "type": "http", "url": "https://torhy.com.ua/mcp" }
  }
}
```

Any other client that supports remote MCP servers with OAuth works the same way: give it the URL. The client
opens a sign-in window on first use.

## Tools

| Tool | Type | What it does |
| --- | --- | --- |
| `search_tenders` | read | Search open Prozorro tenders by keywords, CPV, region, buyer, budget, deadline |
| `get_tender` | read | Full tender: lots, criteria, deadlines, links |
| `get_tender_documents` | read | Text of the tender documents |
| `find_awards` | read | Completed procurements: winners, award values, discounts |
| `get_price_benchmark` | read | Unit-price distribution for a CPV code |
| `get_buyer_profile` | read | Procurement history of a buyer |
| `get_supplier_profile` | read | Wins and prices of a supplier |
| `lookup_cpv` | read | Find CPV / ДК 021 codes |
| `search_ted` | read | Search EU notices in TED |
| `get_ted_notice` | read | One TED notice by publication number |
| `get_company_profile` | read | Your company profile used for matching |
| `save_company_profile` | write | Save or replace the company profile |
| `create_alert` | write | Alert for new tenders that match filters |
| `update_alert` | write | Change an alert |
| `delete_alert` | write | Delete an alert |
| `list_alerts` | read | Your alerts |
| `list_alert_matches` | read | Tenders matched by alerts |
| `watch_tender` | write | Add a tender to the watch list |
| `unwatch_tender` | write | Remove a tender from the watch list |
| `list_watched_tenders` | read | Your watch list |
| `get_usage` | read | Current plan and remaining quota |

Write tools change only the data of the signed-in account and ask for confirmation in the client.

## Example requests

- "Find open Prozorro tenders for medical gloves in Lviv region"
- "Summarize the qualification requirements in tender UA-2026-…"
- "Who won similar CPV 45233000 tenders last year, and at what discount?"
- "Alert me about new IT services tenders from city councils"
- "Find TED notices for drone services in Poland and Lithuania"

## Data sources

Ukrainian tenders come from the public API of [Prozorro](https://prozorro.gov.ua) (synchronised every few
minutes). EU notices come from the [TED](https://ted.europa.eu) Search API (© European Union). Torhy does not
submit bids on your behalf.

## What is in this repository

| File | Purpose |
| --- | --- |
| `plugin.json`, `mcp.json` | [Agent Plugins](https://agent-plugins.org) package: listing metadata and the MCP server |
| `skills/get-started/SKILL.md` | onboarding skill for assistants that load skills |
| `server.json` | card of the [official MCP registry](https://registry.modelcontextprotocol.io) |
| `assets/` | icons |

The service itself is a hosted product and its source code is not part of this repository. The manifests and
documentation here are under the MIT license.

## Support and policies

- Support: support@torhy.com.ua · https://torhy.com.ua/en/contact
- Privacy policy: https://torhy.com.ua/en/legal/privacy · Terms: https://torhy.com.ua/en/legal/terms · Security: https://torhy.com.ua/en/security
- Questions and bug reports are welcome in the issues of this repository.

## Українською

Torhy — пошук і аналіз тендерів Prozorro та ЄС (TED) прямо в Claude, ChatGPT чи Cursor: пошук закупівель, тендерна документація, ціни переможців, сповіщення про нові тендери.

Підключення: додайте адресу `https://torhy.com.ua/mcp` як власний конектор у своєму ШІ-клієнті та увійдіть в обліковий запис.
Покрокові інструкції — https://torhy.com.ua/docs.

---

Built by [Bovsanka](https://bovsanka.com/en), a studio that automates business processes with AI.
