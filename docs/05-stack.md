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

## The decisions behind that table

### Why the ledger is append-only

**What it does.** States are recorded, never overwritten, so the run is safe to repeat and yesterday's belief about a record survives today's correction.

**What was turned down.** Updating the row in place. A smaller store and a simpler query — and an overwrite destroys the evidence of what was believed before it, which in a financial process is the thing an auditor asks for.

**What that costs.** The store grows, and every read has to ask for the latest state rather than selecting one current row.

### Why an unmatched record is held rather than guessed at

**What it does.** Matching is by ID and amount inside a window. Anything outside it is held for a person.

**What was turned down.** Fuzzy matching, to push the automatic rate higher. It would clear more records per run, and a wrong match on money produces false confidence — which is worse than no automation, because nobody goes looking for it.

**What that costs.** A real queue of held records that somebody has to work through. Tolerance rules for fees and FX are configured rather than learned, so a new payment method or a fee change needs the rule updated by hand.

### Why it is self-hosted rather than on an automation cloud

**What it does.** n8n in Docker on a VPS the client controls. No financial data crosses a third-party automation platform.

**What was turned down.** A hosted SaaS. Far less to operate — and order and payout data then transits a vendor, and the failure handling can only ever be as good as what that vendor chooses to expose.

**What that costs.** The client owns uptime, backups and upgrades. Built for one Shopify store against one Stripe account; multiple stores would need a tenant key on every ledger row.

## The rule that applies to all of them

**Nothing that only one person can operate.** A system that depends on the engineer who built it is a liability for the client, however well it runs on the day it is handed over. Every choice above had to survive that test before the technical merits mattered at all.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
