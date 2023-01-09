# %% [markdown]
# ## Details
# Name : Stellla Achar Oiro <br>
# email: stella.achar@azubiafrica.org <br>
# Team: Prague <br>
# Link to Github Repo - ([GitHub](https://github.com/Stella-Achar-Oiro/LP1-Data-Analysis-Project))
# 
# Week 2
# Project - Indian Startup Funding

# %% [markdown]
# # Indian Startup Ecosystem Analysis
# # Intro
# 
# ## Project Intro and Objective
# **Objective** - Our team is trying to venture into the Indian startup ecosystem. As the data experts of the team we are supposed to investigate the ecosystem and propose the best course of action.
# 
# ## Business & Data Understanding
# **How does Venture Capital Funding Work?** The process entails entrepreneurs pitching an idea to potential investors seeking finances (funding) to start/improve the business in various ways. A business plan is often a requirement for Venture Capitalist to assess the viability of the entrepreneur’s idea. **Invention** and **Innovation** are key concepts related to Venture Capital funding. Roughly 80% of funding goes into building infrastructure needed to grow the business. (Expenses `[manufacturing, sales, marketing]` and Balance Sheet `[working capital & assets]`).
# 
# Venture Capital Funding is short-term oriented - it is meant to grow the business to a point where it can be later sold off (to a Corporation or theough IPO). Sometimes the VC wants **equity** (a share of the business). Start-ups (esp. in the new information economy) lack hard assets and can’t therefore access funding from banks (require collateral)
# **Large institutions** are often behind VC funds – insurance companies, pension funds, financial firms, universities. **Angel Investors** who are High net worth individuals are also participants. While screening ideas or after giving funding to businesses, Venture Capitalists can impose restrictions on behaviour of entrepreneurs.
# 
# While looking at the **The Indian Venture Capital context**,  we see a booming start-up ecosystem that has become one of the world’s most vibrant and innovative business environments. Country is increasingly being recognized as popular destinations for venture capital (VC) investments. Early-stage investments are seeing particularly strong growth in recent years while Domestic investors are still the most active investor group.
# 
# The are several stages of **Startup/Venture Capital Funding** - 
# 1. **Seed Funding** - the earliest stage of capital raising process as business hasn't started and is only an idea. It is considered the most risky and complicated as investor doesn’t have enough info to make a decision. Main participants are mostly Angel Investors (appreciate riskier ventures and expect high returns). Management/Soft skills of entrepreneur can determine business success (although modern Tech challenges this view).
# 2. **Series A Fianncing** - A type of equity-based financing (company offers convertible preferred shares). Consists of businesses that already generate revenues but are still in the pre-profit stage. Primary objective of funding is for continued growth. It follows a more formal process – more complete company info, valuation of company done & VC firm does due diligence (progress made since start, management’s efficiency in managing resources). Series A rounds raise approximately $2 million to $15 million and the median Series A funding 2021 = $10 million. ([Investopedia](https://www.investopedia.com/articles/personal-finance/102015/series-b-c-funding-what-it-all-means-and-how-it-works.asp))
# 3. **Series B Financing** - this is the 3rd Stage Start-up financing and the 2nd stage VC financing. Like Series A, it is also equity based. The business is already in middle stages of growth, has a user base and could be generating profit. It is now looking to expand their market. More participants enter at  this stage as they are willing to invest in later stages of growth. The objective of funding here is to take business past development stage, help business scale or meet levels of demand. Most participants here are Venture Capital firms and private equity firms.
# 
#  
# 
# ## Overview of the Data
# 
# The dataset available coonsists of the following peices of data;
# 1. Startup Name/Brand
# 2. Year of Founding
# 3. Location/Headquarters of Business
# 4. Sector of the business
# 5. Founders (Owners)
# 6. Investor (assume it’s the VCs)
# 7. Amount of Funding
# 8. Stage (at which business is in while seeking/offered funding)
# 
# **Note** - The 2018 Data Lacks some of the above data and has conflict of some data (like currency).

