# 04 · Failure handling

The part of the system that took the longest to build and gets written about the least.

---

| What goes wrong | How it is detected | What the system does | Who finds out |
| :--- | :--- | :--- | :--- |
| **Job re-run after a partial failure** | Idempotency key per transaction | Existing ledger entries are not written twice | Nothing to report — by design |
| **Shopify or Stripe rate-limits the pull** | API response code | Backoff and retry rather than a silent skip | Alert only if retries are exhausted |
| **Amounts differ by fees or FX** | Tolerance rules | Treated as expected variance, not flagged | Nobody — this is what avoids alert fatigue |
| **Chargeback or partial refund** | Match logic | Held and flagged as a genuine discrepancy | Finance team alerted with both records |
| **Payout missing entirely** | Unmatched order after the window | Held for review, never auto-reconciled | Finance team alerted |
| **Anything unanticipated** | Global error trigger | Halt before writing to the ledger | Alert with execution ID |

## The three rules behind that table

**1 — Fail closed, not open.** When the system cannot establish that an action is safe, it holds. A held item is a visible problem. An item processed on a guess is an invisible one.

**2 — Nothing disappears.** Anything that cannot be completed is recorded where a human can find it later, not dropped from the run.

**3 — Silence is a fault.** An empty result where results were expected is treated as a possible failure of the source, not as an absence of work. This is the check most automations skip.

---

[← 03 · Architecture](03-architecture.md) · [05 · The stack →](05-stack.md)
