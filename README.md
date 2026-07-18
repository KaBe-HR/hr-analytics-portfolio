# HR Analytics — Portfolio Projects

A collection of analytics projects in the HR / payroll space, built on synthetic data.
Each project shows the full workflow: raw/incomplete data → data model → DAX measures →
interactive dashboard → business insight.

**Tools:** Power Query, Power BI Desktop (data modeling, DAX)

---

## Project — Recruitment / Time-to-Hire Dashboard

### Business problem
Track how quickly open positions get filled, spot which departments and hire sources are
slower or faster, and see recruiter workload — so bottlenecks in the hiring process can be
addressed before they affect the business.

### Data
- **Requisitions** table — job openings with department, position, date opened, date filled
  (blank if still open), hire source, and assigned recruiter
- **Recruiters** table — reference data (recruiter name, region)

### Process
1. One-to-many relationship between Recruiters and Requisitions (via recruiter ID)
2. Calculated column `Status` — open vs filled, based on whether a fill date exists
3. Calculated column `Days_to_fill` — using `DATEDIFF`, explicitly handling still-open
   requisitions (blank fill date) to avoid skewing the average
4. Calculated column `Month_opened` for time-based trends
5. DAX measures: average days to fill (`AVERAGE`), count of open requisitions, count of
   filled requisitions (`CALCULATE` + `COUNTROWS`)

### Dashboard
- 3 KPI cards: average days to fill, open requisitions, filled requisitions
- Bar chart: average days to fill by department
- Bar chart: average days to fill by recruiter
- Line chart: number of requisitions opened by month
- Matrix: hire source × department
- Department slicer

### Business insight
Finance shows the longest average time-to-fill among departments, while the recruiter
breakdown reveals meaningful differences in speed between recruiters — a useful starting
point for a conversation about workload distribution or process bottlenecks specific to
harder-to-fill roles.


<img width="1226" height="618" alt="image" src="https://github.com/user-attachments/assets/6fcaf7fa-b57c-4ee2-9dc4-e01a180389e4" />
 [Project files](./project-1/Recruitment_Dashboard.pbix)


---

## About the data

All data in this project is **synthetic** — generated for learning purposes. It does not
come from any real company and does not represent real individuals.

## About the author

This project was built as part of self-directed learning of Power Query and Power BI,
during a career transition toward HR analytics / process improvement.

