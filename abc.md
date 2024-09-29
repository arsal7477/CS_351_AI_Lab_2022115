<p align="center">
  <img src="https://github.com/user-attachments/assets/aa697654-16be-4b74-9d79-e035dc95833d" alt="Image Description" width="300px">
</p>

<h1 align="center">Artificial Intelligence (Lab)</h1>
<h2 align="center">Lab 2 Task</h2>
<p align="center"><strong>Arsalan Khan</strong><br>2022115<br>Cyber Security</p>
<p align="center">Submitted to: Sir Usama Arshad<br>Date: September 16, 2024</p>

---

## Description

This repository contains my work for Lab 2 of the Artificial Intelligence course, where we predict passenger survival on the Titanic using machine learning models.

---

## Colab Notebook

You can view and run the notebook by clicking the link below:

[Open in Colab](https://colab.research.google.com/github/arsal7477/CS_351_AI_Lab_2022115/blob/main/Untitled3.ipynb)

---

## Code Overview

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score, classification_report

# Load the Titanic dataset from a direct URL
url = 'https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv'
titanic_df = pd.read_csv(url)

# Display the first few rows of the dataset
print(titanic_df.head())

# Set style for the plots
sns.set(style="whitegrid")

# Visualizing the distribution of 'Pclass', 'Age', and 'Sex'
plt.figure(figsize=(15, 5))

# Plotting the distribution of Pclass
plt.subplot(1, 3, 1)
sns.countplot(x='Pclass', data=titanic_df)
plt.title('Distribution of Passengers by Class')
plt.xlabel('Passenger Class')
plt.ylabel('Count')

# Plotting the distribution of Age
plt.subplot(1, 3, 2)
sns.histplot(titanic_df['Age'], bins=30, kde=True)
plt.title('Age Distribution of Passengers')
plt.xlabel('Age')
plt.ylabel('Count')

# Plotting the distribution of Sex
plt.subplot(1, 3, 3)
sns.countplot(x='Sex', data=titanic_df)
plt.title('Distribution of Passengers by Sex')
plt.xlabel('Sex')
plt.ylabel('Count')

plt.tight_layout()
plt.show()

# Checking for missing values in each column
print("Missing values in each column:")
print(titanic_df.isnull().sum())

# Handling missing values
titanic_df['Age'].fillna(titanic_df['Age'].median(), inplace=True)
titanic_df.dropna(subset=['Embarked'], inplace=True)
titanic_df['Fare'].fillna(titanic_df['Fare'].median(), inplace=True)

# Check again for missing values
print("\nMissing values after handling:")
print(titanic_df.isnull().sum())

# Encoding categorical variables
titanic_df['Sex'] = titanic_df['Sex'].map({'male': 0, 'female': 1})
titanic_df['Embarked'] = titanic_df['Embarked'].map({'C': 0, 'Q': 1, 'S': 2})

# Display the first few rows to check the encoded values
print("\nEncoded values:")
print(titanic_df[['Sex', 'Embarked']].head())

# Selecting features and target variable
X = titanic_df[['Pclass', 'Sex', 'Age', 'Fare']]
y = titanic_df['Survived']

# Split the dataset into training and testing sets (70% training, 30% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Implementing k-Nearest Neighbors (k-NN)
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)

# Making predictions on the test set
knn_predictions = knn.predict(X_test)

# Evaluate the performance of k-NN
knn_accuracy = accuracy_score(y_test, knn_predictions)
knn_classification_rep = classification_report(y_test, knn_predictions)

print(f"Accuracy of k-NN: {knn_accuracy * 100:.2f}%")
print("\nClassification Report for k-NN:\n", knn_classification_rep)

# Implementing Decision Tree Classifier
decision_tree = DecisionTreeClassifier(random_state=42)
decision_tree.fit(X_train, y_train)

# Making predictions on the test set
dt_predictions = decision_tree.predict(X_test)

# Evaluate the performance of Decision Tree
dt_accuracy = accuracy_score(y_test, dt_predictions)
dt_classification_rep = classification_report(y_test, dt_predictions)

print(f"Accuracy of Decision Tree: {dt_accuracy * 100:.2f}%")
print("\nClassification Report for Decision Tree:\n", dt_classification_rep)
