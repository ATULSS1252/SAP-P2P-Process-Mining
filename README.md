# SAP S/4HANA Purchase-to-Pay (P2P) Process Mining & Compliance Analysis

> **The Business Problem:** End-to-end purchase-to-pay processes across multi-subsidiary environments frequently suffer from compliance drift, unmapped rework loops, and deviations from standard 3-way matching. This project analyzes **1,500,000+ events** across **76,349 purchase documents** and **251,734 items** to uncover operational bottlenecks and quantify financial risk[span_1](start_span)[span_1](end_span).

---

## 📊 Key Findings Preview
* **Overall Compliance Deviation:** Quantified deviation rate against the standard normative 3-way match path[span_2](start_span)[span_2](end_span).
* **Rework Loops:** Identified high-frequency iteration loops in purchase order item modifications and invoice verifications[span_3](start_span)[span_3](end_span).
* **Post-GR Modifications:** Tracked price and quantity changes occurring strictly *after* goods receipt[span_4](start_span)[span_4](end_span).
* **Invoice Exceptions:** Highlighted clusters of duplicate and blocked invoices[span_5](start_span)[span_5](end_span).
* **Subsidiary Spread:** Mapped the days-to-clear distribution variance across 60 distinct corporate subsidiaries[span_6](start_span)[span_6](end_span).

---

## 🛠️ Tech Stack & Architecture
* **Language & Analysis:** Python, PM4Py (Process Mining for Python)[span_7](start_span)[span_7](end_span)
* **ERP Mapping:** Standard SAP S/4HANA architecture (`EKKO`, `EKPO`, `EKBE`, `RSEG`, `LFA1`)[span_8](start_span)[span_8](end_span)
* **Visualization:** SAP Analytics Cloud (SAC) / Tableau[span_9](start_span)[span_9](end_span)
* **Data Source:** BPI Challenge 2019 event logs (4TU repository)[span_10](start_span)[span_10](end_span)

---

## 📁 Repository Structure
```text
sap-p2p-process-mining/
│
├── data/                  # Instructions and scripts for loading the BPI Challenge 2019 dataset
├── notebooks/             # Clean, sequentially numbered Jupyter notebooks (end-to-end execution)
├── outputs/               # Exported process maps, summary CSVs, and CSN/JSON model definitions
├── MAPPING.md             # SAP table and field alignment documentation
└── README.md              # Project overview and executive summary
