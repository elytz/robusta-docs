# ROBUSTA ERP — User Guide

Complete guide to using every screen in the ERP module. Mirrors the depth of the CRM user guide (the CRM guide), organised one file per **sidebar section** so it stays browseable and the in-app help links can deep-link to the exact screen via `#anchor`.

---

## How to use this guide

- **Looking for a specific screen?** Open the section file the screen lives under (the sidebar groups it the same way) and jump to its `#anchor`. E.g. Cycle Counts lives at [inventory.md#cycle-counts](./inventory.md#cycle-counts).
- **Need the deep workflow for something tricky?** Half a dozen flows are complex enough to deserve a standalone file — see [Deep-dives](#deep-dives) below.
- **Don't know where to start?** Each section file opens with a *Where do I begin?* paragraph that names the 2–3 screens to set up first.

Each screen entry follows the same shape so the guide reads predictably:

> **What it is** — one sentence + a realistic example
> **How records get created** — UI / API / import / auto-from-upstream
> **Fields** — what's required, what's auto, what's optional
> **Statuses / state machine** — when the screen has a lifecycle (mermaid diagram on the complex ones)
> **Actions** — list, view, create, update, delete, plus the screen-specific actions (e.g. *Submit for approval*, *Cancel*, *Generate*)
> **Examples** — 2–3 realistic walkthroughs
> **Gotchas** — multi-tenancy quirks, FOR UPDATE locks, idempotency rules — the things that are non-obvious

---

## Sections

| # | Section | File | Status |
|---|---|---|---|
| 1 | Framework &amp; Setup | [framework.md](./framework.md) | Ready |
| 2 | Items | [items.md](./items.md) | Ready |
| 3 | Inventory | [inventory.md](./inventory.md) | Ready |
| 4 | Procurement (P2P) | [procurement.md](./procurement.md) | Ready |
| 5 | Sales &amp; AR (O2C) | [sales-ar.md](./sales-ar.md) | Ready |
| 6 | Finance, Tax &amp; Master Data | [finance.md](./finance.md) | Ready |
| 7 | General Ledger | [gl.md](./gl.md) | Ready |
| 8 | Cash &amp; Bank | [cash-bank.md](./cash-bank.md) | Ready |
| 9 | HR | [hr.md](./hr.md) | Ready |
| 10 | Payroll | [payroll.md](./payroll.md) | Ready |
| 11 | Fixed Assets &amp; Maintenance | [fixed-assets.md](./fixed-assets.md) | Ready |
| 12 | Manufacturing | [manufacturing.md](./manufacturing.md) | Ready |
| 13 | Quality &amp; Compliance | [quality-compliance.md](./quality-compliance.md) | Ready |
| 14 | Reports &amp; Dashboards | [reports.md](./reports.md) | Ready |
| 15 | Service (contracts / tickets / visits / recurring) | [service.md](./service.md) | Ready |
| 16 | Multi-Entity &amp; Consolidation | [multi-entity.md](./multi-entity.md) | Ready |
| 17 | Platform (PDF, email, import/export, API keys, mobile, i18n) | [platform.md](./platform.md) | Ready |

All 17 sections cover every ERP page that ships today. The recent pass added **Tax Returns** ([finance.md](./finance.md#tax-returns)) and **E-Invoicing** ([platform.md](./platform.md#e-invoicing)) as new canonical sections, and added pointer stubs from [sales-ar.md → Recurring Invoices](./sales-ar.md#recurring-invoices) (canonical in [service.md](./service.md#recurring-invoices)) and [finance.md → Budgets](./finance.md#budgets) (canonical in [reports.md](./reports.md#budgets)) so the operational location is discoverable from the natural sidebar group. The deep-dives below are stubbed with TODO placeholders so the cross-references resolve; the standalone walkthroughs are the next pass.

---

## Deep-dives

Workflows complex enough to deserve standalone treatment. Each has its own file under [`docs/erp-guide/deep-dives/`](./deep-dives/) and is linked from the relevant section file. **All six are TODO stubs today** — see each file's header for what the standalone treatment will add beyond the parent section.

| Topic | File | Why a deep-dive |
|---|---|---|
| Payroll Runs | [`deep-dives/payroll-runs.md`](./deep-dives/payroll-runs.md) | calc → approve → mark-paid lifecycle with retropay, balances, fast formulas |
| Work Orders | [`deep-dives/work-orders.md`](./deep-dives/work-orders.md) | release → issue → complete with BOM explode, backflush, OSP, variances |
| Journal Entries | [`deep-dives/journal-entries.md`](./deep-dives/journal-entries.md) | manual + sub-ledger auto-post + recurring + mass allocation |
| Bank Reconciliation | [`deep-dives/bank-reconciliation.md`](./deep-dives/bank-reconciliation.md) | statement import + auto-match rules + completion |
| Tax Returns | [`deep-dives/tax-returns.md`](./deep-dives/tax-returns.md) | period → compute → file with confirm-zero gate + e-invoicing |
| Inter-Org Transfers | [`deep-dives/inter-org-transfers.md`](./deep-dives/inter-org-transfers.md) | 1-way vs 2-way with in-transit subinv + CAS ship/receive |

---

## In-app help links

Each ERP page header carries a small `?` icon (top-right next to the screen title) that opens the corresponding section file at the exact `#anchor`. The mapping lives in `app/js/pages/erp/help-links.js` (planned in the next pass). If the help icon is missing on a screen, that screen hasn't been wired yet — open an issue or grep `help_anchor` for the pattern.

---

## Contributing

- Keep entries grounded in **what the screen actually does today**, not what the roadmap promises. If you reference a state, action, or field, verify it exists in the corresponding model/controller/page JS.
- Follow the entry shape above. Don't invent new headings unless the screen genuinely needs them — predictability beats personality here.
- Mermaid diagrams are welcome for state machines; skip them for simple CRUD screens.
- Cross-link with relative paths (e.g. `[Items](./items.md#item-master)`) so they work both in GitHub and in any future doc viewer.
