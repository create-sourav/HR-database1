# 💼 HR Analytics & Attrition Risk Dashboard — Power BI + Machine Learning Project

---

## 📌 Project Overview
This project explores employee attrition patterns in a corporate HR dataset to identify key risk factors driving churn, particularly among early-career professionals in the **Sales Department**.  
The analysis combines **Power BI visualization** and **Machine Learning modeling** to create a 360° view of attrition risk.

---

## 🎯 Objectives
- Identify departments, age groups, and job levels most prone to attrition  
- Understand behavioral and financial factors leading to exits  
- Build an ML model to predict attrition probability for each employee  
- Recommend **data-driven HR interventions** to reduce turnover  

---

## 📁 Dataset Details
| Item | Description |
|------|--------------|
| **Dataset Name** | HR database1 |
| **Total Records** | ~1,470 employees |
| **Target** | `Attrition` (Yes / No) |
| **Key Columns** |  
Demographics → Age, Gender, EducationField, MaritalStatus  
Employment → JobLevel, Department, JobRole, MonthlyIncome, YearsAtCompany  
Work Conditions → OverTime, DistanceFromHome  

---

## 🧰 Tools & Technologies
- **Power BI Desktop** — interactive dashboard & data modeling  
- **DAX (Analysis Expressions)** — KPIs & measures  
- **Python (Colab)** — EDA, preprocessing, Random Forest ML model  
- **Excel** — initial cleanup  
- **GitHub** — portfolio storage  

---

## 📊 Power BI Insights

### 🔺 High-Risk Segments
- **Sales Department** has the highest attrition (≈ 20.6 %).  
- **Job Level 1** employees show the most churn.  
- **Age 20 – 30** group = highest leavers.  
- **Marketing/Sales education** fields see higher attrition.  
- **Sales Representatives** are the most vulnerable role.

### 💰 Monthly Income
- Strong inverse relation → higher income = lower attrition.  
- Sales Executives & Managers (high pay) → stable.  
- Sales Reps & Lab Technicians (low pay) → at-risk.

### 🚫 Non-Significant Factors
`DistanceFromHome`, `OverTime`, and `MaritalStatus` show minimal impact.

---

## 📈 Dashboard Visuals
- 📉 Attrition Rate by Age  
- 📊 Attrition Rate and Monthly Income by Department & Gender  
- 📊 Attrition Rate by Job Role and Job Level  
- 📉 Combined trend of Income, Age & Distance vs Attrition  
- 🧮 KPI Cards → Total Income vs Income of Attrition Employees  

---

## 🧮 DAX Measures Used
```DAX
-- Attrition Count
Attrition Count =
CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes")

-- Attrition Rate (%)
Attrition Rate (%) =
DIVIDE(
    CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes"),
    COUNTROWS(EmployeeData)
)

-- Sum of Monthly Income (Attrition)
Sum of MonthlyIncome (Attrition) =
CALCULATE(SUM(EmployeeData[MonthlyIncome]), EmployeeData[Attrition] = "Yes")

-- Total Monthly Income
Total MonthlyIncome = SUM(EmployeeData[MonthlyIncome])

-- Average Distance from Home
Average DistanceFromHome = AVERAGE(EmployeeData[DistanceFromHome])

-- Attrition Rate by Department
Attrition Rate by Department =
CALCULATE([Attrition Count], ALLEXCEPT(EmployeeData, EmployeeData[Department])) /
CALCULATE(COUNT(EmployeeData[EmployeeNumber]), ALLEXCEPT(EmployeeData, EmployeeData[Department]))

-- Attrition Rate by JobLevel
Attrition Rate by JobLevel =
DIVIDE(
    CALCULATE(COUNTROWS(EmployeeData), EmployeeData[Attrition] = "Yes"),
    COUNTROWS(EmployeeData)
)
