# Dayplan Briefing Feed — Open Macro & Business Intelligence for Humans & AI Agents

[![Daily Briefing](https://img.shields.io/badge/Update-Daily%2008%3A00%20CST-0f4c81)](https://dayplan.online/briefing/latest.html)
[![Access](https://img.shields.io/badge/Access-Free%20%26%20No%20API%20Key-117a43)](https://dayplan.online/briefing/latest.json)
[![llms.txt](https://img.shields.io/badge/Agent--Native-llms.txt-58a6ff)](https://dayplan.online/llms.txt)

Open-access, noise-reduced daily intelligence covering **macroeconomics, interest rates, energy & commodities, geopolitics, and tech/industry dynamics**, paired with an **immutable, verifiable forecast ledger** that tracks every published outlook against real-world outcomes.

> **Free & Public Read-Only Data** — No login, no API key, no paywall. Built to be cleanly consumed by both human readers (HTML) and AI agents / workflows (JSON, RSS, `llms.txt`).

---

## Quick Endpoints

| Format | URL | Best For |
|---|---|---|
| **Agent Guide (`llms.txt`)** | `https://dayplan.online/llms.txt` | Automatic discovery by AI agents |
| **Latest Briefing (JSON)** | `https://dayplan.online/briefing/latest.json` | Direct structured consumption (zero HTML overhead) |
| **All Editions Index (JSON)** | `https://dayplan.online/briefing/index.json` | Listing all published dates & headlines |
| **Specific Edition (JSON)** | `https://dayplan.online/briefing/data/YYYY-MM-DD.json` | Historical structured lookup |
| **Forecast Ledger (JSON)** | `https://dayplan.online/briefing/forecasts/data/index.json` | Full immutable forecast history & dated outcomes |
| **RSS 2.0 Feed** | `https://dayplan.online/briefing/feed.xml` | RSS readers, n8n/Zapier/MCP triggers |
| **Human Web Edition** | `https://dayplan.online/briefing/latest.html` | Clean web reading & forecast dashboard |
| **Forecast Dashboard** | `https://dayplan.online/briefing/forecasts/` | Live in-window & closed outlook tracker |

- **Update Schedule**: Daily at **08:00 CST (00:00 UTC)**
- **Language**: Simplified Chinese (`zh-CN`) with primary global sources

---

## Quick Start (3 Lines)

### cURL
```bash
curl -s https://dayplan.online/briefing/latest.json | jq '{date: .edition_date, headline, judgments: (.judgments | length), forecasts: (.forecasts | length)}'
```

### Python
```python
import urllib.request, json

data = json.loads(urllib.request.urlopen("https://dayplan.online/briefing/latest.json").read())
print(data["edition_date"], data["headline"])
for j in data["judgments"]:
    print(f"- [{j['domain']}] {j['title']}: {j['judgment']}")
```

---

## `latest.json` Schema Overview

Each daily edition JSON (`schema_version: "2.0"`) contains:

- `edition_date`, `coverage_start`, `coverage_end`, `published_at` — Exact time window (CST) and publication timestamp
- `headline`, `summary` — Executive summary of the day's primary market/macro shifts
- `judgments[]` — Core analytical judgments (`domain`, `title`, `judgment`, `public_basis`, `business_impact`, `source_ids`)
- `forecasts[]` — High-conviction, verifiable outlooks (`subject`, `horizon_start`, `horizon_end`, `verification_criterion`, `scenarios`, `primary_scenario_id`)
- `forecast_reviews[]` — Dated progress checks & final verdicts (`符合` / `部分符合` / `偏离` / `进行中` / `待核验`) on prior public forecasts
- `watchpoints[]`, `events[]`, `facts[]`, `sources[]` — Structured key figures, timelines, upcoming catalysts, and primary source URLs

---

## Principles

1. **Verifiable & Immutable Forecasts**: Original forecast subjects, horizons, probabilities, and verification criteria are never altered after publication. Subsequent checks are appended as dated events.
2. **Agent-Native by Default**: Clean HTML for search engines and human readers; clean JSON, RSS, and `llms.txt` for automated agents.

---

*For human browsing, start at [dayplan.online/briefing/](https://dayplan.online/briefing/).*
