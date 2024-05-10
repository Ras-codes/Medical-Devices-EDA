![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/66a9d759-ece3-44d4-b771-c35f5d72869e)<div align="center">
  <h1>Exploratory Data Analysis on Biomedical data on Medical Devices for GluMet</h1>
</div>


<div align="center">
Performing Exploratory Data Analysis on Medical Devices for GluMet aiming to uncover insights and patterns regarding a patients' readings.
  
</div>



<div align="center">
  <img src="https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/8fb9cdc0-240f-4b8d-9251-4f448e17de0f" alt="ecommerce-01">
</div>



## Tools

- **Programming Language**: Python 🐍
- **IDE**: Jupyter Notebook 📓
- **Data Manipulation and Analysis**:
  - NumPy 📊
  - pandas 🐼
- **Data Visualization**:
  - Matplotlib 📊
  - Seaborn 📈
- **Date and Time Handling**: datetime ⏰



## Dataset Description: 

### Table- diabetes


### Variables-

**id**
- Type: Categorial (interger)
- Range: 1000 - 41756

**chol**
- Type: Numerical (Float)
- Range: 78 - 443
- Description: Cholesterol level of the patient.
  
**stab.glu**
- Type: Numerical (Integer)
- Range: 48 - 385
- Description: Stabilized glucose level of the patient.
  
**hdl**
- Type: Numerical (Float)
- Range: 12 - 120
- Description: High-density lipoprotein level of the patient.
  
**ratio**
- Type: Numerical (Float)
- Range: 1.5 - 19.299
- Description: Ratio of cholesterol to high-density lipoprotein.
  
**glyhb**
- Type: Numerical (Float)
- Range: 2.7 - 16.1
- Description: Glycosylated hemoglobin level of the patient.
  
**location**
- Type: Categorial (string)
- Values: Buckingham, Louisa
  
**age**
- Type: Numerical (Integer) 
- Values: 19 - 92
  
**gender**
- Type: Categorial (string)
- Values: Male, Female
  
**height**
- Type: Numerical (Float)
- Range: 52 - 76
  
**weight**
- Type: Numerical (Float)
- Range: 99 - 325
  
**frame**
- Type: Categorial (string)
- Values: small, medium, large
  
**bp.1s**
- Type: Numerical (Float)
- Range: 90 - 250
- Description: First systolic blood pressure reading.
  
**bp.1d**
- Type: Numerical (Float)
- Range: 48 - 124
- Description: First diastolic blood pressure reading.
  
**bp.2s**
- Type: Numerical (Float)
- Range: 110 - 238
- Description: Second systolic blood pressure reading.
  
**bp.2d**
- Type: Numerical (Float)
- Range: 60 - 124
- Description: Second diastolic blood pressure reading.
  
**waist**
- Type: Numerical (Float)
- Range: 26 - 56
  
**hip**
- Type: Numerical (Float)
- Range: 30 - 64
  
**time.ppn**
- Type: Numerical (Float)
- Range: 5 - 1560
- Description: Time when labs were drawn.
  
**diagnosis**
- Type: Categorial (string)
- Values: Non-Diabetic, Pre-Diabetes, Diabetic
- Description: Diagnosis of the patient for diabetes
  
**result**
- Type: Numerical (Float)
- Values: 0, 1
- Description: Result of the diagnosis (0 for Non-Diabetic, 1 for Diabetic).
  


# ------------------------------------------------------------------------------


# Exploratory Data Analysis

This repository contains code and resources for Exploratory Data Analysis on Biomedical data on Medical Devices project. The project demonstrates fundamental data manipulation techniques using Python programming language. It covers essential operations such as data loading, cleaning, handling missing values, outliers detection, transformation, analysis and data visualization using popular libraries like Pandas, NumPy, Matplotlib and Seaborn. The repository includes Jupyter notebooks with step-by-step explanations, dataset for practice, and examples showcasing various data manipulation tasks and data visualization graphs.


# ------------------------------------------------------------------------------


# Insights from the Dataset

