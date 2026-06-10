# Work Orders — deep-dive

**Status: TODO.** This page is a stub. The parent section [manufacturing.md](../manufacturing.md#work-orders) has the field tables, lifecycle, and gotchas for Work Orders. This deep-dive will cover:

- The full **release → issue → complete** lifecycle with worked numbers (one BOM, one routing, one work order).
- BOM explode: how the WO snapshots `bom_lines` at release vs. picks up live revisions.
- Backflush at completion: what `BackflushService` filters by `bom_line_type` and what it issues automatically.
- OSP (Outside Processing) operations: the receipt-back-from-vendor handoff.
- Variance accounting: material variance, labor variance, overhead variance — where each lands in the GL.
- Scrap, by-products, and yield loss accounting.
- WIP balance integrity at month-end close.

Until this lands, refer to [manufacturing.md](../manufacturing.md#work-orders) for the operational surface.
