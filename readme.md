# Introduction 
In the highly competitive world of gyms, keeping customers satisfied and loyal is a critical factor for success. Recognizing this challenge, Model Fitness has embarked on an ambitious initiative: leveraging the power of data analytics to predict and prevent customer churn.

Traditionally, measuring customer churn in a gym relied on simple metrics such as membership cancellations or decreased visit frequency. However, this view is limited. Many customers "fade away" silently, without taking explicit cancellation actions.

By analyzing the digital profiles of Model Fitness customers, we aim to develop a predictive model capable of identifying, in advance, those customers most likely to leave the gym.


# Objective 
Our primary objective is to develop a data-driven customer retention strategy for Model Fitness. Through this project, we aim to provide the company with a valuable tool to analyze customer behavior, optimize marketing efforts, and improve the overall customer experience, leading to increased customer retention and sustainable business growth.

# Libraries used 
import pandas as pd
import numpy as np 
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score, confusion_matrix, log_loss
from sklearn.cluster import KMeans
from scipy.cluster.hierarchy import linkage, dendrogram



# Main highlights 




# ML models 

For this section, logistic regression and random forest models will be used.

Logistic regression focuses on predicting the probability that an observation belongs to a specific category, using a sigmoid function to assign a value between 0 and 1. On the other hand, random forests are a set of decision trees that work together to make more accurate and robust predictions. These models differ in their internal functioning, but both are valuable tools in various applications, such as customer classification. The choice of model will depend on the characteristics of the data set and the specific problem to be solved.

## Obtención de variable objetivo y características 
df.drop('effective_cancellation', axis = 1, inplace = True)
X = df.drop('churn', axis = 1)
y = df['churn']

## División en conjuntos de entrenamiento y prueba 
X_train, X_test, y_train, y_test = train_test_split(X, y, train_size=0.2, random_state=0)

## Escalado de variables
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

## Modelos
logistic_model = LogisticRegression()
rf_model = RandomForestClassifier()

## Entrenamiento
logistic_model.fit(X_train_scaled, y_train)
rf_model.fit(X_train_scaled, y_train)

## Predicciones
logistic_pred = logistic_model.predict(X_test_scaled)
rf_pred = rf_model.predict(X_test_scaled)

## Probabilidades para AUC y Log Loss
logistic_prob = logistic_model.predict_proba(X_test_scaled)[:, 1]
rf_prob = rf_model.predict_proba(X_test_scaled)[:, 1]

## Métricas
metrics = {
    "Logistic Regression": {
        "Accuracy": accuracy_score(y_test, logistic_pred),
        "Precision": precision_score(y_test, logistic_pred),
        "Recall": recall_score(y_test, logistic_pred),
        "F1 Score": f1_score(y_test, logistic_pred),
        "AUC-ROC": roc_auc_score(y_test, logistic_prob),
        "Log Loss": log_loss(y_test, logistic_prob),
        "Confusion Matrix": confusion_matrix(y_test, logistic_pred)
    },
    "Random Forest": {
        "Accuracy": accuracy_score(y_test, rf_pred),
        "Precision": precision_score(y_test, rf_pred),
        "Recall": recall_score(y_test, rf_pred),
        "F1 Score": f1_score(y_test, rf_pred),
        "AUC-ROC": roc_auc_score(y_test, rf_prob),
        "Log Loss": log_loss(y_test, rf_prob),
        "Confusion Matrix": confusion_matrix(y_test, rf_pred)
    }
}

## Imprimir las métricas
for model, metric in metrics.items():
    print(f"\n{model} Metrics:")
    for m, value in metric.items():
        if m == "Confusion Matrix":
            print(f"{m}:\n{value}")
        else:
            print(f"{m}: {value:.2f}")

# Results 
Logistic Regression Metrics:
Accuracy: 0.93
Precision: 0.87
Recall: 0.85
F1 Score: 0.86
AUC-ROC: 0.97
Log Loss: 0.18
Confusion Matrix:
[[2246  107]
 [ 129  718]]

Random Forest Metrics:
Accuracy: 0.91
Precision: 0.86
Recall: 0.78
F1 Score: 0.82
AUC-ROC: 0.96
Log Loss: 0.24
Confusion Matrix:
[[2248  105]
 [ 186  661]]


 
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