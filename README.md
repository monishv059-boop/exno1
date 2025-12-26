# Exno:1
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
    import pandas as pd import numpy as np

df=pd.read_csv('drive/MyDrive/Data Science/Data_set.csv')

df_null=df.isnull() print(df_null)
<img width="946" height="671" alt="Screenshot 2025-12-26 184022" src="https://github.com/user-attachments/assets/bf8656aa-56e3-4048-9238-0b88cb05dc94" />
df_sum=df.isnull().sum() print(df_sum)
<img width="455" height="259" alt="Screenshot 2025-12-26 184102" src="https://github.com/user-attachments/assets/47ddbcf4-cb9d-4b22-83f2-0fc68d72e34d" />
df_drop=df.isnull().dropna() print(df_drop)
<img width="861" height="685" alt="Screenshot 2025-12-26 184127" src="https://github.com/user-attachments/assets/81da0f13-0450-4077-977c-ee39d8935c1e" />
df_null_0=df.fillna(0) print(df_null_0)
<img width="964" height="865" alt="Screenshot 2025-12-26 184302" src="https://github.com/user-attachments/assets/6c16b46a-2bda-4865-9704-429af546360f" />
df_null_ffill=df.ffill() print(df_null_ffill)
<img width="954" height="865" alt="Screenshot 2025-12-26 184318" src="https://github.com/user-attachments/assets/a11d408f-e348-4069-8cdf-e8c13633c7c3" />
df_bfill=df.bfill() print(df_bfill)
<img width="968" height="870" alt="Screenshot 2025-12-26 184333" src="https://github.com/user-attachments/assets/8b509340-ab87-49b5-a294-fdaa4f483aad" />
df_mean1=df['num_episodes'].fillna(df['num_episodes'].mean()) print(df_mean1)
<img width="684" height="315" alt="Screenshot 2025-12-26 184345" src="https://github.com/user-attachments/assets/0f99fc10-98d2-4099-8276-767b139fe05c" />
df_mean2=df['rating'].fillna(df['rating'].mean()) print(df_mean2)
<img width="640" height="308" alt="Screenshot 2025-12-26 184354" src="https://github.com/user-attachments/assets/39d22afe-6409-46fc-9c6a-6a1539660c08" />
df_mean3=df['current_overall_rank'].fillna(df['current_overall_rank'].mean()) print(df_mean3)
<img width="792" height="324" alt="Screenshot 2025-12-26 184403" src="https://github.com/user-attachments/assets/d6925df8-78ba-46d5-88be-05cd6d4cb780" />
df_mean4=df['lifetime_popularity_rank'].fillna(df['lifetime_popularity_rank'].mean()) print(df_mean4)
<img width="743" height="318" alt="Screenshot 2025-12-26 184412" src="https://github.com/user-attachments/assets/1af7e7cc-95a1-44c4-9c51-79e3c763179e" />
df_mean5=df['watchers'].fillna(df['watchers'].mean()) print(df_mean5)
<img width="630" height="316" alt="Screenshot 2025-12-26 184420" src="https://github.com/user-attachments/assets/5a6b4361-9a3f-4aa4-82d1-013ba1374fad" />
df_dropna=df.dropna() print(df_dropna)
<img width="905" height="885" alt="Screenshot 2025-12-26 184439" src="https://github.com/user-attachments/assets/e2e26b18-fc89-420e-9a2d-4d894786b6ed" />
import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94] af=pd.DataFrame(age) print(af)
<img width="317" height="398" alt="Screenshot 2025-12-26 184448" src="https://github.com/user-attachments/assets/17243f9f-bf69-48ec-8bc4-0c4f8385aef0" />
sns.boxplot(af)
<img width="965" height="607" alt="Screenshot 2025-12-26 184534" src="https://github.com/user-attachments/assets/1994626c-091f-45c2-b795-3c2445ade77f" />
sns.scatterplot(af)
<img width="867" height="605" alt="Screenshot 2025-12-26 184545" src="https://github.com/user-attachments/assets/64b2d036-e985-4957-ba5a-368893ff79ac" />
q1=af.quantile(0.25) q2=af.quantile(0.5) q3=af.quantile(0.75)

iqr=q3-q1 print(iqr)

Q1=np.percentile(af,25) Q2=np.percentile(af,50) Q3=np.percentile(af,75)

IQR=Q3-Q1

lower_bound=Q1-1.5IQR upper_bound=Q3+1.5IQR

outliers = [x for x in age if x < lower_bound or x > upper_bound]

print('Q1:',Q1) print('Q3:',Q3) print('IQR:',IQR) print('Lower bound:',lower_bound) print('Upper bound:',upper_bound) print('Outliers:',outliers)
<img width="356" height="178" alt="Screenshot 2025-12-26 184556" src="https://github.com/user-attachments/assets/dba05bf5-e4f6-440a-a169-5305445df3ee" />
af=af[((af>=lower_bound)&(af<=upper_bound))] print(af)
<img width="266" height="393" alt="Screenshot 2025-12-26 184605" src="https://github.com/user-attachments/assets/4d1e7074-7cfe-43eb-a864-e5b69a739039" />
af.dropna()
<img width="244" height="523" alt="Screenshot 2025-12-26 184621" src="https://github.com/user-attachments/assets/0dfb9e44-5c20-47af-9704-734efa2e371e" />
sns.boxplot(af)
<img width="876" height="619" alt="Screenshot 2025-12-26 184629" src="https://github.com/user-attachments/assets/203ca4b7-4873-4ee6-8d45-d8c040e80cec" />
from scipy import stats

data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93] df=pd.DataFrame(data)

sns.boxplot(df)
<img width="910" height="639" alt="Screenshot 2025-12-26 184638" src="https://github.com/user-attachments/assets/21b503ab-da23-4f88-a20d-74d7c23f1c85" />
mean=np.mean(data) print(mean) 50.724137931034484

std=np.std(data) print(std) 25.59889080534025

z=np.abs(stats.zscore(df)) print(z)
<img width="930" height="622" alt="Screenshot 2025-12-26 184654" src="https://github.com/user-attachments/assets/1dec01cf-123f-472f-ae46-2d431fccdb8a" />
threshold=3 outliers = df[abs(df) > 3] print("Outliers:") print(outliers)
<img width="293" height="755" alt="Screenshot 2025-12-26 184705" src="https://github.com/user-attachments/assets/200026dd-1d3c-4e4f-a1d9-585d8cdaca1b" />
df_cleaned = df[(z <= threshold)] print(df_cleaned)
<img width="257" height="783" alt="Screenshot 2025-12-26 184713" src="https://github.com/user-attachments/assets/400ed81b-6175-4069-8993-75bb14b2ec0e" />
sns.boxplot(df_cleaned)
<img width="882" height="598" alt="Screenshot 2025-12-26 184730" src="https://github.com/user-attachments/assets/9c64ea89-cbc7-416e-a400-8917ca3fb929" />
sns.scatterplot(df_cleaned)
<img width="912" height="612" alt="Screenshot 2025-12-26 184738" src="https://github.com/user-attachments/assets/1624f141-d5aa-4677-a1d4-cbe4a1eb7203" />





        <<include your coding and its corressponding output screen shots here>>
# Result
          <<include your Result here>>
