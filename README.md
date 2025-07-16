
# 🧠 HR Analytics & Attrition Risk Dashboard – Power BI Project

## 📌 Project Overview

This project explores employee attrition patterns in a corporate HR dataset to identify **risk factors driving employee churn**, especially among **early-career professionals** in the **Sales department**. The goal is to extract actionable insights that can help HR teams design better retention strategies using Power BI.

---

## 🎯 Objective

- Identify **departments**, **age groups**, and **job levels** most prone to attrition  
- Understand **behavioral and financial indicators** leading to employee exits  
- Recommend **data-driven HR interventions** to reduce attrition and improve satisfaction

---

## 📁 Dataset Details

- **Dataset Name**: `HR database1`
- **Total Records**: ~1,470 employees  
- **Key Columns**:
  - **Demographics**: Age, Gender, EducationField, MaritalStatus
  - **Employment**: JobLevel, Department, JobRole, MonthlyIncome, YearsAtCompany
  - **Work Conditions**: OverTime, DistanceFromHome
  - **Target**: `Attrition` (Yes/No)

---

## 🧰 Tools & Technologies Used

- **Power BI Desktop** – for interactive dashboard & data modeling  
- **DAX (Data Analysis Expressions)** – for calculations and KPIs  
- **Excel** – for initial cleanup  
- **GitHub** – for version control and portfolio presentation

---

## 📊 Key Insights

### 🔺 High-Risk Segments
- **Sales Department** has the **highest attrition rate (20.63%)**
- Attrition is heavily concentrated in **Job Level 1**
- **Young employees (age 20–30)** have the highest churn rates
- Employees with **Marketing or Sales education background** are more likely to leave
- **Sales Representatives** are the most vulnerable role

### 💰 Monthly Income
- Strong inverse relationship between **monthly income** and **attrition**
- **Sales Executives & Managers** (higher income) show lower attrition
- **Sales Representatives & Lab Technicians** (lower income) show higher attrition

### 🚫 Non-Significant Factors
- **Distance From Home**, **OverTime**, and **Marital Status** have negligible impact on attrition in this dataset

---

## 📈 Visuals in Dashboard

- 📉 Attrition Rate by Age  
- 📊 Attrition Rate and Monthly Income by Department & Gender  
- 📊 Attrition Rate by Job Role  
- 📊 Attrition Rate by Job Level  
- 📉 Combined trend of Income, Age, and Distance vs Attrition  
- 🧮 KPI Cards:  
  - Sum of Monthly Income (Total)  
  - Sum of Monthly Income (Attrition)

---

## 🖼️ Dashboard Screenshot

[![Attrition Analytics Dashboard](Attrition_Analytics.png)](Attrition_Analytics.png)

---

## 🧮 DAX Measures Used

```DAX
-- Attrition Count
Attrition Count = CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes")

-- Attrition Rate (%)
Attrition Rate (%) = 
DIVIDE(
    CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes"),
    COUNTROWS(EmployeeData)
)

-- Sum of MonthlyIncome (Attrition)
Sum of MonthlyIncome (Attrition) = 
CALCULATE(SUM(EmployeeData[MonthlyIncome]), EmployeeData[Attrition] = "Yes")

-- Total MonthlyIncome
Total MonthlyIncome = SUM(EmployeeData[MonthlyIncome])

-- Average Distance from Home (Optional)
Average DistanceFromHome = AVERAGE(EmployeeData[DistanceFromHome])

-- Attrition Rate by Department
Attrition Rate by Department = 
CALCULATE([Attrition Count], ALLEXCEPT(EmployeeData, EmployeeData[Department])) 
    / 
CALCULATE(COUNT(EmployeeData[EmployeeNumber]), ALLEXCEPT(EmployeeData, EmployeeData[Department]))

-- Attrition Rate by JobLevel (Matrix format)
Attrition Rate by JobLevel = 
DIVIDE(
    CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes"),
    COUNTROWS(EmployeeData)
)
