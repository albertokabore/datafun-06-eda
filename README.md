# datafun-06-eda

# Penguins Exploratory Dataset Analysis

## ALBERT KABORE
Introduction

In this exploratory Data analysis, we examine a dataset featuring measurements of three penguin species: Adelie, Chinstrap, and Gentoo. The dataset includes features such as bill length, bill depth, flipper length, body mass, and the island of observation. Through exploratory Data analysis, we aim to uncover insights about these species.

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
df = sns.load_dataset("penguins")
```

```python
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
df['body_mass_g'].hist()
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
# Renaming a column
df.rename(columns={'species': 'Penguin Species'}, inplace=True)
```

```python
# Verify transformations
print(df.head())
```

2. Add at least one column.

```python
# Adding a new column
df['body_mass_lbs'] = df['body_mass_g'] * 0.00220462
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
Subsection 1: Exploring the Relationship Between Flipper Length and Body Mass
Goal: Investigate how flipper length correlates with body mass across different penguin species.

Chart Type: Scatter plot

 ```python
# Scatter plot of flipper length vs. body mass
plt.figure(figsize=(10, 6))
scatter_plot = sns.scatterplot(data=df, x="flipper_length_mm", y="body_mass_g", hue="Penguin Species")
scatter_plot.set_xlabel("Flipper Length (mm)")
scatter_plot.set_ylabel("Body Mass (g)")
scatter_plot.set_title("Penguin Flipper Length vs. Body Mass")
plt.show()
```
Observation

Chart Type: Regression Plot

 ```python
# Regression plot of flipper length vs. body mass
plt.figure(figsize=(10, 6))
reg_plot = sns.lmplot(data=df, x="flipper_length_mm", y="body_mass_g", hue="Penguin Species", height=6, aspect=1.5)
plt.xlabel("Flipper Length (mm)")
plt.ylabel("Body Mass (g)")
plt.title("Regression of Flipper Length vs. Body Mass by Penguin Species")
plt.show()
 ```



Subsection 2: Comparing Bill Length Across Penguin Species
Goal: Compare the distribution of bill lengths among the different penguin species.Chart Type: Histogram
Chart Type: Box Plot

 ```python
# Box plot for bill length
plt.figure(figsize=(10, 6))
box_plot = sns.boxplot(data=df, x="Penguin Species", y="bill_length_mm", hue="Penguin Species", palette="viridis", dodge=False)
box_plot.set_xlabel("Penguin Species")
box_plot.set_ylabel("Bill Length (mm)")
box_plot.set_title("Distribution of Bill Length by Penguin Species")
plt.legend([],[], frameon=False)  # Removes the legend since we are only using hue for color
plt.show()
 ```
Observation

Subsection 3: Distribution of Body Mass Across Penguin Species
Goal: Examine the distribution of body mass for each penguin species.
Chart Type: Violin Plot

 ```python
# Violin plot for body mass
plt.figure(figsize=(10, 6))
violin_plot = sns.violinplot(data=df, x="Penguin Species", y="body_mass_g", hue="Penguin Species", palette="muted", dodge=False)
violin_plot.set_xlabel("Penguin Species")
violin_plot.set_ylabel("Body Mass (g)")
violin_plot.set_title("Distribution of Body Mass by Penguin Species")
plt.legend([],[], frameon=False)  # Removes the legend since we are only using hue for color
plt.show()
 ```

Observation
Subsection 4: Pairwise Relationships in the Penguin Dataset
Goal: Visualize pairwise relationships and distributions for numerical features in the dataset, separated by species.
Chart type: Pair plot 

```python
 # Pair plot for numerical features
pair_plot = sns.pairplot(df, hue="Penguin Species", diag_kind="kde", markers=["o", "s", "D"])
pair_plot.fig.suptitle("Pairwise Relationships in the Penguin Dataset", y=1.02)
plt.show()
 ```
Subsection 5: Correlation Matrix of Penguin Features
Goal: Examine the correlations between different numerical features in the dataset.
Chart Type: Heatmap

```python
# Compute the correlation matrix for numerical columns
numerical_df = df.select_dtypes(include=['float64', 'int64'])
corr = numerical_df.corr()
# Heatmap of the correlation matrix
plt.figure(figsize=(8, 6))
heatmap = sns.heatmap(corr, annot=True, cmap="coolwarm", center=0)
heatmap.set_title("Correlation Matrix of Penguin Features")
plt.show()
```

Subsection 6: Bill Length and Depth Distribution
Goal: To explore the distribution of bill length and bill depth across different penguin species.
Chart Type: Joint Plot

```python
# Joint plot for bill length vs. bill depth
plt.figure(figsize=(10, 6))
joint_plot = sns.jointplot(data=df, x="bill_length_mm", y="bill_depth_mm", hue="Penguin Species", kind="kde", height=8)
plt.xlabel("Bill Length (mm)")
plt.ylabel("Bill Depth (mm)")
plt.suptitle("Joint Distribution of Bill Length and Depth by Penguin Species", y=1.02)
plt.show()
```

## Step 8. Initial Storytelling and Presentation
Conclusion:

Commit all changes and push them to your GitHub repository:

git add .
git commit -m "Complete project setup and initial analysis"
git push origin main








