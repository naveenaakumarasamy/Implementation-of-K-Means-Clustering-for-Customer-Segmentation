# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

Step 1. Start the program

Step 2. Import the necessary python libraries

Step 3. Read the dataset of Mall_Customers csv file

Step 4. From sklearn libraary select the cluster and import KMeans Clustering

Step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

Step 6. Plot the graph x and y as Number of Clusters and wcss respectively

Step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

Step 8. Stop the program


## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Naveenaa A K
RegisterNumber: 212222230094 
```
```
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("Mall_Customers.csv")
df.head()
df.info()
df.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(df.iloc[:,3:])
y_pred = km.predict(df.iloc[:,3:])
print("Predicted values : ")
y_pred
df["cluster"] = y_pred
df0 = df[df["cluster"]==0]
df1 = df[df["cluster"]==1]
df2 = df[df["cluster"]==2]
df3 = df[df["cluster"]==3]
df4 = df[df["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer segments")
```

## Output:
### head :
![image](https://github.com/user-attachments/assets/067a9c58-9f7f-4424-9e18-7643886f9ad1)
### Info :
![image](https://github.com/user-attachments/assets/2787d851-1d74-4b0e-a4cf-e624f1f8db56)
### No.of Null-Values :
![image](https://github.com/user-attachments/assets/6c25bd0d-2787-47d4-b2ab-035da26b535a)
### Graph:
![image](https://github.com/user-attachments/assets/03b77fd1-4a2a-494b-9aae-2747e447a4ca)
### No.of clusters :
![image](https://github.com/user-attachments/assets/0176533f-b3a9-46b5-8d9f-091de46ce6d1)
### Predicted values :
![image](https://github.com/user-attachments/assets/b23ed3d8-3dcb-4949-a77d-377366b270dd)
### Customer Segments :
![image](https://github.com/user-attachments/assets/8ee21efb-dedb-40da-9642-0b736844e282)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
