# Customer Sales Data Cleaning Using AWS Glue DataBrew

## Project Overview

This project demonstrates how to clean and prepare a large customer sales dataset using Amazon S3 and AWS Glue DataBrew.

The dataset contains approximately 100,000 customer sales records with customer, sales, product, payment, and order information.

## Technologies Used

- Amazon S3
- AWS Glue DataBrew
- AWS IAM
- GitHub
- CSV Dataset

## Dataset

The source file is `customer_sales_100k_databrew.csv`.

The dataset contains approximately 100,000 records and 16 columns:

`customer_id`, `customer_name`, `gender`, `age`, `city`, `state`, `region`, `customer_segment`, `category`, `product`, `quantity`, `unit_price`, `discount_pct`, `sales_amount`, `payment_method`, `order_date`.

The complete dataset is stored in Amazon S3 and is not uploaded to this public GitHub repository.

## Project Architecture

```text
100K Customer Sales CSV
          |
          v
     Amazon S3
          |
          v
   AWS Glue DataBrew
          |
          v
    DataBrew Project
          |
          v
   Data Cleaning Recipe
          |
          v
     DataBrew Job
          |
          v
    Cleaned Dataset
          |
          v
       Amazon S3
```

## Data Cleaning Process

The following transformations were performed using AWS Glue DataBrew:

1. Removed rows with missing `customer_name`.
2. Removed rows with missing `city`.
3. Removed rows with missing `age`.
4. Converted `city` values to uppercase.
5. Converted `state` values to uppercase.
6. Inspected missing values, duplicates, column statistics, data types, and value distributions.

## AWS Glue DataBrew Workflow

1. Uploaded the 100K customer sales CSV file to Amazon S3.
2. Connected the S3 CSV file to AWS Glue DataBrew as a dataset.
3. Created a DataBrew project using the dataset.
4. Created a recipe containing data cleaning and transformation steps.
5. Published the recipe.
6. Created and ran a DataBrew recipe job.
7. Stored the cleaned output in Amazon S3 under the `cleaned-100k/` folder.

## Important Note About DataBrew Samples

AWS Glue DataBrew displays a sample of the dataset in the project interface rather than displaying every record at once.

Therefore, seeing approximately 500 rows in the DataBrew grid does not mean that the original dataset contains only 500 records. The source dataset contains approximately 100,000 records, and the DataBrew job processes the dataset stored in Amazon S3.

## Result

The project demonstrates the complete workflow:

**Amazon S3 → AWS Glue DataBrew → Data Cleaning → DataBrew Job → Cleaned Data → Amazon S3**

The cleaned dataset is stored in Amazon S3, while the project documentation is maintained in GitHub.

## Repository Contents

```text
customer-sales-databrew-100k/
├── README.md
├── data-cleaning-process.md
└── screenshots/
```

## Conclusion

This project demonstrates how AWS Glue DataBrew can be used to clean and transform a large customer sales dataset. The cleaned data is stored in Amazon S3 and can be used for further analysis, reporting, visualization, or machine learning.
