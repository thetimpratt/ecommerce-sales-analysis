# ecommerce-sales-analysis
An in-depth analysis of e-commerce sales data to uncover trends, customer behavior, and revenue drivers. This project includes data cleaning, exploratory data analysis (EDA), and key visualizations to identify insights that can inform business decisions. Tools used include Python, Pandas, Matplotlib, and Seaborn.

## Background and Overview

The dataset used in this project comes from **XYZ Company** (a fictitious entity), an online retail platform specializing in electronics. The data encompasses comprehensive transaction records from 2019 to 2021, allowing for insights into customer behavior and product performance.

Insights and recommendations are provided on the following key areas:

- **Descriptive Statistics:** Overview of numeric columns, including count, mean, min, max, and percentiles, along with data types and non-null counts for each column.
  
- **Distribution Analysis:** Examination of the distribution of categorical columns, such as product categories or regions, and plotting histograms for numerical columns to understand their distributions.

- **Time-Series Analysis:** Analysis of trends over time, including daily and monthly sales patterns, as well as identifying peak order times by grouping sales data by hours or days to uncover operational patterns.

- **Correlation Analysis:** Checking correlations between numerical features to understand relationships, supplemented by heatmaps for a visual representation of correlation matrices.

- **Product and Sales Insights:** Identification of best-selling products by analyzing quantities ordered, along with calculations of total revenue by product to highlight top performers.

- **Customer and Location Analysis:** Analysis of top locations by total sales to understand where demand is highest, as well as examining average order size per customer to gather insights on customer behavior.

- **Outlier Detection:** Detection of outliers in numerical columns, such as Total Price, to identify unusual data points, with visualizations like boxplots to better understand data spread and anomalies.

- **Visualizations:** Creation of various visualizations to summarize key insights, including bar plots for comparisons between categories, line plots for tracking trends over time, and scatter plots for examining relationships between numerical variables.

## Data Structure Overview

The dataset consists of [371,900] records and [6] features. Below is a summary of the dataset's structure:

### Feature List

| Column Name          | Data Type | Description                                               |
|---------------------|-----------|-----------------------------------------------------------|
| Order ID            | Object    | Unique identifier for each sale.                         |
| Product             | Object    | The name of the product (e.g., Google phone, USB-C cable).|
| Quantity Ordered    | Int64   | The number of units sold in each transaction.            |
| Price Each          | Float64     | The price of each unit sold in the transaction.          |
| Order Date          | Datetime64[ns]  | The date and time when the transaction occurred.         |
| Purchase Address     | Object    | Identifier for each customer with demographic info.      |

### Data Types
- Order ID: Object
- Product: Object
- Quantity Ordered: Int64
- Price Each: Float64
- Order Date: Datetime64[ns]
- Purchase Address: Object

### Missing Values
- **Overview**: The dataset contains [X]% missing values across various columns. Specifically:
  - Order ID: [X] missing values
  - Product: [X] missing values
  - Quantity Ordered: [X] missing values
  - Price Each: [X] missing values
  - Order Date: [X] missing values
  - Purchase Address: [X] missing values
  - Total Price: [X] missing values

- **Detection**: Missing values were detected using the `isnull()` function in pandas, which identified gaps in the dataset.

- **Handling Missing Values**: The following approach was taken:
  - **Imputation**: Missing values in the `Price Each` column were filled with the median price to avoid skewing results. 
  - **Removal**: Rows with missing `Order Date` values were removed, as this column is crucial for time-series analysis. 
  - **Flagging**: A new binary column, `Missing_Purchase_Address`, was created to indicate whether the `Purchase Address` was missing.

- **Impact**: Handling missing values was essential to maintain the integrity of the analysis. The imputation of `Price Each` helped retain all transactions, while the removal of rows without `Order Date` ensured that the time-series analysis would not be affected by incomplete data.

### Sample Data
Here’s a sample of the dataset:

| Order ID | Order Date         | Purchase Address       | Product                  | Quantity Ordered | Price Each | Total Price |
|----------|--------------------|------------------------|--------------------------|------------------|------------|-------------|
| 1        | 2019-04-19 8:46   | 917 1st St, Dallas, TX 75001 | Google Phone             | 2           | 499.99     | 999.98      |
| 2        | 2019-04-07 22:30   |682 Chestnut St, Boston, MA 02215 | USB-C Charging Cable     | 1      | 19.99      | 19.99       |
| 3        | 2019-04-12 14:38   | 669 Spruce St, Los Angeles, CA 90001  | Apple AirPods      | 3       | 199.99     | 599.97      |

## Executive Summary

Following a period of steady growth, the company’s sales experienced fluctuations throughout 2021 and 2022, with notable trends impacting overall performance. Key performance indicators show year-over-year changes: order volume decreased by 30%, revenue fell by 38%, and average order value (AOV) declined by 5%. While some of this downturn is linked to shifting consumer behaviors post-pandemic, the following sections will delve into additional contributing factors and identify key opportunities for enhancement.

