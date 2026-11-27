# 📊 HR Employee Attrition & Retention Analysis

## Project Overview

The **HR Employee Attrition & Retention Analysis** is an interactive Power BI Business Intelligence project designed to analyze employee attrition, workforce demographics, tenure patterns, job roles, and factors associated with employee turnover.

The project transforms the **IBM HR Analytics Employee Attrition & Performance dataset** into an interactive HR analytics dashboard that helps identify attrition patterns and potentially high-risk employee groups.

The dashboard provides KPI analysis, demographic segmentation, tenure analysis, job-role analysis, and AI-assisted Key Influencers analysis.

---

## Problem Statement

The HR department is experiencing employee turnover and requires better visibility into the employees leaving the organization and the factors associated with attrition.

The project aims to provide an interactive dashboard that helps HR teams:

- Understand the overall employee attrition rate.
- Identify departments with higher employee attrition.
- Analyze attrition across education fields and job roles.
- Examine employee tenure and attrition patterns.
- Analyze demographic factors associated with employee turnover.
- Use Power BI Key Influencers to investigate potential attrition drivers.

The project requirements specify the need to quantify turnover, perform demographic segmentation, analyze tenure, and use the Key Influencers visual for driver analysis.

---

# 🎯 Project Objectives

The project was developed with the following objectives:

### 1. Quantify Employee Turnover

Calculate:

- Total Employees
- Attrition Count
- Attrition Rate %

### 2. Demographic Segmentation

Analyze employee attrition based on:

- Age
- Gender
- Marital Status
- Education Field
- Department
- Job Role

### 3. Tenure Analysis

Analyze employee attrition based on:

- Years at Company
- Employee tenure patterns

### 4. Driver Analysis

Use the Power BI **Key Influencers** visual to analyze factors associated with employee attrition.

The required explanatory factors include:

- Age
- DistanceFromHome
- JobRole
- OverTime
- MonthlyIncome
- WorkLifeBalance

---

# 📂 Dataset

## Dataset Name

**IBM HR Analytics Employee Attrition & Performance**

## Dataset Source

Kaggle

## Target Variable

The primary target variable is:

```text
Attrition
```

Possible values:

```text
Yes
No
```

Where:

- `Yes` → Employee left the organization
- `No` → Employee remained with the organization

## Important Dataset Attributes

| Category | Columns |
|---|---|
| Demographics | Age, Gender, MaritalStatus, EducationField |
| Job Details | Department, JobRole, JobLevel, BusinessTravel |
| Compensation | MonthlyIncome, PercentSalaryHike |
| Tenure | YearsAtCompany, YearsSinceLastPromotion |
| Distance | DistanceFromHome |
| Target | Attrition |

These attributes were identified in the project requirements as important fields for HR attrition analysis.

---

# 🔍 Data Quality Checks

The dataset was imported into **Power BI Desktop** and reviewed using Power Query.

### Column Quality

The dataset was checked for:

- Missing values
- Empty values
- Errors
- Data quality issues
- Data type issues

The imported dataset contained:

```text
1,470 employee records
35 columns
```

The column quality check showed the imported columns as valid with no identified empty or error values during the project preparation.

---

# 🧹 Data Preparation

The dataset was prepared using **Power Query** before building the dashboard.

## HR Data Table

The main dataset table was renamed to:

```text
HR_Data
```

This table contains the employee-level HR analytics data.

---

## Attrition Flag

An `Attrition_Flag` column was created to represent the Attrition field numerically.

The logic was:

```text
Yes = 1
No = 0
```

This provides a numeric representation of employee attrition for analytical purposes.

---

## Age Band

An age grouping field was created for demographic analysis.

The intended age groups were:

```text
18–25
26–35
36–45
46+
```

The age bands provide a simpler way to analyze attrition across employee age groups instead of analyzing individual ages.

---

# 📐 DAX Measures

Five primary measures were created for the dashboard.

---

## 1. Total Employees

