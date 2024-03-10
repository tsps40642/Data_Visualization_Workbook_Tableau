# Data_Visualization_Workbook_Tableau

This is a notebook for data visualization on Tableau
Below are demonstrations for some steps using sample dataset from: https://youtu.be/47_JlqPxKjY?si=315RZyXXv4nmidq7  

## Data overview
These are some important fields we will use later:  
1. `Neighborhood Group` is a coarser category than `Neighborhood`
2. `Last Review` is in date form  

## Create a map for "average price" in the `Neighborhood` by `Room Type`  
1. Place `Longtitude` in Columns and `Latitude` in Rows (or double click them respectively) -> it will show a map
2. Drag `Neighbor` into Detail -> it will show `Neighborhood` locations on the map, with each data point having `Longtitude` and `Latitude`  
3. Drag `Price` into Color -> change Measure into "Average" -> aggregate neighborhood price by taking the average
4. Drag `Neighborhood Group` into Label -> it will show labels for `Neighborhood Group` (i.e. higher-level neighborhood)
5. Drag `Room Type` into Filter -> randomly select one, Apply, OK -> drop down Filter and select "Show Filter" -> drop down option and select "Single Value (list)" to change filter type (or you can also set "Multiple Values (list)" if you want to select more than one type at a time)  
6. Set the sheet title: Average price in the neighborhoods - room type: -> drop down "Insert" and select `Room Type` -> so that when the user select a type, the title will change correspondingly  
7. Designing the sheet: select "Map" -> "Background Maps" -> select "Dark"  
8. Using heatmap: Marks -> select "Density" -> select "Color" and set "Density Multi-color Light" -> set "Intensity" of 80% -> adjust "Size"    (the more intense the color is, the more data points are in that `Neighborhood`; the more vague the shape is, the lower average price for that `Neighborhood`)    

Suppliment: Tableau does this by grouping overlaying marks, and color-coding them based on the number of marks in the group
https://help.tableau.com/current/pro/desktop/en-us/buildexamples_density.htm  

## Create a stacked barchart for "total bookings" in months and `Neighborhood Group` by `Room Type`  
1. Drag `Last Review` into Columns -> drop down and select "Month"
2. Drag `Name` into Rows -> drop down and change Measure into "Count"
3. Using barchar: Mark -> select "Bar"
4. On the top select "Entire View" to expand the plot in the whole screen
5. Drag `Neighborhood Group` into "Colors"
6. Drag `Room Type` into Filter -> randomly select one, Apply, OK -> drop down Filter and select "Show Filter" -> drop down option and select "Single Value (list)" to change filter type (or you can also set "Multiple Values (list)" if you want to select more than one type at a time)
7. Edit colors: Color -> "Edit Colors" -> "Select Color Palette" -> click "Assign Palette" and OK
8. Set the sheet title: Total bookings in months and Neighborhood Group - room type: -> drop down "Insert" and select `Room Type` -> so that when the user select a type, the title will change correspondingly
9. Duplicate the CNT(`Name`) in Rows: press control and drag CNT(`Name`) to duplicate aside
10. Go to the second barchart and remove `Neighborhood Group` from Color -> select "Line" -> press control and drag CNT(`Name`) into Label -> drop down the second CNT(`Name`) and select "Dual Axis" to combine the bar and the line  

## Create a donut chart for total `Neighborhood` in each `Neighborhood Group` 
1. Drag `Neighborhood Group` into Color -> select "Pie"
2. Drag `Neighborhood` into Size -> drop down and select "Count"
3. Press control to duplicate `Neighborhood` into Label  
4. Press control to duplicate CNT(`Neighborhood`) into Label -> drop down to Quick Table Calculation -> select "Percent of Total"
5. Double click on Rows and enter 0 and get SUM(0) -> press control to duplicate aside
6. Drop everything in the second pie -> decrese size a little bit and set Color white -> drop down the second SUM(0) and select "Dual Axis" to combine two pies    

## Show top 10 hosts by total reviews
1. Drag `Host Name`, `Neighborhood Group`, `Neighborhood`, and `Price` and change aggregation as Average to Rows -> change into "Discrete"
2. Drag `Number Of Reviews` to Columns, use SUM() aggregation, use Continuous  
3. Drag `Host Id` to "Detail" -> drop down and select Filter -> select "Top" -> select "By filed" -> Top, 10, by `Number Of Reviews` -> Apply, OK
4. Press control and duplicate SUM(`Number Of Reviews`) to Label
5. I want to sort the whole table by SUM(`Number Of Reviews`): drag `Number Of Reviews` to Rows, use SUM() aggregation, use Discrete -> place it in the first position so that it will have sorting priority  