- After importing the dataset, our first step is to check if the data is imported properly, we can use `data.shape` to check the number of observations (rows) and features (columns) in the dataset
- Output will be : ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/0e9569bc-b157-46d0-8bf1-2df2709a9dae)
- which means that the dataset contains 403 records and 21 variables.
- We will now use `data.head()` to display the top 5 observations of the dataset
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/c43779dd-7e77-446d-81ca-ce662e27d7ee)
- To understand more about the data, including the number of non-null records in each columns, their data types, the memory usage of the dataset, we use `data.info()`
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/873a6546-0d8e-4d4e-98e8-bcd9dc69ae5c)
- Checking cardinality / uniqueness of data with `data.nunique()`
- Count of distinct values in each column
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/78dbf626-bf40-4bf1-a7e0-d380280bf67a)


# ------------------------------------------------------------------------------


# Data Preparation:

Data can have different sorts of quality issues. It is essential that you clean and preperate your data to be analyzed.  Therefore, these issues must be addressed before data can be analyzed.

### Checking the variable names for appropriate naming convention-
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/2b2616c8-f7c9-41f6-9aa4-2590b5316716)
- A lot of these variables have dots in inbetween the names which is not an appropriate naming convention
- Using list comprehension for replacing dots with underscores in column names of the data.
````
data.columns = [i.replace('.','_') for i in data.columns]
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/0669d6a0-d227-4613-b6cb-3af99852fce3)

### Datatype Conversion-
- Converting datatype of stab.glu from int to float and datatype of id from int to object as it is a categorical variable.
````
data['stab_glu'] = data['stab_glu'].astype('float')
data['id'] = data['id'].astype('object')
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/995964c8-2aaa-4a39-b85a-36a2c1c690fe)

### Checking Data Duplicacy-
- checking if there are any duplicate records in the dataset with `data.duplicated().value_counts()`
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/db73fc1b-23c4-4fe9-8d3f-e0129705be14)
- It can be seen that there is no dupicacy in our data.

### Renaming variables-
- Renaming column 'id' with 'ID'
- renaming variables if needed with `data = data.rename(columns = {'id':'ID'})`
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/c4fd93a0-a581-4291-b8c3-4977c526789e)


# ------------------------------------------------------------------------------


# Handling Missing Values:

Next step is to check for missing values in the dataset. It is very common for a dataset to have missing values.

- `data.isna().sum()` isna() is used for detecting missing values in the dataframe, paired with sum() will return the number of missing values in each column.
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/96e1f60e-5c1f-48fd-a32d-8038577dee8d)
- There are many duplicates in the data which needs to be treated (filled with values)
- Creating a UDF which can automate the missing value treatment.
- Adding a condition for bp_2s and bp_2d so that it will pick the values of corresponding bp_1s and bp_1d instead of mean values of the bp_2s and bp_2d column.
````
def miss_value_treat(s, bp_1s=None, bp_1d=None):
    if s.dtype == 'O':
        s = s.fillna(s.mode())
    elif s.isnull().any():
        if s.name == 'bp_2s':
            s = s.fillna(bp_1s) if bp_1s is not None else s.fillna(s.median())
        elif s.name == 'bp_2d':
            s = s.fillna(bp_1d) if bp_1d is not None else s.fillna(s.median())
        else:
            s = s.fillna(s.median())
    return s
````
- Applying the miss_value_treat UDF to our data
````
data = data.apply(miss_value_treat, args=(data['bp_1s'].median(), data['bp_1d'].median()))
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/2d139d8e-e987-479e-bb87-624c049c01be)
- As per observations 'diagnosis' column is dependent on 'glyhb' readings, hence defining a seperate function for diagnosis column to fill with values since if glyhb is blank diagnosis column will also remain blank
- First, lets see the relation between glyhb and diagnosis variables
````
plt.figure(figsize=(10, 6))
sns.boxplot(x='diagnosis', y='glyhb', data=data, palette='deep')
plt.title('Distribution of Glycosylated Hemoglobin (glyhb) by Diagnosis')
plt.xlabel('Diagnosis')
plt.ylabel('Glycosylated Hemoglobin (glyhb)')
plt.show()
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/1296e6cd-b43c-4ee4-bbf8-23953a67fc16)
- This boxplot shows that if values in glyhb are less than 5.5 then diagnosis will be 'Non-Diabetic', if glyhb values are between 5.6 to 6.4 then diagnosis will be 'Pre-Diabetes' and it the glyhb values are greater than 6.5 then diagnosis will be 'Diabetic'.
- So, creating a new function to fill missing values in 'diagnosis' based on 'glyhb' values
````
def fill_diagnosis(row):
    if row['glyhb'] <= 5.5:
        return 'Non-Diabetic'
    elif 5.6 <= row['glyhb'] <= 6.4:
        return 'Pre-Diabetes'
    else:
        return 'Diabetic'
