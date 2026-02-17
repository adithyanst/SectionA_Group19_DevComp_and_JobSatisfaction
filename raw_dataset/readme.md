# Stack Overflow Developer Survey 2025

## Data Preparation Summary

---

## Why I Processed the Data in Python

The original dataset had too many columns and large text fields.
Google Sheets could not import it properly.

So I used **Pandas** to:

* Load the full dataset
* Remove unnecessary columns
* Create a smaller, focused dataset
* Make it manageable for Google Sheets

---

## How I Imported the Data

```python
import pandas as pd
import sys
import csv

csv.field_size_limit(sys.maxsize)

df = pd.read_csv(
    "./survey_results_public.csv",
    low_memory=False
)

print(df.shape)
```

* Increased CSV field size limit to avoid errors
* Used `low_memory=False` for consistent data types
* Checked dataset size using `df.shape`

---

## Columns Kept for Analysis

```python
columns_to_keep = [
    "Country",
    "ConvertedCompYearly",
    "YearsCode",
    "JobSat",
    "RemoteWork",
    "Industry",
    "OrgSize",
    "Employment",
    "DevType",
    "EdLevel",
    "Age"
]

df = df[columns_to_keep]
```

---

## Why These Columns Were Selected

These columns directly help answer the main question:

**What affects developer compensation and job satisfaction in 2025?**

They cover:

* Salary → `ConvertedCompYearly`
* Satisfaction → `JobSat`
* Experience → `YearsCode`
* Location → `Country`
* Work model → `RemoteWork`
* Industry → `Industry`
* Company size → `OrgSize`
* Employment type → `Employment`
* Role → `DevType`
* Education → `EdLevel`
* Career stage → `Age`

---

## Result

* Reduced dataset size
* Easier to analyze
* Successfully imported into Google Sheets
* Focused only on relevant analytical variables
