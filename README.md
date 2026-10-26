# Power BI: Data Transformation & Data Modeling
A Power BI project exploring e-commerce sales data through data cleaning, transformation, modeling, and aggregation. It uses order, order-detail, and sales-target datasets to prepare data for analysis and examine sales patterns.
## Data files

- `List of Orders.csv`
- `Order Details.csv`
- `Sales target.csv`
## Project objectives

- Import and clean the CSV files in Power Query.
- Merge order and order-detail data using `Order ID`.
- Create calculated and conditional columns.
- Review missing values and duplicates.
- Sort and filter orders for trend and regional analysis.
- Create summary tables for orders, profit, amounts, and targets.
- Establish and verify relationships in the data model.

## Transformations and analysis

### List of Orders

- Limit the table to the first 500 rows.
- Set `Order Date` to the **Date** data type.
- Convert `Amount` and `Target` to **Fixed Decimal Number**, where applicable.
- Format `CustomerName` using proper case.
- Create a `Location` column in the format `City, State`.
- Calculate `Profit Margin` as `Profit / Amount`.
- Add a `Profit Status` column:
  - Profit below 0: **Loss**
  - Profit equal to 0: **Break-Even**
  - Profit above 0: **Profit**
### Merging and summaries

- Merge `List of Orders` and `Order Details` into `Orders Data` using `Order ID`.
- Duplicate `Order Details` to create summaries such as:
  - Order counts by `Order ID`
  - Average profit by category
  - Total amount by sub-category
- Duplicate `Sales Target` to aggregate target amounts by month.

### Sorting and filtering

- Sort orders by `Order Date` in descending order to review recent orders.
- Filter by fields such as `State` or `Category`, including a regional view for Tamil Nadu.

### Data quality

- Identify missing values and document whether they are removed, replaced, or retained based on their meaning.
- Check for duplicate rows and document the chosen approach. Repeated order IDs may represent separate product details, so do not remove them without checking the data’s granularity.

## Data model

Create and verify these relationships in **Manage relationships**:

- `List of Orders[Order ID]` → `Order Details[Order ID]`
- `Order Details[Category]` → `Sales Target[Category]`

Ensure the relationships are active and the columns have compatible data types. Consider column uniqueness and table granularity when configuring relationship cardinality.

## How to use

1. Open the Power BI project file in Power BI Desktop.
2. Make sure the three CSV files are available at the expected paths. Update the source paths if needed.
3. Select **Transform data** to review the Power Query steps and data-quality decisions.
4. Select **Close & Apply** to load the transformed data.
5. Use **Model view** to inspect the relationships.
6. Explore dates, states, categories, and summarized measures using the report filters and visuals, if included.

## Notes
Results depend on the contents and quality of the supplied CSV files. Review the Power Query steps for assumptions about missing values, duplicates, and aggregation. Handle cases where `Amount` is zero or missing when calculating `Profit Margin`. This project is for educational purposes; interpret the analysis in the context of the source data.