# %% [markdown]
# # Hypothesis
# 
# **Null Hypothesis** – No factors determine the amount of funding offered to a start-up by venture capitalists in India.
# 
# **Alternative Hypothesis** – A range of factors about a start-up(characteristics) such as sector it wants to venture into, use of technology or years its has been in existence, stage of growth and location determine the amount of funding offered to start-ups by venture capitalists in India.
# 
# # Research Questions
# 
# **Sector**
# 1. What sectors have attracted the largest funding in the last 4 years?
# 2. Who are the major funders of ventures in India in the last 4 years? And what are the major sectors they are directing their funding?
# 3. What are the Maximum, Minimum, Average and Median Funding amounts offered to each sector/ stage of funding and how do they compare?
# 4. What is the trend of financing over the four years, cumulatively (total funding) and in independent sectors? (Monthly and/Yearly Trends)
# **Technology**
# 5. What business technologies have recieved the highest funding or have been funded more over the last four years?
# **Location**
# 6. What locations have received the biggest funding?
# 7. What is the spread of Venture Capital funding in India regionally and how do they compare?
# **Stage**
# 8. Does the stage of the venture affect the amount of funding offered to ventures?
# 9. How many ventures that have got a previous round of financing gone on to successfully raise another stage of financing?
# **Founders**
# 10. Does the number of business owners (entrepreneurs) in a venture determine the amount/likelihood of funding from investors?
# 11. Does the year of founding determine/influence the funding amount?

# %% [markdown]
# ## Installation
# Here is the section to install all the packages/libraries that will be needed to tackle the challlenge.

# %%
# !pip install pandas

# %% [markdown]
# ## Importation
# Here is the section to import all the packages/libraries that will be used through this notebook.

# %%
# Data handling
import numpy as np
import pandas as pd

# Vizualisation (Matplotlib, Plotly, Seaborn, etc. )
import matplotlib.pyplot as plt
import seaborn as sns

# EDA (pandas-profiling, etc. )
...

# Feature Processing (Scikit-learn processing, etc. )
...

# Machine Learning (Scikit-learn Estimators, Catboost, LightGBM, etc. )
...

# Hyperparameters Fine-tuning (Scikit-learn hp search, cross-validation, etc. )
...

# Other packages
import os


# %% [markdown]
# # Data Loading
# Here is the section to load the datasets (train, eval, test) and the additional files

# %%
# For CSV, use pandas.read_csv

from google.colab import drive
drive.mount('/content/drive')

startupdf_2018 = pd.read_csv('/content/drive/MyDrive/India Startup Funding/startup_funding2018.csv')
startupdf_2019 = pd.read_csv('/content/drive/MyDrive/India Startup Funding/startup_funding2019.csv')
startupdf_2020 = pd.read_csv('/content/drive/MyDrive/India Startup Funding/startup_funding2020.csv')
startupdf_2021 = pd.read_csv('/content/drive/MyDrive/India Startup Funding/startup_funding2021.csv')

# %% [markdown]
# # Exploratory Data Analysis: EDA
# Here is the section to **inspect** the datasets in depth, **present** it, make **hypotheses** and **think** the *cleaning, processing and features creation*.

# %% [markdown]
# ## Dataset overview
# 
# Have a look at the loaded datsets using the following methods: `.head(), .info()`

# %%
# Get a summary of the 2018 data
startupdf_2018.info()

# %%
# Get a summary of the 2019 data
startupdf_2019.info()

# %%
#Make the 2018 data Column names match the 2019-2021 data

startupdf_2018.rename(columns={'Company Name' : 'Company/Brand', 'Industry' : 'Sector', 'Round/Series' : 'Stage', 'Amount' : 'Amount($)', 'Location' : 'HeadQuarter', 'About Company' : 'What it does'}, inplace = True)

# %%
# View the 2018 dataframe columns
startupdf_2018.columns

# %%
#View the 2018 columns data types

startupdf_2018.info()

# %%
#Concatenate all four dataframes
#Vertical concatenation used (axis=0 ) means along rows
#ignore-Index parameter to reset the index

