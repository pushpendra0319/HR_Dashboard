HR Analytics Dashboard — Power BI Project

An interactive, multi-page HR analytics dashboard built in Power BI, covering workforce composition, attendance, performance, payroll, and attrition/recruitment for a company of 3,000+ employees across 13 departments and 52 job roles (2020–2025).

📊 Project Overview

This dashboard turns 10 raw operational datasets into a connected analytics model that lets HR and business leaders explore workforce health from a single executive summary down to department-level and individual-record detail — without touching a spreadsheet.

Data covers: 3,001 employees · 13 departments · 52 job roles · 6 years (2020–2025)

🗂️ Data Sources
Table	Rows	Description
Employees_HR	3,001	Core employee master data (demographics, salary, tenure, status)
Departments_HR	13	Department reference data
Jobs_HR	52	Job roles, grades, and salary bands
Attendance_HR	624,830	Daily attendance records (2020–2025)
Payroll_HR	69,407	Monthly payroll transactions
Performance_HR	9,796	Performance review records
Leave_HR	19,419	Leave requests and approvals
Training_HR	6,450	Training enrollments and completions
Exit_HR	930	Employee exit/termination records
Recruitment_HR	9,001	Recruitment pipeline and candidate records

🏗️ Data Model

A star-schema-style model with Employees_HR as the central hub, Departments_HR and Jobs_HR as pure dimensions, and a dedicated Date Table (generated via DAX, 2020–2025) driving all time-based analysis.

Active relationship: DateTable[Date] ↔ Attendance_HR[Attendance_Date] (main time axis)
Inactive relationships (activated per-measure via USERELATIONSHIP()): Payroll, Leave, Performance, Training, Exit, and Hire dates — kept inactive to avoid ambiguous filter paths, since all fact tables also connect to Employees_HR via Employee_ID

All measures are organized in a dedicated _Measures table (30+ DAX measures) covering workforce, attendance, payroll, performance, training, exit, and recruitment KPIs.

📑 Dashboard Pages
Executive Overview — headcount, attrition rate, payroll cost, and headcount trend at a glance
Workforce Composition — gender split, employment type mix, salary by department
Attendance & Leave — attendance rate vs. target, attendance trend, leave distribution, department-level attendance table
Performance & Training — KPI vs. productivity by department, training cost/completion, department-level performance table
Payroll & Compensation — payroll cost trend, salary vs. job grade bands, pay equity by gender and department
Attrition & Recruitment — exit types, attrition by department, recruitment funnel, department-level exit/hiring table

Every page includes synced slicers (Department, Employment Status, Gender, Year), so filtering on one page carries across the whole dashboard. Two hidden drillthrough pages ("Department Detail" and "Exit & Hiring Detail") provide deeper record-level detail without cluttering the main views.

🛠️ Tools & Techniques Used
Power Query (M) — data cleaning, type correction, custom columns (Age, Tenure, Payroll Month Date), column splitting
Power BI Data Modeling — star schema, active/inactive relationships, date table
DAX — 30+ measures including CALCULATE, DIVIDE, USERELATIONSHIP, time-intelligence patterns
Visualizations — cards, bar/column/line/area charts, donut/pie charts, scatter plot, gauge, funnel chart, combo chart, tables
Interactivity — synced slicers across pages, drillthrough pages, cross-filtering

💡 Key Insights
Attrition is highest in Customer Support (39.6% of everyone ever employed there has exited), followed by Quality Assurance (38.3%) and Legal (36.7%). IT and Sales have the highest raw exit counts, but that's mainly a function of headcount size — rate tells the real story.
Every department is below the 95% attendance target — company-wide average sits around 74-76%, with no meaningful variance between departments. This points to a systemic attendance issue rather than one team underperforming.
Finance shows the widest pay equity gap — men earn ~17.4% more than women on average in that department. Operations shows a smaller gap in the opposite direction (-14.7%). Most other departments (Sales, IT, HR, QA) sit under 2% gap.
Recruitment funnel drop-off is largest at the rejection stage — 50.4% of all 9,001 applications end in "Rejected," compared to 21.3% Hired, 15.4% On Hold, and 12.9% Withdrawn. Half of every applicant pool never converts.

🚀 How to Use
Open HR_Analytics_Dashboard.pbix in Power BI Desktop
Use the slicer row (Department / Status / Gender / Year) on any page to filter the whole report
Right-click a department or exit-type value on Page 2, 3, or 6 to drill through to detail pages
Hover over trend charts for extra context via custom tooltips

Built as a self-guided HR analytics project — Power Query, data modeling, DAX, and dashboard design all done from raw CSV exports to a final 6-page interactive report.
