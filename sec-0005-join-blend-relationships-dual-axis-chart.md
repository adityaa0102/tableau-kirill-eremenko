3 ways to pull data from multiple tables at once: joining, blending and relationships.

I liked video `42. Joining on Multiple Fields`. Might wanna refer to it again sometime. Optional tho.

# Joining vs Blending in Tableau

Download `AmazingMartEU.xlsx` dataset.

Why you cannot simply join the 3 tables together:

![](./markdown-linked-files/sec-0005-0001.png)

You could do the following...

![](./markdown-linked-files/sec-0005-0003.png)

![](./markdown-linked-files/sec-0005-0002.png)

...but then you would lose a lot of information, and would not be able to make a holistic dashboard.

("level of granularity of Table A+B is more than that of Table C")

Open the same excel file as a new **Data Source** for blending. Add `SalesTarget` table as a **logical table** in the **Data Source** tab.

![](./markdown-linked-files/sec-0005-0004.png)

"Blending is a very smart join that can happen on the fly".

Another reason why you sometimes *must* use blending: if you are using multiple *different* kind of data sources (MySQL + Excel + Cloud + Excel file + CSV file + etc.)

Reasons for using blend (generally):

* difference in granularity

* heterogenous **Data Source** types

# Blending data in Tableau

Download `AirlineComparison.xlsx` file.

Create 2 different Data Sources for each airline:

![](./markdown-linked-files/sec-0005-0005.png)

![](./markdown-linked-files/sec-0005-0006.png)

The field `Region` was selected because it has the *same name* in both the Data Sources.

![](./markdown-linked-files/sec-0005-0007.png)

![](./markdown-linked-files/sec-0005-0008.png)

![](./markdown-linked-files/sec-0005-0009.png)

![](./markdown-linked-files/sec-0005-0010.png)

![](./markdown-linked-files/sec-0005-0011.png)

Tableau did not blend `Period` and `Year` automatically because they had different names.

ALTERNATIVE: Just rename `Year` to `Period` and then Tableau will automatically blend them without you needing to **Edit Blend Relationships** manually.

The main difference between normal joining and blending lies in the inner working of blend.

For blending, Tableau queries the other data source such that the data is queried to be aggregated according to the requirements of the visualization, and after aggregation, it is joined on the fly, whenever that particular dimensions is dragged onto the worksheet.

Left join from Region to Region was performed (after aggregation) in the first case.

Secondary data sources are marked with orange colors and orange tick marks.

⚠⚠⚠ NOTE THAT BLENDING IS A "SMART" (cuz aggregation before join) ***LEFT JOIN*** FROM THE PRIMARY DATA SOURCE (blue tick) to the SECONDARY DATA SOURCE (orange tick). Everything that doesn't match in the left table gets discarded:

![](./markdown-linked-files/sec-0005-0012.png)

# Dual axis chart

Build this:

![](./markdown-linked-files/sec-0005-0013.png)

![](./markdown-linked-files/sec-0005-0014.png)

We will also have to add `Month of Order Date` column to the blend.

If you only have the `Category` column in the blend relationship, you will get a net target sales value for each `Category` of product, without considering the monthly targets in that category. The black boxes explain my point:

![](./markdown-linked-files/sec-0005-0015.png)

To prevent this, **Edit Blend Relationships**:

![](./markdown-linked-files/sec-0005-0016.png)

Now, the targets get adjusted:

![](./markdown-linked-files/sec-0005-0017.png)

However, it is difficult to visually compare the targets with the actual sales. So we combine the black and the colored bars to create a Dual Axis Chart.

![](./markdown-linked-files/sec-0005-0018.png)

**Synchronize Axes** with result in axes of the underlapping and overlapping charts to share a common axis. Important step.

Change the order of measures in the Row ribbon to change who is in the foreground and who is in the background:

![](./markdown-linked-files/sec-0005-0019.png)

Final state of the worksheet:

![](./markdown-linked-files/sec-0005-0020.png)

# Creating calculated fields in a blend

