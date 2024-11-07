# Project Title: Customer Segmentation for a Subscription Service 
## Welcome to my Portfolio!
This Project is submitted in partial fulfillment of the requirement for a certification in Data Analysis. In this portfolio, I have included a variety of projects that showcase my data analytics skills. You will find links to the dashboard and reports I have created using various tools such as Power BI, Excel, and SQL. These projects demonstrate my ability to analyze and present data in a clear and visually appealing way, making it easy for decision-makers to understand the insights and take action.
#### Thank you for your time! I am looking forward to receiving feedback from you soon.

[Context](#context)

[Data Sources](#data-sources)

[Data Description](#data-description)

[Tools Used](#tools-used)

[Data Preparations and Cleaning](#data-preparations-and-cleaning)

[Data Analysis](#data-analysis)

[Insights](insights)

[Conclusions](#conclusions)

[Recommendations](#recommendations)

---
## Context
This project involves analyzing customer data for a subscription service to identify segments and trends. The primary goal is to understand customer behavior, track subscription types, and identify key trends in cancellations and renewals. The insights from the data will be valuable for understanding behavioural trends, and demographics of each customer, making it useful for marketers and finance researchers

## Data Sources
The primary source of data used is the Incubator Hub.

## Data Description
This dataset provides insights into the sales pattern of 20 customers, it includes the following column:
- CustomerID
- CustomerName
- Region
- SubscriptionType
- SubscriptionStart
- SubscriptionEnd
- Canceled
- Revenue

## Tools Used
 1. Microsoft Excel: Removed and cleaned any inconsistencies in the data and handled missing values. Also created pivot tables to organize and summarize data. [Download Here](https://www.microsoft.com)
 2. SQL: Loaded the cleaned dataset into SQL Server, wrote, and validated queries to extract insights directly from the dataset. [Download Here](https://www.microsoft.com)
 3. Power BI: Created interactive dashboards to showcase findings and visualizations [Download Here](https://www.microsoft.com)

## Data Preparations and Cleaning
- Data Quality Check: The data types of each column were changed to their respective data types
- Duplicates: the dataset contained over a thousand duplicates, it was detected using conditional formatting, and the duplicates were removed using the remove duplicates in the data tab

## Data Analysis
1. Excel:
 - 	Used the ``` YEAR ``` and ``` MONTH``` function to calculate the average subscription duration and the ``` COUNTIF ``` function to identify the most popular subscription types

 ![Customer Data Table](https://github.com/user-attachments/assets/9ec1519a-4d31-46da-b763-77e111ba6b1e)

 - Used pivot table to analyze customer data to find subscription patterns

 ![Customer Data Pivot Table](https://github.com/user-attachments/assets/045fcaf0-71fd-4f91-adbc-5ca640ea125b)

 - create a report dashboard

  ![Customer Data Excel Dashboard](https://github.com/user-attachments/assets/82e1fc0a-5a9c-4d2d-9ff4-cb8b2d0daa90)


2. SQL: wrote queries to extract key insights
   ### SQL Query
- To retrieve the total number of customers from each region
 ```SQL
 SELECT Region,
 count(CustomerID) AS Total_Customers from Customer_Data
 GROUP BY Region
 ```

- The most popular subscription type by the number of customers
 ```SQL
 select top 1 SubscriptionType,
 count(CustomerID) as SubscriptionType_by_Customer from Customer_Data
 Group by SubscriptionType
 Order by SubscriptionType_by_Customer desc
 ```

- Find customers who canceled their subscription within 6 months
 ```SQL
 select CustomerID, SubscriptionStart, SubscriptionEnd
 from Customer_Data
 where DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6
```

- Average subscription duration for all customers
 ```SQL
 select AVG(DATEDIFF(month, SubscriptionStart, SubscriptionEnd)) as Average_Subscription_Duration
 from Customer_Data
 ```

- Customers with subscriptions longer than 12 months
 ```SQL
 select CustomerID, SubscriptionStart, SubscriptionEnd
 from Customer_Data
 where DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12
 ```

- Total revenue by subscription type
 ```SQL
 select SubscriptionType,
 sum(Revenue) as Total_Revenue
 from Customer_Data
 group by SubscriptionType
 ```

- Top 3 regions by subscription cancellations
 ```SQL
 select top 3 Region,
 count(*) as Cancellations
 from Customer_Data
 where Canceled = 'TRUE'
 group by Region
 order by Cancellations desc
 ```

- Total number of active and canceled subscriptions
 ```SQL
 select Canceled, count (*) as Total from Customer_Data
 group by Canceled
 ```
 
 3. Power BI: created a dashboard that visualizes key customer segments, cancellations, and subscription trends

   ![Customer Data Dashboard Power BI](https://github.com/user-attachments/assets/bfc6a8ee-ce8d-4aee-a1dd-bb793aef021c)


## Insights
1. Revenue by Region: Revenue is evenly distributed across the four regions (East, North, South, West), each contributing 25% to the total revenue.
2. Revenue by Subscription Type: The Basic subscription plan generates the highest revenue, followed by Premium and Standard. This could indicate that most customers prefer the Basic plan.
3. Canceled Subscriptions: 51% of the subscriptions are marked as canceled, indicating a fairly high cancellation rate.
4. Revenue by Customer: Some customers contribute more significantly to revenue, with a visible variation across the customer base.
5. Revenue by Month: There is some monthly fluctuation in revenue, with certain months showing higher revenue generation.
6. Subscription by Month: There is no customer with subscriptions within 6 months and no customer with subscriptions longer than 12 months
7. Average Revenue by Metrics: Average revenue by region and subscription type shows consistent levels across categories, with slightly higher averages for Basic and Premium subscriptions.

## Conclusions
1. High Cancellation Rate: The high percentage of canceled subscriptions suggests there may be issues with customer retention.
2. Popularity of Basic Subscription: The Basic plan is the most popular, which may indicate that customers prefer a more affordable option with essential features.
3. Stable Regional Distribution: All regions contribute equally, indicating a well-established customer base across different areas.
4. Revenue Peaks in Specific Months: The fluctuations in monthly revenue could be due to seasonal trends, promotional activities, or other external factors.

## Recommendations
1. Customer Retention Strategy: Investigate the causes of the high cancellation rate and consider implementing strategies like loyalty programs, special offers, or improved customer support to reduce cancellations.
2. Upselling Opportunities: Since the Basic plan is the most popular, consider creating upsell offers to encourage customers to switch to Premium or Standard plans by highlighting added benefits.
3. Customer Segmentation for Targeted Marketing: Identify high-revenue customers and tailor marketing or engagement efforts to retain them, as they play a significant role in overall revenue.
4. Subscription Improvement: Enhance the Basic plan with additional, low-cost features to increase its value proposition while maintaining affordability, potentially increasing customer satisfaction and retention.
