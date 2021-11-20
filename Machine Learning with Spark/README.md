# Capstone-Project

In this project I used user log data of a fictituous music streaming service Sparkify to predict user churn using the Apache
Spark Python API PySpark. I started off my analyis locally on my desktop computer using a reduced dataset. One of the challenges in working with user log data is that while you have a large number of rows for a single user, this ultimately needs to be reduced to a single row for every single user before a machine learning algorithm can be applied.


Besides using Spark, the special sort of data used for this project and the need to deploy the Notebook to an Amazon Web Services
(AWS) Elastic Map Reduce (EMR) cluster proved somewhat challenging.

### Overview

The project starts off with an analysis of a small subset of the full dataset. At first, all cases of interactions which cannot be attributed to registered users are removed and a brief general overview of the reduced dataset is given. 

Then, churning is defined, a number of different aggregated features (such that for each user only one row will need to be kept) are discussed, created and these features are then compared across the two groups of users, churners and non-churners. In this process, promising features which are subsequently used for the machine learning models are identified.

In the next part the dataset is reduced to one row per customer with only the previously identified relevant features. These features are then further taken care of by removing outliers for numerical features, scaling numerical features using min-max scaling and applying one-hot encoding to categorical features.

Next, the prepared dataset is split into a traing and a test set. This data is then used to compare several different classification machine learning algorithms: logistic regression, random forest classifier, gradient-boosted tree classifier, support vector machines (linear kernel) classifier, decision tree classifier and naive Bayes classifier. In the case of the reduced dataset, the decision tree classifier does best while in the case of the full dataset, the gradient-boosted tree classifier showed the best performance.

Finally, hyperparameter tuning is performed for the best model, feature importances are briefly discussed and a short conclusion is provided.

### Why Predict Churn?

Customer churn is a major issue for many companies since losing customers tends to be directly related to losing revenue. This is also true for the problem considered in this project where customers are either using an ad-financed free version of the service or paying a monthly fee to enjoy music streaming without interruptions by advertisements.

In addition to this, it is generally said that acquiring new customers tends to be more costly than keeping existing ones. Hence, even if a business can somehow compensate for user churn by attracting new users, it will incur an economic loss. Moreover, attracting new users may likely become increasingly difficult over time. 

According to https://smallbiztrends.com/2016/10/customer-retention-statistics.html, lowering churn rates by 5% can increase profitability by between 25% to 125% which is admittedly a rather rough estimate, but it suggests that customer retention should be a major concern for businesses.

Another issue is that as Casey Hill points out in his answer at https://www.quora.com/Why-is-churn-so-important, high churn rates can make it impossible to grow a business and can be thought of as an indicator that there is something inherently wrong with one’s products.

As this brief discussion shows, customer churn is an issue business should take very seriously and try to prevent. Hence, predicting it before it happens can be integral to the success of a business.

While this project is only concerned with predicting whether a user is likely to churn, it is important to keep in mind that a company needs to make use of these predictions and develop a strategy to deal with potential churners. A part of this could be offering these users coupons to entice them to stay. These coupons could also be offered to users in exchange for taking part in a short survey which could help understand why users may be inclined to churn.