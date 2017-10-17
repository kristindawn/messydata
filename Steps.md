# Working with Messy Data Workshop #
## Kristin Lee, Research Data Librarian 

In this workshop we will look at some of the ways that you can use OpenRefine to clean up a dataset for use in visualization and mapping. 

Tools: OpenRefine ([http://openrefine.org/](http://openrefine.org/ "OpenRefine Home"))

Dataset: Barnum Route from 1881 to 1890, Circus Historical Society ([http://www.circushistory.org/Routes/PTB1881.htm](http://www.circushistory.org/Routes/PTB1881.htm "PTB 1881-1890")); slightly cleaner xls [here](https://github.com/kristindawn/messydata/blob/master/PTB1881_wyear-month.xls "PTB 1881-1890 Excel")

###Importing HTML from a URL:

I have provided a slightly cleaned up version on the data to use for the rest of this workshop, so this is provided for information only.

1. Open OpenRefine and choose Create Project from the tabs on the left. 
2. Choose to "Get data from Web Addresses (URLs)" and put in: `http://www.circushistory.org/Routes/PTB1881.htm`
3. Use the default "Line-based text files" and Create Project.

You will notice that there is a lot of extra HTML in your dataset, and that it will require a significant amount of time to clean up. It took me about a day to make it presentable in the format that you can use for the rest of the steps.

###Steps between the HTML and XLS

1. Cleaned up all extra HTML tags until just the years, months, days, and locations were left.
2. Used an Excel macro to add columns for the years and months (which were both headings on the webpage) to the rows that have the dates. 

###Cleaning up the XLS



1. Download the xls file here: `https://github.com/kristindawn/messydata/blob/master/PTB1881_wyear-month.xls`
2. Create a new project in OpenRefine using "Get data from This Computer". Upload the xls file you just downloaded. Leave the rest of the import settings as the default.
2. You can choose to show 5, 10, 25, or 50 rows. I like 50, but choose what works best for you.
3. We are only going to work with the "Route Date" column. The first step is to separate the dates from the locations. In most cases in this data set, the date and location are separated by the first " ". If you open the menu using the button in the column header, you will see that you can use Edit column>Split into several columns... and designate " " as a delimiter and set the Split into [ ] columns at most to 2. This will get you the result you need. 
4. Alternatively, you can use `indexOf(value, " ")` to get the place of the first " " in the string, then use `slice(value, 0, cells["index_for_date"].value)` to separate out the beginning of the string (the date) up to the index of that first space. You can get the end of the string by using `slice(value, cells["index_for_date"].value)`, which starts at the index point and goes to the end. NOTE: your data will not be perfect, but it will give you a place to start!
5. One of the most valuable things about OpenRefine is the ability to use facets to explore  and organize your data. We are going to use a facet and the Cluster function to combine instances of cities that OpenRefine thinks look the same. Use the menu to get to Facet>Text Facet to get the faceted list to appear on the left side of the screen. You can scroll through the data to get a sense of what is there. Click the Cluster button to group similar strings. You will be presented with a new window that shows the items that OpenRefine has grouped together. It will suggest a new value for the cells, which you can adjust as you like. If you want to merge the cells, just click the check box. If you like all of the suggestions, you can choose Select All at the bottom of the page. When you are done, click Merge Selected & Re-Cluster. If no new clusters appear you can close the box.


THIS IS A WORK IN PROGRESS. CHECK BACK TOMRROW.             




