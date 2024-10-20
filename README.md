# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Load and preprocess data by checking for missing values and selecting relevant features for clustering.  
2.Use the Elbow Method to determine the optimal number of clusters by calculating the WCSS for different values of k.  
3.Apply KMeans Clustering with the optimal number of clusters to segment customers based on the selected features.  
4.Visualize the clusters by plotting each cluster on a scatter plot to show customer segments based on annual income and spending score.  
 
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Kalaiselvan J
RegisterNumber: 212223080022
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans = KMeans (n_clusters = i, init ="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
## Dataset:

![278795578-afbcb3f0-41a0-4e9e-bafd-a0fafb3334c0](https://github.com/charumathiramesh/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120204455/ed5b0fe2-4e98-43bd-9b21-f3468d493335)

## Dataset information:
![278795602-253e3aeb-6850-4bfd-b39b-9e82bf90d834](https://github.com/charumathiramesh/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120204455/8d4aa9d8-45dd-4539-8271-f7da5d00dc99)
![278795605-b654a77d-774e-4cc0-9396-4353a521f7cc](https://github.com/charumathiramesh/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120204455/f3c984b3-7e9b-4852-9552-a4026fbfd52d)




## Elbow method graph (wcss vs each iteration):
![278795631-c7b3a69a-089c-4ff3-b253-9a2a0b6e0daa](https://github.com/charumathiramesh/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120204455/65a43453-3ac2-4bea-8187-97cb6cc060d1)


## Cluster represnting customer segments-graph:

![278795641-c898bcee-13f7-49d2-918c-dc151a9702f3](https://github.com/charumathiramesh/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/120204455/5796e66a-5977-4d88-857d-822ee784388d)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
