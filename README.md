# **Connect-NG: Q1 2024 Operational Analytics**

## **📌 Project Overview**

**Connect-NG** is a growing Internet Service Provider (ISP) in Nigeria. In early 2024, the company observed a rise in customer churn and inconsistent revenue patterns across different geopolitical zones.

This project analyzes customer behavior, subscription trends, and billing efficiency during the first quarter (Q1) of 2024\. By integrating fragmented data across customer profiles, service plans, and monthly usage, this analysis provides actionable insights to optimize pricing strategies, improve customer retention, and identify high-value regions for infrastructure expansion.

*Note: This dataset is synthetically generated for data analytics practice. While modeled after real-world Nigerian ISP operations, all PII and financial figures are artificial.*

## **🎯 Key Business Questions Addressed**

1. **Revenue Performance:** What is the total Q1 revenue, and how does it trend month-over-month?  
2. **Churn Analysis:** Which subscription plans and regions have the highest churn rates?  
3. **Geographic Penetration:** Which Nigerian regions/states generate the most revenue and data usage?  
4. **Overage Revenue:** What percentage of users exceed their plan limits, and how does it impact revenue?  
5. **Payment Efficiency:** What is the ratio of Late/Failed payments, and what are the preferred payment methods?

## **🗄️ Dataset Structure**

The analysis is based on a relational data model comprising three main tables:

* **Plans (Dimension Table):** Contains static reference data for internet subscription tiers (e.g., Basic, Premium, Fiber-Home), including base prices, data limits, and overcharge rates.  
* **Customers (Dimension Table):** Stores unique profiles, contact details, geopolitical zones (e.g., South-West, North-Central), and current subscriber status.  
* **Billing\_Usage (Fact Table):** A transaction log detailing monthly data consumption, payment status, payment methods, and support tickets filed.

## **🛠️ Methodology & Tech Stack**

### **1\. Data Cleaning & Preparation (Excel)**

* **Standardization:** Formatted Customer IDs (7 chars) and Transaction IDs (10 chars). Capitalized names using PROPER, standardized emails, and formatted phone numbers.  
* **Geographic Cleaning:** Trimmed and standardized Nigerian Region names. Filled missing regions using corresponding State data.  
* **Data Integrity:** Replaced blanks with "N/A", ensured valid Date formats (DD/MM/YYYY), removed duplicate rows, and validated numeric ranges (e.g., ensuring no negative data usage).

### **2\. Data Modeling & DAX (Power BI)**

* **Relational Modeling:** Established 1-to-Many relationships between Customers & Plans, and Customers & Billing.  
* **Calculated Columns (DAX):**  
  * DataOveruse\_GB: Calculated excess data used beyond the plan limit.  
  * Overcharge: Product of DataOveruse\_GB and the plan's specific overcharge rate.  
  * PlanBill: The base price fetched via the RELATED() function.  
  * TotalBill: Sum of PlanBill and Overcharge.  
* **Date Table:** Created a dynamic date table based on the JoinDate boundaries for time-intelligence reporting.

## **📊 Dashboard Previews & Key Insights**

*(Note to user: Add your dashboard image files to an images/ folder in your repo to display them here)*

### **Overview**

* **Scale:** Analyzed 229 transactions across 120 customers.  
* **Usage:** Total data consumed was 16,200 GB, heavily led by the South-West region.  
* **Preferences:** While "Unlimited" is the most common plan, "Premium" drives the highest share of transactions (24.8%), and "Enterprise" generates the highest base revenue.

### **Revenue, Use & Overuse**

* **Revenue:** Generated ₦5M in Gross Plan Revenue, led by Abuja, Rivers, and Plateau states.  
* **Overages:** A massive 17.48% (2.83K GB) of total data usage was overuse. Basic (46.9%) and Premium (47.7%) plan users account for nearly all data overages, highlighting prime upselling opportunities.  
* **Payments:** Card payments are the most popular (37.9%), followed closely by Cash (22.7%).

### **Customer, Churn & Complain**

* **Churn Risk:** The overall churn rate is 10%. The North-West region is a critical risk zone with a 24% churn rate, significantly higher than the national average.  
* **Product Risk:** The "Fiber-Home" plan experiences the highest product churn (12%).  
* **Support & Friction:** A 29.3% complaint rate (67 total complaints) and a 7.8% failed payment rate indicate significant operational friction points that need addressing to improve retention.

## **🚀 How to Run the Project**

1. Clone this repository to your local machine.  
2. Open the Connect-NG\_Analysis.pbix file using Power BI Desktop.  
3. Review the Data Model view to see the table relationships.  
4. Interact with the slicers and visuals on the three report pages to explore the data.

*Created for portfolio demonstration purposes.*