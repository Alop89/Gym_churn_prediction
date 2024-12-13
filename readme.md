# Introduction 
In the highly competitive world of gyms, keeping customers satisfied and loyal is a critical factor for success. Recognizing this challenge, Model Fitness has embarked on an ambitious initiative: leveraging the power of data analytics to predict and prevent customer churn.

Traditionally, measuring customer churn in a gym relied on simple metrics such as membership cancellations or decreased visit frequency. However, this view is limited. Many customers "fade away" silently, without taking explicit cancellation actions.

By analyzing the digital profiles of Model Fitness customers, we aim to develop a predictive model capable of identifying, in advance, those customers most likely to leave the gym.


# Objective 
Our primary objective is to develop a data-driven customer retention strategy for Model Fitness. Through this project, we aim to provide the company with a valuable tool to analyze customer behavior, optimize marketing efforts, and improve the overall customer experience, leading to increased customer retention and sustainable business growth.

# Libraries used 

![Libraries](https://github.com/Alop89/Gym_churn_prediction/blob/main/images/libraries.png)



# Main highlights 

![Heat to show correlation between the variables and determine which ones are important.](https://github.com/Alop89/Gym_churn_prediction/blob/main/images/heatmap.png)

![Dendrogram showing the clusters obtained.](https://github.com/Alop89/Gym_churn_prediction/blob/main/images/dendogram.png)


# ML models 

For this section, logistic regression and random forest models were used.

Logistic regression focuses on predicting the probability that an observation belongs to a specific category, using a sigmoid function to assign a value between 0 and 1. On the other hand, random forests are a set of decision trees that work together to make more accurate and robust predictions. These models differ in their internal functioning, but both are valuable tools in various applications, such as customer classification. The choice of model will depend on the characteristics of the data set and the specific problem to be solved.


![ML results](https://github.com/Alop89/Gym_churn_prediction/blob/main/images/ml_results.png)


![Scores](https://github.com/Alop89/Gym_churn_prediction/blob/main/images/scores.png)

 
* Accuracy: Logistic regression has a slightly higher accuracy (0.93 vs 0.91).
* Precision: Both models have the same accuracy (0.87).
* Recall: Logistic regression has a better recall (0.85 vs 0.79).
* F1 Score: Logistic regression has a higher F1 Score (0.86 vs 0.83).
* AUC-ROC: Logistic regression has a slightly higher AUC-ROC (0.97 vs 0.96).
* Log Loss: Logistic regression has a better log loss (0.18 vs 0.24).
* Confusion Matrix: Logistic regression has fewer false negatives (129 vs 181) and slightly more false positives (107 vs 101).

Based on these results, it can be considered that the logistic regression model has a better performance.



# Some strategies to improve customer loyalty

* Cluster 0: It is recommended to offer rewards for reaching attendance milestones, such as free classes or discounts on gym products (to increase their average spending), as well as organize some exclusive events, and maintain communication that highlights their progress.
* Cluster 1: Offer discounts and rewards to promote the renewal of their contract before it ends, promote packages that fit their short-term goals, and you could also implement promotions to recommend the gym.
* Cluster 2: Introduce flexible memberships, include classes that may be more attractive to this group of customers. Offer close follow-up to check their satisfaction, as well as send motivational messages to generate greater attendance.
* Cluster 3: You can offer free trials of classes that interest them so they find something they like, create an initiation program that is not complicated to follow with trainers who can guide new users, to increase the support of new users.
* Cluster 4: Carry out activities to foster a sense of belonging and community, encourage class attendance by giving some benefits to increase the feeling of the value of membership.
