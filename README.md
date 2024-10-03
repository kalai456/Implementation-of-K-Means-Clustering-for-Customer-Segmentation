# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
 Step 1: Start

 Step 2: Data Preparation: Load and explore customer data.
 
 Step 3: Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
 
 Step 4: Apply K Means Clustering: Perform clustering on customer data.
 
 Step 5: Visualize Segmented Customers: Plot clustered data to visualize customer segments.
 
 Step 6: End
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Rajalakshmi R
RegisterNumber: 212223110037
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("C:/Users/admin/Downloads/printed pdfs/Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:,3:])
y_pred


data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:

![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/b6d05d6a-240a-4363-a3ec-930baf12b706)
### y_pred:
![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/4d502d17-a83c-4478-9e03-9e2d721d8780)
### cluster:
![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/72c303f8-a9a3-4ef6-a395-82d8424ad990)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
