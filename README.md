## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:

```
 import pandas as pd
 df=pd.read_csv("Encoding Data.csv")
 df
```
<img width="395" height="481" alt="image" src="https://github.com/user-attachments/assets/dc7aaf4b-c3c5-45c0-8dae-fc2d755765b0" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
<img width="213" height="254" alt="image" src="https://github.com/user-attachments/assets/4985146d-c25c-47f8-8ae6-5a9483c085cb" />

```
 df['bo2']=e1.fit_transform(df[["ord_2"]])
 df
```
<img width="460" height="486" alt="image" src="https://github.com/user-attachments/assets/6c4374ef-ef4d-4c24-a684-0f2561c7fe69" />

```
 le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc
```
<img width="477" height="480" alt="image" src="https://github.com/user-attachments/assets/76343fd4-d302-44ee-bbe7-e0767c36a565" />

```
 from sklearn.preprocessing import OneHotEncoder
 ohe=OneHotEncoder(sparse_output=False)
 df2=df.copy()
 enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
 df2=pd.concat([df2,enc],axis=1)
 df2
```
<img width="608" height="483" alt="image" src="https://github.com/user-attachments/assets/d8ecbd92-5b0b-4603-9369-2ce07176fe26" />

```
 pd.get_dummies(df2,columns=["nom_0"])
```
<img width="867" height="473" alt="image" src="https://github.com/user-attachments/assets/afee0e10-909d-4f71-b10c-8e4df7dbe8fa" />

```
 from category_encoders import BinaryEncoder
 df=pd.read_csv("data.csv")
 df
```
<img width="637" height="481" alt="image" src="https://github.com/user-attachments/assets/30098584-21bf-42d2-b7f0-0e23007f38d1" />

```
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df
```
<img width="637" height="484" alt="image" src="https://github.com/user-attachments/assets/e67fd1ec-120b-4d0a-a376-2ac203cd82cc" />

```
 dfb=pd.concat([df,nd],axis=1)
 dfb
```
<img width="912" height="488" alt="image" src="https://github.com/user-attachments/assets/f1448919-a13f-450d-bf2b-cd5a7482c471" />

```
 from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
```

<img width="735" height="480" alt="image" src="https://github.com/user-attachments/assets/b6f34946-3ee4-4483-91a6-5c486429fb73" />

```
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df
```

<img width="1043" height="569" alt="image" src="https://github.com/user-attachments/assets/5df18d24-ba86-4b89-82c6-443295772b44" />

```
 df.skew()
```

<img width="428" height="278" alt="image" src="https://github.com/user-attachments/assets/33e0ff4b-9973-4526-88a2-7dc8510d240b" />

```
 np.log(df["Highly Positive Skew"])A
```

<img width="394" height="613" alt="image" src="https://github.com/user-attachments/assets/374279cd-ace8-45ee-8427-80fc3f86d794" />

```
 np.reciprocal(df["Moderate Positive Skew"])
```

<img width="409" height="613" alt="image" src="https://github.com/user-attachments/assets/5acbcc9d-8613-41fb-9f47-e7988b2f8f89" />

```
 np.sqrt(df["Highly Positive Skew"])
```

<img width="409" height="612" alt="image" src="https://github.com/user-attachments/assets/1592d1ac-144e-4b61-8e91-1653913a11f8" />

```
np.square(df["Highly Positive Skew"])
```

<img width="379" height="616" alt="image" src="https://github.com/user-attachments/assets/f4930ab2-7da6-4930-814b-90f4a7aa073f" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```

<img width="1331" height="557" alt="image" src="https://github.com/user-attachments/assets/fd491d7e-ec28-4bee-afa6-ad474534f263" />
```
df.skew()
```

<img width="474" height="318" alt="image" src="https://github.com/user-attachments/assets/3ced6f5f-381f-4de3-b5c4-7e8345d025d8" />

```
 df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
 df.skew()
```

<img width="517" height="365" alt="image" src="https://github.com/user-attachments/assets/c8b9cbb9-757f-4b34-8e98-28230b60dee7" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```

<img width="1621" height="470" alt="image" src="https://github.com/user-attachments/assets/edf7dbf3-5941-4450-abaa-94754a912635" />

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="782" height="500" alt="image" src="https://github.com/user-attachments/assets/dcc195ff-0ce7-4a96-8dc2-59422de6da41" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()  
```

<img width="706" height="502" alt="image" src="https://github.com/user-attachments/assets/dc91f617-b81a-4204-bfb4-ce145483cc9c" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="725" height="503" alt="image" src="https://github.com/user-attachments/assets/eb6c1a5e-fda1-4b08-96f7-5caac2602154" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```

<img width="775" height="503" alt="image" src="https://github.com/user-attachments/assets/ab4e58bf-b9ab-49df-a57d-d2566a9e585a" />

```
dt=pd.read_csv("titanic_dataset.csv")
dt
```

<img width="1300" height="465" alt="image" src="https://github.com/user-attachments/assets/6d5c5afb-c3e7-4ae8-95af-25c607d6c5f5" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45') 
plt.show()
```

<img width="682" height="500" alt="image" src="https://github.com/user-attachments/assets/f31d692a-0097-4d36-8680-afe7ca439ee8" />

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```

<img width="722" height="497" alt="image" src="https://github.com/user-attachments/assets/ef632ce8-3079-420f-99ea-b1294e2d9616" />


# RESULT:
   Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
