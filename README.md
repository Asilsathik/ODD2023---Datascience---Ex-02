# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,


AIM :

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them


EXPLANATION :

An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.


ALGORITHM :

Step1: Read the given Data.

Step2: Get the information about the data.

Step3: Detect the Outliers using IQR method and Z score.

Step4: Remove the outliers.

Step5: Plot the datas using Box Plot.

#CODE :

bhp.csv :
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```

HIEGHT_WEIGHT.CSV :

```
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
#OUTPUT :

bhp.csv :

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/4aa4d75d-e357-40c3-b2f2-a46dad101666)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/ef2cf560-c259-429e-b184-2ca17463c73d)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/5fa25adc-e096-49ae-afd9-149ac8371a55)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/bbbaee2e-061a-4a82-bbf4-ca0c72cfa495)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/263def6e-4083-4b08-b3f5-5aa3cc162bcd)

weight_height.csv:


![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/003a6d3c-2683-4888-a76b-39d66b73e9de)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/f4175473-de5b-48ff-8347-45b3c3d986c8)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/42df73cc-6275-4a41-96f8-bac9ac4b4075)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/0fe343d7-f148-4c6a-b309-10b0baf1ac35)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/aca568f3-f7a9-4700-8c86-3ba652690116)

![image](https://github.com/Asilsathik/ODD2023---Datascience---Ex-02/assets/119476247/234f52d9-75ba-4dc3-b8e5-4fa2195aa56e)

#RESULT :

Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.





