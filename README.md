# LW5_Applying-DAX-Fundamentals-in-Power-BI-From-Measures-to-Contextual-Analysis



DAX Essentials: Simple Answers to Guided Questions
I. Foundational Concepts
1. Excel formula vs. DAX
Excel formula works on one cell or a fixed range. It doesn’t care about relationships between tables.

DAX works with entire tables and respects the connections (relationships) between them. It’s built for dynamic reporting.

2. Why do we need DAX?
Raw numbers from a dataset are just static data. The gap DAX fills is dynamic calculation — numbers that change when you slice, filter, or interact with your report. Without DAX, you can’t create measures like “Total Sales for selected region” that update automatically.

II. Calculated Columns vs. Measures
3. Which increases file size?
Calculated Columns increase file size because the result is stored for every row in the table.
Why this matters: For large datasets (millions of rows), too many calculated columns can slow down refresh times and bloat the model.

4. Filter Context effect on Measures
A measure changes its result based on filters applied to the report — like slicers, row selections, or chart axes.
Example: A measure Total Sales shows 
100
f
o
r
“
N
o
r
t
h
”
r
e
g
i
o
n
i
f
y
o
u
f
i
l
t
e
r
b
y
N
o
r
t
h
,
a
n
d
100for“North”regionifyoufilterbyNorth,and200 for “South” if you filter by South. That’s filter context at work.

III. Function Application & Syntax
5. The RELATED function
Why needed: To pull a value from another table (e.g., category name into a sales table).

What must exist: A proper relationship (one-to-many or many-to-one) between the two tables in the Model View.

6. Formula breakdown
DAX
Total Sales = SUM(Sales[Sales Amount])
Part	Example
Measure Name	Total Sales
Function	SUM
Table	Sales
Column	Sales Amount
Why include table name? To avoid ambiguity — two tables might have a column with the same name (e.g., both Sales and Products have a Name column). It also improves performance and readability.

IV. Analysis & Troubleshooting
7. Negative profit — broken formula or real data?
It doesn’t mean the formula is broken. It likely means the business actually lost money on that category.
How to verify:

Create a simple card visual with raw SUM(Profit) to check.

Filter to that category and manually inspect the source data for returns, discounts, or costs exceeding revenue.

If the manual check matches the measure → data is correct. If not → check the DAX logic.

8. Profit Margin % — Column or Measure?
Use a single Measure.
Why:

Margin = SUM(Profit) / SUM(Sales)

A calculated column stores a value per row → wasteful and slower.

A measure calculates it on the fly, respects filter context, and uses far less memory.

Efficiency tip from DAX: Aggregate first with SUM, then divide — never store row-by-row percentages if you can avoid it.