## Create a horizontal stacked barchart for "total bookings" by `Room Type` and `Neighbor Group` 
1. Drag `Neighborhood Group` into Rows
2. Drag `Name` into Columns -> drop down "Measure" and select "Count"
3. Drag `Room Type` into "Colors" and edit colors if you want
4. On the top change "Standard" into "Entire View" for wider visualization  
5. Left click field name and select "Hide Field Labels for Rows" if you want
6. Edit the title  

## Create a barchart for "total reviews" by "year" 
1. Drag `Last Review` into Columns (this field is in date form) and select "Year"  
2. Drag `Number Of Reviews` into Rows -> select "Bar" in "Mark" section
3. On the top change "Standard" into "Entire View" for wider visualization
4. Press control and duplicate SUM(`Number Of Reviews`) to Label
5. Remove null values by click on "Null" and select Exclude"
6. Edit the title

## Create a treemap for "average price" by `Neighborhood Group` and `Room Type` 
1. Drag `Neighborhood Group` into Rows
2. Drag `Price` into "Text" -> drop down "Measure" and select "Average"
3. Drag `Room Type` into "Filters" -> randomly select one, Apply, OK -> drop down Filter and select "Show Filter" -> drop down option and select "Single Value (list)" to change filter type (or other types)
4. Click "Show Me" and select treemaps -> edit the colors if you want
5. Press control and duplicate AVG(`Price`) to Label
6. Drop down AVG(`Price`) and select "Format" -> change "Number" into "Currency(Standard)" to show average price in currency form
7. Edit the title

## Horizontal barchart for "average price" in each `Neighborhood` by `Neighborhood Group`
1. Drag `Neighbor` into Rows
2. Drag `Neighbrhood` into "Filters" -> randomly select one, Apply, OK -> drop down Filter and select "Show Filter" -> drop down option and select "Single Value (list)" to change filter type (or other types)
3. Drag `Price` into Columns -> drop down "Measure" and select "Average"
4. Press control and duplicate AVG(`Price`) to Label
5. Drop down AVG(`Price`) and select "Format" -> change "Number" into "Currency(Standard)" to show average price in currency form
6. Left click field name and select "Hide Field Labels for Rows" if you want
7. Edit the title

## Create a highlight table for "average reviews per month" by `Room Type` and `Neighborhood Group` 
1. Drag `Neighborhood Group` into Columns
2. Drag `Room Type` into Rows
3. Drag `Reviews Per Month` into "Text" -> drop down "Measure" and select "Average"
4. Click "Show Me" and select highlight table -> select "Entire View" -> hied field names if you want -> edit the colors if you want

## Create 4 text sheets 
First need to create 4 calculated fields:   
on the LHS click "Create Calculated Field" -> type "Total hosts", "Total neighborhoods in NYC", "Avg. reviews per month", "Total reviews"  

### Total hosts 
1. Drag `Total hosts` into "Text"
2. Drag `Host Id` into "Text" -> drop down "Measure" and select "Count(Distinct)"

### Total neighborhood in NYC
1. Drag `Total neighborhoods in NYC` into "Text"
2. Drag `Neighborhood` into "Text" -> drop down "Measure" and select "Count(Distinct)"

### Average reviews per month 
1. Drag `Avg. reviews per month` into "Text"
2. Drag `Review Per Month` into "Text" -> drop down "Measure" and select "Average"

### Total reviews
1. Drag `Total reviews` into "Text"
2. Drag `Number Of Reviews` into "Text" -> drop down "Measure" and select "Sum"

## Format the worksheets 
### Sheet 1  
1. On the top click "Format" -> "Shading" -> change the color for "Worksheet" if you want 
2. Edit the color of title if you want -> right click and select "Format Title" -> change the color of "Border" if you want

### Sheet 2
1. Edit grid line and font if you want
2. Double click the y-axis to edit is name
3. Right click x-axis and select "Format" -> in "Dates" select "Abbreviation"
4. Edit border of the chart if you want
5. Right click the title and select "Format Title" -> edit border if you want
6. Hide field name of Columns if you want
7. Edit the filter format if you want

### Sheet 3
1. Double click the y-axis and delete its name (since we don't need) -> then "Tick Marks" select "None", and do the same things for another y-axis
2. In "Format" remove "Zero Lines" and edit other lines if you want
3. "Hide card" for CNT(`Neighborhood`)

### Sheet 4 
1. Edit the grid line if you want
2. Delete the title for barchart since we already have that in the first column
3. Drop donw and select "Format" in AVG(Price) in Rows to edit the format of number 

### Sheet 5 
Hide the title of x-axis since we don't need (can be inferred from the title)

### Sheet 6-13
Similar actions for these sheets  

## Create a dashboard
1. 

