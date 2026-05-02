<!-- studiomeyer-mcp-stack-banner:start -->
> **Part of the [StudioMeyer MCP Stack](https://studiomeyer.io)** — Built in Mallorca 🌴 · ⭐ if you use it
<!-- studiomeyer-mcp-stack-banner:end -->

# StudioMeyer CRM

**AI-native CRM as MCP Server. 33 tools, 3 resources, 3 prompts. No dashboard needed — your AI is the interface.**

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-io.studiomeyer%2Fcrm-blue)](https://registry.modelcontextprotocol.io/servers/io.studiomeyer/crm)
[![MCPize](https://img.shields.io/badge/MCPize-studiomeyer--crm-purple)](https://mcpize.com/mcp/studiomeyer-crm)
[![Glama](https://glama.ai/mcp/servers/studiomeyer-io/studiomeyer-crm/badges/score.svg)](https://glama.ai/mcp/servers/studiomeyer-io/studiomeyer-crm)

---

## What is this?

StudioMeyer CRM is a **headless contact server** built as an MCP server. Instead of clicking through a CRM dashboard, you talk to your AI assistant — it manages companies, contacts, deals, leads, follow-ups, and revenue analytics for you.

The only production-ready standalone MCP CRM on the market. Not a bridge to HubSpot or Salesforce — a complete CRM that lives inside your AI workflow.

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

## Tools (33)

### Core CRM (23)

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
| `crm_dashboard` | Pipeline + MRR + health + activity + alerts in one call |
| `crm_stats` | Aggregate metrics |
| `crm_sync_stripe` | Sync revenue data from Stripe |
| `crm_revenue_report` | MRR/ARR/growth by company and product |
| `crm_import` | Bulk CSV/JSON import (auto-maps DE+EN headers, dedup, dry-run) |
| `crm_export` | CSV/JSON export: contacts, companies, deals, leads |
| `crm_audit_log` | Audit trail: who changed what, when |
| `crm_connect` | Zero-knowledge credentials: configure integrations via browser |

### Management (5 Delete Tools)

| Tool | Description |
|------|-------------|
| `crm_company_delete` | Hard-delete company + cascaded data |
| `crm_contact_delete` | Hard-delete contact |
| `crm_deal_delete` | Hard-delete deal |
| `crm_note_delete` | Hard-delete note |
| `crm_lead_delete` | Hard-delete lead |
| `crm_follow_up_delete` | Hard-delete follow-up |

### System (5)

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
| Tools | 33 | ~10 | ~8 | ~5 |
| MCP-native | Yes | Wrapper | Wrapper | Yes |
| Pipeline + Deals | Yes | Via HubSpot | Via Pipedrive | No |
| Lead Management | Yes | Via HubSpot | Via Pipedrive | No |
| Follow-ups | Yes | No | No | No |
| CSV Import/Export | Yes | No | No | No |
| Revenue Analytics | Yes | Via HubSpot | Via Pipedrive | No |
| Health Scores | Yes | No | No | No |
| Audit Log | Yes | No | No | No |
| Built-in Guide | 12 topics | No | No | No |
| Stripe Sync | Yes | No | No | No |
| Zero-Knowledge Creds | Yes | No | No | No |
| Hosted MCP | Yes | No | No | No |

---

## Pricing

| Plan | Price | Included |
|------|-------|----------|
| **Free** | $0/mo | 33 tools, 200 calls/day, 1 user |
| **Pro** | $29/mo | 33 tools, 10K calls/day, priority support |
| **Team** | $49/mo | 33 tools, unlimited, 5 users, shared pipeline |

---

## Security

- **Magic Link Authentication** — email verification on every sign-in. No passwords stored. You receive a single-use link that expires in 10 minutes. Nobody can access your data without proving email ownership.
- **OAuth 2.1** with PKCE S256 (RFC 8414, 7591, 9728, 7009)
- **Database:** Supabase EU (Frankfurt, Germany), SOC 2 Type II
- **Multi-tenant:** Shared-table isolation with Row Level Security
- **Zero-Knowledge Credentials:** AES-256-GCM encryption, browser-based entry
- **Input Validation:** Zod schemas on all 33 tools
- **Audit Log:** Every mutation tracked with tenant isolation

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