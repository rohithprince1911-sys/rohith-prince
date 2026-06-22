

# Disease Analysis
disease_count = df['Disease'].value_counts()

plt.figure(figsize=(8,5))
sns.barplot(x=disease_count.index, y=disease_count.values)
plt.title("Patient Count by Disease")
plt.xlabel("Disease")
plt.ylabel("Number of Patients")
plt.show()
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Create Dataset
data = {
    'Patient_ID':[1,2,3,4,5,6,7,8],
    'Name':['Ram','Priya','Arun','Divya','Kumar','Sneha','Ravi','Anu'],
    'Age':[25,40,60,30,50,18,45,35],
    'Gender':['Male','Female','Male','Female','Male','Female','Male','Female'],
    'Disease':['Fever','Diabetes','Heart Disease','Fever','Diabetes','Asthma','Fever','Asthma'],
    'Admission_Date':['2025-01-10','2025-01-15','2025-02-12','2025-02-20',
                      '2025-03-05','2025-03-18','2025-04-10','2025-04-22']
}

df = pd.DataFrame(data)

# Display Dataset
print("Dataset Preview")
print(df)

# Data Cleaning
df.drop_duplicates(inplace=True)
df.dropna(inplace=True)

print("\nCleaned Dataset")
print(df)
# Age Group Analysis
bins = [0,18,35,50,100]
labels = ['0-18','19-35','36-50','51+']

df['Age_Group'] = pd.cut(df['Age'], bins=bins, labels=labels)

age_count = df['Age_Group'].value_counts()

plt.figure(figsize=(6,4))
age_count.plot(kind='bar')
plt.title("Patients by Age Group")
plt.xlabel("Age Group")
plt.ylabel("Count")
plt.show()

# Admission Trend
df['Admission_Date'] = pd.to_datetime(df['Admission_Date'])

monthly_admission = df.groupby(df['Admission_Date'].dt.month).size()

plt.figure(figsize=(8,5))
monthly_admission.plot(marker='o')
plt.title("Monthly Admission Trend")
plt.xlabel("Month")
plt.ylabel("Number of Admissions")
plt.grid(True)
plt.show()

# Final Output
print("\nMost Common Disease:", df['Disease'].mode()[0])
print("Total Patients:", len(df))# rohith-prince
