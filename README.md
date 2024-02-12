# Data_Visualization_Workbook_Tableau

This is a notebook for data visualization on Tableau
Below are demonstrations for some steps using sample dataset from: https://youtu.be/47_JlqPxKjY?si=315RZyXXv4nmidq7  

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
1. Drag `Last Review` to Columns -> drop down and select "Month"
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

## 