Calculates the total number of employee records.

```DAX
Total Employees =
COUNTROWS(HR_Data)
```

### Result

```text
1,470
```

---

## 2. Attrition Count

Calculates the number of employees whose Attrition value is `Yes`.

```DAX
Attrition Count =
CALCULATE(
    [Total Employees],
    HR_Data[Attrition] = "Yes"
)
```

### Result

```text
237
```

---

## 3. Attrition Rate

Calculates the percentage of employees who left the organization.

```DAX
Attrition Rate =
DIVIDE(
    [Attrition Count],
    [Total Employees],
    0
)
```

### Result

```text
16.1%
```

---

## 4. Average Age

Calculates the average age of employees.

```DAX
Average Age =
AVERAGE(HR_Data[Age])
```

### Result

```text
36.92
```

---

## 5. Average Tenure

Calculates the average number of years employees have been with the company.

```DAX
Average Tenure =
AVERAGE(HR_Data[YearsAtCompany])
```

### Result

```text
7.01 Years
```

---

# 📊 Dashboard KPIs

The dashboard header contains five primary HR KPIs.

| KPI | Result |
|---|---:|
| Total Employees | **1,470** |
| Attrition Count | **237** |
| Attrition Rate | **16.1%** |
| Average Age | **36.92** |
| Average Tenure | **7.01 Years** |

The project requirements specify these five KPIs as the primary dashboard metrics.

---

# 📈 Dashboard Visualizations

The dashboard contains several visuals designed to analyze employee attrition from different perspectives.

---

## 1. Attrition by Department

### Visual

**Donut Chart**

This visualization shows the number of employees who left the organization by department.

### Results

| Department | Attrition Count |
|---|---:|
| R&D | **133** |
| Sales | **92** |
| HR | **12** |
| **Total** | **237** |

### Purpose

This visual helps identify which departments account for the largest number of employee exits.

---

# 2. Attrition by Education Field

### Visual

**Bar Chart**

The Education Field visual compares employee attrition across different educational backgrounds.

### Purpose

It helps identify whether particular education fields have higher numbers of employees leaving the organization.

---

# 3. Attrition by Years at Company

### Visual

**Line Chart**

The YearsAtCompany field is plotted against Attrition Count.

### Purpose

This visualization helps identify patterns in employee turnover across different levels of company tenure.

It can help HR investigate whether attrition is concentrated among:

- New employees
- Mid-tenure employees
- Long-tenure employees

The PRD specifically requires tenure analysis using `YearsAtCompany`.

---

# 4. Attrition by Job Role

### Visual

**Bar Chart**

The Job Role visualization compares employee attrition across different job roles.

### Purpose

This helps identify job roles with comparatively higher employee turnover and provides a basis for deeper HR investigation.

---

# 5. Key Influencers Analysis

### Visual

**Power BI Key Influencers**

The Key Influencers visual was configured to analyze employee attrition.

### Analyze

```text
Attrition = Yes
```

### Explain By

The following fields were added:

- Age
- DistanceFromHome
- JobRole
- OverTime
- MonthlyIncome
- WorkLifeBalance

### Purpose

The Key Influencers visual helps identify factors that are statistically associated with the selected attrition outcome.

The PRD specifically requires Key Influencers analysis using these employee and work-related factors.

---

# 🎛️ Interactive Filters

The dashboard includes three interactive slicers.

## 1. Gender

Allows HR users to analyze attrition across different gender groups.

## 2. Department

Allows users to focus the dashboard on a specific department.

## 3. Marital Status

Allows analysis of attrition across different marital-status groups.

These slicers provide interactive segmentation of the HR workforce.

---

# 🔄 Dashboard Interactivity

The dashboard supports interactive filtering between visuals.

For example, selecting a department allows the dashboard KPIs and other visuals to update according to the selected department.

This enables users to move from an overall workforce view to a more focused departmental analysis.

---

# 🧪 Dashboard Testing & Validation

