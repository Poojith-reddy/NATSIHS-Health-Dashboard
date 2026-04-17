# Indigenous Health Analytics Dashboard — NATSIHS Survey Analysis

> **Course:** IFN585 Systems Innovation and Design | **University:** Queensland University of Technology (QUT) | **Semester:** S1 2026

An interactive Tableau dashboard analysing the **National Aboriginal and Torres Strait Islander Health Survey (NATSIHS)** data from the Australian Bureau of Statistics (ABS). This project covers the full analytics pipeline — from raw data cleaning and transformation to interactive dashboard creation — with a focus on ethical data practices aligned with the **AIATSIS Code of Ethics**.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Data Preparation](#data-preparation)
- [Dashboard & Visualisations](#dashboard--visualisations)
  - [1. Health Trends Over Time by Remoteness](#1-health-trends-over-time-by-remoteness)
  - [2. Detailed Health Conditions by Remoteness Area](#2-detailed-health-conditions-by-remoteness-area)
  - [3. Health Service Utilisation](#3-health-service-utilisation)
  - [4. Queensland vs National Comparison](#4-queensland-vs-national-comparison)
  - [5. Interactive Dashboard (Combined)](#5-interactive-dashboard-combined)
- [Ethical Considerations](#ethical-considerations)
- [Tools & Technologies](#tools--technologies)
- [Repository Structure](#repository-structure)
- [How to Use](#how-to-use)
- [Key Findings](#key-findings)
- [Report](#report)
- [References](#references)
- [Author](#author)

---

## Project Overview

This project was developed as part of the **IFN585 Systems Innovation and Design** unit at QUT. The goal was to:

1. **Clean and transform** raw ABS survey data from human-readable report format into analytics-ready (tidy) format suitable for Tableau.
2. **Design and build** an interactive Tableau dashboard that enables stakeholders (policymakers, health researchers, community organisations) to explore Indigenous health indicators across different remoteness areas and time periods.
3. **Apply ethical reasoning** using the AIATSIS Code of Ethics and four ethical lenses (Rights-Based, Relational, Justice & Fairness, Care Ethics) to ensure the data is handled respectfully and responsibly.
4. **Write an analytical report** presenting findings and recommendations grounded in evidence from the dashboard.

The project follows the **Systems Thinking** approach taught in the course — treating data as a system component where the input format must match the processing requirements for the system to function correctly.

---

## Dataset Description

**Source:** Australian Bureau of Statistics (ABS) — [National Aboriginal and Torres Strait Islander Health Survey](https://www.abs.gov.au/statistics/people/aboriginal-and-torres-strait-islander-peoples/national-aboriginal-and-torres-strait-islander-health-survey/latest-release)

The cleaned dataset (`NATSIHS_Cleaned_All_Datasets.xlsx`) contains **4 sheets**, each structured in tidy format:

| Sheet Name | Rows | Columns | Description |
|---|---|---|---|
| `TimeSeries_Remoteness` | 205 | 4 | Health condition proportions tracked across survey years (2004–05 onwards) by remoteness area |
| `Detailed_Remoteness` | 97 | 3 | Granular breakdown of health conditions across 5 remoteness categories (Major Cities → Very Remote) |
| `Health_Service_Use` | 31 | 3 | Health service utilisation rates (GP visits, hospital admissions, etc.) by remoteness |
| `QLD_vs_National` | 61 | 3 | Queensland-specific health indicators compared against national averages |

**Key Variables:**
- `Year` — Survey period (e.g., 2004-05, 2012-13, 2018-19)
- `Remoteness` — Geographic classification (Major Cities, Inner Regional, Outer Regional, Remote, Very Remote, Non-Remote)
- `Health_Condition` — Health indicator (e.g., Self-Assessed Health: Excellent/Very Good, Diabetes/High Sugar Levels, Current Smoker)
- `Health_Service` — Type of health service accessed
- `Region` — QLD-specific vs National comparison groups
- `Proportion_Percent` — Percentage value for the given indicator

> **Note on Data Sovereignty:** The raw ABS survey data is not included in this repository out of respect for Indigenous data sovereignty principles. The cleaned dataset is provided for reproducibility purposes only. Please refer to the [ABS website](https://www.abs.gov.au/) for the original data and its terms of use.

---

## Data Preparation

A significant portion of this project (approximately 80% of the effort, consistent with industry norms) was spent on **data preparation**. The raw ABS data was in human-readable report format with:

- Merged cells and branding/logos
- Multi-level headers with entangled variables (State + Year in column headers)
- Footnotes, metadata rows, and summary/total rows mixed with data
- Inconsistent formatting and blank rows/columns

### Cleaning Steps Performed:

1. **Removed non-data rows** — Logos, titles, footnotes, and metadata rows that would confuse Tableau's data interpreter.
2. **Restructured headers** — Ensured Row 1 contains only variable names and all subsequent rows contain observations.
3. **Converted wide format to long (tidy) format** — Unpivoted crosstab layouts so that each variable has its own column and each observation has its own row (following [tidy data principles](https://vita.had.co.nz/papers/tidy-data.pdf)).
4. **Standardised data types** — Ensured numeric columns contain only numbers (removed percentage signs, commas, text annotations).
5. **Removed aggregate/total rows** — Eliminated "Total" rows that would cause double-counting in Tableau.
6. **Validated row counts** — Cross-checked expected row counts against actual (e.g., States × Years × Categories = expected rows).

### Before vs After:

| Aspect | Raw Data (Before) | Cleaned Data (After) |
|---|---|---|
| Format | Wide / crosstab with merged cells | Long / tidy format |
| Row 1 | Logos and titles | Variable names |
| Empty rows | Multiple | None |
| Data types | Mixed text and numbers | Consistent per column |
| Tableau compatible | No — import fails | Yes — immediate use |

---

## Dashboard & Visualisations

Below are the individual charts and the combined interactive dashboard built in Tableau.

### 1. Health Trends Over Time by Remoteness

<!-- <img width="469" height="182" alt="image" src="https://github.com/user-attachments/assets/8d69008f-9f68-4959-9e94-f3e333ede8ef" />
: screenshots/01_time_series_trends.png -->![Uploading image.png…]()

![Health Trends Over Time](screenshots/01_time_series_trends.png)

**Chart Type:** Line chart with colour-coded remoteness areas

**What it shows:** How key health indicators (self-assessed health, chronic conditions, smoking rates) have changed across survey years for Remote vs Non-Remote populations.

**Key Insight:** *(Add your specific finding here, e.g., "The gap in self-assessed excellent/very good health between Remote and Non-Remote areas has narrowed from X% in 2004-05 to Y% in the latest survey.")*

---

### 2. Detailed Health Conditions by Remoteness Area

<!-- ADD YOUR SCREENSHOT: screenshots/02_detailed_remoteness.png -->
![Detailed Remoteness Breakdown](screenshots/02_detailed_remoteness.png)

**Chart Type:** Grouped bar chart / heat map

**What it shows:** A granular comparison of health conditions across the 5 remoteness categories (Major Cities, Inner Regional, Outer Regional, Remote, Very Remote).

**Key Insight:** *(Add your specific finding here, e.g., "Smoking rates are significantly higher in Very Remote areas compared to Major Cities.")*

---

### 3. Health Service Utilisation

<!-- ADD YOUR SCREENSHOT: screenshots/03_health_service_use.png -->
![Health Service Use](screenshots/03_health_service_use.png)

**Chart Type:** Horizontal bar chart / stacked bar chart

**What it shows:** The proportion of Indigenous Australians accessing different health services (GP, specialist, hospital, etc.) broken down by remoteness area.

**Key Insight:** *(Add your specific finding here, e.g., "GP and specialist visit rates are notably lower in Remote areas, while hospital admission rates are higher.")*

---

### 4. Queensland vs National Comparison

<!-- ADD YOUR SCREENSHOT: screenshots/04_qld_vs_national.png -->
![QLD vs National](screenshots/04_qld_vs_national.png)

**Chart Type:** Side-by-side bar chart / butterfly chart

**What it shows:** How Queensland's Indigenous health indicators compare to the national average, highlighting areas where QLD performs better or worse.

**Key Insight:** *(Add your specific finding here)*

---

### 5. Interactive Dashboard (Combined)

<!-- ADD YOUR SCREENSHOT: screenshots/05_full_dashboard.png -->
![Full Interactive Dashboard](screenshots/05_full_dashboard.png)

**Features:**
- Filter by remoteness area, health condition, and survey year
- Interactive tooltips showing exact proportions and context
- Linked highlighting across charts — selecting a remoteness area in one chart filters all others
- Designed for multiple stakeholder groups (policymakers, researchers, community organisations)

---

## Ethical Considerations

This project handles data about **Aboriginal and Torres Strait Islander peoples**, which requires heightened ethical awareness. The analysis was guided by the **AIATSIS Code of Ethics** and four ethical lenses from the IFN585 curriculum:

| Ethical Lens | AIATSIS Principle | How It Was Applied |
|---|---|---|
| **Rights-Based Ethics** | Indigenous Self-Determination | Respected data sovereignty — raw data is not redistributed; the ABS source is cited for access |
| **Relational Ethics** | Indigenous Leadership | Acknowledged that this analysis is an academic exercise; real-world use would require co-design with Indigenous communities |
| **Justice & Fairness Ethics** | Impact and Value | Ensured visualisations do not reinforce deficit narratives; presented data in context with systemic factors |
| **Care Ethics** | Sustainability & Accountability | Considered long-term wellbeing implications; avoided sensationalising health disparities |

> This project is an academic exercise completed for coursework at QUT. It does not claim to represent Indigenous community perspectives and acknowledges that meaningful engagement with Indigenous communities and leadership is essential for any real-world application of this analysis.

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| **Microsoft Excel** | Data cleaning, transformation (wide → long format), validation |
| **Tableau Desktop** | Dashboard design, interactive visualisations, calculated fields |
| **ABS Data** | Source data — National Aboriginal and Torres Strait Islander Health Survey |

---

## Repository Structure

```
NATSIHS-Health-Dashboard/
│
├── README.md                           # This file — full project documentation
├── .gitignore                          # Git ignore rules
│
├── data/
│   ├── NATSIHS_Cleaned_All_Datasets.xlsx   # Cleaned, analytics-ready dataset (4 sheets)
│   └── data_dictionary.md              # Description of all variables and sheets
│
├── screenshots/
│   ├── 01_time_series_trends.png       # Health trends over time chart
│   ├── 02_detailed_remoteness.png      # Detailed remoteness breakdown chart
│   ├── 03_health_service_use.png       # Health service utilisation chart
│   ├── 04_qld_vs_national.png         # QLD vs National comparison chart
│   └── 05_full_dashboard.png          # Complete interactive dashboard
│
├── tableau/
│   └── NATSIHS_Dashboard.twbx         # Tableau packaged workbook (optional)
│
└── docs/
    └── IFN585_Assignment_Report.pdf    # Final submitted report (optional)
```

---

## How to Use

### Prerequisites
- [Tableau Desktop](https://www.tableau.com/products/desktop) or [Tableau Public](https://public.tableau.com/) (free)

### Steps to Reproduce

1. **Clone this repository:**
   ```bash
   git clone https://github.com/Poojith-reddy/NATSIHS-Health-Dashboard.git
   cd NATSIHS-Health-Dashboard
   ```

2. **Open the dataset in Tableau:**
   - Launch Tableau Desktop → Connect → Microsoft Excel
   - Navigate to `data/NATSIHS_Cleaned_All_Datasets.xlsx`
   - Select the sheet you want to visualise

3. **Build visualisations:**
   - Drag dimensions (Remoteness, Health_Condition, Year) to Columns/Rows
   - Drag `Proportion_Percent` to the measure shelf
   - Apply filters and colours as needed

4. **Or open the packaged workbook directly:**
   - Double-click `tableau/NATSIHS_Dashboard.twbx` (if included)

---

## Key Findings

*(Update these with your actual findings from the dashboard)*

1. **Health disparities persist by remoteness** — Indigenous Australians in Remote and Very Remote areas consistently report lower self-assessed health compared to those in Major Cities.

2. **Health service access varies significantly** — GP and specialist consultation rates drop in remote areas, while hospital utilisation patterns differ, suggesting access barriers rather than lower health needs.

3. **Queensland-specific patterns** — QLD shows distinct trends compared to national averages in several indicators, warranting state-level policy attention.

4. **Temporal trends show mixed progress** — While some health indicators have improved over time, others remain stable or have widened, particularly for chronic conditions.

---

## Report

The analytical report (2,000 words) accompanies this dashboard and covers:
- **Introduction** — Context and purpose of the analysis
- **Background** — Overview of Indigenous health data landscape and the NATSIHS
- **Findings** — Evidence-based insights from the dashboard with ethical analysis
- **Conclusion** — Summary of key findings and recommendations

---

## References

- Australian Bureau of Statistics. *National Aboriginal and Torres Strait Islander Health Survey.* [https://www.abs.gov.au/](https://www.abs.gov.au/)
- Australian Institute of Aboriginal and Torres Strait Islander Studies. *AIATSIS Code of Ethics.* [https://aiatsis.gov.au/research/ethical-research/code-ethics](https://aiatsis.gov.au/research/ethical-research/code-ethics)
- Wickham, H. (2014). Tidy Data. *Journal of Statistical Software*, 59(10).
- QUT IFN585 Course Materials — Systems Innovation and Design, S1 2026.

---

## Author

**Poojith Reddy Menthem**
- Master of Data Science — Queensland University of Technology (QUT)
- [LinkedIn](https://www.linkedin.com/in/poojith-reddy-menthem-25219124a/)
- [GitHub](https://github.com/Poojith-reddy/)
- Email: pmenthem@gmail.com
