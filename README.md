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


# CODE
```
#Data.csv
import pandas as pd   
import seaborn as sbn 
df=pd.read_csv("/content/data.csv") 
df.info() 
df.isnull().sum()
from sklearn.preprocessing import LabelEncoder 
le = LabelEncoder() 
df['Ord_2'] = le.fit_transform(df['Ord_2']) 
sbn.set(style ="darkgrid") 
sbn.countplot(df['Ord_2'])
from sklearn.preprocessing import OneHotEncoder 
enc = OneHotEncoder() 
enc = enc.fit_transform(df[['City']]).toarray() 
encoded_colm = pd.DataFrame(enc) 
df = pd.concat([df, encoded_colm], axis=1) 
df = df.drop(['City'], axis=1) 
df.head(10) 
df = pd.get_dummies(df, prefix=['Ord_2'], columns=['Ord_2']) 
df.head(10) 
df = pd.get_dummies(df, prefix=['Ord_1'], columns=['Ord_1']) 
df.head(10)

#Encoding.csv
import pandas as pd 
import seaborn as sbn 
data=pd.read_csv("/content/Encoding Data.csv") 
data.info() 
data.isnull().sum() from sklearn.preprocessing import LabelEncoder 
le = LabelEncoder() data['ord_2'] = le.fit_transform(data['ord_2']) 
sbn.set(style ="darkgrid") 
sbn.countplot(data['ord_2']) from sklearn.preprocessing import OneHotEncoder 
en = OneHotEncoder() 
en = en.fit_transform(data[['nom_0']]).toarray() 
encoded_colm = pd.DataFrame(en) 
data= pd.concat([data, encoded_colm], axis=1) 
data= data.drop(['nom_0'], axis=1) 
data.head(10) 
data = pd.get_dummies(df, prefix=['bin_2'], columns=['bin_2']) 
data.head(10)

#Titanic.csv
import pandas as pd 
import seaborn as sbn 
dt=pd.read_csv("/content/titanic_dataset.csv") 
dt.info() 
dt.isnull().sum() 
dt['Age']=dt['Age'] . fillna(dt ['Age'].mean()) 
dt ['Cabin']=dt['Cabin']. fillna(dt['Cabin']. mode() [0]) 
dt ['Embarked']=dt['Embarked'] . fillna(df ['Embarked'].mode( )[0]) 
dt.isnull().sum( ) from sklearn.preprocessing import LabelEncoder 
lc = LabelEncoder() 
df['Sex'] = lc.fit_transform(df['Sex']) 
sbn.set(style ="darkgrid") 
sbn.countplot(df['Sex']) from sklearn.preprocessing import OneHotEncoder 
enc= OneHotEncoder() 
enc= enc.fit_transform(dt[['Name']]).toarray() 
encoded_colm = pd.DataFrame(enc) 
dt= pd.concat([dt, encoded_colm], axis=1) 
dt= dt.drop(['Name'], axis=1) 
dt.head(10) 
dt = pd.get_dummies(dt, prefix=['Ticket'] ,columns=['Ticket']) 
df.head(10) 
dt = pd.get_dummies(dt, prefix=['Embarked'] ,columns=['Embarked']) 
df.head(10)

```

# OUTPUT

# Data.csv

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/01.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/02.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/03.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/04.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/05.png)


# Encoding.csv

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/06.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/07.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/08.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/09.png)


# Titanic.csv

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/10.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/11.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/12.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/13.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/14.png)

![](https://github.com/Hariharan5354/EX-05-Feature-Generation/blob/main/15.png)


# Result

Thus the program for Feature Generation is executed successfully.
