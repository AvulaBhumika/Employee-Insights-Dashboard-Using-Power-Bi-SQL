# 🧠 Employee Insights Dashboard — Power BI Project

![Dashboard](image-1.png)

### 📊 Overview

This project presents an **Employee Insights Dashboard** built in **Microsoft Power BI**, designed to analyze workforce distribution, compensation, and organizational structure using multiple relational tables from an HR schema (`hr_boom`).

The dashboard provides clear visual insights into key HR metrics such as **average salary**, **employee distribution**, **department-wise headcount**, **geographic spread**, and **hiring trends over years**.

---

## 🚀 Objectives

* Build a **relational data model** from multiple HR tables (Employees, Departments, Locations, Jobs).
* Create a unified **Power BI dashboard** for HR analytics.
* Use **DAX measures**, **visual interactions**, and **filters** for deeper insights.
* Enable data-driven understanding of workforce composition and trends.

---

## 🗂️ Dataset Information

The project uses sample HR schema tables imported from **MySQL Workbench** into Power BI:

| Table Name            | Description             | Key Columns                                                                   |
| --------------------- | ----------------------- | ----------------------------------------------------------------------------- |
| `hr_boom employees`   | Employee master data    | `employee_id`, `department_id`, `salary`, `hire_date`, `job_id`, `manager_id` |
| `hr_boom departments` | Department details      | `department_id`, `department_name`, `location_id`                             |
| `hr_boom locations`   | Location and city data  | `location_id`, `city`, `country_id`                                           |
| `hr_boom jobs`        | Job title and role data | `job_id`, `job_title`, `min_salary`, `max_salary`                             |

---

## 🧩 Data Modeling

### **Relationships**

The data model was built in **Power BI Model View**, connecting tables via primary and foreign keys:

```
hr_boom locations[location_id]  1 ──── ∞  hr_boom departments[location_id]
hr_boom departments[department_id]  1 ──── ∞  hr_boom employees[department_id]
hr_boom jobs[job_id]  1 ──── ∞  hr_boom employees[job_id]
```

All relationships were configured with **Cross Filter Direction: Both** to allow bidirectional data filtering across visuals.

---

## 🧮 DAX Measures Used

| Measure Name               | Formula                                                                   | Purpose                             |
| -------------------------- | ------------------------------------------------------------------------- | ----------------------------------- |
| **Employee Count**         | `Employee Count = COUNT('hr_boom employees'[employee_id])`                | Total number of employees           |
| **Average Salary**         | `Average Salary = AVERAGE('hr_boom employees'[salary])`                   | Average employee salary             |
| **No. of Departments**     | `No of Departments = DISTINCTCOUNT('hr_boom departments'[department_id])` | Unique departments count            |
| **Max Experience (Years)** | `Max Experience = MAX('hr_boom employees'[Experience (Years)])`           | Highest years of experience         |
| **Hire Year**              | `Hire Year = YEAR('hr_boom employees'[hire_date])`                        | Extract year for hiring trend chart |

---

## 🧰 Steps Followed

### **1️⃣ Connecting to MySQL**

* Installed and configured **MySQL Connector/NET**.
* Connected Power BI Desktop to the MySQL database via
  **Get Data → MySQL Database → Server = localhost:3306 → Database = hr_boom**.

### **2️⃣ Data Preparation**

* Imported relevant tables (`employees`, `departments`, `locations`, `jobs`).
* Cleaned missing values and irrelevant columns.
* Ensured matching data types (IDs as integers, salary as numeric, dates as date/time).

### **3️⃣ Building Relationships**

* Opened **Model View**.
* Established correct 1→∞ relationships between tables.
* Corrected any auto-generated mismatched relationships (like manager_id to employee_id).

### **4️⃣ Creating DAX Measures**

* Created new DAX measures for KPI cards (Employee Count, Avg Salary, etc.).
* Used DISTINCTCOUNT and AVERAGE where appropriate.
* Verified measure values with sample data cross-check.

### **5️⃣ Designing the Dashboard Layout**

* Created four main zones:

  * **KPI Section:** Max Experience, Avg Salary, No. of Departments, Total Employees.
  * **Distribution Section:** Employee count by department, job title.
  * **Geographic Section:** Employees by city (map + bar chart).
  * **Trend Section:** Hiring trend over the years.
* Added **slicers** for Department Name and Country.
* Applied consistent color theme and fonts for a cohesive design.

### **6️⃣ Formatting & Refinement**

* Customized all **card titles** and fonts via Format Pane → Title → Title Text.
* Sorted bar charts by descending metric values.
* Removed blank entries using visual-level filters (uncheck `(Blank)` under city).
* Applied background color and uniform grid alignment for presentation quality.

---

## 📊 Dashboard Features

### **KPI Cards**

| Metric                      | Description                      |
| --------------------------- | -------------------------------- |
| **Max Years of Experience** | Longest employee tenure in years |
| **Average Salary in USD**   | Average of all employee salaries |
| **Total Departments**       | Distinct count of departments    |
| **Total Employees**         | Total employee count             |

### **Visuals**

| Visualization         | Data Used                    | Description                            |
| --------------------- | ---------------------------- | -------------------------------------- |
| **Donut Chart**       | Employee Count by Department | Workforce distribution by department   |
| **Bar Chart**         | Avg Salary by Department     | Compares departmental average salaries |
| **Pie Chart**         | Employee Count by Job Title  | Highlights role distribution           |
| **Map Visualization** | Employee Count by City       | Displays geographic spread             |
| **Line Chart**        | Hire Count by Year           | Shows hiring trends over time          |

---

## 🌍 Insights Derived

* **Shipping & Sales** departments hold the majority of employees.
* **Executive** department records the **highest average salary**.
* Most employees are concentrated in **South San Francisco** and **Oxford** cities.
* Hiring peaked in the **late 1990s**, indicating company growth during that phase.
* **107 total employees** spread across **12 departments** and multiple countries.

---

## 🛠️ Tools & Technologies

| Tool                                | Purpose                                            |
| ----------------------------------- | -------------------------------------------------- |
| **Power BI Desktop**                | Data modeling, visualization, and dashboard design |
| **MySQL Workbench**                 | Source database management                         |
| **MySQL Connector/NET**             | Integration between Power BI and MySQL             |
| **DAX (Data Analysis Expressions)** | Calculated measures & KPIs                         |
| **Power Query Editor**              | Data transformation and cleaning                   |

---

## 📷 Dashboard Preview

*(Add your dashboard image here — for example, the one you shared)*

```
![Employee Insights Dashboard](images/dashboard_preview.png)
```

---

## 📁 Project Structure

```
Employee_Insights_Dashboard/
│
├── README.md
├── Employee_Insights.pbix       # Power BI project file
├── data/
│   ├── hr_boom_employees.csv
│   ├── hr_boom_departments.csv
│   ├── hr_boom_locations.csv
│   └── hr_boom_jobs.csv
└── images/
    └── dashboard_preview.png
```

---

## 🏁 Conclusion

This Power BI dashboard serves as a complete **HR Analytics Solution**, transforming relational MySQL data into an intuitive and interactive interface.

It enables stakeholders to:

* Monitor organizational workforce metrics.
* Track hiring trends and geographic presence.
* Compare salary distributions and departmental performance.

---

## ✨ Future Enhancements

* Add **Attrition and Retention Analysis** using termination dates.
* Include **Employee Performance Index** (if available).
* Integrate Power BI with **Power Automate** for scheduled email reporting.

---

### 👨‍💻 Author

**Avula Bhumika**

*Data Analytics | Data Visualization*
📍 Bangalore, India

---

