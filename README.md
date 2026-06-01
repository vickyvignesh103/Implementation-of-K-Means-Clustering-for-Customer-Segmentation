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

# Load dataset
data = pd.read_csv("Mall_Customers.csv")

print(data.head())
print(data.info())
print(data.isnull().sum())

# Elbow Method
wcss = []

for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=0)
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.figure(figsize=(8, 5))
plt.plot(range(1, 11), wcss, marker='o')
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

# K-Means Clustering
km = KMeans(n_clusters=5, random_state=0)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])

# Add cluster column
data["cluster"] = y_pred

# Separate clusters
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

# Plot clusters
plt.figure(figsize=(8, 6))

plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"],
            c="black", label="Cluster 0")

plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"],
            c="cyan", label="Cluster 1")

plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"],
            c="yellow", label="Cluster 2")

plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"],
            c="blue", label="Cluster 3")

plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"],
            c="green", label="Cluster 4")

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
