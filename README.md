# Customer Personality Data Cleaning & Preprocessing

## Project Overview

This project focuses on cleaning and preprocessing the **Customer Personality Analysis** dataset using **Python and Pandas**.

The objective is to transform raw customer marketing data into a clean, structured, and analysis-ready dataset by handling missing values, inconsistent data, incorrect data types, duplicate records, and inconsistent categorical values.

---

## Objective

The main objectives of this project are:

* Identify and handle missing values
* Remove duplicate records
* Standardize column names
* Convert data types appropriately
* Convert customer dates into a consistent datetime format
* Identify and handle inconsistent categorical values
* Check numerical data for potential outliers
* Prepare a clean dataset for further analysis and visualization

---

## Tools & Technologies

* **Python**
* **Pandas**
* **Jupyter Notebook**
* **VS Code**
* **Git & GitHub**

---

## Dataset

The dataset contains **2,240 customer records and 29 columns** related to customer demographics, purchasing behavior, website activity, campaign responses, and complaints.

### Main Categories of Data

* Customer demographics
* Education and marital status
* Income
* Household information
* Purchase behavior
* Web, catalog, and store purchases
* Marketing campaign responses
* Customer complaints

---

## Data Cleaning Process

### 1. Load Raw Dataset

The original dataset was loaded using Pandas with tab-separated values.

```python
raw_df = pd.read_csv(
    "../data/raw/marketing_campaign.csv",
    sep="\t"
)
```

### 2. Standardize Column Names

Column names were converted to lowercase and standardized using underscores.

Example:

```text
Year_Birth → year_birth
Marital_Status → marital_status
MntWines → mntwines
```

This makes the dataset easier to work with in Python.

### 3. Handle Missing Values

The `income` column originally contained **24 missing values**.

The missing income values were replaced using the **median income**:

```python
df["income"] = df["income"].fillna(df["income"].median())
```

After cleaning:

```text
Missing Values = 0
```

### 4. Remove Duplicates

Duplicate rows were checked and removed.

Final result:

```text
Duplicate Rows = 0
```

### 5. Convert Date Column

The `dt_customer` column was converted from text into a proper datetime data type.

```python
df["dt_customer"] = pd.to_datetime(
    df["dt_customer"],
    format="%d-%m-%Y"
)
```

### 6. Standardize Categorical Values

In the `marital_status` column, inconsistent values such as:

* `Alone`
* `Absurd`
* `YOLO`

were identified and standardized as `Unknown`.

Final categories include:

* Married
* Together
* Single
* Divorced
* Widow
* Unknown

### 7. Check Numerical Data

Numerical columns were checked for invalid values and potential outliers.

For example, `year_birth` contained unusually old birth years such as:

```text
1893
1899
1900
```

These records were investigated separately rather than blindly deleting them.

The income column was also examined for extreme values, including:

```text
666666
```

This was identified as a potential outlier and documented during the cleaning process.

### 8. Validate Binary Columns

Marketing campaign and response columns were checked to ensure they contained valid binary values:

```text
0 = No
1 = Yes
```

The following columns were validated:

* acceptedcmp1
* acceptedcmp2
* acceptedcmp3
* acceptedcmp4
* acceptedcmp5
* complain
* response

---

## Final Dataset Quality

| Data Quality Check |       Result |
| ------------------ | -----------: |
| Rows               |        2,240 |
| Columns            |           29 |
| Missing Values     |            0 |
| Duplicate Rows     |            0 |
| Date Column        |     Datetime |
| Income Data Type   |        Float |
| Binary Columns     |    Validated |
| Column Names       | Standardized |

---

## Project Structure

```text
Customer-Personality-Data-Cleaning/
│
├── data/
│   ├── raw/
│   │   └── marketing_campaign.csv
│   │
│   └── processed/
│       └── marketing_campaign_cleaned.csv
│
├── notebooks/
│   └── customer_personality_cleaning.ipynb
│
├── CLEANING_SUMMARY.md
│
└── README.md
```

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/niteshprajapati07/Customer-Personality-Data-Cleaning.git
```

### 2. Open the project

Open the project folder in **VS Code**.

### 3. Install Pandas

```bash
pip install pandas
```

### 4. Run the Notebook

Open:

```text
notebooks/customer_personality_cleaning.ipynb
```

and execute the cells sequentially.

---

## Outcome

The raw customer marketing dataset was successfully transformed into a **clean and analysis-ready dataset**.

The final dataset contains:

* **2,240 rows**
* **29 columns**
* **0 missing values**
* **0 duplicate rows**
* Standardized column names
* Proper datetime formatting
* Cleaned categorical values
* Validated numerical and binary fields

The cleaned dataset can now be used for **Exploratory Data Analysis (EDA), customer segmentation, marketing analysis, visualization, and machine learning**.

---

## Author

**Nitesh Prajapati**

BCA | Aspiring Data Analyst

**Skills:** Python, Pandas, Excel, SQL, Power BI