The dashboard was tested to verify that the KPI calculations and interactive filters produced the expected results.

## Overall Validation

The expected overall values were:

```text
Total Employees = 1,470
Attrition Count = 237
Attrition Rate = 16.1%
```

These values were checked against the dataset.

---

## Department Filter Test

The dashboard was tested using the **Sales** department filter.

### Sales Department

```text
Total Employees = 446
Attrition Count = 92
Attrition Rate = 20.6%
```

This confirmed that the dashboard responded correctly to department-level filtering.

---

## Combined Filter Test

The dashboard was also tested using:

```text
Department = Sales
Gender = Female
```

The resulting values were:

```text
Total Employees = 189
Attrition Count = 38
Attrition Rate = 20.1%
```

The filters were then cleared to return the dashboard to the overall workforce view.

---

# 💡 Key HR Insights

The completed dashboard provides the following initial insights.

## Overall Attrition

The organization has:

```text
1,470 Employees
237 Employees with Attrition = Yes
16.1% Overall Attrition Rate
```

This establishes the baseline employee turnover level.

---

## Departmental Attrition

R&D has the highest attrition count among the three departments analyzed:

```text
R&D → 133
Sales → 92
HR → 12
```

R&D therefore accounts for the largest number of employees who left in this dataset.

---

## Sales Department

When filtering the dashboard to Sales:

```text
Employees = 446
Attrition = 92
Attrition Rate = 20.6%
```

The Sales department's filtered attrition rate is higher than the overall workforce attrition rate.

---

## Gender & Department Analysis

When combining:

```text
Department = Sales
Gender = Female
```

the dashboard shows:

```text
Employees = 189
Attrition = 38
Attrition Rate = 20.1%
```

This demonstrates the value of combining slicers to investigate specific employee segments.

---

## Tenure Analysis

The YearsAtCompany analysis provides a view of attrition across employee tenure.

This can help HR investigate whether employee exits are concentrated at particular stages of the employee lifecycle.

---

## Job Role Analysis

The Job Role analysis provides a more detailed view of employee turnover and helps identify roles that may require additional investigation.

---

## Key Influencers

The Key Influencers visual provides an AI-assisted analytical view of factors associated with employee attrition.

The analysis includes:

- Age
- DistanceFromHome
- JobRole
- OverTime
- MonthlyIncome
- WorkLifeBalance

The visual should be interpreted as identifying statistical associations in the dataset rather than proving direct causation.

---

# ❓ Business Questions Addressed

The dashboard was designed to help answer the following HR questions:

### Workforce

- How many employees are currently represented in the dataset?
- How many employees have left?
- What is the overall attrition rate?

### Department

- Which department has the highest attrition?
- How does Sales compare with R&D and HR?

### Demographics

- How does attrition vary by gender?
- How does attrition vary by marital status?
- Which education fields show higher attrition?

### Tenure

- At what levels of YearsAtCompany is attrition higher?
- Are employees leaving earlier or later in their tenure?

### Job Roles

- Which job roles experience higher employee attrition?

### Employee Factors

- Does distance from home relate to attrition?
- Does overtime relate to attrition?
- Does monthly income relate to attrition?
- Does WorkLifeBalance relate to attrition?

These questions align with the HR analytics objectives defined in the project requirements.

---

# 📊 Dashboard Design

The dashboard was designed around the following analytical structure:

```text
HR Workforce
     ↓
KPI Overview
     ↓
Department Analysis
     ↓
Education Analysis
     ↓
Tenure Analysis
     ↓
Job Role Analysis
     ↓
Key Influencers
     ↓
Interactive Filtering
```

The dashboard provides both high-level KPI monitoring and detailed employee attrition analysis.

---

# 🗂️ Project Structure

