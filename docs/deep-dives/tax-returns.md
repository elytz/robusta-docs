# Tax Returns — deep-dive

**Status: TODO.** This page is a stub. The parent section [finance.md → Tax Returns](../finance.md#tax-returns) has the field tables, lifecycle, and gotchas for Tax Returns. This deep-dive will cover:

- The full **period → compute → file** flow with worked numbers (one regime, one period, mixed output/input/recoverable scenarios).
- The **confirm-zero gate**: why filing a literally-zero return needs explicit confirmation, and what the audit trail captures.
- Recovery percentages: how `tax_recovery_rates` interacts with input tax, the 100% fallback warning.
- E-invoicing linkage: why compute reads invoice lines (not e_invoice_documents) and what that means for IRN-failed transactions.
- Multi-regime tenants: filing one return per regime, period UNIQUE, post-file lock interplay with `accounting_periods`.
- File-once + cancel-recreate recovery: the only path to undo a wrongly-filed return.

Until this lands, refer to [finance.md → Tax Returns](../finance.md#tax-returns) for the operational surface.
