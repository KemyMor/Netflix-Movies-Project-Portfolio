# Netflix-Movies-Project-Portfolio
Netflix is a streaming service that offers an extensive collection of award-winning TV shows, movies, anime, documentaries and more on thousands of internet-connected devices. The streaming giant has become our primary source of entertainment, especially after the pandemic hit the world. Netflix doesn’t only symbolize entertainment, though. For geeks of the data world, Netflix is a major source of bucketloads of data, too. 

In this project, let me walk you through the basics of the data analysis process, from listing the objective questions to cleaning the outliers and finally deriving insights from data and data visualization. 
Step1: Structure
Step 2: Analysis using pivot Table
Step 3: Visuals; adding KPIs
Step 4: Add Slicers

Dataset Source: www.kaggle.com

## Objective Questions
How Many countries with Netflix coverage?
Which Is The Title With The Longest Runtime?
Which Is The Title With The Least Runtime?
What are they top 10 Genres?
How Many Films And Series Have Been Released On The Same Date?
Though you could derive tens and hundreds of questions, I have addressed these five in this guide for simplification. Through these five questions, we’ll be analyzing the data using Excel.

## Step 1: Studying The Data
While this isn’t a step many are talking about, it is quite essential. You need to study your data. It doesn’t have to be extensive, just sift through the data, note down the column labels and the content of your data before you roll your sleeves.

Quick insight:

The number of rows: 8808

The number of columns: 11

## Step 2: Converting the data to Table
The table provides features normal rows and columns don’t, including filters and pivot tables.

After converting the data into a table and applying some basic modifications such as alignment and styling, my table looks!
![Netflix_Table](https://github.com/KemyMor/Netflix-Movies-Project-Portfolio/blob/main/Netflix_Table.jpg)

### Identify And Eliminate Duplicate Data

Now that we’re done rectifying the outliers, we should consider duplicate data. In this dataset, there are several duplicate values but not the ones that matter.

### Identify column with irregualr data
Select the data: Highlight the range of cells containing the text you want to split.
Access the Text to Columns wizard:
Go to the "Data" tab on the Excel ribbon.
In the "Data Tools" group, click on "Text to Columns".
Choose the delimiter:

In the Text to Columns wizard, select "Delimited" and click "Next".
Choose the delimiter that separates your text (e.g., Comma, Tab, Semicolon, Space, etc.).
You can preview how your data will be split in the Data preview section.
Specify column format (optional):

If needed, you can specify the data format for each column in the "Column data format" section.
Select each column and choose the appropriate format (e.g., General, Text, Date, etc.).
Finish the wizard:

Click "Finish" to split the text into separate columns based on the chosen delimiter.
After completing these steps, Excel will separate the text into different columns based on the specified delimiter. Each piece of text separated by a comma will be placed into its own column.

If you prefer using formulas, you can also use the Text functions like LEFT, MID, RIGHT, or the combination of FIND and MID to extract the text into separate columns. However, the Text to Columns feature is usually more convenient for this task, especially for large datasets.

## Step 3: Generating Insights From The Cleansed Dataset
Here’s when the interesting part arrives!

Remember the objective questions I listed above? We’ll try finding the answers to each of them now.

Answer 1

Our first task is to count the number of titles with a runtime of 100 minutes. To accomplish this, I’ll be using the countifs formula. The first task we’ll be doing is to create a pivot table in a new sheet.

Select the Pivot Table option from the Insert ribbon, and Excel will automatically direct you to a new sheet. Select and drag the Title option to the row field and Duration Minutes to the value field. And tada, here’s your pivot table ready!

The formula using which I am counting the number of titles present in the range B6: B6176 with the duration mentioned in the R6 cell is:

COUNTIFS(B6:B6176, R6)
A cell reference (R6) is used to add a dynamic touch. If the number in the R6 cell changes, so will the count.

One formula for all the durations!


Source: Photo by Author
Output:


Source: Photo by Author
Let us crosscheck our formula and the results using a subset of our dataset quickly!


Source: Photo by Author

Source: Photo by Author
Now, how about a shortcut?

You can easily add a slicer to the pivot table, and it’ll list the available durations and list only those values matching the criteria. Slicer acts as a filter and can easily simplify your work.


Source: Photo by Author
As you can see above, the slicer returns the same count as the formula I wrote, which means our first question has an answer!

Answer 2, 3:

Which Is The Title With The Longest Runtime?

The answer to this question is quite simple, but I’m breaking it down into three parts to simplify it further. In the first part, I’ll take runtime as an input and give the corresponding title as the output. In the second, I’ll find out the maximum runtime of a title and the minimum in the third.

The formula for the first part:

INDEX($A$4:$B$6174,MATCH(J5,B5:B6174,0)+1, 1)
J5 is the cell in which input is entered; range A consists of Titles, and B contains Duration.

I’m using match to get me the index of the row containing the value mentioned in J5. The index function will then take up the value returned by match and give the corresponding Title as output.

For the second and third parts, functions min and max are used along with xlookup.

Formula:

XLOOKUP(J8,B5:B6174,A5:A6174)
Here, J8 is the cell that contains the maximum runtime value, the second parameter is the array in which the value is to be searched for, and the last is the array from which the corresponding value is to be returned.


Source: Photo by Author
Here’s the final output:


Source: Photo by Author
Answer 4

I’m adding a filter (actually, two) to the pivot table for this answer. To do this, open the field list in the PivotTable Analyze ribbon and add the Ratings as a filter. Next, do the same to count the titles sorted by ratings, and you’re done!


Source: Photo by Author
Answer 5

For the last answer, to find the title released given the date, I’ll be using Lookup again. This formula is probably my favourite and will soon be yours, too!

The formula used here is where G6 is the cell in which the date is entered as the output.

XLOOKUP(G6,C8:C6177,A8:A6177)

Source: Photo by Author
Conclusion
Okay, so it has been a long discussion (almost 1500 words) and you probably need a long coffee break because I do, too. So, I wouldn’t take a lot of your time. Just wanted to let you know that I’m so glad I completed this article, even if it took me quite a long time. I would be even more glad if it helped you.

Stay tuned for more such extensive case studies with interactive dashboards. Have a good day, folks!
