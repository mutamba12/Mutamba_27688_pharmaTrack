# Phase II — Data Sourcing, Normalization and Logical Design

**Project:** Pharmacy Inventory and Expiry Monitoring System  
**Student:** Alice Mutamba  
**Student ID:** 27688  
**Group:** B  
**Course:** INSY 8311 — Database Development with PL/SQL  
**Main raw dataset:** `salesdaily.csv` (2,106 records)

## Phase II deliverables
- `data/raw/salesdaily.csv` — original raw file, preserved unchanged.
- `data/dataset_card.md` — source, format, record meaning, scope and limitations.
- `docs/design/data_quality_report.md` — measured quality checks and counts.
- `docs/design/normalization.md` — worked UNF → 1NF → 2NF → 3NF transformation, real sample values and raw-field mapping.
- `docs/design/erd.png` — logical ERD.
- `docs/design/data_dictionary.md` — attributes, keys, required/unique status, cardinality and optionality.

## Important dataset scope
The selected file contains daily aggregate sales values for eight ATC categories. It does not include product-level, supplier, purchase, batch, expiry, customer or stock-on-hand data. These must be sourced separately or clearly labelled as synthetic demonstration data in later phases. Do not describe them as fields from this Kaggle dataset.

## Before submission
1. Confirm the licence displayed on the original Kaggle dataset page and update `data/dataset_card.md` if necessary.
2. Confirm the date on which you personally downloaded the file.
3. Review the unusual `Hour` values (248 and 190) and confirm the field meaning.
4. Open the ERD and check that you can explain every primary key, foreign key and relationship.
5. Be ready to open one original row and show how its eight category values become eight rows in `DAILY_CATEGORY_SALES`.
6. Ensure the GitHub repository contains these files and that the raw CSV has not been edited.
