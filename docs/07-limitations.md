# 07 · Limitations

Written by the person who made the trade-offs.

---

- Built for one Shopify store against one Stripe account. Multiple stores would need a tenant key on every ledger row.

- Tolerance rules for fees and FX are configured, not learned. A new payment method or a fee change needs the rule updated.

- Matching is by ID and amount within a window. Deliberately conservative — an unmatched record is held rather than guessed at.

## On reading this section

A limitations section is not a disclaimer. It is the fastest way to tell whether a system was designed or assembled. Every one of the constraints above was a decision with a reason behind it, and each one could be lifted — at a cost that was not worth paying for this client's actual problem.

If your situation makes a different trade the right one, that is a conversation worth having.

---

[← 06 · Results](06-results.md) · [README](../README.md)
