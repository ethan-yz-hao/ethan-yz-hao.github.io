---
title: "E-Commerce Platform Data Analysis and Predictive Modeling"
excerpt: "A course project (Python Analytics and Cases, Fall 2021) analyzing the sales data from a e-commerce platform, involving RFM analysis, predictive model and customer lifetime value analysis.<br/><img src='/images/portfolio-2-RFM3D.png' width='600'>"
collection: portfolio
---

## Data Source
1. Online Retail Dataset (https://archive.ics.uci.edu/ml/datasets/Online%20Retail) 

    This dataset contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail.The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

## Overview
Python Package Used: datetime, pandas, numpy, matplotlib, seaborn

### Customer Nationality

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-country.png){: width="600"} | 
|:--:| 
| *Customer Nationality* |

### Sales Trend

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-volume-week.png){: width="600"} | 
|:--:| 
| *Sales Grouped by Week* |

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-volume.png){: width="600"} | 
|:--:| 
| *Average Sales of Each Day in a Week* |

## RFM Analysis
Python Package Used: datetime, pandas, numpy, matplotlib, seaborn

Using recency, frequency, and monetary value, all customer is segmented into 8 categories with each indicator splits into "high" or "low" based on the median of each indicator.

| Customer Type | Recency | Frequency | Monetary |
|:--------|:-------:|:-------:|--------:|
| High-Value Loyalist | High | High | High |
| High-Value Loyalist At Risk | Low | High | High |
| Active Potential Loyalist | High | Low | High |
| Hibernating Potential Loyalist | Low | Low | High |
| Low-Value Loyalist | High | High | Low |
| Low-Value Loyalist At Risk | Low | High | Low |
| New Customer | High | Low | Low |
| Hibernating | Low | Low | Low |

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-RFM-customer.png){: width="300"} ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-RFM-money.png){: width="300"} |
|:--:| 
| *Proportion of Different Types of Customer and Amount of money spent grouped by Customer Type* |

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-RFM3D.png){: width="600"} | 
|:--:| 
| *RFM Analysis Result* Note: Frequency and monetary axis is on log10 scale. |

The result of RFM analysis is compared using Kmeans clustering algorithm. Prior to training Kmeans, RFM value is standardized using the standard scaler. The number of clusters is set to 8 to better compare RFM results.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-Kmeans3D.png){: width="600"} | 
|:--:| 
| *Kmeans Result* Note: Frequency and monetary axis is on log10 scale. |

## Churn Prediction
Python Package Used: datetime, pandas, numpy, matplotlib, seaborn, statistics, sklearn

To determine whether a customer is churned, a criterion of 90-days purchase interval from the last purchase is chosen based on the density graph below.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-interval.png){: width="600"} | 
|:--:| 
| *Customer Purchase Interval* |

A number of feature variables is derived based on the original dataset. The nationality of customer is transformed into dummy variable.

| Variable Code | Meaning |
|:--------|--------:|
| AveMonetery | The average amount of money spent based on frequency |
| NumBuy | The number of different types of things brought |
| AveQuantBuy | The average quantity of things brought in each invoice |
| AvePriceBuy | The average price of things brought in each invoice |
| AveTotalBuy | The average amount of money spent in each purchase |

A number of different predictive algorithms is tested using k-fold cross validation.

| Model	| Average Accuracy | Standard Deviation	| Maximum Accuracy | Minimum Accuracy |
|:--------|:-------:|:-------:|:-------:|--------:|
| Logistic Regression | 0.719752 | 0.011095 | 0.735823 | 0.699862 |
| Gradient Boosting | 0.713528 | 0.009773 | 0.73029 | 0.697095 |
| Ada Boost | 0.712604 | 0.011968 | 0.728907 | 0.692946 |
| Random Forest | 0.702928 | 0.007709 | 0.71231 | 0.688797 |
| K-Neighbors | 0.683798 | 0.00671 | 0.69018 | 0.669433 |
| SVC | 0.666745 | 0.002955 | 0.669433 | 0.661602 |
| Gaussian Naive Bayes | 0.663287 | 0.003052 | 0.666667 | 0.65884 |
| Decision Tree | 0.635171 | 0.008165 | 0.650069 | 0.627939 |

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-ROC.png){: width="600"} | 
|:--:| 
| *ROC of Logistic Regression* |

The feature importance of the logistic regression model is further analyze using the permutation method.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-importance.png){: width="600"} | 
|:--:| 
| *Feature Importance* |

## Customer Lifetime Value Analysis
Python Package Used: datetime, pandas, numpy, matplotlib, seaborn, lifetimes

Using the Beta Geometric Negative Binomial Distribution (BG-NBD) model, the the expected number of future purchases and possibility of whether a customer is alive is estimated based on frequency and recency.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-frequency_recency_matrix.png){: width="400"} | 
|:--:| 
| *Frequency Recency Matrix* |

| ![alt]({{ site.url }}{{ site.baseurl }}/images/portfolio-2-probability_alive_matrix.png){: width="400"} | 
|:--:| 
| *Probability Alive Matrix* |

Based on the above analysis, 5 customer with highest expected purchases in the next period is selected.

| Customer ID | Frequency | T | Recency | Monetary | predicted_purchases |
|:--------|:-------:|:-------:|:-------:|:-------:|--------:|
| 14911 | 132 | 373 | 372 | 1089.583788| 0.316007 |
| 12748 | 114 | 373 | 372 | 295.787105| 0.273483 |
| 17841 | 112 | 373 | 371 | 365.996161 | 0.268593 |
| 15311 | 90 | 373 | 373 | 675.198889| 0.216880 |
| 14606 | 89 | 373 | 372 | 136.591573| 0.214418 |

Using the Gamma Gamma model, the average expected value of each customer can be estimated. 5 customer with highest expected value is selected.

| Customer ID | Frequency | T | Recency | Monetary | predicted_purchases | conditional_expected_average_profit |
|:--------|:-------:|:-------:|:-------:|:-------:|:-------:|--------:|
| 16446 | 2 | 205 | 204 | 84236.250000 | 0.013693 | 84660.425564 |
| 12346 | 1 | 325 | 0 | 77183.600000 | 0.000047 | 77965.789328 |
| 15098 | 1 | 182 | 0 | 39916.500000 | 0.000306 | 40326.709551 |
| 15749 | 2 | 332 | 97 | 22267.150000 | 0.001654 | 22383.590581 |
| 16000 | 1 | 2 | 0 | 12393.700000 | 0.037296 | 12529.192039 |