startup_df = pd.concat([startupdf_2018, startupdf_2019, startupdf_2020, startupdf_2021], axis=0, ignore_index=True, sort=False)

# %%
#View concatenated dataframe to confirm

startup_df

# %%
#View number of columns and rows of new dataframe
startup_df.shape


# %%
#View data types of the columns of the new dataframe
startup_df.info()

# %%
# Remove/Drop the extra null column - Unnamed: 9
startup_df.drop('Unnamed: 9', inplace=True, axis=1)

# %%
# View the dataframe to confirm column deletion
startup_df

# %% [markdown]
# ### Start Cleaning the Amounts Column
# 
# In this section, we will start cleaning the Amounts column of the dataframe as it contains the info that relates to all our questions 

# %%
# Check types of data in the Amounts Column

startup_df['Amount($)'].apply(type).unique()

# %%
#drop the words "Undisclosed" and "undisclosed" in Amounts column

startup_df =startup_df.drop(startup_df[(startup_df['Amount($)'] == 'Undisclosed') | (startup_df['Amount($)'] == 'undisclosed')].index )

# %%
#Replace commas with ''

startup_df['Amount($)'] = startup_df['Amount($)'].apply(lambda x: x.replace(',',''))
#startup_df['Amount($)'] = startup_df['Amount($)'].str.replace(',','', regex=True)

# %%
#Replace Rupee sign with ''

startup_df['Amount($)'] = startup_df['Amount($)'].apply(lambda x: x.replace('₹',''))
#startup_df['Rupee-Amount'] = startup_df['Amount($)'].str.replace('₹','', regex=True)

# %%
#Replace Dollar sign with ''

startup_df['Amount($)'] = startup_df['Amount($)'].apply(lambda x: x.replace('$',''))
#startup_df['Amount($)'] = startup_df['Amount($)'].str.replace('₹','', regex=True)

# %%
startup_df.head(10)

# %%
startup_df.shape

# %%
startup_df.describe()

# %%
startup_df.dtypes

# %%
#Check null values in each column

startup_df.isna().sum()

# %%
# Check for duplicated rows

startup_df.duplicated().sum()

# %%
# Check for Duplicated columns

startup_df.T.duplicated().sum()

# %%
#Drop duplicates and create another dataframe with unduplicated columns

unduplicated_startup_df = startup_df.drop_duplicates()
unduplicated_startup_df

# %%
unduplicated_startup_df.shape

# %% [markdown]
# ## Univariate Analysis
# 
# ‘Univariate analysis’ is the analysis of one variable at a time. This analysis might be done by computing some statistical indicators and by plotting some charts respectively using the pandas dataframe's method `.describe()` and one of the plotting libraries like  [Seaborn](https://seaborn.pydata.org/), [Matplotlib](https://matplotlib.org/), [Plotly](https://seaborn.pydata.org/), etc.
# 
# Please, read [this article](https://towardsdatascience.com/8-seaborn-plots-for-univariate-exploratory-data-analysis-eda-in-python-9d280b6fe67f) to know more about the charts.

# %%
# Code here

# %% [markdown]
# ## Multivariate Analysis
# 
# Multivariate analysis’ is the analysis of more than one variable and aims to study the relationships among them. This analysis might be done by computing some statistical indicators like the `correlation` and by plotting some charts.
# 
# Please, read [this article](https://towardsdatascience.com/10-must-know-seaborn-functions-for-multivariate-data-analysis-in-python-7ba94847b117) to know more about the charts.

# %%
# Code here

# %% [markdown]
# # Feature processing
# Here is the section to **clean** and **process** the features of the dataset.

# %% [markdown]
# ## Missing/NaN Values
# Handle the missing/NaN values using the Scikif-learn SimpleImputer

# %%
# Code Here

# %% [markdown]
# ## Scaling
# Scale the numeric features using the Scikif-learn StandardScaler, MinMaxScaler, or another Scaler.

# %%
# Code here

# %% [markdown]
# ## Encoding
# Encode the categorical features using the Scikif-learn OneHotEncoder.

# %%
# Code here


