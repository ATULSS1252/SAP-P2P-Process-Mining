# SAP Table & Attribute Mapping (`MAPPING.md`)

This document maps the attributes from the event log (BPI Challenge 2019) to standard SAP S/4HANA database tables and fields. It forms the structural baseline for process discovery, conformance checking, and compliance evaluation.

## 1. Core Purchase-to-Pay (P2P) Table Architecture

| Process Concept / Log Attribute | SAP Table | SAP Field | Technical & Functional Description |
| :--- | :--- | :--- | :--- |
| **Purchase Document ID** | `EKKO` / `EKPO` | `EBELN` / `EBELP` | Purchasing Document Header (`EKKO`) and Item (`EKPO`) tables tracking commercial terms, purchasing organization, and purchasing group. |
| **Vendor Information** | `LFA1` / `LFB1` | `LIFNR` | Central Vendor Master (`LFA1`) paired with company code-specific vendor data (`LFB1`) handling payment terms and reconciliation accounts. |
| **Purchase Requisition** | `EBAN` | `BANFN` | Internal requirement tracking object preceding the purchase order conversion. |
| **Goods Receipt (Inbound)** | `MKPF` / `MSEG` | `MBLNR` / `ZEILE` | Material Document Header (`MKPF`) and Item (`MSEG`) confirming physical inventory movement and valuation impact into stock. |
| **Invoice Verification** | `RSEG` | `BELNR` / `BUZEI` | Incoming supplier invoice item details matched against purchase orders and goods receipts during invoice receipt. |
| **Purchase Order History** | `EKBE` | `EBELN`, `ZEKKN` | History tracking table linking purchase order items to subsequent goods receipts, invoice receipts, and cancellations. |

---

## 2. Impact of Goods Receipt-Based Invoice Verification

A critical element of this repository's matching logic accounts for the **Goods Receipt-Based Invoice Verification** flag:

* **Standard Logic:** Without the flag, system matching allows invoice verification immediately following purchase order creation, provided tolerances are met.
* **GR-Based Logic:** When active, the system strictly restricts invoice verification until a corresponding physical or service Goods Receipt (`MKPF`/`MSEG`) is posted. 
* **Process Mining Implication:** Conformance checking filters out paths where invoices precede goods receipt unless explicitly permitted by master data rules, isolating true compliance deviations from authorized process variations.

---

## 3. SD Module References (Cross-Module Visibility)
While the primary focus is Purchase-to-Pay (MM-PUR / MM-IM), secondary downstream document flows link procurement to sales and distribution structures where applicable:
* **Sales Header & Item:** `VBAK` / `VBAP`
* **Delivery Header & Item:** `LIKP` / `LIPS`
* **Billing Header & Item:** `VBRK` / `VBRP`
