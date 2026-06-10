# Inter-Org Transfers — deep-dive

**Status: TODO.** This page is a stub. The parent section [inventory.md → Inter-Org Transfers](../inventory.md#inter-org-transfers) has the field tables, lifecycle, and gotchas. This deep-dive will cover:

- The **1-way** transfer (no in-transit, direct subinventory-to-subinventory across orgs).
- The **2-way** transfer (uses the `_SYS_IN_TRANSIT` subinventory as the destination of ship, source of receive).
- CAS ship/receive interlock: the compare-and-swap that prevents double-ship and double-receive.
- Cost handover: the ship org's cost basis vs. the receive org's cost basis, the variance bucket.
- Inter-company accounting: when the orgs belong to different legal entities, the IC payable/receivable per leg.
- Cancellation: what's allowed pre-ship vs. mid-transit vs. post-receive.
- Reconciliation: the in-transit aging report for stuck transfers.

Until this lands, refer to [inventory.md → Inter-Org Transfers](../inventory.md#inter-org-transfers) for the operational surface.
