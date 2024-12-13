
# Credit Card Financial Performance Dashboard 📊

This project provides an interactive **Credit Card Financial Performance Dashboard** built using Power BI. It provides actionable insights into revenue, spending patterns, and customer demographics, allowing for strategy refinement and financial improvement.

---


## 🖼️ Full Dashboard Snapshot


![data-analysis-power-bI](https://github.com/user-attachments/assets/2f18e09f-b4f6-400d-a2b4-20a03047d4ad)


---

### Live Interactive Dashboard Link : https://app.powerbi.com/view?r=eyJrIjoiMDFjMmY0YTItMGMwYS00ZjliLWIzZTQtNjFhZWI0ZjNjOGE3IiwidCI6ImFiMWYyNWI0LTc0YjgtNDc4MS1hZDM0LWVlZjE2OTg2MDViNiIsImMiOjEwfQ%3D%3D

---

## 🛠️ Problem Statement

The dashboard helps financial institutions:

1. Analyze customer spending patterns and segment performance.
2. Understand the impact of demographic factors on financial metrics.
3. Drive better decisions to optimize credit card offerings and marketing.

---

## 🚀 Key Features

- **Revenue Tracking:** Displays total revenue and interest earned.
- **Customer Segmentation:** Provides insights into gender, age group, income levels, and job-based revenue distribution.
- **Spending Trends:** Breakdown of expenditures into categories like groceries, travel, entertainment, and more.
- **Utilization Analysis:** Visualizes the average credit card utilization ratio.
- **Interactive Insights:** Users can filter by card categories, age groups, marital status, and other demographics.
-**Drill-through Features:** Enabled deeper analysis of specific visuals for users.
---

## 📝 Steps Followed

### Data Preparation
1. Imported the dataset into Power BI Desktop from a `.csv` file.
2. Cleaned and transformed data in Power Query Editor:
   - Removed null/blank values.
   - Ensured data consistency for accurate aggregation.

3. Created calculated columns and measures using DAX for dynamic insights.
4. Ensured interactivity by adding slicers for filtering the dashboard.

### Dashboard Development
- **Theming:** Applied an attractive and appropriate color palette.
- **Custom Visuals:**
  - **Pie Charts** for gender and expenditure breakdown.
  - **Bar Graphs** for revenue by job categories and state-wise performance.
  - **KPI Cards** for quick metrics like total revenue, utilization, and transactions.
- **Advanced Features:** 
  - Added tooltips and dynamic titles for a better user experience.

---

## 📈 Insights and Analysis

1. **Key Metrics:**
   - **Total Revenue:** $55.3M  
   - **Interest Earned:** $7.8M  
   - **Total Transactions:** 656K  
   - **Average Utilization Ratio:** 27.49%  

2. **Spending Breakdown:** 
   - **Bills** contributes the most revenue at 24.9%, followed by **Entertainment** at 17.2%.  
   - **Business professionals** generated $16M in revenue.

3. **Demographic Insights:**  
   - **Male customers** contribute 58% of total revenue.  
   - Most revenue comes from the 40–50 age group.  

4. **Quarterly Trends:**  
   - Stable quarterly revenue with seasonal dips in Q4.  

---

## 🔧 DAX Code Snippets

### 1. Age Group  
```DAX
Age_Groups = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)
```

### 2. Income Group  
```DAX
IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 35000, "Low",
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med",
    'public cust_detail'[income] >= 70000, "High",
    "unknown"
)
```

### 3. Week Number  
```DAX
Week_Num = WEEKNUM('public cc_detail'[week_start_date])
```

### 4. Revenue  
```DAX
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
```

### 5. Current Week Revenue  
```DAX
Current_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[WeekNumber]=MAX('public cc_detail'[WeekNumber])))
```

### 6. Previous Week Revenue  
```DAX
Previous_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    Filter(
        ALL('public cc_detail'),
        'public cc_detail'[WeekNumber]=MAX('public cc_detail'[WeekNumber])-1))

```

---

## 📤 Project Deployment

The dashboard was deployed on Power BI Service for easy sharing.

---

## 🛠️ Tools & Technologies Used 

- Data Visualization (Power BI) 
- Data Analysis Expressions (DAX)

## ⚙️ How to Use the Dashboard

1. **Select Filters:** Use slicers on the left to filter data by card category, age group, education level, marital status, and income group.
2. **Explore KPIs:** View key metrics like total revenue, utilization ratio, and transactions in the top KPI cards.
3. **Analyze Trends:** Click on pie charts, bar graphs, and maps to explore demographic and geographical trends.
