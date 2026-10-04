# Data Cleaning Process

## 1. Project Objective

The objective of this project is to clean and prepare a large customer sales dataset using **AWS Glue DataBrew**.

The source dataset contains approximately **100,000 customer sales records** stored as a CSV file in Amazon S3.

---

## 2. AWS Services Used

- **Amazon S3** – stores the source and cleaned CSV files.
- **AWS Glue DataBrew** – performs data profiling, cleaning, and transformation.
- **AWS Glue DataBrew Recipe** – records the cleaning steps.
- **AWS Glue DataBrew Job** – applies the recipe to the dataset and generates the cleaned output.
- **GitHub** – stores project documentation and screenshots.

---

## 3. Source Dataset

The source file is:

`customer_sales_100k_databrew.csv`

The file is stored in an Amazon S3 bucket.

The dataset contains customer and sales information such as:

- Customer ID
- Customer Name
- Gender
- Age
- City
- State
- Region
- Customer Segment
- Category
- Product
- Quantity
- Unit Price
- Discount Percentage
- Sales Amount
- Payment Method
- Order Date

The original CSV contains approximately **100,000 records**.

> **Note:** DataBrew displays a sample of the source data in the project grid. The displayed sample (for example, 500 rows) does not represent the total number of records in the source CSV.

---

## 4. DataBrew Dataset Creation

The following steps were performed:

1. Opened **AWS Glue DataBrew**.
2. Selected **Datasets**.
3. Connected the CSV file from Amazon S3.
4. Created the dataset named:

`customer-sales-100k-dataset`

5. Verified the dataset source and S3 location.

---

## 5. DataBrew Project

A DataBrew project was created using the 100K dataset.

The project was used to inspect:

- Column names
- Data types
- Missing values
- Unique values
- Duplicate values
- Minimum and maximum values
- Data distributions

This helped identify data quality issues before applying transformations.

---

## 6. Data Cleaning Recipe

A DataBrew recipe was created to clean the dataset.

### Step 1 – Remove missing customer names

Rows with missing values in `customer_name` were removed.

**Reason:** Customer name is important for identifying and analyzing customer records.

### Step 2 – Remove missing cities

Rows with missing values in `city` were removed.

**Reason:** City is useful for geographical sales analysis.

### Step 3 – Remove missing ages

Rows with missing values in `age` were removed.

**Reason:** Age can be useful for customer segmentation and demographic analysis.

### Step 4 – Convert city to uppercase

The `city` column was converted to uppercase.

Example:

```text
Hyderabad → HYDERABAD
Bengaluru → BENGALURU
Chennai → CHENNAI
```

**Reason:** Standardizing text values makes grouping and analysis more consistent.

### Step 5 – Convert state to uppercase

The `state` column was converted to uppercase.

**Reason:** This standardizes state names and avoids differences caused by capitalization.

---

## 7. Recipe Publishing

After verifying the transformations, the DataBrew recipe was published.

The published recipe represents the repeatable data-cleaning workflow.

---

## 8. DataBrew Job

A recipe job was created using:

- **Dataset:** `customer-sales-100k-dataset`
- **Recipe:** `customer-sales-100k-project-recipe`

The job applies the recipe to the source data and generates the cleaned output.

---

## 9. Cleaned Output

The DataBrew job writes the cleaned data back to Amazon S3.

The cleaned output is stored under the:

`cleaned-100k/`

folder.

The output can then be used for:

- Sales analysis
- Customer segmentation
- Business reporting
- Data visualization
- Further analytics or machine learning

---

## 10. End-to-End Workflow

```text
100K Customer Sales CSV
          |
          v
     Amazon S3
          |
          v
AWS Glue DataBrew Dataset
          |
          v
   DataBrew Project
          |
          v
   Data Profiling
          |
          v
   Cleaning Recipe
          |
          v
    Recipe Job
          |
          v
    Cleaned Dataset
          |
          v
     Amazon S3
```

---

## 11. Result

The project successfully demonstrates a complete cloud-based data preparation workflow.

The main achievements are:

- Stored the 100K CSV dataset in Amazon S3.
- Connected the dataset to AWS Glue DataBrew.
- Inspected the dataset and identified data quality issues.
- Removed records with missing required values.
- Standardized city and state values.
- Published a reusable DataBrew recipe.
- Created and executed a DataBrew job.
- Stored the cleaned output in Amazon S3.
- Documented the project in GitHub.

---

## 12. Evidence

Screenshots included in this repository demonstrate:

1. Source 100K CSV in Amazon S3.
2. DataBrew dataset configuration.
3. DataBrew data preview.
4. Data cleaning recipe.
5. Published recipe.
6. DataBrew job.
7. Cleaned output in Amazon S3.

---

## Conclusion

This project shows how **AWS Glue DataBrew** can be used to clean and standardize a large customer sales dataset without manually processing every record.

The workflow is repeatable because the cleaning operations are stored in a DataBrew recipe and can be applied to the full dataset through a DataBrew job.