````
- Applying the function to diagnosis column only
````
data['diagnosis'] = data.apply(fill_diagnosis, axis=1)
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/0c0ce472-2872-42fc-978b-577bd53afc48)
- Now we can see that there are 0 missing values in our data!


# ------------------------------------------------------------------------------


# Data Preprocessing:

### Dividing the dataset into 2 datasets - categorical values and numerical values

**For categorical dataset**
````
cat = [var for var in data.columns if data[var].dtype == 'O']
categorical_data = data[cat]
categorical_data.head(2)
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/92eb0ea4-c13d-462f-9233-b39c5b281d62)

**For numerical dataset**
````
num = [var for var in data.columns if data[var].dtype != 'O']
numerical_data = data[num]
numerical_data.head(2)
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/ff53eb2d-9c76-424b-aa67-5f3a29e0a069)

**For merge**
- Later for merging if needed, a common column is needed between the 2 datasets, hence adding 'ID' column to categorical dataset
`categorical_data['ID'] = data['ID']`
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/3bf82e6b-9398-482a-aeea-fa485a766d74)


# ------------------------------------------------------------------------------


# Outlier Detection

Outliers are data points that deviate significantly from the overall pattern of the dataset and can indicate atypical or rare cases. Outliers in medical data can be indicative of unique cases or anomalies that deviate significantly from the general pattern, and their presence is something to be expected.


- To detect outliers in your dataset, you can use statistical methods or visualizations.
- Visualize the distribution of each numerical feature using box plots.
````
for col in numerical_data:
    plt.figure(figsize=(4, 3))
    sns.boxplot(numerical_data[col])
    plt.title(f'Boxplot of {col}')
    plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/c95e91e7-88c6-4b80-87a6-e8b50cb02667) ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/6d9da898-2f77-46d7-996e-e7911c96e777) ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/54d9f94e-fd3e-4094-b9b1-ff53a20e7371) ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/ca260cbf-0acb-4c18-bc9e-506383a19eca)

- In a box plot, potential outliers are typically represented as individual points that fall outside the whiskers of the plot.
- The whiskers of the box plot extend to the smallest and largest data points within a certain range from the lower and upper quartiles.
- As per observations it seems that the potential outliers are also very near to the whiskers of the box plot.

**Potential Ouliers**

- Calculating interquartile range (IQR) for numerical data
````
Q1 = numerical_data.quantile(0.25)
Q3 = numerical_data.quantile(0.75)
IQR = Q3 - Q1
````
- Identifying upper and lower limits
````
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
````
- Displaying potential outliers
````
potential_outliers = ((numerical_data < lower_bound) | (numerical_data > upper_bound)).sum()
print("Potential Outliers:\n", potential_outliers)
````
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/66e75ee2-df4a-476f-8cfa-65acf7dfc018)

**We see the presence of outliers in our dataset.In medical data, outliers can represent unusual or extreme observations that deviate significantly from the typical patterns within the dataset. These observations may point to unique cases, rare conditions, or outliers that exhibit characteristics different from the majority of the data. While outliers are often considered errors in some datasets, in medical data, they may have important clinical implications.**


# ------------------------------------------------------------------------------


# Visualizing Data:

## Univariate analysis:
Univariate analysis helps in understanding the distribution and characteristics of a single variable, which helps in pattern recognition. The chosen visualization method depends on the nature of the data — bar charts for discrete (numerical) data, histograms for continuous (numerical) data, and pie charts for categorical data.

