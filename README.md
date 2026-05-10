# LW5_Applying-DAX-Fundamentals-in-Power-BI-From-Measures-to-Contextual-Analysis

Google slide link ==== https://docs.google.com/presentation/d/1CkAtBVoF8MlFCuaQ_vWUd35rOCMpwDJsjYVq1FLM4Rk/edit?slide=id.p#slide=id.p

# I. Foundational Concepts

### 1. DAX Basics
DAX is different from regular Excel formulas. While Excel calculates cell by cell, DAX works with entire tables and columns in Power BI. This makes DAX better for data analysis because your calculations automatically adjust based on user selections like filters and slicers.

### 2. Why Use DAX?
Raw data alone isn't enough for most reports. You usually need calculated insights like profit, margins, averages, and rankings. DAX lets you build custom calculations that update automatically as people interact with your dashboard.

---

## II. Calculated Columns vs. Measures

### 3. Storage Impact
Calculated Columns save results for every single row, which makes your Power BI file bigger. Measures only run when you actually use them in a visual.

For big datasets, this matters. Too many calculated columns slow things down and eat up memory. Measures handle large data much better.

### 4. How Filter Context Works
Measures respond to whatever filters are active. Click a region or category, and the measure recalculates instantly for just that selection.

Calculated columns don't do this — they're static once created. That's why measures feel more interactive.

---

## III. Functions & Syntax

### 5. RELATED Function
Use RELATED when you need to pull data from a different table. But first, you must set up a relationship between those tables in Model View (usually through matching keys like ProductID).

Without that relationship, Power BI won't know how to connect the data.

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
