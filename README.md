# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. 
2. 
3. 
4. 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: 
RegisterNumber:  
*/
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
# Read dataset
data = pd.read_csv("Mall_Customers (1).csv")
# Display information
print(data.head())
print(data.info())
# Check missing values
print(data.isnull().sum())
# Elbow Method
wcss = []
X = data.iloc[:, 3:]   # Annual Income and Spending Score
for i in range(1, 11):
    kmeans = KMeans(
        n_clusters=i,
        init="k-means++",
        random_state=42,
        n_init=10
    )
    kmeans.fit(X)
    wcss.append(kmeans.inertia_)
# Plot Elbow graph
plt.figure(figsize=(8,5))
plt.plot(range(1,11), wcss, marker='o')
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
# Create KMeans model with 5 clusters
km = KMeans(
    n_clusters=5,
    random_state=42,
    n_init=10
)
km.fit(X)
# Predict clusters
y_pred = km.predict(X)

# Add cluster column
data["cluster"] = y_pred
# Separate clusters
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
# Plot clusters
plt.figure(figsize=(8,6))
plt.scatter(
    df0["Annual Income (k$)"],
    df0["Spending Score (1-100)"],
    c="black",
    label="Cluster 0"
)
plt.scatter(
    df1["Annual Income (k$)"],
    df1["Spending Score (1-100)"],
    c="cyan",
    label="Cluster 1"
)
plt.scatter(
    df2["Annual Income (k$)"],
    df2["Spending Score (1-100)"],
    c="yellow",
    label="Cluster 2"
)
plt.scatter(
    df3["Annual Income (k$)"],
    df3["Spending Score (1-100)"],
    c="blue",
    label="Cluster 3"
)
plt.scatter(
    df4["Annual Income (k$)"],
    df4["Spending Score (1-100)"],
    c="green",
    label="Cluster 4"
)
# Plot cluster centers
plt.scatter(
    km.cluster_centers_[:,0],
    km.cluster_centers_[:,1],
    s=300,
    marker='*',
    label="Centroids"
)
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()
```

## Output:
<img width="962" height="463" alt="image" src="https://github.com/user-attachments/assets/c21a8fb0-5f81-40f4-a075-2e63d436a07f" />
<img width="722" height="468" alt="image" src="https://github.com/user-attachments/assets/0e921d9f-24eb-490c-8680-723f9d8b65ed" />
<img width="695" height="545" alt="image" src="https://github.com/user-attachments/assets/1b22c6ee-5b70-4d12-b333-08accfe52d87" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
