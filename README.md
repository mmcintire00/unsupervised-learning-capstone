# Airline Customer Segmentation
#### Thinkful Unsupervised Learning Capstone Project
#### Mike McIntire (m.mcintire00@gmail.com)

## UPDATE IN PROGRESS (7/24/21): Converting categorical variables to dummies

# Introduction

Businesses frequently conduct customer satisfaction surveys measuring the quality of the service they are providing. The goal of these surveys is to improve the overall experience next time. This project will explore airline passenger satisfaction information acuired after a flight and attempt to cluster the information using several clustering algorithms.

# Goal

The goal of the project is to segment the passenger experiences by customer satisfaction.

# Business Purpose

Clustering passengers based off experience can be extremely useful to executives and mangers in charge of improving the overall experience of the passenger. Specfic elements of a passengers experience can be compared accross groups to identify what controls satisfaction vs. unsatisfied vs. neutral.

# Description

This project will be split into 4 main parts: Data Exploration, Data Cleaning, Data Scaling and Dimenionality Reduction, and Clustering. I'll test several methods for dimensionality reduction: PCA, t-SNE (visualization only), and UMAP. The clustering algorithms implemented will be KMeans, DBSCAN, and Gausian Mixture Model (GMM). I attempted to use Agglomerative Clustering for this project, but run times and computational intensity increased due to the large amount of data points. I decided to unlitmately leave hierarchicak clustering out.

# Data: 

This dataset contains an airline passenger satisfaction survey. It was taken from Kaggle [1] and contains 129880 rows and 24 variables, including the target variable (satisfaction). I'll be using the target variable only for calculating the Adjusted Rand Index(ARI).

* #### Variables:

  * Gender: Gender of the passengers (Female, Male)

  * Customer Type: The customer type (Loyal customer, disloyal customer)

  * Age: The actual age of the passengers

  * Type of Travel: Purpose of the flight of the passengers (Personal Travel, Business Travel)

  * Class: Travel class in the plane of the passengers (Business, Eco, Eco Plus)

  * Flight distance: The flight distance of this journey

  * Inflight wifi service: Satisfaction level of the inflight wifi service (0:Not Applicable;1-5)

  * Departure/Arrival time convenient: Satisfaction level of Departure/Arrival time convenient

  * Ease of Online booking: Satisfaction level of online booking

  * Gate location: Satisfaction level of Gate location

  * Food and drink: Satisfaction level of Food and drink

  * Online boarding: Satisfaction level of online boarding

  * Seat comfort: Satisfaction level of Seat comfort

  * Inflight entertainment: Satisfaction level of inflight entertainment

  * On-board service: Satisfaction level of On-board service

  * Leg room service: Satisfaction level of Leg room service

  * Baggage handling: Satisfaction level of baggage handling

  * Check-in service: Satisfaction level of Check-in service

  * Inflight service: Satisfaction level of inflight service

  * Cleanliness: Satisfaction level of Cleanliness

  * Departure Delay in Minutes: Minutes delayed when departure

  * Arrival Delay in Minutes: Minutes delayed when Arrival

# Conclusions

After evaluating PCA, t-SNE, and UMAP for dimensionality reduction, UMAP provides the best results, showing separation into 5 distinct clusters. Using UMAP transformed data, the best clustering methods are KMeans, with 5 components, and GMM, with 4 components. Further analyzing Kmeans, I split the data in half looking at consistency between group 0 and group 1. None of the cluster numbers show consistency between sample group 0 and 1, which might be a reason for concern. The GMM clustering method gives a silhouette score of 0.57 and breaks the data into 4 clusters. I would move forward with the GMM model.

# Recommendations

Moving forward with the GMM clustering results and using the UMAP transformed data, the data is broken into 4 clusters. The four groups would have differing levels of customer satisfaction. Although there are only two target groups identified for the target variable, 4 clusters make sense. The four clusters would likely be divided as Highly Satisfied, Moderately Satisfied, Moderately Unsatisfied, and Highly Unsatisfied. From my analysis, the best way to address customers concerns is by looking at the end members of the data. This would mean comparing the scores and experience of the Highly Satisfied vs. the Highly Unsatisfied group. What are the major differences between the two groups? Are these issues that can be addressed by the airline (ease of booking, seat comfort, check-in, etc.), or are they things outside the companies control (flight delays for weather)?

# Sources Cited

**[1] Kaggle Data:** https://www.kaggle.com/johndddddd/customer-satisfaction

**[2] Wikipedia; Flight length:** https://en.wikipedia.org/wiki/Flight_length

**[3] DBSCAN Parameter Estimation:** https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html

**[4] Sklearn GMM parameter selection plot:** https://scikit-learn.org/stable/auto_examples/mixture/plot_gmm_selection.html#sphx-glr-auto-examples-mixture-plot-gmm-selection-py

**[5] BIC & AIC use discussion:** https://www.methodology.psu.edu/resources/AIC-vs-BIC/

**[6] BIC Explaination:** https://en.wikipedia.org/wiki/Bayesian_information_criterion