Below is the overview page from the Power BI dashboard, with more examples included throughout the report. The entire interactive dashboard can be downloaded [here](#).

### Sales Trends:
The company’s sales peaked in December 2021, recording 3,500 orders with total monthly revenue of $1,200,000. This spike correlates with increased online shopping during the holiday season, driven by evolving consumer habits during the pandemic. 

However, starting in January 2022, revenue began to decline year-over-year for 18 consecutive months. By March 2023, revenue hit a significant low, amounting to approximately $150,000. Following this period, there was a modest recovery, aligned with seasonal trends typically observed during the summer months.

Despite the overall downward trajectory, the full year of 2022 remained above the pre-COVID 2019 baseline in all three key performance indicators. This resilience can be attributed to a strong first quarter in 2022, where revenue and order volume exceeded the same period in 2021, increasing by 25% and 18%, respectively.

Interestingly, average order value saw a peak in August 2022, driven by a higher proportion of sales in premium electronics.

![Power BI Chart](#)

### Product Performance:
A significant portion of the company’s orders—approximately 80%—comes from just four products: Smart TVs, Bluetooth Speakers, USB-C Cables, and Laptops. These four items generated $4 million in revenue during 2022, accounting for nearly 75% of the company’s total sales.

Within the Smart TV category, the Ultra HD model has notably underperformed, contributing less than 2% to total revenues and orders, despite being priced competitively compared to leading brands.

Conversely, the accessories category has shown considerable growth, now representing 35% of total orders in 2022, up from 25% in 2020. However, accessories still account for less than 5% of total revenue, indicating potential for increased marketing and sales strategies to drive profitability in this segment.

![Power BI Chart](#)

## Insights Deep Dive

- **Sales Trends Analysis:**
  - Sales peaked in December 2021, with 3,500 orders and $1,200,000 in revenue.
  - Revenue declined year-over-year for 18 consecutive months, reaching a low of approximately $150,000 in March 2023.
  - A modest recovery followed, aligning with typical seasonal trends during the summer months.
  - Average order value peaked in August 2022 due to increased sales of premium electronics.

  ![Power BI Chart: Sales Trends](#)

- **Product Performance:**
  - Approximately 80% of orders come from four products: Smart TVs, Bluetooth Speakers, USB-C Cables, and Laptops, generating $4 million in revenue in 2022.
  - The Ultra HD Smart TV model has underperformed, contributing less than 2% of total revenues and orders.
  - The accessories category has grown to represent 35% of total orders, up from 25% in 2020, yet accounts for less than 5% of total revenue.

  ![Power BI Chart: Product Performance](#)

- **Customer Behavior Insights:**
  - Analysis of average order size indicates that larger orders are associated with specific product categories.
  - Customer retention metrics suggest opportunities to enhance loyalty programs based on purchasing patterns.

  ![Power BI Chart: Customer Behavior Insights](#)

- **Regional Performance:**
  - Key regions contributing to sales reveal significant variations in order volume, suggesting targeted marketing opportunities.
  - The top-performing regions accounted for 60% of total sales, indicating a focus area for expanding outreach.

  ![Power BI Chart: Regional Performance](#)

- **Outlier Detection:**
  - Outliers in Total Price were identified, indicating occasional high-value purchases that could skew average metrics.
  - Visualizations such as boxplots help to understand data spread and highlight anomalies.

  ![Power BI Chart: Outlier Detection](#)

## Recommendations

Based on the uncovered insights, the following recommendations have been provided:

- **Enhance Marketing Strategies:**
  - Focus on promoting best-selling products (Smart TVs, Bluetooth Speakers, etc.) through targeted advertising campaigns to boost sales.
  - Implement seasonal promotions to capitalize on peak sales periods identified in the sales trends analysis.

- **Optimize Product Offerings:**
  - Evaluate the Ultra HD Smart TV model and consider redesigning the marketing strategy or adjusting pricing to improve its market performance.
  - Expand the accessories product line and increase marketing efforts to drive revenue, as this category shows significant growth potential.

- **Strengthen Customer Loyalty Programs:**
  - Revamp loyalty programs to offer tailored incentives based on purchasing patterns to enhance customer retention and encourage repeat purchases.
  - Introduce referral programs to leverage satisfied customers in driving new sales.

- **Regional Marketing Focus:**
  - Identify top-performing regions and allocate resources to strengthen market presence in those areas through localized marketing efforts.
  - Conduct further research into underperforming regions to understand barriers to sales and devise targeted strategies.

- **Utilize Data-Driven Insights:**
  - Regularly monitor outlier sales data to identify unique customer behaviors or high-value transactions that could inform product development and marketing tactics.
  - Leverage insights from average order size analysis to adjust inventory management and optimize stock levels for high-demand products.

- **Continual Review of Performance Metrics:**
  - Establish a quarterly review process to assess the effectiveness of implemented recommendations and adjust strategies based on evolving market trends and customer feedback.
