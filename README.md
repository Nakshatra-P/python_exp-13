# Data Preprocessing with Pandas

## Aim

To perform data preprocessing on a Pandas DataFrame using Python, including handling missing values, type conversion, string normalization, and date formatting — and to understand key Pandas functions used in the process.

---

## Theory

Data preprocessing is the process of cleaning and transforming raw data into a usable format. Pandas provides several functions for this.

### 1. `isna()` and `notna()`
`isna()` returns `True` wherever a value is missing in the DataFrame, and `notna()` does the opposite. Using `.sum()` on `isna()` gives the total count of missing values in each column.

### 2. `dropna()`
Removes rows or columns that contain missing values. By default it drops rows (`axis=0`); passing `axis=1` drops columns instead.

### 3. `fillna()`
Replaces missing values with a specified value, this can be a constant like `0`, a string like `'Default'`, or a statistical value like the column mean using `df.mean()`.

### 4. `replace()`
Substitutes one value with another across the DataFrame. Here it is used to replace the `"-"` placeholder with `np.nan`, so Pandas can recognise those entries as missing values.

### 5. `pd.to_numeric()` with `errors='coerce'`
Converts a column to a numeric data type. The `errors='coerce'` argument ensures that any value that cannot be converted (like `NaN` or stray strings) is set to `NaN` instead of throwing an error.

### 6. `.str.upper()`
Converts all string entries in a column to uppercase. Used here to fix inconsistent casing in the Department column, so values like `"cse"` and `"CSE"` are treated as the same category.

### 7. `pd.to_datetime()` with `format="mixed"` and `dayfirst=True`
Converts a column of date strings into a proper datetime format. `format="mixed"` handles multiple date formats in the same column, and `dayfirst=True` ensures dates are read in the DD-MM-YYYY order.

---

## Conclusion

The experiment demonstrated how Pandas can be used to systematically clean and preprocess a raw dataset. Missing values were identified and imputed using column means to preserve statistical integrity. String placeholders were replaced with `NaN` and columns were cast to appropriate numeric types. Categorical inconsistencies were resolved through string normalization, and heterogeneous date formats were unified using `pd.to_datetime()`. These preprocessing steps ensure the data is consistent, correctly typed, and ready for downstream analysis or modelling.
