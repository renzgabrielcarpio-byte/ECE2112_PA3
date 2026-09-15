# ECE2112_PA3
## Experiment 3: PYTHON DATA ANALYSIS (PANDAS)
Renz Gabriel P. Carpio  |  2ECE-A

OBJECTIVES:
At the end of this laboratory activity, the student should be able to:
1. Load a CSV dataset into a Pandas DataFrame;
2. Select rows and columns using positional and label-based indexing;
3. Filter records using conditions on a DataFrame column; and
4. Extract a well-defined subset of data without changing the source data.

II. Instructions
Use the same cars.csv dataset supplied for Experiment 3. Write the solutions in one Jupyter Note-
book and import Pandas as pd. The dataset contains the Model column together with the vehicle
variables used in the original experiment.
• Load the CSV file into a DataFrame named cars.
• Use Pandas subsetting, slicing, indexing, and Boolean conditions. Do not manually type any
requested table or answer.
• Do not modify values in cars; create a new DataFrame or Series for each requested subset.
• Preserve the row order of the source dataset unless stated otherwise.
• Display every requested result in an executed notebook cell.

# **A. POSITIONAL AND LABEL-BASED SLICING**

Load the `cars.csv` dataset into a DataFrame named `cars`. Display its shape and column names, then extract rows 6 through 10 (1-indexed) into `cars_6_to_10` using positional indexing, and display only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` using label-based indexing.

The following functions and methods were used in this problem:

• `pd.read_csv()` - loads the contents of a CSV file into a Pandas DataFrame structure.

Example: `cars = pd.read_csv('cars.csv')`

• `.shape` & `.columns` - attributes used to inspect the dimensional structure (number of rows and columns) and the complete list of column labels in the DataFrame.

• `.iloc[]` - purely integer-location based indexing used to slice rows by their integer position. Slicing indices `5:10` extracts the 6th through 10th rows because Python follows 0-based indexing.

• Label-Based Column Selection (`[['Model', 'mpg', ...]]`) - selects a specific subset of columns by passing a list of column names inside square brackets.

Combining these operations, the final implementation for this problem is as follows:

```python
import pandas as pd

# Load dataset
cars = pd.read_csv("cars.csv")

# a. Display shape and column names
print("Dataset Shape:", cars.shape)
print("Columns:", list(cars.columns))

# b. Positional slicing: rows 6 through 10 (index 5 to 9)
cars_6_to_10 = cars.iloc

# c. Label-based selection: Model, mpg, cyl, hp, and gear
selected_columns = cars_6_to_10[["Model", "mpg", "cyl", "hp", "gear"]]
print("\nRows 6 to 10 with specified columns:\n", selected_columns)
```

# **B. MODEL LOOKUP 
Perform Boolean indexing on the Model column to locate specific vehicle records without hard-coding row indices. Display the complete row for "Toyota Corolla" and store it in toyota, then display only Model, mpg, hp, and wt for "Pontiac Firebird" and store it in pontiac.  

The following functions and methods were used in this problem:

• Boolean Masking (cars['Model'] == 'value') - creates a Series of True/False values evaluating whether each entry in the Model column matches the target string[cite: 3].

Example: cars['Model'] == 'Toyota Corolla'

[cite: 3]

• Row Filtering - passing the Boolean mask into the DataFrame indexer selects only the records that satisfy the condition[cite: 3].

• Label Projection - chaining column selection brackets after filtering retrieves only the designated columns for the matched row[cite: 3].

Combining these methods, the final implementation for this problem is as follows:

```python
import pandas as pd

# a. Complete row for Toyota Corolla
toyota = cars[cars["Model"] == "Toyota Corolla"]
print("Toyota Corolla Record:\n", toyota)

# b. Specified columns for Pontiac Firebird
pontiac = cars[cars["Model"] == "Pontiac Firebird"][["Model", "mpg", "hp", "wt"]]
print("\nPontiac Firebird Record:\n", pontiac)
```

# **C. MULTI-MODEL SUBSETTING

Filter the dataset by model name to create a new DataFrame named selected_cars containing records for "Datsun 710", "Lotus Europa", and "Ferrari Dino", retaining only the columns Model, mpg, cyl, hp, and gear[cite: 3].

The following functions and methods were used in this problem:

• .isin() - a Boolean filtering method that checks whether each value in a column is present within a specified list or iterable[cite: 3].

Example: cars['Model'].isin(['Datsun 710', 'Lotus Europa', 'Ferrari Dino'])

[cite: 3]

• Subset Indexing - filtering rows with .isin() and immediately scoping the column subset to ['Model', 'mpg', 'cyl', 'hp', 'gear'][cite: 3].

• Required Verification - checking .shape to ensure the final DataFrame contains exactly 3 rows and 5 columns[cite: 3].

Combining these techniques, the final implementation for this problem is as follows:

```python
import pandas as pd

# Define target vehicle models and columns
target_models = ["Datsun 710", "Lotus Europa", "Ferrari Dino"]
target_columns = ["Model", "mpg", "cyl", "hp", "gear"]

# Filter rows by model names and select the columns
selected_cars = cars[cars["Model"].isin(target_models)][target_columns]

# Required checks
print("Selected Cars DataFrame:\n", selected_cars)
print("\nShape of selected_cars:", selected_cars.shape)
```
