import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("LPU_Student_Performance_PowerBI.csv")

# Display basic info
print(df.info())
print(df.describe())

# Check for missing values
print("\nMissing Values:")
print(df.isnull().sum())

# Correlation Heatmap
plt.figure(figsize=(10,6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm", linewidths=0.5)
plt.title("Correlation Heatmap of Student Performance Factors")
plt.show()

# GPA Distribution
plt.figure(figsize=(8,5))
sns.histplot(df["GPA"], bins=10, kde=True, color='blue')
plt.title("Distribution of GPA")
plt.xlabel("GPA")
plt.ylabel("Count")
plt.show()

# Relationship between Study Hours and GPA
plt.figure(figsize=(8,5))
sns.scatterplot(x=df["Study_Hours_Per_Week"], y=df["GPA"], hue=df["Internet_Access"], palette='coolwarm')
plt.title("Study Hours vs. GPA")
plt.xlabel("Study Hours Per Week")
plt.ylabel("GPA")
plt.show()

# Boxplot of GPA by Extracurricular Activities
plt.figure(figsize=(8,5))
sns.boxplot(x=df["Extracurricular_Activities"], y=df["GPA"], palette="Set2")
plt.title("GPA Distribution by Extracurricular Activities")
plt.xlabel("Extracurricular Activities Participation")
plt.ylabel("GPA")
plt.show()

print("Analysis Completed! Insights ready for Power BI.")
