# Uber Booking Analysis Dashboard

## Project Overview

The **Uber Booking Analysis Dashboard** is a one-page Microsoft Power BI report designed to analyze ride demand, booking outcomes, revenue, vehicle mix, payment behavior, and waiting-time patterns. The dashboard turns raw Uber booking data into an interactive business-intelligence view that allows users to monitor key performance indicators and explore trends over time.

**Power BI file:** `Igboanugo_Nkeonyelu_Uber_Dashboard.pbix`

The report title and subtitle are:

> **Uber Booking Analysis Dashboard**  
> Demand trends, vehicle mix, payment behavior, waiting time and key booking metrics

---

## Business Purpose

The dashboard is designed to help a business or operations user answer questions such as:

- How many rides were requested and successfully completed?
- How much revenue was generated?
- What is the average fare for completed rides?
- What percentage of bookings were cancelled by customers?
- How does ride demand change over time?
- What does the 7-day trend indicate beyond daily fluctuations?
- Which vehicle types contribute most to ride volume?
- Which payment methods are most common for completed rides?
- How does average waiting time vary by booking status?

The report therefore combines **operational performance**, **customer behavior**, **financial metrics**, and **time-series analysis** in a single dashboard.

---

## Data Model

The Power BI model contains two visible model tables:

- **`uber_powerbi_data`** — the primary Uber booking dataset containing operational fields such as vehicle type, payment method, and booking status.
- **`Calendar`** — a date-oriented table used for date filtering, date hierarchy analysis, and report measures.

The dashboard uses a date hierarchy with **Year, Quarter, Month, and Day** levels, allowing the time-series visual to support analysis at different levels of detail.

The report includes a date slicer configured as a **Between** filter for the 2024 reporting period.

---

## Key Performance Indicators

The main KPI area contains five measures:

| KPI | Purpose |
|---|---|
| **Total Rides** | Measures overall ride/booking volume. |
| **Completed Rides** | Measures successfully completed rides and helps distinguish completed activity from total demand. |
| **Total Revenue** | Summarizes revenue generated from the booking data. |
| **Avg Fare per Completed Ride** | Shows the average financial value of a successfully completed ride. |
| **Customer Cancel %** | Measures the proportion of bookings cancelled by customers. |

These KPIs provide a concise executive-level view of overall booking performance before the user moves into more detailed analysis.

---

## Dashboard Visuals

### 1. Ride Demand and 7-Day Rolling Average

A **line chart** compares:

- **Total Rides**
- **7-Day Rolling Average**

against the Calendar date hierarchy.

The rolling-average measure smooths short-term variation and makes the underlying demand trend easier to identify. This is useful when daily ride counts fluctuate heavily and the analyst wants to distinguish temporary spikes from sustained movement.

**Skills demonstrated:**

- Time-series visualization
- Date hierarchy analysis
- Rolling-window analytics
- Trend interpretation
- Power BI measure usage

---

### 2. Vehicle Mix by Month

A **100% stacked column chart** analyzes:

- **Month**
- **Vehicle Type**
- **Total Rides**

This view shows how the composition of ride activity changes across vehicle categories over time. Because the chart is normalized to 100%, it is particularly useful for comparing **vehicle-type share/mix** rather than only comparing absolute ride counts.

**Skills demonstrated:**

- Categorical segmentation
- Monthly trend analysis
- Composition analysis
- Interactive visual design

---

### 3. Completed Rides by Payment Method

A **donut chart** breaks down **Completed Rides** by **Payment Method**.

The visual displays each payment method as a percentage of completed rides, helping the user understand customer payment preferences and the relative importance of each payment channel.

**Skills demonstrated:**

- Customer behavior analysis
- Percentage-of-total visualization
- Business segmentation
- Completed-ride analysis

---

### 4. Average Waiting Time by Booking Status

A **bar chart** compares **Average Waiting Time** across **Booking Status** categories.

This provides an operational view of whether certain booking outcomes are associated with longer waiting periods. It can help identify potential service issues and support investigation into whether waiting time contributes to cancellations or other unsuccessful booking outcomes.

**Skills demonstrated:**

- Operational performance analysis
- Category comparison
- Service-quality analysis
- Business interpretation of metrics

---

### 5. Date Slicer

The dashboard contains an interactive **date slicer** using the `Calendar[Date]` field.

The slicer allows users to narrow the dashboard to a selected time period so that KPIs and visuals can be analyzed for a specific date range rather than only for the full dataset.

**Skills demonstrated:**

- Interactive filtering
- Date-table usage
- Report usability
- Dynamic dashboard analysis

