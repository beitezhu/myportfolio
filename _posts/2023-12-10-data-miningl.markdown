---
layout: post
title:  Utilizing Machine Learning to Predict Lung Cancer Risk
date:   2023-12-10 20:20:20 +0300
tags:   Machinelearning
---
![image](../assets/image/ML_visual.png)  
I utilized data to train a machine learning model for predicting different stages of lung cancer, accompanied by visualization.
<br/>
<br/>


> - Language: Python(Pandas/NumPy)
- Datasheet:  [Kaggle datasets](https://www.kaggle.com/datasets/thedevastator/cancer-patients-and-air-pollution-a-new-link)
- Sourcecode: [Colab sourcecode](https://colab.research.google.com/drive/18BJ_5277dq9CV8afj87kwjO96tXePM78#scrollTo=y0b-KNePLHaE)
- My role: collaborating with my team members to write code and analyze the results, transforming them into visual presentations and insights.


<br/>
##### Summary: 
I have learned about various machine learning models, including Random Forest, Logistic Regression, and Decision Tree. Normally, during the training process, I usually split the data into a training set and a validation set. I then use the training set to test the accuracy of each model. After comparing the different models, I can identify the most suitable one. Finally, I use that model for prediction.

In this project, my team members and I aim to utilize data to train a machine learning model to predict different stages of lung cancer. This involves an in-depth analysis of risk factors and symptoms associated with lung cancer, using a dataset of 26 discrete variables. These variables describe risk factors and symptoms and their impact on lung cancer, ranging in severity from highest (7) to lowest (1)

The dataset encompasses a broad spectrum of attributes, including demographic information, health-related variables, lifestyle choices, and potential symptoms. These attributes are primarily classified into two categories: “Lung Cancer Risk Factors” and “Lung Cancer Symptoms.”

To achieve our objective, we employ various machine learning algorithms, including Random Forest, Logistic Regression, and Decision Tree. These methods will be instrumental in identifying the relationships between dependent and independent variables, ultimately aiding in accurately predicting lung cancer stages.

![image](../assets/image/ML_slide_sturcture.png)

<br/>
##### Here are the details of how I did that

Step 1: I prepared for a data analysis and machine learning task

```
import numpy as np
import pandas as pd
from matplotlib import pyplot as plt
import seaborn as sns
import statsmodels.formula.api as smf # use both linear and logistic regression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import roc_auc_score
```

Step 2 I split the data into a training set and a test set.

```
df = pd.read_csv("./cancer patient data sets.csv")

print(list(df.columns))

# Convert to numerical encoding
df = df.replace({'Level':{'Low': 1, 'Medium': 2, 'High': 3}})
print(df.shape)

X=df.drop('Level', axis=1)
#remove irrelevant data
X=df.drop('Patient Id', axis=1)

y=df['Level']

X_train,X_test,y_train,y_test = train_test_split(X, y, test_size=0.90, random_state=42)

print("=" * 50)
```

Step 3: I used the logistic regression model to train the data.

```
## Logistic Regression ##

LogClassifier = LogisticRegression(solver='liblinear')

LogClassifier.fit(X_train,y_train)

y_pred_logistic = LogClassifier.predict(X_test)

Results = pd.DataFrame({'Actual':y_test, 'Predictions':y_pred_logistic})

print("Accuracy score with logistic regression")

print(accuracy_score(y_test, y_pred_logistic))

report = classification_report(y_test, y_pred_logistic)
print("Classification Report:\n", report)
print("=" * 50)
```

Step 4 I used the Random Forest Classifier model to train the data.

```
## Random Forest Classifier ##

RForestClassifier = RandomForestClassifier()

RForestClassifier.fit(X_train, y_train)

# Make predictions on the test set
y_pred_rforest = RForestClassifier.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred_rforest)
report = classification_report(y_test, y_pred_rforest)

print(f"Accuracy with Random Forest: {accuracy}")
print("Classification Report:\n", report)
print("=" * 50)
```

Step 5 I used the Decision Tree Classifier model to train the data.

```
## Decision Tree Classifier
DTreeClassifier = DecisionTreeClassifier(random_state=42)
DTreeClassifier.fit(X_train, y_train)

# Make predictions on the test set
y_pred_rforest = DTreeClassifier.predict(X_test)

# Evaluate the model
accuracy = accuracy_score(y_test, y_pred_rforest)
report = classification_report(y_test, y_pred_rforest)

print(f"Accuracy with Decision Tree: {accuracy}")

print("Classification Report:\n", report)
print("=" * 50)
```

Step 6 I studied various contributing factors to determine which ones matter, and then plotting them in a graph.

```
## Studying various contributing factors, what really matters?

columns = list(df.columns)
columns.remove('Level')
columns.remove('Patient Id')

# Creating subplots for each column
fig, axes = plt.subplots(nrows=1, ncols=len(columns), figsize=(60, 6))

# Looping through each column and creating a violin plot
for i, column in enumerate(columns):
    sns.boxplot(x="Level", y=column, data=df, ax=axes[i])
    axes[i].set_title(column)

# Adjusting the spacing between subplots
plt.tight_layout()

# Showing the plot
plt.show()
```

Step 7 I tried to examine how detailed smoking-related lifestyle factors would affect the results.

```
# Smoking related lifestyle

X=df[['Air Pollution', 'Smoking', 'Passive Smoker']]

y=df['Level']

X_train,X_test,y_train,y_test = train_test_split(X, y, test_size=0.90, random_state=42)

Classifier_smoking_lifestyle = RandomForestClassifier()

Classifier_smoking_lifestyle.fit(X_train,y_train)

y_pred_logistic = Classifier_smoking_lifestyle.predict(X_test)

Results = pd.DataFrame({'Actual':y_test, 'Predictions':y_pred_logistic})

print("Accuracy of prediction Considering Lifestyle related to smoking: \n 'Air Pollution', 'Smoking', 'Passive Smoker'")

print(accuracy_score(y_test, y_pred_logistic))

report = classification_report(y_test, y_pred_logistic)
print("Classification Report:\n", report)
print("=" * 50)
```

Step 8  I tried to examine how d other factors would affect the results.

```
# Other related lifestyle

X=df[['Alcohol use','OccuPational Hazards',
       'Balanced Diet', 'Obesity' ]]

y=df['Level']

X_train,X_test,y_train,y_test = train_test_split(X, y, test_size=0.90, random_state=42)

Classifier_other_lifestyle = DecisionTreeClassifier()

Classifier_other_lifestyle.fit(X_train,y_train)

y_pred_logistic = Classifier_other_lifestyle.predict(X_test)

Results = pd.DataFrame({'Actual':y_test, 'Predictions':y_pred_logistic})

print("Accuracy of prediction considering other lifestyle: \n 'Alcohol use','OccuPational Hazards', 'Balanced Diet', 'Obesity'")

print(accuracy_score(y_test, y_pred_logistic))

report = classification_report(y_test, y_pred_logistic)
print("Classification Report:\n", report)
print("=" * 50)
```




<br>
##### Project Slides

<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQwa-ptnnxCUfU8Ua_B_izqK60omq7sCE-oZri0sUd6PWQYy-tuSBKips8XN_LA3bfiKZ3CvkM5RyUJ/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>



