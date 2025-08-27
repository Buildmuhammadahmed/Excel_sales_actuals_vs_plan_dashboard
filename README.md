# Sales Performance Dashboard (Excel)

<img width="2420" height="1067" alt="Screenshot 2025-08-26 063308" src="https://github.com/user-attachments/assets/48852691-810c-46f8-940c-df4f5e7ca151" />

##  Project Summary

This Excel dashboard analyzes **regional sales performance** across multiple store locations by comparing **Actual sales**, **Previous Year (PY) sales**, and **Planned sales** for a selected Year & Month.
The dashboard highlights year-over-year changes and variance against plan to help leadership quickly identify growth opportunities and areas that need attention.

---

## Business Questions Addressed

* How are current sales performing compared to the previous year (Y-O-Y)?
* Which cities are meeting, exceeding, or missing their sales plans?
* Where are the largest positive and negative variances?
* Which regions require immediate corrective actions or further investigation?

---

## Value Delivered

* Single-page snapshot to monitor sales performance by city.
* Helps prioritize regions for sales interventions and resource allocation.
* Supports quota planning and executive reporting with clear visuals.
* Makes it easy to spot trends and variances (actual vs plan, actual vs PY).

---

## Data Overview

### Actual Sales 

* Columns: `Year`, `Month`, `Store Location`, `Sales`, `Comments`
* Granularity: Monthly sales by store location across multiple years.

### Plan Sales 

* Structure: Rows contain store locations; columns contain monthly plan values (Jan → Dec).
* Used to lookup planned targets for each store and month.

---

## Key Formulas

These formulas power the dashboard lookups and variance calculations.

**Actual (for selected Year & Month)**

```excel
=XLOOKUP($C$4&$C$5&B9, Table2[Year]&Table2[Month]&Table2[Store Location], Table2[Sales], "")
```

**Previous Year (PY)**

```excel
=XLOOKUP($C$4-1&$C$5&B9, Table2[Year]&Table2[Month]&Table2[Store Location], Table2[Sales], "")
```

**Plan (lookup by Store and Month)**

```excel
=XLOOKUP($B9, Plan!$A$3:$A$13, XLOOKUP($C$5, Plan!$B$2:$M$2, Plan!$B$3:$M$13), "")
```

**Change vs PY (%)**

```excel
=IFERROR((C9/D9)-1, "")
```

**Change vs Plan (%)**

```excel
=IFERROR((C9/E9)-1, "")
```
