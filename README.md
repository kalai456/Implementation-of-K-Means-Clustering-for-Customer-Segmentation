# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and Inspect Data: Load the Mall_Customers.csv dataset, check for missing values, and display the first few rows.
2. Elbow Method: Use the Elbow method by calculating the Within-Cluster Sum of Squares (WCSS) for clusters from 1 to 10 and plot the results to determine the optimal number of clusters.
3. Apply KMeans: Apply KMeans clustering with 5 clusters (from the Elbow method), and assign the resulting cluster labels (y_pred) to the data.
4. Assign Clusters: Add the cluster labels as a new column in the dataset (cluster).
5. Segment Data: Create separate dataframes (df0, df1, etc.) for each cluster.
6. Plot Results: Plot the customer segments based on Annual Income (k$) and Spending Score (1-100) with different colors for each cluster.
## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: KALAISELVAN J
RegisterNumber:  212223080022
```
```
import pandas as pd 
import matplotlib.pyplot as plt
d=pd.read_csv("Mall_Customers.csv")
```

![image](https://github.com/user-attachments/assets/3679d1af-a179-4514-b49b-a968b645c913)


![image](https://github.com/user-attachments/assets/376cb220-7c08-496b-a4a7-522d6fb835ce)

![image](https://github.com/user-attachments/assets/eb3a848f-8aaa-455e-a410-9eed91bdad94)


```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    Kmeans=KMeans (n_clusters = i, init ="k-means++")
    Kmeans.fit(d.iloc[:,3:])
    wcss.append(Kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
km=KMeans(n_clusters=5)
km.fit(d.iloc[:,3:])
y_pred = km.predict(d.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/3bf16206-07f5-4a33-93b2-8443c838503d)

```
d["clusters"]=y_pred
df0=d[d["clusters"]==0]
df1=d[d["clusters"]==1]
df2=d[d["clusters"]==2]
df3=d[d["clusters"]==3]
df4=d[d["clusters"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="clusters0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="clusters1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="clusters2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="clusters3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="clusters4")
plt.legend()
plt.title("Customer Segments")
```
![image](https://github.com/user-attachments/assets/757ca343-0874-4523-a093-c1107bdaae9a)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
