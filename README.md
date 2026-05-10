# LW5_Applying-DAX-Fundamentals-in-Power-BI-From-Measures-to-Contextual-Analysis

Google slide link ==== https://docs.google.com/presentation/d/1CkAtBVoF8MlFCuaQ_vWUd35rOCMpwDJsjYVq1FLM4Rk/edit?slide=id.p#slide=id.p

# I. Foundational Concepts

## 1. Defining DAX
Based on the tutorial, the difference between a standard Excel formula and DAX is that Excel formulas usually work on individual cells, while DAX works with tables and columns inside Power BI. DAX is more powerful for data analysis because it can create dynamic calculations that change depending on filters, slicers, and report visuals.

---

## 2. The “Why” of DAX
We cannot rely only on the raw numbers from the imported dataset because raw data only contains basic information. In reports, we often need more advanced calculations such as total profit, profit margin, averages, rankings, and filtered summaries. DAX fills this gap by allowing us to create custom calculations and business logic that automatically update when users interact with the dashboard.

---

# II. Calculated Columns vs. Measures

## 3. The Storage Difference
Calculated Columns increase the file size of the Power BI model because the calculated values are stored for every row in the table. Measures do not store values for each row because they are only calculated when needed in a visual or report.

This is important for large datasets because storing many calculated rows can slow down Power BI and use more memory. Measures are more efficient for performance.

---

## 4. Context Clues – Filter Context
Filter Context affects a Measure because the result changes depending on the filters, slicers, or visuals selected in the dashboard.

For example, if I click a specific category or region in the report, the measure recalculates and only shows the result for that selected data. This makes measures dynamic and interactive compared to calculated columns, which stay fixed after being created.

---

# III. Function Application & Syntax

## 5. The RELATED Function
The RELATED function is used when we need to get data from another table. It helps connect information between multiple related tables in Power BI.

For the RELATED function to work correctly, a relationship between the tables must first be created in the Model View. Usually, this relationship is based on matching IDs or keys such as ProductID or CustomerID.

Without a relationship, Power BI will not know how the tables are connected.

---

## 6. Deconstructing the Formula

DAX
Total Sales = SUM(Sales[Sales Amount])

- *Measure Name:* Total Sales
- *Function:* SUM
- *Table:* Sales
- *Column:* Sales Amount

It is considered best practice to include the table name because it makes the formula easier to read and understand. It also helps avoid confusion when different tables contain columns with similar names.

---

# IV. Analysis & Troubleshooting

## 7. Data Interpretation
If the “Total Profit” measure shows a negative number for a category, it does not automatically mean the DAX formula is broken. It may simply indicate that the business lost money in that category because expenses were higher than sales.

To verify this, I can:
1. Check the original data values
2. Compare sales and cost values
3. Review the DAX formula
4. Test the calculation using filtered data

If the numbers match the source data, then the negative result reflects the actual business performance.

---

## 8. Optimization
It is more efficient to create a single Measure for Profit Margin Percentage instead of creating a Calculated Column for every row.

Example:

DAX
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)

A measure is better because it:
- Uses less memory
- Calculates only when needed
- Works dynamically with filters and visuals
- Improves performance for large datasets

A calculated column would store values for every row, which would increase the file size and reduce efficiency.
