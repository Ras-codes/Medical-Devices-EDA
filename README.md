<div align="center">
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
  





# Exploratory Data Analysis









## Insights from the Dataset

- After importing the dataset, our first step is to check if the data is imported properly, we can use `data.shape` to check the number of observations (rows) and features (columns) in the dataset
- Output will be : ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/0e9569bc-b157-46d0-8bf1-2df2709a9dae)
- which means that the dataset contains 403 records and 21 variables.
- We will now use `data.head()` to display the top 5 observations of the dataset
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/c43779dd-7e77-446d-81ca-ce662e27d7ee)
- To understand more about the data, including the number of non-null records in each columns, their data types, the memory usage of the dataset, we use `data.info()`
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/873a6546-0d8e-4d4e-98e8-bcd9dc69ae5c)



## Data Preparation:

### Renaming the variable names with appropriate naming convention
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/2b2616c8-f7c9-41f6-9aa4-2590b5316716)
- `data.columns = [i.replace('.','_') for i in data.columns]`
- Using list comprehension for replacing dots with underscores in column names of the data according to naming convention
- ![image](https://github.com/Ras-codes/Medical-Devices-EDA/assets/164164852/0669d6a0-d227-4613-b6cb-3af99852fce3)






























