# Normalization Report — Pharma Sales Daily Dataset

## 1. Purpose and source
This report transforms the supplied `salesdaily.csv` from a wide daily-sales file into a logical relational design. The selected file contains 2,106 records and 13 columns. The eight category columns are `M01AB`, `M01AE`, `N02BA`, `N02BE`, `N05B`, `N05C`, `R03`, and `R06`.

A raw row represents one date and contains one sales value for each of the eight ATC categories. The normalization examples below use actual records from the uploaded file.

## 2. Functional dependencies used
- `sales_date → year, month_no, hour_source_value, weekday_name`
- `category_code → category_code` (the code identifies the category; no category description is supplied in the raw file)
- `(sales_date, category_code) → sales_quantity`

The date determines its calendar attributes. The combination of date and category determines the category's sales measure.

## 3. UNF — Unnormalized Form
The source is a wide record with eight repeated category-measure attributes. The values are scalar, but the category measures form a repeating set of columns that must be transformed into rows to support a relational child table.

Actual first three source rows:

| datum | M01AB | M01AE | N02BA | N02BE | N05B | N05C | R03 | R06 | Year | Month | Hour | Weekday Name |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1/2/2014 | 0 | 3.67 | 3.4 | 32.4 | 7 | 0 | 0 | 2 | 2014 | 1 | 248 | Thursday |
| 1/3/2014 | 8 | 4 | 4.4 | 50.6 | 16 | 0 | 20 | 4 | 2014 | 1 | 276 | Friday |
| 1/4/2014 | 2 | 1 | 6.5 | 61.85 | 10 | 0 | 9 | 1 | 2014 | 1 | 276 | Saturday |


**UNF issue:** Each daily record stores eight category sales values side by side. Adding another category would require another column and changes to queries and application code. The repeating category group is not represented as a separate relation.

## 4. 1NF — First Normal Form
To reach 1NF, unpivot the eight category columns into one row per date and category. Each row contains one date, one category code, and one sales quantity. Keep zero values because zero is a valid numeric value in this dataset.

Candidate/composite key: **(sales_date, category_code)**.

Actual first five rows generated from the 2014-01-02 source record:

| sales_date | category_code | sales_quantity |
| --- | --- | --- |
| 1/2/2014 | M01AB | 0 |
| 1/2/2014 | M01AE | 3.67 |
| 1/2/2014 | N02BA | 3.4 |
| 1/2/2014 | N02BE | 32.4 |
| 1/2/2014 | N05B | 7 |


**Dependency removed:** The repeating group of eight category columns is removed by converting it into separate category rows; each field now contains one atomic value.

The full unpivoted relation would contain 2,106 × 8 = **16,848 rows**, including zero-valued category observations.

## 5. 2NF — Second Normal Form
The 1NF relation has composite key `(sales_date, category_code)`. Date attributes depend on only `sales_date`, not on the whole composite key. The category identifier depends only on `category_code`. Only `sales_quantity` depends on the complete composite key.

Decompose into:
- `SALES_DATE(sales_date, year_id, month_no, hour_source_value, weekday_name)`
- `ATC_CATEGORY(category_code)`
- `DAILY_CATEGORY_SALES(sales_date, category_code, sales_quantity)`

The actual first five sales rows above illustrate the sales-detail relation. The date attributes for the sample date are: sales_date = 2014-01-02; year = 2014; month = 1; hour source value = 248; weekday = Thursday.

**Dependency removed:** Partial dependencies are removed from the composite-key relation by moving date attributes to `SALES_DATE` and category identity to `ATC_CATEGORY`; the sales measure remains in `DAILY_CATEGORY_SALES` because it depends on the complete key.

## 6. 3NF — Third Normal Form
For the final logical design, calendar reference values are separated into `CALENDAR_YEAR` and `CALENDAR_MONTH`. `SALES_DATE` stores foreign keys to these reference tables rather than repeating year/month descriptions in every date record. `ATC_CATEGORY` stores the eight category codes from the source. `DAILY_CATEGORY_SALES` stores the measured value for each date/category combination.

Final relations:
1. `CALENDAR_YEAR(year_id)`
2. `CALENDAR_MONTH(month_no, month_name)`
3. `SALES_DATE(sales_date, year_id, month_no, hour_source_value, weekday_name)`
4. `ATC_CATEGORY(category_code)`
5. `DAILY_CATEGORY_SALES(sales_date, category_code, sales_quantity)`

**Dependency removed:** The calendar labels are represented once in their reference tables and linked by foreign keys, preventing repeated month names/year reference values in date records; each non-key attribute in the final relations depends on the key, the whole key, and nothing but the key.

### Note on calendar reference tables
`CALENDAR_YEAR` and `CALENDAR_MONTH` are small reference tables introduced as logical lookup tables to normalize calendar attributes and meet the brief's aim of at least five related tables. Their year/month values are derived from the source dates; month names are standard calendar labels, not extra observed sales facts. If the instructor prefers a simpler design, the two lookup tables can be folded into `SALES_DATE`, leaving a valid three-table design. Do not claim that the raw dataset itself contains month names or separate year/month entities.

## 7. Final table cardinalities
- One `CALENDAR_YEAR` can be associated with many `SALES_DATE` rows.
- One `CALENDAR_MONTH` can be associated with many `SALES_DATE` rows.
- One `SALES_DATE` has eight `DAILY_CATEGORY_SALES` rows in the unpivoted model.
- One `ATC_CATEGORY` can appear in many `DAILY_CATEGORY_SALES` rows.
- Each `DAILY_CATEGORY_SALES` row references exactly one date and one category.

## 8. Source-field mapping
| Raw field | Target table | Target column | Treatment / conversion |
| --- | --- | --- | --- |
| datum | SALES_DATE | sales_date | Text MM/DD/YYYY → DATE in Phase IV. |
| M01AB | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code M01AB. |
| M01AE | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code M01AE. |
| N02BA | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code N02BA. |
| N02BE | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code N02BE. |
| N05B | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code N05B. |
| N05C | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code N05C. |
| R03 | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code R03. |
| R06 | DAILY_CATEGORY_SALES | sales_quantity | Unpivot to a row with category_code R06. |
| Year | CALENDAR_YEAR | year_id | Integer value becomes year reference key; verify matches datum. |
| Month | CALENDAR_MONTH | month_no | Integer 1–12; month_name is a standard lookup label. |
| Hour | SALES_DATE | hour_source_value | Preserve numeric source value; meaning needs confirmation. |
| Weekday Name | SALES_DATE | weekday_name | Text; validate against parsed date in Phase IV. |


## 9. Important scope limitation
The source is aggregated by date and ATC category. It does not contain individual product, supplier, purchase, batch, expiry, customer, or stock-on-hand fields. Those entities must not be fabricated as if they came from this dataset. If required for the broader inventory application, collect a separate legitimate source or create clearly labelled synthetic demonstration data in a later phase.

## 10. Phase IV preparation
- Preserve `data/raw/salesdaily.csv` unchanged.
- Create a separate staging/working copy.
- Parse `datum` into DATE.
- Verify date-derived `Year`, `Month`, and `Weekday Name`.
- Investigate `Hour` values 248 and 190 and confirm the field meaning.
- Unpivot the eight category columns into 16,848 category/day rows.
- Retain zero quantities.
