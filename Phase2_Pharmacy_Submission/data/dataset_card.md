# Dataset Card — Pharmacy Inventory and Expiry Monitoring System

## 1. Dataset identification
- **Dataset title:** Pharma Sales Data
- **Dataset creator/author:** Milan Zdravković (as attributed on Kaggle)
- **Original source:** https://www.kaggle.com/datasets/milanzdravkovic/pharma-sales-data
- **Selected raw file:** `salesdaily.csv`
- **File format:** CSV (comma-separated values)
- **File size:** 117,854 bytes (about 115.1 KiB), as received in the uploaded archive
- **Rows:** 2,106 data records (header excluded)
- **Columns:** 13
- **Observed date range:** 2014-01-02 through 2019-10-08
- **Download/collection date for this project:** 20 November 2026 (the date the student supplied the file in this project; replace if your actual Kaggle download date differs)
- **Licence:** A public copy of the dataset repository attributes CC BY-NC 4.0 to the dataset. The Kaggle page should be checked directly and the displayed licence recorded before final submission. Source for the public-copy attribution: https://github.com/mcallara/pharma-sales-data

## 2. What one record represents
One row represents one calendar day's aggregated sales quantities for eight ATC-coded medicine categories. It is not one individual medicine sale, one patient, one prescription, one stock batch, or one expiry record.

## 3. Original columns
`datum`, `M01AB`, `M01AE`, `N02BA`, `N02BE`, `N05B`, `N05C`, `R03`, `R06`, `Year`, `Month`, `Hour`, and `Weekday Name`.

The eight ATC columns contain the daily quantity/value recorded for each category in the source file. The source file itself does not provide individual product names or descriptions.

## 4. Intended use in this project
The file is used as historical daily category-level sales data for the logical design and future sales/stock-demand analysis of the Pharmacy Inventory and Expiry Monitoring System.

## 5. Known limitations
The dataset does not contain individual medicine/product IDs, supplier records, purchase orders, stock-on-hand balances, batch/lot numbers, expiry dates, customer details, or individual sale-line transactions. Therefore, it cannot independently support real batch-level expiry monitoring or supplier/purchase management. Those features require a separately sourced and documented dataset or clearly labelled synthetic demonstration data in a later phase. Do not present synthetic records as Kaggle observations.

## 6. Raw-data preservation
The original downloaded `salesdaily.csv` is stored at `data/raw/salesdaily.csv`. It has been copied without editing. Data correction and type conversion are deferred to Phase IV, as required by the project brief.
