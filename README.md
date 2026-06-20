<!-- studiomeyer-mcp-stack-banner:start -->
> **Part of the [StudioMeyer MCP Stack](https://studiomeyer.io)** — Built in Mallorca 🌴 · ⭐ if you use it
<!-- studiomeyer-mcp-stack-banner:end -->

# StudioMeyer CRM

[![smithery badge](https://smithery.ai/badge/cod-gb2l/StudioMeyer-CRM)](https://smithery.ai/servers/cod-gb2l/StudioMeyer-CRM)

**AI-native CRM as MCP Server. 37 tools, 3 resources, 3 prompts, and an interactive in-chat dashboard. No separate dashboard to log into — your AI is the interface.**

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-io.studiomeyer%2Fcrm-blue)](https://registry.modelcontextprotocol.io/servers/io.studiomeyer/crm)
[![MCPize](https://img.shields.io/badge/MCPize-studiomeyer--crm-purple)](https://mcpize.com/mcp/studiomeyer-crm)
[![Glama](https://glama.ai/mcp/servers/studiomeyer-io/studiomeyer-crm/badges/score.svg)](https://glama.ai/mcp/servers/studiomeyer-io/studiomeyer-crm)

---

## A note from us

We have been building tools and systems for ourselves for the past two years. The fact that this repo is small and has few stars is not because it is new. It is because we only just decided to share what we have built. It is not a fresh experiment, it is a long story with a recent commit.

We love building things and sharing them. We do not love social media tactics, growth hacks, or chasing stars and followers. So this repo is small. The code is real, it gets used, issues get answered. Judge for yourself.

If it helps you, sharing, testing, and feedback help us. If it could be better, an issue is more useful. If you build something with it, tell us at hello@studiomeyer.io. That genuinely makes our day.

From a small studio in Palma de Mallorca.

## What is this?

StudioMeyer CRM is a **headless contact server** built as an MCP server. Instead of clicking through a CRM dashboard, you talk to your AI assistant — it manages companies, contacts, deals, leads, follow-ups, and revenue analytics for you. When you want to *see* the pipeline, it renders an interactive dashboard right inside the chat.

A production-ready, **EU-hosted, GDPR-native** standalone MCP CRM. Not a bridge to HubSpot or Salesforce — a complete CRM that lives inside your AI workflow, with subject-rights (Art. 15 / Art. 17) built in as tools.

---

## Quick Start

### Option 1: Claude Desktop / Cowork

Add the server URL in Claude Desktop settings:

```
https://crm.studiomeyer.io/mcp
```

You'll receive a sign-in link via email to verify your identity — no passwords needed.

### Option 2: Claude Code

```bash
claude mcp add crm --transport streamable-http https://crm.studiomeyer.io/mcp
```

### Option 3: Cursor / VS Code / Windsurf / Zed

```bash
npx mcp-remote https://crm.studiomeyer.io/mcp
```

### Option 4: MCPize

```
https://mcpize.com/mcp/studiomeyer-crm
```

Subscribe and connect via the MCPize gateway.

---

## Tools (37)

### Discovery & insight

| Tool | Description |
|------|-------------|
| `crm_schema` | The CRM's own schema — entities, required-for-create fields, valid enums, relations. Call it before writing so the AI uses the right shape instead of guessing. |
| `crm_attention` | "What should I act on?" — overdue follow-ups, stale deals, deals missing a value, unconverted hot leads, each with a recommended next step. |

### Core CRM

| Tool | Description |
|------|-------------|
| `crm_company` | Create, get, or update a company |
| `crm_list_companies` | List companies with filters, pagination, sorting |
| `crm_contact` | Add or update contacts |
| `crm_list_contacts` | List contacts with filters |
| `crm_deal` | Create or update deals (auto-probability by stage) |
| `crm_list_deals` | List deals with filters |
| `crm_get_pipeline` | Pipeline view: deals by stage, forecast, MRR/ARR |
| `crm_log_interaction` | Log emails, calls, meetings (auto-updates lastInteractionAt) |
| `crm_get_timeline` | Chronological timeline of interactions + notes |
| `crm_add_note` | Add notes to companies or deals |
| `crm_list_notes` | List notes with filters |
| `crm_lead` | Ingest, list, update, or convert leads (auto-dedup, temperature detection) |
| `crm_follow_up` | Create, list, or complete follow-ups with priority and overdue tracking |
| `crm_search` | Full-text search across all entities (German + English stemming) |
| `crm_health_scores` | Health scores 0-100 with factor breakdown |
| `crm_dashboard` | Pipeline + MRR + health + activity + alerts in one call — renders the in-chat dashboard widget |
| `crm_stats` | Aggregate metrics |
| `crm_sync_stripe` | Sync revenue data from Stripe |
| `crm_revenue_report` | MRR/ARR/growth by company and product |
| `crm_record_revenue` | Record monthly revenue per company/product |
| `crm_import` | Bulk CSV/JSON import (auto-maps DE+EN headers, dedup, dry-run) |
| `crm_export` | CSV/JSON export: contacts, companies, deals, leads |
| `crm_audit_log` | Audit trail: who changed what, when (with a `since` filter for change-tracking) |
| `crm_connect` | Zero-knowledge credentials: configure integrations via browser |

### Compliance (GDPR / DSGVO)

| Tool | Description |
|------|-------------|
| `crm_gdpr` | Subject rights by natural language — **Art. 15** access export (the full record held for a data subject) and **Art. 17** erasure (preview the cascade with `dryRun`, then erase), logged for the compliance trail |

### Management — delete (with `dryRun` safety)

Every delete accepts `dryRun: true` to preview exactly what would be removed (including cascade) before you confirm. Deletes also snapshot the record into the audit log, so they are forensically restorable.

| Tool | Description |
|------|-------------|
| `crm_company_delete` | Hard-delete company + cascaded data |
| `crm_contact_delete` | Hard-delete contact |
| `crm_deal_delete` | Hard-delete deal |
| `crm_note_delete` | Hard-delete note |
| `crm_lead_delete` | Hard-delete lead |
| `crm_follow_up_delete` | Hard-delete follow-up |
| `crm_interaction_delete` | Hard-delete a logged interaction |

### System

| Tool | Description |
|------|-------------|
| `crm_guide` | Interactive onboarding with 12 topics |
| `crm_handoff` | Task queue between Claude Code and Cowork |
| `server_status` | Server health and configuration |

### Resources (3)

| Resource | Description |
|----------|-------------|
| `crm://pipeline` | Current pipeline state |
| `crm://dashboard` | Dashboard overview |
| `crm://follow-ups` | Pending follow-ups |

### Prompts (3)

| Prompt | Description |
|--------|-------------|
| `client-review` | Weekly client review |
| `daily-briefing` | Morning briefing with priorities |
| `pipeline-forecast` | Revenue forecast |

Every tool returns **structured output** (`structuredContent`) alongside text, so hosts and the in-chat dashboard widget read typed results without re-parsing.

---

## Search

3-phase search cascade for maximum recall:

1. **Full-text search** with German stemming (tsvector + GIN index)
2. **Trigram fuzzy matching** with unaccent + word_similarity
3. **ILIKE prefix fallback**

Searches across companies, contacts, interactions, deals, notes, leads, and tags. Perfect for DACH market with umlaut support.

---

## What Makes This Different

| Feature | StudioMeyer CRM | HubSpot MCP | Pipedrive MCP | nxt3d/mcp-crm |
|---------|-----------------|-------------|---------------|---------------|
| Standalone CRM | Yes | Bridge only | Bridge only | SQLite PoC |
| Tools | 37 | ~10 | ~8 | ~5 |
| MCP-native | Yes | Wrapper | Wrapper | Yes |
| In-chat dashboard (MCP App) | Yes | No | No | No |
| Schema discovery tool | Yes | No | No | No |
| Pipeline + Deals | Yes | Via HubSpot | Via Pipedrive | No |
| Lead Management | Yes | Via HubSpot | Via Pipedrive | No |
| Follow-ups | Yes | No | No | No |
| CSV Import/Export | Yes | No | No | No |
| Revenue Analytics | Yes | Via HubSpot | Via Pipedrive | No |
| Health Scores | Yes | No | No | No |
| Audit Log | Yes | No | No | No |
| GDPR subject rights (Art. 15/17) | Yes | No | No | No |
| Safe deletes (dry-run preview) | Yes | No | No | No |
| Built-in Guide | 12 topics | No | No | No |
| Stripe Sync | Yes | No | No | No |
| Zero-Knowledge Creds | Yes | No | No | No |
| EU-hosted (Frankfurt) | Yes | US | US | self-host |
| Hosted MCP | Yes | No | No | No |

---

## Pricing

| Plan | Price | Included |
|------|-------|----------|
| **Free** | €0/mo | 37 tools, 200 calls/day, 1 user |
| **Pro** | €19/mo | 37 tools, 10K calls/day, priority support |
| **Team** | €39/mo | 37 tools, unlimited, 5 users, shared pipeline |

---

## Security

- **Magic Link Authentication** — email verification on every sign-in. No passwords stored. You receive a single-use link that expires in 10 minutes. Nobody can access your data without proving email ownership.
- **OAuth 2.1** with PKCE S256 (RFC 8414, 7591, 9728, 7009)
- **Database:** Supabase EU (Frankfurt, Germany), SOC 2 Type II
- **Multi-tenant:** Shared-table isolation enforced in the data layer, with a static CI gate that fails the build if a query forgets its tenant scope
- **GDPR / DSGVO:** EU data residency + Art. 15 access export and Art. 17 erasure as first-class tools
- **Zero-Knowledge Credentials:** AES-256-GCM encryption, browser-based entry
- **Input Validation:** Zod schemas on all 37 tools
- **Audit Log:** Every mutation tracked with tenant isolation; deletes snapshot the record for forensic restore

---

## Built by StudioMeyer

AI and design studio in Mallorca, working with clients worldwide. Building AI tools since 2024.

- [Website](https://studiomeyer.io)
- [CRM Landing Page](https://studiomeyer.io/en/services/crm)
- [Memory Server](https://memory.studiomeyer.io)
- [GEO Server](https://geo.studiomeyer.io)
- [Crew Server](https://crew.studiomeyer.io)

---

## About StudioMeyer

[StudioMeyer](https://studiomeyer.io) is an AI and design studio based in Palma de Mallorca, working with clients worldwide. We build custom websites and AI infrastructure for small and medium businesses. Production stack on Claude Agent SDK, MCP and n8n, with Sentry, Langfuse and LangGraph for observability and an in-house guard layer.

## License

MIT — see [LICENSE](LICENSE). This repository contains documentation only.
The CRM server is hosted at [crm.studiomeyer.io](https://crm.studiomeyer.io).
