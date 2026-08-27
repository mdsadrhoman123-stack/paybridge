# 02 · The journey

What this looks like from the outside, for **E-commerce businesses on Shopify + Stripe**.

---

### 01 — Nothing to do

The job runs on a schedule. No one exports a CSV.

### 02 — Every order is matched

Order and payout are paired by ID and amount, with fees and currency applied.

### 03 — Expected variance is ignored

Fees and FX differences do not become alerts. That is the difference between a useful system and a noisy one.

### 04 — Real problems surface

A chargeback, a partial refund or a missing payout is held and flagged with both records attached.

### 05 — The ledger is permanent

Every state change is appended. Nothing is overwritten, so last month can always be re-read.

### 06 — Re-running is safe

If the job is run again it will not double-count. This requirement shaped the whole build.

---

## The one decision that shaped everything else

Scheduled, rate-limit-aware pulls from both APIs feed a matching engine with tolerance rules for expected variance. Everything lands in an append-only ledger that is safe to re-run, and only genuine mismatches raise an alert.

---

[← 01 · The problem](01-problem.md) · [03 · Architecture →](03-architecture.md)
