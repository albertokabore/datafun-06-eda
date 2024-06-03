# datafun-06-eda
Specification for Project 6 EDA Notebook
Overview
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
