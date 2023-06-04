# EX-05-Feature-Generation


# AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# DATE:
 GITHUB LINK:https://github.com/viswapriyaG/EX-05-Feature-Generation.git
 
 COLAB LINK: https://colab.research.google.com/drive/1JCxLAGYHNjz2N2LvErIkZuqOdRhHTKxK#scrollTo=2Fh7Pk_H1YSr
 
# ALGORITHM

## STEP 1
Read the given Data
## STEP 2
Clean the Data Set using Data Cleaning Process
## STEP 3
Apply Feature Generation techniques to all the feature of the data set
## STEP 4
Save the data to the file


# CODE

DEVELOPED BY: VISWA PRIYA G

REGISTER NUMBER: 212221220061

#Data.csv

```

import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

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

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
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
#Encoding.csv

```

import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

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

#feature scaling
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
#Titanic.csv

```

import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

# removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

# data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

# feature encoding
from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

# feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5

```

# OUTPUT

# Data.csv

Initial Dataset:

![fg1](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/2a90bf81-aa8a-40e9-893a-58423b354edc)

Binary encoding:

![fg2](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/9b99b1b1-b2b0-4f5b-85e8-72864a1f502b)

![fg3](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/8080f731-0d83-4899-b117-8c6774e544c5)

Encoded Dataset:

![fg4](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/31923614-3e26-4bc4-8b53-1161821dc5e3)

Data Scaling using MinMaxScaler:

![fg5](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/e1a879c7-7bae-49e6-bb73-d3a67c1d7862)

Data Scaling using StandardScaler:

![fg6](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/57ec0b86-deb7-4659-bf33-efd0f48be9aa)

Data Scaling using MaxAbsScaler:

![fg7](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/0996a8d8-aaa5-4dbb-b0c4-c2b06890502c)

Data Scaling using MaxAbsScaler:

![fg8](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/b7944a96-9239-48cf-947f-9d23970a3100)


# Encoding.csv

Initial Dataset:

![fg9](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/f7a403d9-a65c-4697-9954-1c21cf7031c2)

Binary Encoding:

![fg10](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/b887b376-11be-4067-84c5-ff20777abe93)

![fg11](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/3d013685-c3f1-4859-b5a2-246e5d841477)

Encoded Dataset:

![fg12](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/6a47b418-e2ec-493c-93a8-397e4cb1ad14)

Data Scaling using MinMaxScaler:

![fg13](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/93d8b60d-81bd-4c1a-80db-224f6c79c229)

Data Scaling using StandardScaler:

![fg14](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/ffabba1e-fa71-49a3-a53e-805be17162f5)

Data Scaling using MaxAbsScaler:

![fg15](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/0bf84ba4-6028-44cc-bbb3-2f950978a697)

Data Scaling using RobustScaler:

![fg16](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/047efb50-5b69-46d9-816d-5773b60e7143)


# Titanic.csv

Initial Dataset:

![fg17](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/12d5f3c8-ba9e-4941-8bc5-af3e32232aba)

Data cleaning before encoding:

![fg18](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/cfd45335-aa0f-4a9a-bdff-f5eee68ff35e)

Cleaned Dataset:

![fg19](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/01fbe176-b1a9-434a-a0fb-ccbfa4dcd4ef)

Binary Encoding:

![fg20](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/04c67804-86e2-4a46-9e65-0a61ccd49be9)

Encoded Dataset:

![fg21](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/5f7bc518-3c10-4e85-825c-aa7563da94ee)

Data Scaling using MinMaxScaler:

![fg22](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/b861b6c8-1ac3-4218-a23f-65a73cc1c1fa)

Data Scaling using StandardScaler:

![fg23](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/3190ea10-3472-49e1-99c2-a8f3593c31bf)

Data Scaling using MaxAbsScaler:

![fg24](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/493be6f5-6933-43b9-9406-fcd32ebd4017)

Data Scaling using RobustScaler:

![fg25](https://github.com/viswapriyaG/EX-05-Feature-Generation/assets/131427787/48f42568-4732-4c05-ab3b-433b5b4af247)


# Result

Thus the program for Feature Generation is executed successfully.
