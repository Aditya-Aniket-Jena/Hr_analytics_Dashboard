# HR Analytics Dashboard

An interactive Power BI dashboard analyzing employee attrition and workforce demographics, built on a single HR dataset.

## Files

| File | Description |
|---|---|
| `Company_Data.xlsx` | Source dataset — one row per employee |
| `Dashboard.pbix` | Power BI report (data model + "Dashboard" page) |

## Dataset

`Company_Data.xlsx` (sheet: **HR data**) contains employee-level records with the following fields:

| Column | Description |
|---|---|
| `Employee Number` | Unique employee ID |
| `Attrition` | Yes/No — whether the employee has left |
| `Business Travel` | Travel frequency (Non-Travel, Travel_Rarely, Travel_Frequently) |
| `Age` / `Age Group` | Employee age and bucketed age range (Under 25, 25-34, 35-44, 45-54, Over 55) |
| `Department` | Sales, R&D, HR |
| `Education Field` | Life Sciences, Medical, Marketing, Technical Degree, Other |
| `Education` | Highest degree (High School through Doctoral) |
| `Gender` | Male/Female |
| `Job Role` | e.g. Sales Executive, Research Scientist, Laboratory Technician, Manager |
| `Job Level` | Seniority level (1-5) |
| `Marital Status` | Single, Married, Divorced |
| `Over Time` | Whether the employee regularly works overtime |
| `Distance From Home` | Commute distance |
| `Environment Satisfaction` / `Job Satisfaction` / `Work Life Balance` | Self-reported ratings (1-4) |
| `Monthly Income` | Monthly salary |
| `Total Working Years` | Total career length |
| `Years At Company` / `Years In Current Role` / `Years Since Last Promotion` / `Years With Curr Manager` | Tenure metrics |

## Dashboard

The `.pbix` contains a single report page, **"Dashboard,"** with the following visuals:

**KPI cards**
- Total Employees
- Total Attrition
- Attrition Rate
- Active Employees
- Sum of Age
- Sum of Monthly Income

**Charts**
- **Clustered bar chart** — Attrition Rate by Job Role
- **Area chart** — Total Attrition by Age
- **Clustered column chart** — Total Employees by Age Group, split by Gender
- **Donut chart** — Total Attrition by Department
- **Funnel chart** — Total Attrition by Education Field
- **Pivot table** — Total Employees by Job Role (rows) × Job Satisfaction (columns)

**Filters (slicers)**
- Business Travel
- Marital Status
- Gender
- Education

**Other**
- A "Dashboard" title textbox and a reset/navigation action button

## How to use

1. Open `Dashboard.pbix` in Power BI Desktop (free download from Microsoft).
2. The report loads its own copy of the data — `Company_Data.xlsx` is provided as the underlying source in case you want to refresh, audit, or extend the data model.
3. Use the slicers (Business Travel, Marital Status, Gender, Education) at the top to filter the whole dashboard interactively.
4. Hover over any chart to see exact values in tooltips; click a data point to cross-filter the rest of the page.

## Key questions this dashboard answers

- What is the overall attrition rate, and how many employees are currently active?
- Which job roles and departments have the highest attrition?
- How does attrition vary by age and education field?
- How is the workforce distributed across age groups and gender?
- How does employee count break down by job role and job satisfaction level?

## Notes / possible improvements

- Measures like `Attrition Rate`, `Total Attrition`, and `Active Employee` are DAX measures defined in the Power BI data model (not present as raw columns in the Excel source) — open the report's Model view to inspect or edit their formulas.
- Consider adding a trend visual (e.g. attrition by tenure/`Years At Company`) or an Over Time vs. Attrition breakdown, since `Over Time` is a commonly predictive field not yet visualized.
- If refreshing from a new extract of `Company_Data.xlsx`, confirm column headers match exactly, since Power BI queries reference them by name.
