# Changelog

## 2.13.0 — July 2026

Current version on the hosted service (crm.studiomeyer.io): **37 tools**.

- **Agent-native tool surface** — 37 tools covering companies, contacts, deals, leads, notes, follow-ups, interactions, health scores, revenue analytics and an audit trail, plus a schema-discovery tool so an assistant can learn the data model instead of being told.
- **GDPR subject rights as tools, not tickets** — `crm_gdpr` handles Article 15 access export and Article 17 erasure, with a `dryRun` preview of the cascade before anything is removed. EU-hosted in Frankfurt.
- **Interactive in-chat dashboard** — `crm_dashboard` renders pipeline, MRR, health buckets and alerts directly in the conversation, with no separate login to check where things stand.
- **Safer deletes** — every delete accepts `dryRun: true` to preview exactly what would be removed, and snapshots the record into the audit log so it stays restorable.
- **Stripe revenue sync** — `crm_sync_stripe` reconciles revenue against Stripe.
- **Security and reliability hardening.** No action needed on your side.
- **German and English search stemming**, for DACH-market contact and company names.

Free tier: 50 companies and 200 contacts.

## 1.0.0

Initial public release.
