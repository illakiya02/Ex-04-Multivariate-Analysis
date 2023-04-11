# Ex-04-Multivariate-Analysis
import pandas as pd
import numpy as np
import seaborn as sbn
import matplotlib.pyplot as plt
df = pd.read_csv("/content/SuperStore.csv")
df.head(10) 
![image](https://user-images.githubusercontent.com/112244898/231169565-b1ea292e-d103-4337-b925-2ec31ba715c2.png)
df.info() 
df.describe() 
![image](https://user-images.githubusercontent.com/112244898/231171397-be1eda90-f55e-4428-b144-1b2211ecf19e.png)
df.isnull().sum()
![image](https://user-images.githubusercontent.com/112244898/231171993-3a0b74cb-14c3-402d-88d6-34fc0a12656a.png)
df['Postal Code'] = df["Postal Code"].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()
![image](https://user-images.githubusercontent.com/112244898/231172296-3cd23ed9-d7dd-46a1-a4a6-ae638fe72e3f.png)
df.dtypes
sbn.scatterplot(df['Postal Code'],df['Sales']) 
states=df.loc[:,["State","Sales"]] 
states=states.groupby(by=["State"]).sum().sort_values(by="Sales") 
plt.figure(figsize=(17,7)) 
sbn.barplot(x=states.index,y="Sales",data=states) 
plt.xticks(rotation = 90)
plt.xlabel=("STATES") 
plt.ylabel=("SALES") 
plt.show()
![image](https://user-images.githubusercontent.com/112244898/231171993-3a0b74cb-14c3-402d-88d6-34fc0a12656a.png)
states=df.loc[:,["State","Postal Code"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Postal Code") 
plt.figure(figsize=(17,7))
sbn.barplot(x=states.index,y="Postal Code",data=states) 
plt.xticks(rotation = 90)
plt.xlabel=("STATES")
plt.ylabel=("Postal Code") 
plt.show() 
![image](https://user-images.githubusercontent.com/112244898/231174652-17d4d22a-c336-417b-8472-af506d8d2008.png)
states=df.loc[:,["Segment","Sales"]]
states=states.groupby(by=["Segment"]).sum().sort_values(by="Sales") 
#plt.figure(figsize=(10,7)) sbn.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SEGMENT")
plt.ylabel=("SALES")
plt.show()
![image](https://user-images.githubusercontent.com/112244898/231175115-ab0c9073-7560-4b60-8771-39d4da2de356.png)
sbn.barplot(df['Postal Code'],df['Ship Mode'],hue=df['Region'])
df.corr()
![image](https://user-images.githubusercontent.com/112244898/231175383-64f3a7bf-795b-403d-8d3d-b7f807afd845.png)
sbn.heatmap(df.corr(),annot=True)
![image](https://user-images.githubusercontent.com/112244898/231176824-f95153db-93be-4153-9876-d005a21306ff.png)










