# ECE-2112-PA-3: Python Data Analysis (Pandas)

**Made by: Zechariah Sampang | 2ECE-C**

This repository contains **Programming Assignment 3 (PA-3)** / **Experiment 3: Python Data Analysis (Pandas)** for the course **ECE 2112: Advanced Computer Programming and Algorithms** for S.Y. 2026-2027. This project covers three Python problems pertaining to Module 3 - Pandas.

---

## Overview & Learning Objectives

The objective of this assignment is to perform basic to intermediate data manipulation and subsetting on tabular automotive data (`cars.csv`) using Python's **Pandas** library.

**Key Concepts Covered:**
- Loading CSV datasets into Pandas DataFrames.
- Slicing data using positional (`iloc`) and label-based (`loc`) indexing.
- Filtering records using Boolean indexing on specific column conditions.
- Subsetting multi-column and multi-row data structures without mutating original data.

### **A. Positional and Label-Based Slicing**
#### **Tasks:**
1. Display the shape and complete list of column names of the `cars` DataFrame.
2. Extract rows **6 through 10** using positional slicing (`iloc`).
3. Filter and display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` in that specific order using label-based indexing (`loc`).

#### **Methods Used:**
- `cars.shape` - Returns a tuple `(32, 12)` representing rows and columns.
- `list(cars)` - Retrieves column headers as a list.
- `cars.iloc[6:11]` - Performs positional integer slicing to select rows 6 to 10 (inclusive of index 6 up to 10).
- `.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]` - Performs label-based column selection.

- 
```python
import pandas as pd

cars = pd.read_csv('cars.csv') # Load dataset
cars

car_shape = cars.shape #Display the shape of cars
car_shape
list(cars) #show the complete list of columns
cars.loc[:,'Model'] #model of cars

cars_6_to_10 = cars.iloc[6:11] #positional slicing
cars_6_to_10

#Column selection using labels
cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']] #display only columns in this order
```
### **B. Model Lookup**
#### **Tasks:**
Use Boolean indexing on the Model column to answer both requests.
a. Display the complete row for Toyota Corolla.
b. For Pontiac Firebird, display only Model, mpg, hp, and wt.
Store the two results in toyota and pontiac, respectively. Do not use a hard-coded row number to locate either model

#### **Methods Used:**
- `cars['Model'] == 'Toyota Corolla'` - Creates a Boolean mask matching the target model name.
- `cars.loc[condition, columns]` - Evaluates the Boolean mask and extracts specified column attributes dynamically.

```python
toyota = cars.loc[cars['Model'] == 'Toyota Corolla'] #display complete row for corolla
toyota
pontiac = cars.loc[cars['Model'] == 'Pontiac Firebird'] #and the same for firebird
pontiac
```
### **C.Multi-Model Subsetting**
#### **Tasks:**
Create a DataFrame named selected cars containing only the records for three models: Datsun 710,
Lotus Europa, and Ferrari Dino. For these records, retain only Model, mpg, cyl, hp, and gear. Select the rows by their model values rather than by row numbers. Display selected cars and its shape. Required check: The final DataFrame must contain exactly three rows and five columns.

#### **Methods Used:**
- `| `(Bitwise OR Operator) - Combines multiple equality conditions (==) across model names to perform multi-criteria filtering.
- `.loc[condition, ['Model', 'mpg', 'cyl', 'hp', 'gear']]` - Performs combined row filtering and column selection.
- `selected_cars.shape` - Displays the row and column dimensions of the subset to confirm the expected (3, 5) structure.

```python
selected_cars = cars.loc[
    (cars['Model'] == 'Datsun 710') |
    (cars['Model'] == 'Lotus Europa')|
    (cars['Model'] =='Ferrari Dino')
    ,['Model', 'mpg', 'cyl', 'hp', 'gear']]
selected_cars
selected_cars.shape
```

Thank you for reading! 

To see the main python program for Programming Assignment 3, click this [link](https://github.com/imwithiu/ECE2112-SAMPANG-PA3/blob/main/PA3_SAMPANG.ipynb) and download. Open on Jupyter Notebook, then run all cells.
