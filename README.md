# Exno:1

### NAME : PREETHI D
### REGISTER NUMBER : 212224040250

Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
 ``` python

import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df

```
![image](https://github.com/user-attachments/assets/51555fb0-4eb0-4061-a6ff-b173fe377fc0)

``` python

df.info()

```
![image](https://github.com/user-attachments/assets/b328ea97-e1ce-4e0c-8060-ba9a39c829dd)

``` python

df.describe()

```
![image](https://github.com/user-attachments/assets/fc811825-8d43-4ef7-9e59-0899f80ea5fa)

``` python

df.shape

```
![image](https://github.com/user-attachments/assets/99f40f7a-48d6-47a4-ab2a-818326c23121)

``` python

df.isnull()

```
![image](https://github.com/user-attachments/assets/ba868fe8-a85d-467b-b857-8a2c8d6b76f3)

```python

df.notnull()

```
![image](https://github.com/user-attachments/assets/76a7c038-fab7-42e7-a7a4-cff2dbff8dac)

``` python
df.dropna(axis=0)
```

![image](https://github.com/user-attachments/assets/643e2ebc-b6b5-46f2-978f-6ec48bb2fbd6)

``` python

df.dropna(axis=1)

```
![image](https://github.com/user-attachments/assets/a52fbf5e-7a6e-4915-90b5-3eca1c1df35d)

``` python

dfs=df[df['TOTAL']>270]
dfs

```
![image](https://github.com/user-attachments/assets/608532fe-443e-47a3-8290-a1f8ec5e8442)

``` python

dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
dfs

```

![image](https://github.com/user-attachments/assets/88862cdc-3219-4bf4-9be8-8464ac67a0b7)

``` python

df.iloc[0:4,1:4]

```
![image](https://github.com/user-attachments/assets/4f1b0198-ebd2-4c5b-89cd-6fa58741dbab)

![image](https://github.com/user-attachments/assets/70cb0bcc-5e82-4532-ad02-7ba07f53d2bf)

``` python

dff=df.fillna(0)
dff

```
![image](https://github.com/user-attachments/assets/edc3525c-5f96-457e-acea-8d43fc92c2f6)

![image](https://github.com/user-attachments/assets/03dca230-f9a4-4e44-9412-447f3bb49243)

![image](https://github.com/user-attachments/assets/77d16ac9-631f-4613-ad03-731c344cd075)

``` python

df['TOTAL'].fillna(value=df['TOTAL'].mean())

```
![image](https://github.com/user-attachments/assets/7c943a6d-950d-4562-ae65-ff85a409cfda)

``` python

df.isnull().sum()

```

![image](https://github.com/user-attachments/assets/f523b52a-f310-4226-b23c-e63ed90f0d0e)

``` python

df.dropna(how='any')

```
![image](https://github.com/user-attachments/assets/079c9370-a076-4078-adf4-276d75807d82)
![image](https://github.com/user-attachments/assets/70f6e545-72af-43aa-bbd5-500024521729)
![image](https://github.com/user-attachments/assets/36370d24-689e-46b3-99ee-65df994a47a1)

``` python

mn=df.TOTAL.mean()
print(mn)

df.fillna(mn,inplace=True)
df

```
![image](https://github.com/user-attachments/assets/f93ff58b-7a7c-44ff-967b-8edc8b6ce042)
![image](https://github.com/user-attachments/assets/44103bb7-00b0-4a50-9a8c-95b815c0f234)


``` python

import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

```

![image](https://github.com/user-attachments/assets/9c5c1109-2ade-4f4f-bf87-47daaaf3610d)


``` python

df.dropna(inplace = True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

```

![image](https://github.com/user-attachments/assets/4ee0a189-9270-4104-b210-1853b69feebd)


```python

OUTLIER DETECTION
import pandas as pd
import seaborn as sns
import numpy as np
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af = pd.DataFrame(age)
af

```
![image](https://github.com/user-attachments/assets/c67400e2-adf9-4f71-be8d-9f451cf22f52)

``` python

sns.boxplot(data=af)

```
![image](https://github.com/user-attachments/assets/a78b0b7e-dbd8-4a27-87a3-68977a0fc3e9)

![image](https://github.com/user-attachments/assets/be5e6010-d7de-4cdb-8aa4-26e7a1df600a)

![image](https://github.com/user-attachments/assets/f4a1f3c7-97a7-4d7f-89fe-60c99aa73470)

![image](https://github.com/user-attachments/assets/c901b506-8b89-4d23-958f-75056b2767fb)

![image](https://github.com/user-attachments/assets/373a0f20-4549-4de9-94e1-6bc210fd7c08)


``` python

sns.boxplot(data=af)

```
![image](https://github.com/user-attachments/assets/fe202f10-c2f4-4e2b-9d2e-3184d66f87b5)
![image](https://github.com/user-attachments/assets/e13c857c-1cb8-4057-b80c-77219d9a609b)


``` python
Z SCORE METHOD

```
![image](https://github.com/user-attachments/assets/300236b7-1adb-49ef-9594-5bacf623da58)

```
 data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

```
![image](https://github.com/user-attachments/assets/d6baf798-3279-4498-be50-215905268e3f)

![image](https://github.com/user-attachments/assets/a462f340-fd27-445e-84aa-264f98df2e74)


# Result
          Thus we have carried out data cleansing and removed the outliers by detection using IQR and Z Score method.
