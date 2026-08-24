# 01 · The problem

**PayBridge** — E-commerce business on Shopify + Stripe

---

An e-commerce finance team was closing their books by hand every month — days of cross-referencing exported spreadsheets and manual lookups.

The cost was not only the days. Partial refunds, currency conversion adjustments and the occasional failed payout are easy to miss in a manual process, so real revenue could go unaccounted for with nobody noticing until much later, if at all.

Financial reconciliation has no tolerance for “close enough”. A job that is mostly accurate on money is worse than no automation, because it creates false confidence.

## Why it was not solved already

Every business in this position has already tried the obvious answers: a shared inbox, a spreadsheet, a rule in an off-the-shelf tool, a reminder to be more careful. Those work until volume grows or someone is on holiday.

The gap is not effort. It is that the process lives in people's habits rather than in a system, so it degrades quietly and nobody can measure by how much.

## What the requirement actually was

Scheduled, rate-limit-aware pulls from both APIs feed a matching engine with tolerance rules for expected variance. Everything lands in an append-only ledger that is safe to re-run, and only genuine mismatches raise an alert.

---

[← README](../README.md) · [02 · The client journey →](02-journey.md)
