# EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
## DATE: 04-08-2026
## REG NO: 212224040023
## AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
## Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
## Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

## Program:
```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

df = pd.read_csv("clustervisitor.csv")

X = df[['Age']]

kmeans = KMeans(n_clusters=3, random_state=42)

df['Cluster'] = kmeans.fit_predict(X)

print(df)

for i in range(3):
    print(f"\nCluster {i}")
    print(df[df['Cluster'] == i])

```
## Output:
<img width="923" height="659" alt="image" src="https://github.com/user-attachments/assets/941abd50-cdc4-49b6-a592-e1521cc6e4cb" />
<img width="460" height="600" alt="image" src="https://github.com/user-attachments/assets/06704d52-1c30-448e-aa08-3ca39754d3dc" />

## Visualization:
```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))

for i in range(3):
    cluster = df[df['Cluster'] == i]
    plt.scatter(cluster['Age'], cluster['Cluster'], label=f'Cluster {i}')

plt.scatter(
    kmeans.cluster_centers_,
    range(3),
    color='red',
    marker='X',
    s=200,
    label='Centroids'
)

plt.xlabel("Age")
plt.ylabel("Cluster")
plt.title("Visitor Segmentation using K-Means")
plt.legend()
plt.grid(True)
plt.show()
```
## Output:
<img width="700" height="468" alt="image" src="https://github.com/user-attachments/assets/c87546eb-bd80-4ae0-9657-88d19a2a41ce" />


## Result:
Thus the code has been executed successfully.
