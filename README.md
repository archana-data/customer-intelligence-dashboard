# Customer Intelligence Dashboard | Power BI, RFM Analysis & K-Means Clustering

## 📌 Project Overview

This project analyzes customer purchasing behaviour using the **Online Retail dataset** and builds an interactive customer intelligence dashboard in Microsoft Power BI.

The objective is to understand customer value, identify different customer groups, and generate actionable insights that can support customer retention, engagement, and marketing strategies.

The project combines **data cleaning, exploratory data analysis (EDA), Recency-Frequency-Monetary (RFM) analysis, K-Means clustering, and interactive Power BI visualizations**.

## 🎯 Project Objectives

* Clean and prepare transaction-level retail data for analysis.
* Analyze customer purchasing patterns and spending behaviour.
* Segment customers using RFM analysis.
* Apply K-Means clustering to identify customer groups based on purchasing behaviour.
* Compare customer groups using recency, frequency, and monetary value.
* Build an interactive Power BI dashboard to communicate findings.
* Suggest data-driven strategies for customer engagement and retention.

## 📂 Dataset

**Dataset:** Online Retail

**Source:** UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/352/online+retail

The dataset contains transactions from a UK-based online retail business between December 2010 and December 2011.

### Dataset attributes

| Column      | Description                                  |
| ----------- | -------------------------------------------- |
| InvoiceNo   | Invoice number associated with a transaction |
| StockCode   | Product identifier                           |
| Description | Product description                          |
| Quantity    | Quantity of products purchased               |
| InvoiceDate | Date and time of the transaction             |
| UnitPrice   | Price per unit                               |
| CustomerID  | Customer identifier                          |
| Country     | Customer's country                           |

### Dataset summary

| Metric                       |        Result |
| ---------------------------- | ------------: |
| Original transaction records |       541,909 |
| Records after cleaning       |       392,692 |
| Unique customers analyzed    |         4,338 |
| Total revenue analyzed       | £8,887,208.89 |
| Total units sold             |     5,152,002 |
| Unique invoices / orders     |        18,532 |

*Note: These figures reflect the results obtained in this project. Revenue and order totals depend on the cleaning rules and transaction filters applied.*

## 🧹 Data Cleaning and Preparation

The raw dataset was cleaned before performing customer-level analysis.

The preparation process included:

* Handling missing customer identifiers.
* Removing invalid or unsuitable transaction records according to the cleaning rules.
* Preparing transaction dates for recency calculations.
* Calculating transaction revenue using quantity and unit price.
* Aggregating transaction-level data into customer-level metrics.
* Preparing a clean dataset for RFM analysis and clustering.

After cleaning, the dataset contained **392,692 records** for the subsequent analysis.

## 📊 Exploratory Data Analysis

Exploratory analysis was used to understand the retail dataset and establish a foundation for customer segmentation.

Key business metrics included:

* Total revenue
* Total orders
* Total customers
* Total units sold
* Average order value

The analysis also examined customer purchasing frequency, spending patterns, and the time elapsed since each customer's latest purchase.

## 👥 RFM Analysis

RFM analysis segments customers using three behavioural measures.

| Metric        | Meaning                                          | Business interpretation                                     |
| ------------- | ------------------------------------------------ | ----------------------------------------------------------- |
| Recency (R)   | Days since the customer's most recent purchase   | Lower recency generally indicates a more recent purchase    |
| Frequency (F) | Number of purchases or orders made by a customer | Higher frequency indicates more repeat purchasing           |
| Monetary (M)  | Total customer spending                          | Higher monetary value indicates greater historical spending |

Customer-level RFM metrics were calculated and used to create RFM scores. Customers were then assigned to rule-based segments using the project's scoring and segmentation logic.

### RFM segments

The project identified eight customer segments:

| Segment            | Customers |
| ------------------ | --------: |
| Inactive           |     1,074 |
| High-Value Loyal   |       942 |
| Regular            |       814 |
| At-Risk Frequent   |       486 |
| Recent & Frequent  |       483 |
| High Spender       |       333 |
| At-Risk High Value |       175 |
| Recent Big Spender |        31 |

These segments help distinguish customers by purchase recency, repeat behaviour, and monetary contribution.

### Potential business applications

* **Inactive:** Consider re-engagement campaigns.
* **High-Value Loyal:** Consider loyalty rewards and personalized offers.
* **Regular:** Encourage repeat purchases and customer engagement.
* **At-Risk Frequent:** Investigate declining engagement and consider win-back campaigns.
* **Recent & Frequent:** Encourage continued purchasing.
* **High Spender:** Explore relevant premium products and personalized offers.
* **At-Risk High Value:** Consider targeted retention efforts.
* **Recent Big Spender:** Encourage a second purchase and longer-term engagement.

These actions are recommendations based on segment characteristics, not measured campaign outcomes.

## 🤖 K-Means Clustering

K-Means clustering was used as a second approach to customer segmentation.

The clustering process used the three customer-level RFM features:

* Recency
* Frequency
* Monetary value

