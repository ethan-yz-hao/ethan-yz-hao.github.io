---
title: "Beijing Foreign Studies University Global Index 2021 – Global Intelligence Innovation Index"
collection: "research"
type: "Research Assistant"
permalink: "/research/2020-10-research-1"
venue: "Beijing Foreign Studies University"
start: "2020-10"
end: "2023-07"
location: "Beijing, China"
excerpt: "This research aims to develop the Global Intelligence Innovation Index (GIII), a composite index for measuring the intelligence innovation levels of different countries. I designed a machine-learning-based method using K-means and Random Forest algorithm for index construction. Based on the national intelligence innovation framework, the index system of GIII is proposed then used to analyzed the intelligence innovation of 101 countries, providing a global landscape for policy-makers.<br><img src='/images/GIII_method.png' width='600'>"
---

 This research aims to develop the Global Intelligence Innovation Index (GIII), a composite index for measuring the intelligence innovation levels of different countries. I designed a machine-learning-based method using K-means and Random Forest algorithm for index construction. Based on the national intelligence innovation framework, the index system of GIII is proposed then used to analyzed the intelligence innovation of 101 countries, providing a global landscape for policy-makers.

---
Publications:

Ma, Xiaoyu; Hao, Yizhi; Li, Xiao; Liu, Jun; Qi, Jiasen (2023): Evaluating global intelligence innovation: An index based on machine learning methods. In *Technological Forecasting and Social Change* 194, p. 122736. DOI: [10.1016/j.techfore.2023.122736](https://doi.org/10.1016/j.techfore.2023.122736).

---
## Machine-Learning-Based Method for Constructing GIII  
 GIII employed a machine-learning-based method for index construction, specifically for weight calculation. The method, an unsupervised clustering-based random forest model, uses K-means model to obtain cluster label as the target variable for training the subsequent Random Forest Model. The Random Forest Model is used obtain the Mean Decrease of Impurity as index weight, which is then linear aggregated with the standardized dataset to calculate GIII. 

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_method.png){: width="600"} | 
|:--:| 
| *Main procedures of the unsupervised clustering-based random forest model* |

---
## Insights from GIII  
 
 **About Income**  
 In general, countries' intelligence innovation increases with their level of economic development. However, the variance of countries' GIII scores increases with GDP per capita, suggesting that other factors beyond income affect a country' intelligence innovation more significantly when country enters higher income level.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_income_1.png){: width="210"} ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_income_2.png){: width="200"} | 
|:--:| 
| *GIII and GDP per capita* |

 **About Unemployment**  
 GIII is slightly negatively correlated with the unemployment rate, and positively correlated with the labor income share, which is contrary to the usual concern that intelligence innovation and automation in general would increase unemployment and render labor factor redundant in production. In addition, the increasing labor share with GIII suggests that labor plays a more important role in developing intelligence innovation, while generally capital plays a more important role in economic development when the economy grows.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_unemploy_1.png){: width="300"} | 
|:--:| 
| *GIII and Unemployment (Labor Share)* |

 **About Aging**  
 The positive relationship between intelligence innovation and population aging suggests the impact of endogenous response of technology – countries experiencing more severe aging problems turn to automation to compensate for the labor shortage. 

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_age_1.png){: width="200"} | 
|:--:| 
| *GIII and Aging* |

 **About Economic Sector Share**  

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_share_1.png){: width="400"} | 
|:--:| 
| *GIII and the Share of Economic Sectors* |

---
 To launch the newly designed index, along with other indexes in Beijing Foreign Studies University Global Index 2021, a Seminar was held in September 2, 2021.

| ![alt]({{ site.url }}{{ site.baseurl }}/images/GIII_seminar.jpg){: width="600"} | 
|:--:| 
| *The Seminar about GIII* |
