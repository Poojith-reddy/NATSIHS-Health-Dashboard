# Data Dictionary — NATSIHS Cleaned Dataset

**File:** `NATSIHS_Cleaned_All_Datasets.xlsx`
**Source:** Australian Bureau of Statistics (ABS) — National Aboriginal and Torres Strait Islander Health Survey
**Format:** Microsoft Excel (.xlsx) with 4 sheets in tidy (long) format

---

## Sheet 1: `TimeSeries_Remoteness`

Tracks health condition proportions across multiple survey years, split by remoteness area.

| Column | Type | Description | Example Values |
|---|---|---|---|
| `Year` | Text | Survey period | `2004-05`, `2012-13`, `2018-19` |
| `Remoteness` | Text | Geographic remoteness classification | `Non-Remote`, `Remote` |
| `Health_Condition` | Text | Health indicator being measured | `Self-Assessed Health: Excellent/Very Good`, `Current Smoker` |
| `Proportion_Percent` | Numeric | Percentage of the population with this condition | `44`, `38.2` |

**Rows:** 205 | **Use case:** Line charts showing trends over time

---

## Sheet 2: `Detailed_Remoteness`

Provides a more granular remoteness breakdown (5 categories instead of 2) for the latest survey period.

| Column | Type | Description | Example Values |
|---|---|---|---|
| `Remoteness` | Text | Detailed remoteness area | `Major Cities`, `Inner Regional`, `Outer Regional`, `Remote`, `Very Remote` |
| `Health_Condition` | Text | Health indicator being measured | `Self-Assessed Health: Excellent/Very Good`, `Diabetes/High Sugar Levels` |
| `Proportion_Percent` | Numeric | Percentage value | `43.7`, `12.5` |

**Rows:** 97 | **Use case:** Grouped bar charts or heat maps for cross-remoteness comparison

---

## Sheet 3: `Health_Service_Use`

Captures health service utilisation rates by remoteness area.

| Column | Type | Description | Example Values |
|---|---|---|---|
| `Remoteness` | Text | Geographic remoteness classification | `Non-Remote`, `Remote` |
| `Health_Service` | Text | Type of health service accessed | `Saw GP or Specialist`, `Visited Hospital`, `Used Telehealth` |
| `Proportion_Percent` | Numeric | Percentage who used this service | `84.6`, `22.3` |

**Rows:** 31 | **Use case:** Horizontal bar charts comparing service access by remoteness

---

## Sheet 4: `QLD_vs_National`

Compares Queensland-specific Indigenous health indicators against national averages.

| Column | Type | Description | Example Values |
|---|---|---|---|
| `Region` | Text | Geographic comparison group | `QLD Non-Remote`, `QLD Remote`, `National Non-Remote`, `National Remote` |
| `Health_Condition` | Text | Health indicator being measured | `Self-Assessed Health: Excellent/Very Good`, `Asthma` |
| `Proportion_Percent` | Numeric | Percentage value | `38`, `15.2` |

**Rows:** 61 | **Use case:** Side-by-side or butterfly charts for QLD vs National comparison

---

## Notes

- All sheets follow **tidy data principles**: each variable is a column, each observation is a row, each value is a cell.
- `Proportion_Percent` values are percentages (0–100 scale), not decimals.
- Remoteness classifications follow the ABS Australian Statistical Geography Standard (ASGS).
