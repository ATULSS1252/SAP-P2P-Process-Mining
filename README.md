# SAP Purchase-to-Pay Process Mining

**Business question:** where does the purchase-to-pay process actually deviate from the standard 3-way-match-with-goods-receipt path, and which deviations cost the business the most time and rework? This repository mines 1.6M real events from 76,349 purchase orders to answer it, and maps every finding back to the SAP tables (`EKKO`, `EKPO`, `EKBE`, `RSEG`, `LFA1`) an analyst would query to investigate it.

## Data

[BPI Challenge 2019 (OCEL)](https://data.4tu.nl/datasets/46a7e15b-10c7-4ab2-988d-ee67d8ea515a) — CC BY 4.0, Khayatbashi, Hartig & Jalali (2023), 4TU.ResearchData. Real purchase-order-handling data from a multinational coatings and paints company: 1,595,923 events, 76,349 purchase documents, 251,734 line items, 42 activities. See [`data/README.md`](data/README.md) for the exact download step — the raw file is ~1.5GB and is not committed to this repo.

## Findings (in progress — Week 1 of 4)

* **Compliance deviation rate** against the standard 3-way-match-with-GR path — *quantification lands in Week 2*
* **Rework loops** in purchase order item changes and invoice re-verification
* **Post-goods-receipt price/quantity changes** — changes happening after the point they should be locked
* **Duplicate and blocked invoices**
* **Days-to-clear spread** across the 60 subsidiaries in the dataset

## Repository structure

```
notebooks/
  01_load_and_explore.ipynb     # load the OCEL, sanity-check scale, inspect object/event types
  02_bottleneck_analysis.ipynb  # flatten to PO, discover heuristics net / BPMN / performance map
  outputs/                      # rendered process maps (PNG)
data/
  README.md                     # how to get BPIC19.jsonocel
MAPPING.md                      # log attribute -> SAP table/field mapping
LICENSE                         # MIT (code); dataset itself is CC BY 4.0
```

## Tech stack

* Python, [PM4Py](https://pm4py.fit.fraunhofer.de/) — object-centric and classical process discovery
* SAP S/4HANA table architecture as the mapping target: `EKKO`, `EKPO`, `EKBE`, `RSEG`, `LFA1` (full mapping in [`MAPPING.md`](MAPPING.md))
* Planned: SAP Analytics Cloud / Tableau for the interactive story (Week 3)

## Reproducing this

```bash
git clone https://github.com/ATULSS1252/SAP-P2P-Process-Mining.git
cd SAP-P2P-Process-Mining
pip install -r requirements.txt
# then follow data/README.md to place BPIC19.jsonocel in data/
jupyter notebook notebooks/01_load_and_explore.ipynb
```

## Status

Week 1 of a 4-week build: data loaded, repo structured, first process maps discovered. `notebooks/outputs/po_performance_map.png` still needs a top-variant filter pass before it is presentable — the unfiltered version is too dense to read at a glance (see the note in `02_bottleneck_analysis.ipynb`). Week 2 adds conformance checking and the five quantified findings above.

## License

Code in this repository is MIT-licensed (see [`LICENSE`](LICENSE)). The BPI Challenge 2019 (OCEL) dataset is CC BY 4.0 — cite Khayatbashi, Hartig & Jalali (2023) if you reuse it.
