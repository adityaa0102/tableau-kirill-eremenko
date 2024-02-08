# What format your data should be in

Machines do not like the following format:

![](./markdown-linked-files/sec-0007-0001.png)

Neither this:

![](./markdown-linked-files/sec-0007-0002.png)

Machines will prefer this:

![](./markdown-linked-files/sec-0007-0003.png)

👆 More columns, the better. Machines do not like pivoted/aggregated\* data. Also, notice that there is no formatting/headers/coloring in a machine-friendly dataset. Also, no `Total` values or other aggregate values.

Gaps like the below image are good for humans, but not for machines:

![](./markdown-linked-files/sec-0007-0004.png)

Tableau has some provisions for data preparation for such kind of datasets.

# Data Interpreter

Download `PersonalVehicleSalesGlobal.xlsx` from Kirill's website.

The Excel file is very messy. You might have to do some key cleaning before importing the file to Tableau.

After cleaning, import it as a Data Source and then:

![](./markdown-linked-files/sec-0007-0005.png)

# Pivot

Our data is still not machine-optimized as there are seperate columns or years.

Use `Pivot` to do this:

![](./markdown-linked-files/sec-0007-0006.png)

Outcome:

![](./markdown-linked-files/sec-0007-0007.png)

[This](./markdown-linked-files/sec-0007-0022.pdf) is what ChatGPT had to say about the pivoting functionality in Tableau.

# Splitting a column into different columns

Example: extracting the last word from each row of the `Regions` column.

Example: you might want to split the first ame and the last name from the full name from a dataset in the future. This is why you Split.

![](./markdown-linked-files/sec-0007-0008.png)

![](./markdown-linked-files/sec-0007-0010.png)

Outcome (a section of it):

![](./markdown-linked-files/sec-0007-0009.png)

Alternatively, you may split from the Worksheet:

![](./markdown-linked-files/sec-0007-0011.png)

# Metadata grid

![](./markdown-linked-files/sec-0007-0012.png)

Rename columns, and delete the last column:

![](./markdown-linked-files/sec-0007-0013.png)

Build this:

![](./markdown-linked-files/sec-0007-0014.png)

![](./markdown-linked-files/sec-0007-0015.png)

![](./markdown-linked-files/sec-0007-0016.png)

Final state of worksheet:

![](./markdown-linked-files/sec-0007-0017.png)

# Fixing geographical data errors

Create the following map:

![](./markdown-linked-files/sec-0007-0018.png)

There are errors due to spelling mistakes:

![](./markdown-linked-files/sec-0007-0019.png)

Fix them and click OK.

![](./markdown-linked-files/sec-0007-0020.png)

---

A data scientist's 70% time is spent on data preparation (even before analysis).

---

![](./markdown-linked-files/sec-0007-0021.png)