```text
HR-Employee-Attrition-Analysis-PowerBI/
│
├── README.md
│
├── PROJECT_DOCUMENTATION.md
│
├── HR Employee Attrition Analysis.pbix
│
├── dataset/
│   └── HR_Analytics.csv
│
├── Screenshots/
│   ├── hr-attrition-overview.png
│   ├── department-education-analysis.png
│   ├── tenure-jobrole-analysis.png
│   └── key-influencers.png
│
└── documentation/
    └── Project_Insights.md
```

> File and folder names can be adjusted according to the final files included in the GitHub repository.

---

# 🛠️ Tools & Technologies

## Microsoft Power BI

Used for:

- Dashboard development
- Data visualization
- KPI creation
- Interactive filtering
- Key Influencers analysis

## Power Query

Used for:

- Data import
- Data quality checking
- Data transformation
- Column preparation

## DAX

Used for:

- KPI calculations
- Attrition calculations
- Average calculations
- Analytical measures

## CSV

Used as the source data format.

## Kaggle

Used as the source of the IBM HR Analytics dataset.

## VS Code

Used for:

- Project documentation
- Markdown files
- Git/GitHub project management

## Git & GitHub

Used for:

- Version control
- Project portfolio management
- Repository management

---

# 🧠 Skills Demonstrated

This project demonstrates practical skills in:

- Data Cleaning
- Data Quality Validation
- Data Transformation
- Power Query
- Data Modeling
- DAX
- KPI Development
- Data Visualization
- Interactive Dashboard Development
- HR Analytics
- Employee Attrition Analysis
- Demographic Analysis
- Tenure Analysis
- Job Role Analysis
- Key Influencers Analysis
- Business Intelligence
- Business Insights
- Analytical Storytelling

---

# ⚠️ Project Limitations

The following limitations should be considered when interpreting the analysis:

- The analysis is based on the IBM HR Analytics dataset.
- The dataset represents a specific HR analytics scenario and should not automatically be treated as the actual workforce profile of another organization.
- Key Influencers identifies statistical associations and should not be interpreted as proof of direct causation.
- Dashboard results depend on the quality and structure of the source dataset.
- Additional HR data may be required for deeper retention analysis.

---

# 📦 Project Deliverables

The project deliverables include:

1. **Interactive Power BI `.pbix` file**
2. **GitHub README**
3. **Detailed Project Documentation**
4. **Dashboard Screenshots**
5. **HR Insights Summary**

The PRD identifies the Power BI file, static report, and insights summary as project deliverables.

---

# 🚀 Future Improvements

Potential improvements to the project include:

- Salary comparison between employees who left and stayed.
- Job-level attrition analysis.
- Overtime vs Attrition analysis.
- WorkLifeBalance vs Attrition analysis.
- JobSatisfaction analysis.
- EnvironmentSatisfaction analysis.
- More detailed employee risk segmentation.
- Additional HR retention recommendations.
- Additional dashboard pages for employee satisfaction and compensation analysis.

---

# 📝 Conclusion

The **HR Employee Attrition & Retention Analysis** project demonstrates how Power BI can transform employee-level HR data into an interactive Business Intelligence solution.

The dashboard provides a structured view of:

- Workforce size
- Employee attrition
- Attrition rate
- Employee demographics
- Department-level attrition
- Education-field attrition
- Tenure patterns
- Job-role attrition
- Potential attrition factors

The project combines **Power Query, DAX, data visualization, interactive filtering, and Key Influencers analysis** to create a practical HR analytics dashboard.

The final solution demonstrates the ability to take a raw HR dataset, prepare the data, create analytical measures, develop interactive visualizations, validate results, and communicate meaningful business insights.

---

# 👩‍💻 Author

**Deepika M**

### Junior Data Analyst / Power BI Developer

**Core Skills:**

```text
Power BI
SQL
Python
Power Query
DAX
Data Analytics
Data Visualization
Business Intelligence
```

---

## 📌 Project Status

**Status: Completed ✅**

The HR Employee Attrition & Retention Analysis Power BI project has been completed with KPI cards, department analysis, education-field analysis, tenure analysis, job-role analysis, Key Influencers, and interactive slicers.