### Distribution of patients by their age-
Here we will be making bins of age groups to make it an easily readable graph
````
age_bins = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
labels = ['0-10', '11-20', '21-30', '31-40', '41-50', '51-60', '61-70', '71-80', '81-90', '91-100']

data['age_group'] = pd.cut(data['age'], bins=age_bins, labels=labels)

data['age_group'].value_counts().sort_index().plot(kind='bar', color='skyblue')
plt.title("Distribution of patients by age group")
plt.xlabel("Age Group")
plt.ylabel("Number of patients")
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/3bab1622-dd15-41ac-b11b-c63c56a84a25)

### Distribution of patients by their location-
````
colors = sns.color_palette('GnBu')
plt.pie(data['location'].value_counts(), labels=['Louisa','Buckingham'], autopct='%1.1f%%', startangle=140, colors=colors)
plt.title('Distribution of Patients by Location')
plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/61e6a42b-0f42-466a-a9d1-6b05e3a1aee3)

### Distribution of patients by their gender-
````
colors = sns.color_palette('Blues')
plt.pie(data['gender'].value_counts(), labels=['Female', 'Male'], autopct='%1.1f%%', startangle=140, colors=colors)
plt.title('Distribution of Patients by Gender')
plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/763723b0-762a-4660-bf01-31a0bdeaeefb)

### Distribution of patients by diagnosis-
````
plt.pie(data['diagnosis'].value_counts(), labels=['Non-Diabetic', 'Diabetic', 'Pre-Diabetic'], autopct='%1.1f%%', startangle=140, colors=['thistle', 'pink', 'lavender'])
plt.title('Distribution of Patients by Diagnosis')
plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/f6dab837-2425-4709-8aae-314350690dbb)

### Distribution of 'glyhb' in patients-
````
sns.histplot(data['glyhb'], bins=15, kde=True, color='lightsteelblue')
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/90a98fb1-590d-48e7-a833-14774ede963b)

### Distribution of 'chol' in patients
````
sns.histplot(data['chol'], bins=15, kde=True, color='lightsalmon')
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/36643896-f5bf-478c-b1e4-03aa0bbd8073)

### Distribution of 'ratio' in patients
````
sns.histplot(data['ratio'], bins=15, kde=True, color='peachpuff')
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/fb16e5d6-ae84-4bb0-9418-71d37a9ef2be)

### Distribution of 'time_ppn' in patients
````
sns.histplot(data['time_ppn'], bins=15, kde=True, color='lightcoral')
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/2dfb876e-7c54-4952-ba63-329ca626ca8a)


## Bivariate and Multivariate analysis:

Bivariate analysis examines relationships between pairs of variables using scatter plots, line charts for trends, box plots for distribution, and heatmaps for correlations. These visualizations are crucial for uncovering connections and dependencies in the dataset. Box plots provide a summary of key statistical measures, including the minimum value, maximum value, median, and quartiles. Pair plots helps to explore relationships between multiple variables simultaneously. This visualization technique creates a grid of plots, each revealing the connection between two variables.

### Distribution of height and weight with box plot 
````
plt.figure(figsize=(10, 6))
sns.boxplot(x='height', y='weight', data=data, palette='viridis')
plt.title('Distribution of height and weight')
plt.xlabel('height')
plt.ylabel('weight')
plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/b5bf39de-f864-43fe-af70-907410ec2992)

### Distribution of glyhb against stab.glu for diagnosis with scatter plot
````
sns.scatterplot(x=data.stab_glu,y=data.glyhb, hue=data['diagnosis'])
plt.xlabel('stab.glu')
plt.ylabel('glyhb')
plt.title('Scatter plot of glyhb against stab.glu')
plt.show
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/e5de16d8-e237-48f0-87b0-5df39595c0c4)

### Distribution of chol, stab_glu, hdl, ratio, glyhb, bp_1s, bp_1d with pair plot
````
selected_columns = ['chol', 'stab_glu', 'hdl', 'ratio', 'glyhb', 'bp_1s', 'bp_1d']
sns.pairplot(data[selected_columns])
plt.show()
````
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/2e1be90b-4071-4b6e-ab0a-d48a4dea4202)
![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/4e66c1b4-1d74-4c0f-b34e-9f9b43c347b7)






































