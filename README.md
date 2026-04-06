# 🏢 Atlas Labs HR Analytics | Power BI Dashboard

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?style=for-the-badge&logo=powerbi)
![DAX](https://img.shields.io/badge/Language-DAX-512BD4?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

## 📌 Project Overview

An end-to-end HR Analytics case study built as part of the
**DataCamp Data Analyst in Power BI Career Track**.

The goal was to answer two core business questions:
- 🎯 **Monitor Key HR Metrics on Employees**
- 🎯 **Understand What Factors Impact Attrition**

---

## 🎬 Dashboard Demo

> *(Waych demo inside assets folder)*

![Dashboard Demo](assets/demo.mp4)

---

## 📊 Report Pages

### 1️⃣ Overview
Key KPIs including Total Employees, Active Employees,
Inactive Employees and Attrition Rate.
Includes hiring trends over the years (2012–2022)
and employee distribution by department and job role.

![Overview](screenshots/overview.png)

### 2️⃣ Demographics
Deep dive into workforce demographics:
- Age distribution & gender breakdown
- Marital status analysis
- Ethnicity vs. Average Salary

![Demographics](screenshots/demographics.png)

### 3️⃣ Performance Tracker
Individual employee performance tracking over time:
- Satisfaction metrics (WorkLife, Job, Environment,
  Relationship)
- Self Rating vs. Manager Rating year-over-year

![Performance Tracker](screenshots/performance_tracker.png)

### 4️⃣ Attrition Analysis
Identifying attrition drivers:
- By Job Role, Tenure, Travel Frequency, Hire Date
- Overtime impact on attrition

![Attrition](screenshots/attrition.png)

---

## 🗄️ Data Model

Star Schema with **1 Fact Table** and **5 Dimension Tables**:

| Table | Type | Description |
|-------|------|-------------|
| `Fact_PerformanceRating` | Fact | Core performance & satisfaction metrics |
| `Dim_Employee` | Dimension | Employee demographics & attributes |
| `Dim_RatingLevel` | Dimension | Rating scale (1–5) |
| `Dim_SatisfiedLevel` | Dimension | Satisfaction scale (1–5) |
| `Dim_EducationLevel` | Dimension | Education classification |
| `DimDate` | Dimension | Date table (generated via DAX code) |

![Data Model](data_model/data_model.png)

### Key Modeling Decisions
- Applied **Role-Playing Relationships** using
  Active & Inactive Relationships with `USERELATIONSHIP()`
- All DAX measures organized in a dedicated `_Measures` table
  for cleaner project structure

---

## 🧮 Key DAX Measures
```dax
-- Attrition Rate
Attrition Rate =
DIVIDE(
    CALCULATE(COUNTROWS(Dim_Employee),
              Dim_Employee[Attrition] = "Yes"),
    COUNTROWS(Dim_Employee)
)

-- Active Employees
Active Employees =
CALCULATE(
    COUNTROWS(Dim_Employee),
    Dim_Employee[Attrition] = "No"
)
```

**Functions Used:** `CALCULATE`, `USERELATIONSHIP`,
`FILTER`, `DISTINCTCOUNT`, `DIVIDE`, `COUNTROWS`

---

## 🔧 Skills Applied

| Skill | Details |
|-------|---------|
| Data Transformation | Type validation, preprocessing based on metadata |
| Data Modeling | Star Schema, Role-Playing Relationships |
| DAX | Calculated measures, time intelligence |
| Visualization | Multi-attribute visuals, cross-page storytelling |
| Report Design | 4-page interactive dashboard |

---

## 📁 Project Structure
atlas-labs-hr-analytics/
│
├── Atlas_Labs_HR.pbix
├── README.md
├── screenshots/
│   ├── overview.png
│   ├── demographics.png
│   ├── performance_tracker.png
│   └── attrition.png
└── data_model/
└── data_model.png

---

## 🎓 Context

Built as part of the
[DataCamp Data Analyst in Power BI Career Track](https://www.datacamp.com)
— End-to-End Project (Case Study HR Analytics in Power BI).

---

## 📬 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat&logo=linkedin)]((https://www.linkedin.com/in/ali-elsabaa-a4b757219/))
