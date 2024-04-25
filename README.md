# education-dataset
Plot-1

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Read the CSV file into a pandas DataFrame
df = pd.read_csv('study_performance.csv')

# Create countplots for test preparation and lunch before exam with genders
plt.figure(figsize=(12, 6))

# Countplot for test preparation course
plt.subplot(1, 2, 1)
sns.countplot(data=df, x='test_preparation_course', hue='gender')
plt.title('Count of Students by Test Preparation Course and Gender')

# Countplot for lunch before exam
plt.subplot(1, 2, 2)
sns.countplot(data=df, x='lunch', hue='gender')
plt.title('Count of Students by Lunch Before Exam and Gender')

plt.tight_layout()
plt.show()

--------------------------------------------------------
Plot-2

# Calculate average score
df['average_score'] = (df['math_score'] + df['reading_score'] + df['writing_score']) / 3

# Set up the figure with 4 subplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot histograms for math, reading, writing scores, and average score
sns.histplot(df['math_score'], kde=True, ax=axes[0, 0], color='skyblue')
axes[0, 0].set_title('Math Score Distribution')

sns.histplot(df['reading_score'], kde=True, ax=axes[0, 1], color='salmon')
axes[0, 1].set_title('Reading Score Distribution')

sns.histplot(df['writing_score'], kde=True, ax=axes[1, 0], color='green')
axes[1, 0].set_title('Writing Score Distribution')

sns.histplot(df['average_score'], kde=True, ax=axes[1, 1], color='orange')
axes[1, 1].set_title('Average Score Distribution')

plt.tight_layout()
plt.show()

--------------------------------------------------------
Plot-3

# Calculate average score
df['average_score'] = (df['math_score'] + df['reading_score'] + df['writing_score']) / 3

# Set up the figure with 4 subplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot violin plots for math, reading, writing scores, and average score by race/ethnicity
sns.violinplot(data=df, x='race_ethnicity', y='math_score', ax=axes[0, 0])
axes[0, 0].set_title('Math Score Distribution by Race/Ethnicity')

sns.violinplot(data=df, x='race_ethnicity', y='reading_score', ax=axes[0, 1])
axes[0, 1].set_title('Reading Score Distribution by Race/Ethnicity')

sns.violinplot(data=df, x='race_ethnicity', y='writing_score', ax=axes[1, 0])
axes[1, 0].set_title('Writing Score Distribution by Race/Ethnicity')

sns.violinplot(data=df, x='race_ethnicity', y='average_score', ax=axes[1, 1])
axes[1, 1].set_title('Average Score Distribution by Race/Ethnicity')

plt.tight_layout()
plt.show()

--------------------------------------------------------
Plot-4

fig, axes = plt.subplots(2,2, figsize=(18,12))

sns.kdeplot(df, x='math_score', hue='gender', ax=axes[0,0])
axes[0,0].set_title("Math Score Distribution with Gender")

sns.kdeplot(df, x='reading_score', hue='gender', ax=axes[0,1])
axes[0,1].set_title("Reading Score Distribution with Gender")

sns.kdeplot(df, x='writing_score', hue='gender', ax=axes[1,0])
axes[1,0].set_title("Writing Score Distribution with Gender")

sns.kdeplot(df, x='average_score', hue='gender', ax=axes[1,1])
axes[1,1].set_title("Average Score Distribution with Gender")
