# 06 · Results

---

## Counted

| | |
| :--- | :--- |
| Workflow nodes | **38** |
| Ledger writes | **Append-only** |
| Safe to re-run | **Idempotent** |

These are counts from the built system: nodes, stages, versions, gates, retries. They are verifiable from the workflow itself.

## What changed in the process

| | Before | After |
| :--- | :--- | :--- |
| **Month-end close** | Days of manual spreadsheet work | Runs continuously in the background |
| **Discrepancy found** | Weeks later, if at all | Within hours of occurring |
| **Alert volume** | Everything looked like a mismatch | Only genuine mismatches surface |
| **Audit trail** | None | Append-only financial ledger |
| **Where the data lives** | Third-party cloud tools | Self-hosted, client-controlled |

## What is deliberately not claimed

No time-saved percentage, cost-reduction figure or throughput multiplier appears in this repository. Those numbers require a measured baseline and a measured after, over a stated period, on a stated definition. Where that measurement exists it will be published with its method. Where it does not, the number is not worth more than the process description above.

> An unsourced percentage in a portfolio is a claim the reader has to take on trust. A node count is a claim they can check.

---

[← 05 · The stack](05-stack.md) · [07 · Limitations →](07-limitations.md)
