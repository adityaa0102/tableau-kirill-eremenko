# Joining data in Tableau

We will cover **relationships** in a later section, for now, **join** the `ListOfOrders` and `OrderBreakdown` tables using the physical layer in the **Data Source** tab in Tableau, immediately after connecting to `P1-AmazingMartEU2.xlsx` as data source.

Double click a **logical table** to see it's **physical tables** as components. Now drag and drop tables to create joins:

![](./markdown-linked-files/sec-0004-0001.png)

# Creating a map, working with hierarchies

Tableau already created a hierarchy for us, but let's delete that:

![](./markdown-linked-files/sec-0004-0002.png)

Drag and drop upon parent to create a hierarchy:

![](./markdown-linked-files/sec-0004-0003.png)

Drag this heirachy onto the worksheet and let Show Me create a map. Notice the plus sign on the Country dimension, click on it to increase the granularity according to hierarchy:

![](./markdown-linked-files/sec-0004-0004.png)

Final product:

![](./markdown-linked-files/sec-0004-0005.png)

# Creating a scatterplot, applying filters to multiple worksheets

#### (i.e., the same filter should apply changes to all worksheets)

![](./markdown-linked-files/sec-0004-0006.png)

![](./markdown-linked-files/sec-0004-0007.png)

Final scatter plot in the 2nd worksheet:

![](./markdown-linked-files/sec-0004-0008.png)

# Creating your first dashboard

Final output:

![](./markdown-linked-files/sec-0004-0009.png)

# Interactive Action: Filter

2 main types of actions in Tableau: filtering and highlighting

Use as filter:

![](./markdown-linked-files/sec-0004-0010.png)

![](./markdown-linked-files/sec-0004-0011.png)

![](./markdown-linked-files/sec-0004-0012.png)

You can create your own Actions by going to **Dashboard** > **Actions**.

imo, **Use as Filter** is pretty fast and useful, you might not need creating your own Actions.

You can click on multiple circles on the map by holding down Ctrl, or by selecting the **Rectangular Selection** button from the **Show/Hide View Toolbar**.

---

### Filter vs Highlight

**Highlight** keeps other marks, but greys them out.

**Filter** removes all other marks, and only keeps the ones that match the filtering criteria. (All sizes, coloring, details, etc. now becomes in relation to the filtered data, and not relative to the whole dataset. You may see changes in size and color immediately, such that info *relative* (⭐) to the data after filtering is presented.)

Finer things in life:

![](./markdown-linked-files/sec-0004-0017.png)

---

# Interactive Action: Highlighting

Even after adding an Highlighting action onto the map, you will see that there is no highlighting.

Solution:

![](./markdown-linked-files/sec-0004-0013.png)

![](./markdown-linked-files/sec-0004-0014.png)

Now highlighting actions will work:

![](./markdown-linked-files/sec-0004-0015.png)

More control btw:

![](./markdown-linked-files/sec-0004-0016.png)