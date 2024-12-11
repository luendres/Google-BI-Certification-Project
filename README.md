# Google-BI-Certification-Project - Fiber Customer Insights Dashboard

A data-driven project showcasing insights into customer service trends and repeat call analysis, completed as part of the Google Business Intelligence Certification.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [BI Documents](#bi-documents)
3. [Data Processing](#data-processing)
4. [Dashboard Creation](#dashboard-creation)
5. [Findings and Presentation](#findings-and-presentation)

---

## Project Overview

The purpose of this project is to design a business intelligence dashboard for Google Fiber’s customer service team. The dashboard aims to provide insights into customer repeat call trends, enabling leadership to assess the team’s effectiveness in resolving customer inquiries on the first contact. 

Using anonymized, fictional data, the project explores call volumes, repeat call patterns, and problem types across different markets. By visualizing these trends, the dashboard offers actionable insights for improving customer satisfaction and optimizing operational efficiency.

### Tools and Technologies Used:
- **BigQuery**: For storing and processing raw data from three CSV files.
- **Tableau**: For data visualization and dashboard creation.
- **SQL**: For querying and transforming data.
- **Google Slides**: For presenting findings to stakeholders.

---

## BI Documents

Three key business intelligence documents were created to structure and guide the project:

1. **Stakeholder Requirements Document**  
   Outlines the goals and needs of the Google Fiber team.
   [View Document](Documents/Stakeholder_Requirements.pdf)

2. **Project Requirements Document**  
   Details the data sources, schema, and success metrics.  
   [View Document](Documents/Project_Requirements.pdf)

3. **Strategy Document**  
   Describes the approach for analyzing trends in repeat calls.  
   [View Document](Documents/Strategy_Document.pdf)

---

## Data Processing
Data was received in three anonymized CSV files representing fictional market data. The following steps were performed:

### Step 1: Data Import and Setup in BigQuery
  The project began with three anonymized CSV files containing data on:
- **Customer call volumes**.
- **Repeat calls (1-7 days since the first contact)**.
- **Problem types** (e.g., account management, technician troubleshooting).

The files were imported into BigQuery and combined into a single database. The consistent column structure allowed for straightforward merging. Key steps included:
- Renaming columns for clarity (e.g., `new_market`, `new_type`).
- Standardizing `0` and `NULL` values for uniformity.
- Joining tables to create a merged dataset.

### Step 2: Query for Insights
SQL queries were used to generate reporting tables for Tableau. For instance, the following query calculated repeat call volumes by market and problem type:
```sql
SELECT 
    new_market,
    new_type,
    COUNT(*) AS total_repeat_calls
FROM 
    summer-drive-441617-s4.fiber.merged_markets
WHERE 
    contacts_n_1 IS NOT NULL 
    OR contacts_n_2 IS NOT NULL 
    OR contacts_n_3 IS NOT NULL 
    OR contacts_n_4 IS NOT NULL 
    OR contacts_n_5 IS NOT NULL 
    OR contacts_n_6 IS NOT NULL 
    OR contacts_n_7 IS NOT NULL
GROUP BY 
    new_market, new_type
ORDER BY 
    new_market, total_repeat_calls DESC;

```
### Step 3: Export for Visualization
The final reporting table was exported from BigQuery and connected directly to Tableau for visualization. The table included:

Aggregated call metrics.
Breakdown by market and problem type.
Repeat call trends over time.

---

## Dashboard Creation
The dashboard was created using Tableau to provide a visual representation of key metrics and insights. It includes interactive features to explore trends in repeat caller volumes, problem types, and market performance.

### Key Insights Presented:
**Repeat Caller Trends:**

Visualized the frequency of repeat calls across seven days post-initial contact.
Most calls occur within the first three days after initial contact, with Market 2 having the highest repeat call volumes.

**Problem Type Breakdown:**

Highlighted which problem types (e.g., account management, technician troubleshooting) contribute most to repeat calls.
Internet and Wi-Fi (Type 5) dominates repeat calls, followed by Construction (Type 4).

**Market Performance:**

Compared repeat call volumes across different markets (Market 1, Market 2, Market 3).
Market 1 has the lowest repeat call volumes, indicating more effective customer service.

### Dashboard Highlights:
Here are some visual examples of the Tableau dashboard:

**Overall Repeat Calls to Custumer Support by Months**

![image](https://github.com/user-attachments/assets/71f2cfdb-22f7-4bd6-8885-bb78d04e9037)

**Market-wise Repeat Calls Overview**

![image](https://github.com/user-attachments/assets/5acfacbe-1745-4cc3-8b7c-de9b75941dd9)

**Problem Type Repeat Calls Overview**

![image](https://github.com/user-attachments/assets/ee1a7974-bd51-4901-9286-41457d9be239)

**You can access the full Tableau dashboard here:**

https://public.tableau.com/views/Fiber_17322885877340/TrendsinRepeatCalls?:language=pt-BR&:sid=&:display_count=n&:origin=viz_share_link

## Findings and Presentation
The project revealed several key insights about repeat caller volumes and customer service issues:

**Market Trends:**

Market 2 had the highest volume of repeat calls, suggesting a need for targeted customer service improvements.
Market 1 showed a higher resolution rate, indicating better initial inquiry handling.

**Problem Type Analysis:**

Internet and Wi-Fi (Type 5) was the leading cause of repeat calls across all markets.
Construction issues (Type 4), while less frequent, had the longest resolution times.

**Repeat Call Trends:**

Most repeat calls occurred within 2-3 days after the initial contact, highlighting gaps in immediate problem resolution.

## Presentation of Findings:
The findings were summarized in a slide presentation to stakeholders, focusing on actionable recommendations for reducing repeat calls and improving overall customer satisfaction.

Download Findings Presentation (PDF)


