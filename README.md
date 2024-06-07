# datafun-06-eda

# Iris Dataset Analysis

## ALBERT KABORE
Introduction
The Iris dataset is a classic dataset in the field of machine learning and statistics, containing measurements of sepal length, sepal width, petal length, and petal width for three species of iris flowers: Setosa, Versicolor, and Virginica. Our goal is to explore and understand the relationships between these measurements and how they vary across different species.

## Specification for Project 6 EDA Notebook
## Overview
## Project 6 is an opportunity to create your own custom exploratory data analysis (EDA) project using GitHub, Git, Jupyter, pandas, Seaborn and other popular data analytics tools.

Project Setup Instructions
1. Create a New GitHub Repository
## Open your browser and navigate to GitHub.
## Create a new repository named datafun-06-eda. Make sure to initialize it with a default README.md.
2. Clone the Repository
## Clone the repository to your local machine:

```PowerShell
git clone https://github.com/albertokabore/datafun-06-eda
```
3. Create a Virtual Environment
## Navigate to the project directory and create a virtual environment in the .venv folder:

```PowerShell
py -m venv .venv
```
4. Activate the Virtual Environment
Activate the virtual environment:

```PowerShell
.venv\Scripts\activate
```
5. Install Dependencies
## Install a Package

```PowerShell
py -m pip install requests
```

## Install initial project dependencies:

```PowerShell
py -m pip install jupyterlab pandas pyarrow matplotlib seaborn
``` 
## List Installed Packages

```PowerShell
py -m pip list
```

6. Freeze Dependencies
## Freeze the installed requirements into a requirements.txt file:

```PowerShell
py -m pip freeze > requirements.txt
```

7. Update .gitignore
## Create or update the .gitignore file in the root project folder and add the following entries:

```PowerShell
.venv/
.ipynb_checkpoints/
```

8. Commit Changes
## Add the changes to git and commit them:

```PowerShell
git add .
git commit -m "Initial commit"
git push origin main
```
9. Working with Jupyter Notebooks
## Setting Up Jupyter Notebook:

Ensure that Jupyter is installed within your virtual environment. If not, install it using pip:

```PowerShell
py -m pip install jupyter
```
## Start the Jupyter notebook to begin working on your project:
jupyter notebook
## Create a new notebook with the .ipynb extension in the root project folder, e.g., yourname_eda.ipynb.

```
Albertkabore_eda.ipynb
```
10. Using the Notebook:
## Add a markdown cell at the top of your notebook with the title, your name, the date, and the purpose of the project.
## Import necessary libraries at the beginning of your notebook:

```python

import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
```
11. Perform exploratory data analysis (EDA), starting with data acquisition, initial inspections, and moving through descriptive statistics, data distribution, and initial visualizations.
## Step 1. Data Acquisition
Load the data into a pandas DataFrame. Use the pd read functions such as pd.read_csv() or pd.read_excel() as appropriate. To read from the Seaborn dataset, we'll use sns.load_dataset() function and pass in the 'iris' (the name without .csv) to populate our DataFrame.

```python
# Load the dataset into a pandas DataFrame - adjust this process for your custom data
df = sns.load_dataset('iris')
# Inspect first rows of the DataFrame
print(df.head())
```
## Step 2. Initial Data Inspection
Display the first 10 rows of the DataFrame, check the shape, and display the data types of each column using df.head(10), df.shape, and df.dtypes.

```python
print(df.head(10))
print(df.shape)
print(df.dtypes)
```
## Step 3. Initial Descriptive Statistics

```python
print(df.describe())
```
Observation

## Step 4. Initial Data Distribution for Numerical Columns
Choose a numerical column and use df['column_name'].hist() to plot a histogram for that specific column. To show all the histograms for all numerical columns, use df.hist().

```python
# Inspect histogram by numerical column
df['sepal_length'].hist()
# Inspect histograms for all numerical columns
df.hist()
# Show all plots
plt.show()
```
Observation

## Step 5. Initial Data Distribution for Categorical Columns
Choose a categorical column and use df['column_name'].value_counts() to display the count of each category. Use a loop to show the value counts for all categorical columns.

```python
# Inspect value counts by categorical column
df['species'].value_counts()
# Inspect value counts for all categorical columns
for col in df.select_dtypes(include=['object', 'category']).columns:
    # Display count plot
    sns.countplot(x=col, data=df)
    plt.title(f'Distribution of {col}')
    plt.show()
# Show all plots
plt.show()
```
Observation

## Step 6. Initial Data Transformation and Feature Engineering
1. Rename at least one column.

```python
df.rename(columns={'species': 'flower_species'}, inplace=True)
```

```python
# Verify transformations
print(df.head())
```

2. Add at least one column.

```python
# Adding a new column 'sepal_area' as the product of sepal length and sepal width
df['sepal_area'] = df['sepal_length'] * df['sepal_width']
```

```python
# Verify transformations
print(df.head())
```

```python
# Display the updated DataFrame with the new column
print(df.head(10))
```

## Step 7. Initial Visualizations
1. Distribution of Sepal Lengths by Species
Goal:
Explore the distribution of sepal lengths across different species to understand if there are distinct differences
Chart Type: Violin Plot

 ```python
# Violin plot to show distribution of sepal lengths by species
plt.figure(figsize=(10, 6))
sns.violinplot(x='flower_species', y='sepal_length', data=df)
plt.title('Distribution of Sepal Lengths by Species')
plt.xlabel('Species')
plt.ylabel('Sepal Length')
plt.show()
```
Observation

2. Distribution of Sepal Lengths
Goal:
Explore the distribution of sepal lengths across different species.
Chart Type: Histogram

 ```python
# Histogram for sepal length
plt.figure(figsize=(10, 6))
sns.histplot(data=df, x='sepal_length', hue='flower_species', multiple='stack', palette='viridis')
plt.title('Distribution of Sepal Lengths by Species')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Count')
plt.show()
 ```
Observation

4. Relationship Between Sepal Length and Sepal Width
Goal:
Examine the relationship between sepal length and sepal width across different species.
Chart Type: Scatter Plot

 ```python
# Scatter plot for sepal length vs. sepal width
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='sepal_length', y='sepal_width', hue='flower_species', palette='viridis')
plt.title('Sepal Length vs. Sepal Width by Species')
plt.xlabel('Sepal Length (cm)')
plt.ylabel('Sepal Width (cm)')
plt.show()
 ```
Observation

5. Sepal Area Distribution
Goal:
Investigate the distribution of the newly created sepal area feature across different species.
Chart Type:Box plot

 ```python
# Box plot for sepal area
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, x='flower_species', y='sepal_area', hue='flower_species', palette='viridis', dodge=False)
plt.title('Distribution of Sepal Area by Species')
plt.xlabel('Species')
plt.ylabel('Sepal Area (cm^2)')
plt.legend([],[], frameon=False)
plt.show()
 ```
 Observation

## Step 8. Initial Storytelling and Presentation
Conclusion:


Commit all changes and push them to your GitHub repository:

git add .
git commit -m "Complete project setup and initial analysis"
git push








