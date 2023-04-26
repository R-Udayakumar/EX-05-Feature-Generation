# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# PROGRAM  
```python
Developed By Udayakumar R
Ref.No: 22008609

[1]

import pandas as pd
df=pd.read_csv("data.csv")
print(df)
import category_encoders as ce
be=ce.BinaryEncoder()
df1=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
df1
be=ce.BinaryEncoder()
df2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
df2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()
df1["City"] = ohe.fit_transform(df1[["City"]])
temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])
edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=(['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target']))
df2
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
```python
[2]

import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf
be=ce.BinaryEncoder()
ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()
df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])
df1

from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4
```
```python
[3]

import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df.isnull().sum()
df

import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df['Sex'])
ndf
df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df4
```

## OUTPUT
[1].

![ss](https://user-images.githubusercontent.com/118707079/232985316-8b2b5676-037c-4230-a839-80c76a54b51f.jpg)

![ss1](https://user-images.githubusercontent.com/118707079/232985325-5ca12edf-2558-42a1-964d-798ef20d26cd.jpg)

![ss2](https://user-images.githubusercontent.com/118707079/232985360-4c6a3590-6e13-4770-ad13-d54559bfc497.jpg)

![ss3](https://user-images.githubusercontent.com/118707079/232985378-5c03e91a-042d-464b-baf2-6273b0ff9e51.jpg)

## MIN-MAX SCALER:

![mm](https://user-images.githubusercontent.com/118707079/232986167-55fd493a-5cf0-43ba-8533-c2f2f0fa4c2a.jpg)

## MAX-MIN SCALER:

![stan](https://user-images.githubusercontent.com/118707079/232986180-77fee453-ba62-468f-a26b-4a2891a82ec0.jpg)

## MAX-ABS SCALER :

![ms](https://user-images.githubusercontent.com/118707079/232986195-a0b17f87-652c-454c-90cc-0139971859e2.jpg)

## ROBUST SCALER :

![rs](https://user-images.githubusercontent.com/118707079/232986250-a7466c6f-cb85-424d-8317-a459706af67a.jpg)

[2]

![ed](https://user-images.githubusercontent.com/118707079/232986357-6f722cdb-e842-4635-b447-b56eb46d37be.jpg)
![ed1](https://user-images.githubusercontent.com/118707079/232986437-aa0c1711-3cf2-4583-9612-f6de764d32aa.jpg)
![ed2](https://user-images.githubusercontent.com/118707079/232986454-d524659f-7a58-45b9-a1e3-a04aca60c401.jpg)

## MIN-MAX SCALER :

![mms](https://user-images.githubusercontent.com/118707079/232986554-8680028e-76d5-4763-a50a-f8e8d6cb470f.jpg)

## STANDARD SCALER :

![sss](https://user-images.githubusercontent.com/118707079/232986634-2f2da3de-76ad-4f0d-b788-9a8a10190dfb.jpg)

## MAX-ABS SCALER :

![max](https://user-images.githubusercontent.com/118707079/232986716-1d3884cd-6e71-407c-aa8d-6b4fe9c1bd0b.jpg)

## ROBUST SCALER :

![ro](https://user-images.githubusercontent.com/118707079/232986810-b7ba4556-522d-4b2c-af4c-0e4dd92ab866.jpg)

[3]

![tt](https://user-images.githubusercontent.com/118707079/232987011-31f01ffa-0928-4da7-ba6e-14af7198b02a.jpg)

## NULL VALUES DETECTION :
![rem](https://user-images.githubusercontent.com/118707079/232987028-36843e83-e66f-4c92-9fe2-da34e0130d98.jpg)
![rem2](https://user-images.githubusercontent.com/118707079/232987096-559aebf4-aa66-4d07-a368-acb90ecbf3d9.jpg)


![en](https://user-images.githubusercontent.com/118707079/232987212-a1b6c697-e782-45b6-8a34-b1408d797894.jpg)
![enn](https://user-images.githubusercontent.com/118707079/232987261-b8c08654-23a5-4cc6-ad42-53f351202887.jpg)

## MIN-MAX SCALER :

![minmax](https://user-images.githubusercontent.com/118707079/232987340-65f4aade-b9dc-4da7-a146-abbc2eb90f85.jpg)

## STANDARD SCALER :

![std](https://user-images.githubusercontent.com/118707079/232987460-9eb98382-0cdc-430c-bebf-75a4ed61acd6.jpg)

## MAX-ABS SCALER:

![mxab](https://user-images.githubusercontent.com/118707079/232987557-653a13c3-9b73-433f-9946-d2feb6b78710.jpg)

## ROBUST SCALER :

![rob](https://user-images.githubusercontent.com/118707079/232987647-70c3bdb4-a3dc-431f-8232-c5d7fd7b2d38.jpg)

## Result:

Thus the Feature Generation and Feature Scaling process is applied to the given data set.







