# Data Quality Assessment — salesdaily.csv

## 1. Scope and method
The inspection was performed on the supplied original `salesdaily.csv`. The raw file was not edited. Counts below are calculated from the 2,106 data rows and 13 columns.

## 2. Quality results

| Check | Result | Interpretation |
| --- | --- | --- |
| Record count | 2,106 | Meets the lecturer minimum of 500 records. |
| Column count | 13 | Eight category measures and five date/time descriptors. |
| Missing values | 0 across all 13 columns | No null/blank values were detected by the CSV parser. |
| Exact duplicate rows | 0 | No complete duplicate rows detected. |
| Duplicate dates | 0 | Each date appears once in the daily file. |
| Invalid/unparseable dates | 0 | All values in datum parsed using month/day/year format. |
| Negative numeric values | 0 | No negative values in the eight category columns or numeric descriptors. |
| Rows with all eight category values equal to zero | 26 | Retain and investigate; zero is a valid numeric observation, not a missing value. |
| Zero values among the 16,848 category cells | 2,393 | Zero sales for a category should not be treated as missing. |
| Hour = 276 | 2,104 rows | Dominant source value; meaning should be confirmed from source documentation. |
| Hour = 248 | 1 row | Unusual value; investigate in Phase IV, do not change now. |
| Hour = 190 | 1 row | Unusual value; investigate in Phase IV, do not change now. |
| Observed date range | 2014-01-02 to 2019-10-08 | Covers the period represented in the supplied daily file. |
| Raw file size | 117,854 bytes | Measured from the uploaded file. |


## 3. Column-level completeness
All 13 columns have 2,106 non-missing values. No missing values were found in `datum`, the eight ATC category columns, `Year`, `Month`, `Hour`, or `Weekday Name`.

## 4. Data type observations
- `datum` is read as text and should be converted to an Oracle DATE in Phase IV.
- The eight ATC category columns are numeric decimal values in the CSV.
- `Year`, `Month`, and `Hour` are integer-valued numeric columns.
- `Weekday Name` is text.
- The `Hour` column contains 276 in 2,104 rows, 248 in one row, and 190 in one row. Its precise business meaning is not established by the file alone. Preserve the original field and investigate it; do not assume it is a clock hour.

## 5. Issues and Phase IV cleaning checklist
1. Confirm the licence on the original Kaggle page and record the exact displayed terms.
2. Confirm the semantic meaning and valid range of `Hour` with the dataset documentation/creator.
3. Convert `datum` text to DATE after validating the format.
4. Check that `Year`, `Month`, and `Weekday Name` agree with the parsed date.
5. Retain numeric zero values; do not replace them with NULL.
6. Preserve the raw CSV unchanged and perform any cleaning on a separate working copy in Phase IV.

**Important:** This phase reports quality; it does not modify or clean the source data.
