# Data Dictionary — 3NF Logical Design

**Note:** Per the Phase II instructions, Oracle physical data types and sizes are intentionally omitted. They will be selected in Phase IV.

## 1. CALENDAR_YEAR
| Column | Meaning | Key | Required? | Unique? |
|---|---|---|---|---|
| year_id | Calendar year represented by the source date | PK | Yes | Yes |

## 2. CALENDAR_MONTH
| Column | Meaning | Key | Required? | Unique? |
|---|---|---|---|---|
| month_no | Numeric month, 1–12 | PK | Yes | Yes |
| month_name | Standard month label (January–December) | — | Yes | Yes |

## 3. SALES_DATE
| Column | Meaning | Key | Required? | Unique? |
|---|---|---|---|---|
| sales_date | Calendar date for the daily observation | PK | Yes | Yes |
| year_id | Year of the observation | FK → CALENDAR_YEAR.year_id | Yes | No |
| month_no | Month of the observation | FK → CALENDAR_MONTH.month_no | Yes | No |
| hour_source_value | Original numeric value from the source `Hour` field; meaning to be verified | — | Yes | No |
| weekday_name | Original weekday label from the source | — | Yes | No |

## 4. ATC_CATEGORY
| Column | Meaning | Key | Required? | Unique? |
|---|---|---|---|---|
| category_code | One of the eight ATC category codes present in the CSV | PK | Yes | Yes |

Seed codes from the supplied source: `M01AB`, `M01AE`, `N02BA`, `N02BE`, `N05B`, `N05C`, `R03`, `R06`.

## 5. DAILY_CATEGORY_SALES
| Column | Meaning | Key | Required? | Unique? |
|---|---|---|---|---|
| sales_date | Date of the daily category sales observation | PK, FK → SALES_DATE.sales_date | Yes | No |
| category_code | ATC category measured | PK, FK → ATC_CATEGORY.category_code | Yes | No |
| sales_quantity | Daily numeric value recorded for the category in the source | — | Yes | No |

**Composite primary key:** `(sales_date, category_code)`. Zero is allowed because the source contains zero values; it must not be treated as missing.

## Relationships, cardinality and optionality
1. `CALENDAR_YEAR (1) —— (0..*) SALES_DATE`: each SALES_DATE must reference exactly one year; a year may have zero or many dates.
2. `CALENDAR_MONTH (1) —— (0..*) SALES_DATE`: each SALES_DATE must reference exactly one month; a month may have zero or many dates.
3. `SALES_DATE (1) —— (0..*) DAILY_CATEGORY_SALES`: each sales detail must reference exactly one date; a date may have zero or many detail rows (the intended complete unpivot has eight).
4. `ATC_CATEGORY (1) —— (0..*) DAILY_CATEGORY_SALES`: each sales detail must reference exactly one category; a category may have zero or many daily observations.

## Design notes
- The primary key of DAILY_CATEGORY_SALES is composite.
- The source data has no individual medicine product identifier. `ATC_CATEGORY` therefore represents the source's category codes, not individual products.
- Supplier, purchase, batch, expiry, customer, and stock balance attributes are outside this dataset and are not included in this source-derived logical schema.
- No Oracle data types or sizes are shown because this is Phase II logical design.