---

## Power BI Skills Demonstrated

This project provides practical evidence of the following Power BI and data-analytics skills:

### Data Analysis

- Exploratory business analysis
- Ride-volume analysis
- Revenue analysis
- Customer cancellation analysis
- Payment-method analysis
- Waiting-time analysis
- Vehicle-mix analysis
- Time-series and rolling-average analysis

### Power BI

- Power BI Desktop report development
- Semantic-model measures
- KPI/card visuals
- Line charts
- Bar charts
- Donut charts
- 100% stacked column charts
- Date slicers
- Date hierarchies
- Interactive filtering
- Visual sorting
- Percentage-of-total presentation
- Dashboard layout and information hierarchy

### Data Modeling

- Use of a dedicated **Calendar** table
- Separation of date-oriented analysis from the primary Uber dataset
- Measure-driven reporting
- Combining fact-level booking attributes with reusable business metrics

### Business Intelligence

- Translating raw booking data into meaningful KPIs
- Designing visuals around business questions
- Combining financial, operational, and customer metrics
- Building a dashboard that supports both summary and detailed analysis
- Communicating analytical findings visually

---

## Analytical Workflow Demonstrated

The project represents the following business-intelligence workflow:

```text
Raw Uber Booking Data
        ↓
Data Preparation / Modeling
        ↓
Calendar + Booking Data
        ↓
Business Measures
        ↓
KPI Calculation
        ↓
Trend and Segmentation Analysis
        ↓
Interactive Power BI Dashboard
        ↓
Business Interpretation
```

This demonstrates that Power BI was used not simply to create charts, but to organize data into a decision-support dashboard.

---

## Examples of Insights the Dashboard Supports

The dashboard is structured to support analysis such as:

- Identifying periods of higher or lower ride demand.
- Comparing daily ride activity with a smoothed 7-day trend.
- Determining whether the mix of vehicle types changes from month to month.
- Evaluating which payment methods account for the largest share of completed rides.
- Monitoring customer cancellation behavior.
- Comparing waiting times across booking outcomes.
- Evaluating how operational and financial performance changes when the reporting period is filtered.

The exact conclusions depend on the selected date range and data values, so the dashboard is intended to support **interactive analysis rather than a single static conclusion**.

---

## Skills Matrix Evidence

This Power BI artifact provides direct evidence for **CIDM/ECON 6308 — Seminar in Data Analytics**.

### Strong skills demonstrated

1. **Power BI dashboard development**
2. **KPI design and business-metric analysis**
3. **Data visualization and visual storytelling**
4. **Time-series and rolling-average analysis**
5. **Interactive filtering and segmentation**

It complements the course's machine-learning project by demonstrating the **business-intelligence and data-visualization side of data analytics**.

---

## GitHub / Portfolio Evidence

A portfolio repository for this project could contain:

```text
uber-booking-powerbi-dashboard/
│
├── README.md
├── docs/
│   ├── dashboard-overview.md
│   ├── data-dictionary.md
│   └── screenshots/
│       └── uber-dashboard.png
│
├── powerbi/
│   └── Igboanugo_Nkeonyelu_Uber_Dashboard.pbix
│
└── analysis/
    └── key-insights.md
```

The repository README should explain:

- The business problem
- The dataset
- The KPIs
- The Power BI data model
- The visualizations
- The analytical questions addressed
- Screenshots of the completed dashboard
- Key skills demonstrated

---

## Potential Enhancements

The existing dashboard is a strong business-intelligence artifact. Future improvements could include:

- Additional drill-through pages for vehicle, customer, or location analysis
- Geographic pickup/drop-off mapping if location fields are available
- Driver cancellation and incomplete-booking KPIs
- Revenue trends by vehicle type
- Fare distribution analysis
- Peak-hour/day-of-week analysis
- Tooltip pages for richer detail
- More explicit data-quality indicators
- Forecasting or anomaly detection
- Row-level security for different business-user groups
- Automated refresh if connected to a live or cloud-hosted data source

These enhancements are optional and are **not required to demonstrate the core Power BI skills already shown by the project**.

---

## Summary

The **Uber Booking Analysis Dashboard** demonstrates the ability to transform booking data into an interactive Power BI decision-support tool. It combines KPI reporting, time-series analysis, customer/payment behavior, vehicle segmentation, waiting-time analysis, date filtering, and visual storytelling.

For the skills matrix, this project is strong evidence of:

> **Power BI dashboard development, exploratory/business analysis, KPI design, data visualization, time-series analysis, and interactive business intelligence.**
