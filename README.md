# Toronto Building Permit Dashboard | Power BI

Analyzed City of Toronto Building Permits from 1980-2024 to track permit volume, status, and construction value trends over 44 years.

## Data Source
**City of Toronto Open Data - Building Permits**

- Dataset: https://open.toronto.ca/dataset/building-permits-active-permits/

Dataset is public under Open Government Licence - Toronto. Downloaded as 1 CSV and imported into Power BI.

![Dashboard](Building%20Permit%20Dashboard.png)

## Key KPIs
- **Total Permits:** 200K
- **Total Construction Value:** $146.08bn
- **Avg Construction Cost:** $1.33M
- **Closed Permits:** 5,577 (2.79%)
- **Open Permits:** 38K (19.24%)
- **In Progress Permits:** 156K (77.97%)

### 1. Year Bucket (New)
Created a custom Year Bucket column in Power Query / DAX to group 44 years into clear periods for trend analysis:
- 1980 - 1989
- 1990 - 1999
- 2000 - 2009
- 2010 - 2019
- 2020 - 2024

This makes it easy to compare construction activity across decades instead of looking at 44 individual years.

## Key Insights
1. **Permit volume exploded after 2020** - stayed flat until 2000, then steady growth, then sharp spike to 25K+ per year.
2. **78% are still In Progress** - huge backlog, very few permits are fully closed.
3. **Small Residential Projects dominate** - 45K permits, followed by Plumbing (43K) and Mechanical (36K).
4. **Construction Value exploded after 2020** - stayed below $5bn for 40 years, then jumped past $10bn to almost $14bn. This is the biggest story in the data.

## Tools Used
Power BI Desktop, Power Query, DAX

## DAX Measures Used
- `Total Permits = COUNTROWS(Permits)`
- `Total Construction Value = SUM(Permits[Construction_Value])`
- `Avg Construction Cost = AVERAGE(Permits[Construction_Value])`
- `Status Measures = CALCULATE(COUNTROWS(Permits), Permits[Status_Group] = "Closed" / "Open" / "In Progress")`

## Files in this Repo
- `Building Permit Dashboard.png` - Dashboard screenshot
- `Toronto-Building-Permit-Dashboard.pbix` - Power BI file (65.8MB) - Available on request, too large for GitHub web upload (25MB limit)