Let's say we want to visualize the difference between actual sales and target sales for each department.

For that we will have to create calculated fields, across the blended data sources.

![](./markdown-linked-files/sec-0005-0021.png)

👆 Take care of aggregation functions. Tableau is too intelligent/dumb man.

Final state of the worksheet:

![](./markdown-linked-files/sec-0005-0022.png)

# New challenge and dataset

Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

Read the description on the website to understand the data columns and the data schema. (optional)

# The Data Model

Won't be dealing with the following part of the database:

![](./markdown-linked-files/sec-0005-0023.png)

Since we do not want to combine all these tables into one huge tables to maintain readability and modularity when working, hence we will not use Joins. We will use **relationships** between **logical tables**.

⚠⚠ Recall that to **join** 2 tables, we would double click a **logical table** and then **join** 2 **physical tables** inside it. But for **relationships**, we will be working only at the logical level.

Use the "noodles" (🥰) to esablish relationships between tables. Tableau automatically picks how to relate them:

![](./markdown-linked-files/sec-0005-0024.png)

Click on the noodles to change anything you want.

Final schema created in tableau:

![](./markdown-linked-files/sec-0005-0025.png)

👆 In any one of these tables, you can go to their physical layer and join another table to them. (but then that wouldn't be readable too, and that's not the point of the **relationships** feature in Tableau.)

# Working with relationship

**The challenge:** Create a map showing sellers in their geolocations with bubbles to illustrate how much money in total payments they have received from customers.

To avoid confusion, we will rename the following:

![](./markdown-linked-files/sec-0005-0026.png)

Let's also rename the overall name:

![](./markdown-linked-files/sec-0005-0027.png)

![](./markdown-linked-files/sec-0005-0028.png)

![](./markdown-linked-files/sec-0005-0029.png)

Tableau is very intelligent. It understands when to aggregate data.

You could have used a join while using relationships, but the whole point of **relationships** is to avoid combining tables into huge cumbersome tables. You could have done the following, but it would still be a bad use of **relationships**:

![](./markdown-linked-files/sec-0005-0030.png)

Tableau recommends using **relationships** instead of **joins**. So if you are in doubt, use a **relationship**.

Final state of worksheet:

![](./markdown-linked-files/sec-0005-0031.png)

# Section recap

### Joining data

* Type of joins (jose portilla ki jay 🙏)

* Joining with duplicate values (jose portilla ki jay 🙏)

* Joining on multiple fields (jose portilla ki jay 🙏)

### Blending data

* a "smart LEFT join on the fly from the primray data source (blue) to the secondary data source (orange)"

* common fields with the same name are picked up automatically as the blend clause

* Data > **Edit Blend Relationships**

* blending occurs at the granularity of your visualization (smOrt)

* aggregation happens before blend

* blends are unique to each worksheet. You gotta create new blends on new worksheets.

### Joining vs Blending

##### Use joins when

* combining data at row level

* when you don't mind losing some data to help with evening the granularity

##### Use blends when

* data sources have different levels of granulaty aka aggregation

* data sources come from different systems (SQL, Excel, text, etc.)

### Relationships

* The data model consists of a **logical layer** and a **physical layer**

* physical layer - creating joins

* logical layer - creating relationships

* **Relationships** are more flexible than **joins**

* Tables are treated as seperate

* You can combine fields on the fly

* If in doubt - use a **relationship**

### Other topics

* dual axis charts

* remember to synchronize the axes

* move charts to foreground/background as required

* calculated fields in a blend

![](./markdown-linked-files/sec-0005-0032.png)

![](./markdown-linked-files/sec-0005-0033.png)

![](./markdown-linked-files/sec-0005-0034.png)

![](./markdown-linked-files/sec-0005-0035.png)

![](./markdown-linked-files/sec-0005-0036.png)

Key takeaway from this section: You can combine datasets/tables in 3 ways: **joins**, **blends** and **relationships**.

Preference: **relationships** > **blends** > **joins** (imo).