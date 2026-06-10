# Journal Entries — deep-dive

**Status: TODO.** This page is a stub. The parent section [gl.md](../gl.md#journal-entries) has the field tables, lifecycle, and gotchas for Journal Entries. This deep-dive will cover:

- Manual journals: balanced-debit/credit invariant, the 0.0001 epsilon, multi-currency handling.
- Auto-posted journals from sub-ledgers: how `gl_sub_ledger_postings` works, the `event_type` → `journal_template` mapping, idempotency on `(tenant, source_type, source_id)`.
- Recurring journals: cadence, copy-forward, end-of-life.
- Mass allocation: the allocation basis (head-count / square-footage / revenue-share), how the basis snapshot is taken, why allocations don't re-run when the basis changes.
- Reversal: how `is_reversal_of_id` lineage works, period-locked reversals.
- Period close interplay: what statuses block posting, the `permanently_closed` one-way door.

Until this lands, refer to [gl.md](../gl.md) for the operational surface.
