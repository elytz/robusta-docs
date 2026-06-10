# Bank Reconciliation — deep-dive

**Status: TODO.** This page is a stub. The parent section [cash-bank.md](../cash-bank.md#bank-reconciliations) has the field tables, lifecycle, and gotchas for Bank Reconciliations. This deep-dive will cover:

- Statement import: file format (BAI2 / CAMT.053 / CSV), parsing, idempotency on `(tenant, bank_account, statement_number)`.
- Auto-match rules: how `reconciliation_rules` are evaluated in priority order, the rule predicate language (amount-equal / amount-tolerance / date-window / memo-regex / reference-exact).
- Manual match: one-to-one, one-to-many, many-to-one splits.
- Unmatched bucket: what stays here vs. what moves to "to be created" suggestions.
- Completing a reconciliation: book-vs-statement variance, the manual adjusting journal, the lock that prevents post-complete edits.
- Outstanding items report: stale uncleared checks, deposits-in-transit.

Until this lands, refer to [cash-bank.md](../cash-bank.md) for the operational surface.
