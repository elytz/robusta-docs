# Payroll Runs — deep-dive

**Status: TODO.** This page is a stub. The parent section [payroll.md](../payroll.md) has the field tables, lifecycle, and gotchas for the Runs screen. This deep-dive will cover:

- The full **calc → approve → mark-paid** lifecycle with worked numbers (one assignment, one element classification chain, one retropay scenario).
- How element-entry effective-dating interacts with the run period.
- Retropay: what triggers it, what it back-fills, what it doesn't.
- Balance integrity: YTD balances, current-period balances, payslip totals.
- Fast Formula evaluation order across classifications (Earnings → Pre-Tax Deductions → Taxes → Post-Tax Deductions → Net).
- Failure recovery: what happens if calc throws mid-run, what cleanup is required.
- GL posting on mark-paid (sub-ledger postings for net pay, employer cost, tax liability).

Until this lands, refer to [payroll.md](../payroll.md#payroll-runs) for the operational surface.
