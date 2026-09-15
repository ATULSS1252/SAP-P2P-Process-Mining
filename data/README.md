# Data

This project uses the **BPI Challenge 2019 (OCEL)** event log:

> Khayatbashi, Shahrzad; Hartig, Olaf; Jalali, Amin (2023): *BPI Challenge 2019 (OCEL)*. Version 1. 4TU.ResearchData. https://doi.org/10.4121/46a7e15b-10c7-4ab2-988d-ee67d8ea515a

License: CC BY 4.0.

## Getting the file

1. Go to the [dataset page](https://data.4tu.nl/datasets/46a7e15b-10c7-4ab2-988d-ee67d8ea515a) and download `BPIC19.zip` (~68MB).
2. Unzip it — you get `BPIC19.jsonocel` (~1.5GB).
3. Place it here as `data/BPIC19.jsonocel`. This folder is gitignored, so the raw file never gets committed.

The dataset covers purchase order handling at a multinational coatings and paints company in 2018: 1,595,923 events, 76,349 purchase documents, 251,734 line items, 42 activities, across 4 matching types (3-way with GR-based invoicing, 3-way without, 2-way, consignment).