A four-cluster solution (**K = 4**) was selected to provide interpretable customer groups, even though the silhouette analysis did not indicate that four clusters had the highest silhouette score.

### Cluster results

| Cluster   | Customers | Share | Mean Recency | Mean Frequency | Mean Monetary |
| --------- | --------: | ----: | -----------: | -------------: | ------------: |
| Cluster 0 |     3,054 | 70.4% |   43.70 days |           3.68 |     £1,353.63 |
| Cluster 1 |     1,067 | 24.6% |  248.08 days |           1.55 |       £478.85 |
| Cluster 2 |        13 |  0.3% |    7.38 days |          82.54 |   £127,187.96 |
| Cluster 3 |       204 |  4.7% |   15.50 days |          22.33 |    £12,690.50 |

### Cluster interpretation

**Cluster 0 — Regular Customers**

The largest cluster, characterized by relatively recent purchases and lower average purchase frequency and spending than the smaller high-value groups.

**Cluster 1 — Inactive / At-Risk**

Customers with a longer time since their last purchase, low average purchase frequency, and lower average monetary value.

**Cluster 2 — Very High-Value Customers**

A small group of 13 customers with exceptionally high average purchase frequency and monetary value.

**Cluster 3 — High-Value Frequent Customers**

Customers with relatively recent purchases, frequent purchasing behaviour, and high average monetary value.

Cluster names are descriptive interpretations of the observed averages rather than labels inherently generated by K-Means.

### RFM segmentation vs. K-Means

The project uses both rule-based RFM segmentation and K-Means clustering. These methods produce different group definitions, so their customer counts should not be treated as interchangeable.

RFM segmentation assigns customers according to scoring rules, while K-Means groups customers based on similarities in their RFM feature values.

## 📈 Power BI Dashboard

An interactive Power BI report was developed to present customer intelligence findings in a business-friendly format.

### 1. Overview

Provides a high-level summary of the business and customer base, including KPI cards, segment counts, cluster information, and customer details.

### 2. Segments

Explores the rule-based RFM segments through customer counts, average monetary value comparisons, segment descriptions, and key insights.

### 3. Clusters

Compares the four K-Means clusters using customer counts, a frequency-versus-monetary scatter chart, cluster-level averages, and business interpretations.

### 4. Customers

Provides a customer-level table with metrics such as CustomerID, Segment, Cluster, Recency, Frequency, Monetary, and RFM score. Filters allow users to explore customers by segment and cluster.

### Dashboard capabilities

* Interactive filtering with slicers.
* Customer-level exploration.
* Comparison of RFM segments.
* Comparison of K-Means clusters.
* Visualization of purchase frequency and spending.
* Customer value and retention insights.

## 💡 Key Findings

* The cleaned analysis included 4,338 unique customers.
* The RFM approach identified eight distinct rule-based customer segments.
* K-Means produced four customer clusters with different purchasing profiles.
* Cluster 0 contained approximately 70.4% of the analyzed customers.
* Cluster 1 had the highest mean recency, indicating that these customers had gone the longest since their latest purchase.
* Cluster 2 contained only 13 customers but had the highest average monetary value.
* The two segmentation approaches provide complementary perspectives on customer behaviour.

## 🛠️ Tools and Technologies

* **Python:** Data preparation and analytical workflow.
* **Pandas:** Data manipulation and customer-level aggregation.
* **Scikit-learn:** K-Means clustering and cluster evaluation.
* **RFM Analysis:** Rule-based customer segmentation.
* **Microsoft Power BI:** Interactive dashboards and visual analytics.
* **CSV:** Export and transfer of customer-level analytical results.

## 🚀 How to Explore the Project

1. Download or clone this repository.
2. Review the analysis notebook, if included.
3. Open `powerbi/Customer_Intelligence.pbix` using Microsoft Power BI Desktop.
4. If prompted, reconnect the data source to the appropriate CSV file.
5. Explore the Overview, Segments, Clusters, and Customers pages.
6. Use the slicers to investigate different customer groups.

## ⚠️ Limitations

* The analysis covers the time period represented by the source dataset and does not represent current customer behaviour.
* Historical purchasing patterns do not guarantee future customer behaviour.
* Very high-spending customers can influence cluster averages.
* The four-cluster solution was selected for interpretability rather than the highest silhouette score.
* The recommended marketing actions have not been validated through controlled experiments.

## 🔮 Future Improvements

* Compare additional clustering algorithms and cluster counts.
* Evaluate the effects of feature scaling and outlier handling.
* Develop customer lifetime value estimates.
* Analyze customer retention and repeat-purchase trends over time.
* Integrate more recent transaction data.
* Measure the effectiveness of targeted marketing campaigns.

## 👤 Author

**ARCHANA S**

Aspiring Data Analyst | Customer Analytics | Python | SQL | Power BI

LinkedIn: [(https://www.linkedin.com/in/archana-s-b1b3562ba/)]

## 📄 Acknowledgements

Dataset: UCI Machine Learning Repository — Online Retail Dataset.

https://archive.ics.uci.edu/dataset/352/online+retail

---

*This project was developed for data analytics and portfolio demonstration purposes.*
