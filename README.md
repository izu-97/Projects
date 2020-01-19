# Shark attack database

The shark attack database project consist on cleaning a very messy db of shark attacks register over the years in different places all over the world. The main goal of the project is to  

## Usage

First we will have to import the pandas, numpy and matplotlib for this project. And resize the display of the rows in the jupyter notebook.

```python
import pandas as pd
import numpy as np
pd.options.display.max_rows = 200
pd.options.display.max_columns = 200
import matplotlib.pyplot as plt
plt.close('all')
```
## 1. Examine the data 

First we open the database in our jupyter notebook 

```python
df = pd.read_csv("GSAF5.csv", sep = ",", engine = "python")
```
After having an initial look at our database we realize that there are a lot of columns that appear to be empty or duplicate. 
So first we check for duplicate columns. After comparing the case columns we determine that they are almost identical. Then we check how many rows does our database have, and we check the type of each column. We see that a lot of columns do not have an appropriate type.
Then we check for the porcentage of nulls in each columns and we encounter that the Unnamed columns are mostly empty with 99% of null values.

## 2. Droping columns

After we determine the columns we dont need for our analysis we can start dropping them.

* Drop Unnamed :22 and Unnamed :23 since they are mostly empty.
* Drop case number.1 and case number.2 since they hold the same info as case number.
* Drop href formula and href since they are links that are not usefull for our analysis.
* Drop name for privacy reasons and because we dont really care about the names and 1/3 of the information is missing. 
* Drop pdf, case number, investigator source since they are not usefull for our analysis.

## 3. Rearrange and rename columns

We rearrange the colums and keep original number column as an ID primary key just in case we need to link this table to another one in the future. we remove the white spaces from sex and species foe saving us trouble in the future. And we rename the Fatal (Y/N) column to Survive (True/False) so we can assing a bool type to this column later.

## 4. Data cleaning

After dropping unnecessary columns and rearranging and renaming we can start cleaning of our data.

first we start by cleaning the date column by removing prefixes and extra words that might interfer with our analysis.
Then we convert this column to a date type so we have a more comprehensive view of the values. 
After removing this prefixes we count the nulls in the column and the total sum is 347 which is a value that we can live with since the total number of rows is 5992. 

We do the same for the age column we start by removing sub and prefexis to clean our data. Then we replace the words teen for the age 15 and young with 8 since this are the aproximate ages of people on this categories.
Then we convert this column to a float type for future analysis.

We change the data types of the columns caseid to int and the survive column to bool.

## 5. Analisys

After we clean or data we can start doing a little analysis which is describe on the ipynb file

## 6. Export as csv

Finally we export or file as a csv file.

