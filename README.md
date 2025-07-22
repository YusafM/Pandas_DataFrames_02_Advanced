# 🐼 Pandas DataFrames – Part 2: Working with Real Data

This notebook focuses on loading and analyzing real-world datasets using Pandas. I used a dataset called `mpg.csv` and practiced reading, summarizing, and slicing tabular data using common Pandas methods.

---

## 🎯 Purpose of This Notebook

The main goal of this session was to:
- Learn how to load a CSV file into a Pandas DataFrame
- Explore and inspect data using `.head()`, `.tail()`, and `.count()`
- Understand how to select and analyze specific columns
- Calculate simple statistics like mean and sum using Pandas

---

## 📘 Summary of What I Learned

- How to import data using `pd.read_csv()`
- How to interact with datasets using `.head()`, `.tail()`, and tab-complete
- Selecting multiple columns using single or double square brackets
- Using methods like `.mean()` and `.count()` to quickly summarize numerical data
- Leveraging column-level access to perform lightweight analysis

---

## 🧠 What I Practiced in This Notebook

### 1. 📥 Importing Libraries and Loading Data

```python
import pandas as pd

from google.colab import files
uploaded = files.upload()
```

**What I learned**:  
- `pandas` is required to manipulate tabular data  
- `files.upload()` is a Colab tool that allows you to upload local files (like `mpg.csv`) directly into your Colab environment

---

### 2. 📄 Reading a CSV File

```python
mpg = pd.read_csv("mpg.csv")
mpg
```

**What I learned**:  
- `pd.read_csv()` reads a comma-separated file and returns a DataFrame  
- Simply typing the variable name (`mpg`) returns the full DataFrame in Colab

---

### 3. 💡 Using Help & Autocomplete

```python
# Use the .count? or .head? syntax to bring up documentation in notebooks
mpg.count?
mpg.head?
```

**What I learned**:  
- Appending `?` to a method shows its docstring (inline documentation)  
- Helpful for quickly understanding what a function does without leaving the notebook

---

### 4. 🔚 Viewing Data Samples

```python
mpg.tail(3)
```

**What I learned**:  
- `.tail(n)` returns the last `n` rows of the DataFrame  
- Useful for peeking at the dataset without printing it all

---

### 5. 🧾 Selecting Columns of Interest

```python
columns_of_interest = ["displ", "cty", "hwy"]
mpg[columns_of_interest].head()

mpg[["cty", "hwy"]].head()
```

**What I learned**:  
- You can pass a list of column names inside `[]` to access multiple columns  
- This works with either a variable containing the list or directly using double square brackets

---

### 6. 📊 Summary Statistics

```python
mpg[["cty", "hwy"]].mean(axis=0)
```

**What I learned**:  
- `.mean()` calculates the average value across the specified axis  
- `axis=0` means column-wise, which is the default  
- This gives you a quick look at city and highway mileage averages


---

### 7. 🔄 Row-wise Averages Using axis=1

```python
mpg[["cty", "hwy"]].mean(axis=1).head()
```

**What I learned**:  
- `axis=1` means operate **across columns** (row-wise)
- This line calculates the average of `cty` and `hwy` mileage for each vehicle

---

### 8. ➕ Creating a New Column in the DataFrame

```python
mpg["average_mileage"] = mpg[["cty", "hwy"]].mean(axis=1)
mpg.head()
```

**What I learned**:  
- You can assign the result of a calculation to a new column in the DataFrame
- `average_mileage` is now a persistent feature in the dataset

---

### 9. 🔢 Value Counts for Categorical Data

```python
mpg.cyl.value_counts()
```

**What I learned**:  
- `value_counts()` shows the distribution of unique values
- Useful for understanding the frequency of categorical features (e.g., cylinder counts)

---

### 10. ✅ Boolean Filtering: Counting Matches

```python
(mpg.manufacturer == "audi").sum()
```

**What I learned**:  
- Boolean Series can be summed because `True = 1` and `False = 0`
- This counts how many rows match the condition (`manufacturer == "audi"`)

---

### 11. 📊 Calculating Proportions

```python
(mpg.cyl == 4).mean()
```

**What I learned**:  
- You can calculate proportions by taking the mean of a Boolean Series
- This gives the percentage of cars with 4 cylinders in the dataset

---

### 12. 🔍 Filtering Rows by Condition

```python
mpg[mpg.cyl == 5]
```

**What I learned**:  
- Simple filtering returns a subset of the DataFrame
- Here, only cars with 5 cylinders are included

---

### 13. 🧮 Combining OR Conditions

```python
mpg[(mpg.model == "maxima") | (mpg.cyl == 5)]
```

**What I learned**:  
- You can combine filters using the pipe symbol `|` (OR)
- This selects cars that are either a maxima or have 5 cylinders

---

### 14. 🔗 Combining AND Conditions

```python
mpg[(mpg["class"] == "midsize") & (mpg["displ"] < 2)]
```

**What I learned**:  
- The ampersand `&` is used for combining multiple conditions (AND)
- Filters must be grouped with parentheses for proper evaluation

---

### 15. ⚠️ Understanding References and DataFrame Copies

```python
original_df = pd.DataFrame({"x": [1, 2, 3]})
original_df

new_df = original_df
```

**What I learned**:  
- Assigning one DataFrame to another like `new_df = original_df` does **not** make a copy
- Both variables point to the same data in memory, which can lead to unexpected results

---

## ✅ Conclusion

This notebook expanded my understanding of working with real datasets using Pandas. I practiced selecting, filtering, summarizing, and even modifying data in a DataFrame. I now feel more confident working with real-world tabular data and performing light analysis using Python.

---

## 🙏 Acknowledgements

Special thanks to **Ryan Orsinger** for authoring the foundational material that guided this practice. His examples helped me apply Pandas tools to real data in a way that was easy to understand and meaningful.

---
