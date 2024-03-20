# Max Fashion Analysis-Dashboard

## Problem Statement

The current sales analysis system at Max Fashion relies primarily on basic sales reports generated from the point-of-sale (POS) system. These reports typically include metrics such as total sales, product categories sold, and sales by store location. However, the existing system lacks in-depth analysis capabilities and fails to provide insights into underlying trends, customer behavior, or seasonality patterns. Moreover, the analysis is often manual and time-consuming, limiting the ability to make timely and informed decisions. As a result, there is a need for a more robust and automated sales analysis system that can delve deeper into the data, uncover actionable insights, and drive strategic decision-making to optimize sales performance and enhance overall business outcomes, improve revenue generation, and enhance customer satisfaction

### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a xlsx file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values.
- Step 5 : For calculating Month Over Month by Sales and Location by Sales and Customer name by sales and Profit by Ordertype.
- Step 6 : In the report view, under the view tab, theme was selected.. 
- Step 7 : Visual filters (Slicers) were added for four fields named "Product Category", "Product names".
- Step 8 : Three card visuals were added to the canvas, one representing Total sales & other representing Total profit & other representing Profit Margin.
           Using visual level filter from the filters pane, basic filtering was used & null values were unselected for consideration into average calculation.
           
           Although, by default, while calculating average, blank values are ignored.

- Step 9 : In the report view, under the insert tab, one text boxes were added to the canvas, in one of them name of the Max Fashion Analysis Dashboard was mentioned.
- Step 10 : In the report view, under the insert tab, using image option from elements group a images was inserted TotalSales and profit and profit margin and Filter logo was added to the report design area. 
- Step 11 : Calculated column was created in which, Month over Month by sales.

for creating new column following DAX expression was written;
       
        Date = CALENDAR(DATE(YEAR(MIN(Data[Sale date])),1,1),DATE(YEAR(MAX(Data[Sale date])),12,31))

- Step 12 : New measure was created to find Last month by sales.

Following DAX expression was written for the Last month by sales,
        
        Last month = CALCULATE([Total sales],DATEADD('Date'[Date],-1,MONTH))

- Step 13 : New measure was created to find Current Month.

Following DAX expression was written for the Current Month,
        
        Current month = CALCULATE([Total sales],DATESMTD('Date'[Date]))

- Step 14 : New measure was created to find Month over Month variance.

Following DAX expression was written for the Month over Month variance,
        
        MOM variance = [Current month]-[Last month]

- Step 15 : New measure was created to find Month over Month %.

Following DAX expression was written for the Month over Month %,
        
        MOM% = DIVIDE([Current month]-[Last month],[Last month],0)

A clusted column visual was used to represent Month over Month % sales.

![Month over Month %](https://github.com/jaikannan035/Max-Fashion-Analysis-Dashboard/assets/164223373/003b1414-9211-4abb-a02b-b366524acd8d)

           
- Step 16 : New measure was created to find Total sales.

Following DAX expression was written for the Total sales,
        
        Total sales = SUM(Data[Sales Amount])

A card visual was used to represent Total sales.

![TotalSales](https://github.com/jaikannan035/Max-Fashion-Analysis-Dashboard/assets/164223373/ec97ecb1-d0f0-4bb1-9f43-e73a86bde153)

- Step 17 : New measure was created to find Profit.

Following DAX expression was written for the Profit,
        
        profit = SUM(Data[Profit])

A card visual was used to represent Profit.

![profit](https://github.com/jaikannan035/Max-Fashion-Analysis-Dashboard/assets/164223373/1180c793-b1bd-4f1e-b535-6d73a11b73f5)



- Step 18 : New measure was created to find Profit margin.

Following DAX expression was written for the Profit margin,
        
        profit margin = [profit]/[Total sales]*1

A card visual was used to represent Profit Margin.

![Profit margin](https://github.com/jaikannan035/Max-Fashion-Analysis-Dashboard/assets/164223373/b5bf250c-9839-468e-8de1-68860fb6c1dd)
 
 - Step 19 : The report was then published to Power BI Service.


 
 # Report Snapshot (Power BI DESKTOP)

![Dashboard](https://github.com/jaikannan035/Max-Fashion-Analysis-Dashboard/assets/164223373/24ca4100-1977-44d1-95da-f69c4368464d)



