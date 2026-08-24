# 05 · The stack

Each choice, and the reason for it.

---

| Component | Why this one |
| :--- | :--- |
| **n8n** | Self-hosted — no financial data through a third-party automation cloud |
| **Shopify API** | Order side of the match |
| **Stripe API** | Payout side of the match |
| **PostgreSQL** | Append-only ledger: states are recorded, never overwritten |
| **Docker on a self-hosted VPS** | Reproducible deployment under the client's own control |

## What was deliberately not used

- **A hosted automation SaaS.** Client data would transit a third party, and the failure handling would be limited to what that vendor exposes.
- **A bespoke application where automation was enough.** The cheapest system to maintain is the one with the least custom code in it.
- **Anything that could not be redeployed by someone else.** A system only one person can operate is a liability for the client.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
