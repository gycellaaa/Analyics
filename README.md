
# Analytics Technique Portfolio

## Assignment details
The task involves analyzing a given dataset to provide insights that will support an upcoming business strategy review.

To assist with this, you have been provided with several datasets containing data about sales, customers, products, stores and sales teams.
Your initial investigation of the dataset revealed the following:

All currency amounts are:
- Recorded in the same currency, and
Have been adjusted for inflation across years.
- Each row in the Sales spreadsheet represents a sale of a Product to a Customer. The sale is made at a Store and delivered from a Warehouse. Each sale lists the Order Quantity (of the Product) sold at an Item Price (the Item Price can vary for each sale). The Total Gross Sale amount is the Order Quantity multiplied by the Item Price. Sales Teams are responsible for arranging the sale.
- There is a Discount Band which applies to each sale. The following discounts are applied depending on the Discount Band. The amount of the Discount is calculated by multiplying the Total Gross Sale by the Discount Band percentage.
Band
% of Gross Sale
NIL
0%
LOW
1%
MED
2%
HI
5%
 
- The Total Net Sale Amount is the Total Gross Sale minus the Discount.
- Sale Cost is the total costs that have been incurred in completing the sale.
- The Profit is the Total Net Sale minus Sale Cost.
- Each Product has a Category.
- Each Sale has a Customer.

## What to do?
### A. Use PowerBI Desktop to create visualisations that will help to answer each of the following questions:

1. What are the top 3 stores by total net sales amount for each of the years 2021-2022?
2. Are there months in which sales of a particular product any of the states are significantly higher than others?
3. Which sales team has the highest profit margin?
4. Which warehouse(s) should be shut down?
5. Do cities with a higher population have higher profit?

### B. Write an explanation of how your visualisation (or visualisations) addresses each of the questions (i.e., five explanations of no more than 1 page each). 
       
    Include a screenshot of your visualisation(s) for the question and refer to it/them in your explanation.

### C. Write an explanation of your data transformation process. 
    
    It should include details of any changes you make to the structure of the original dataset
     and any additional columns or measures you create to complete the analyses. 

    Please note, this is focused on your data transformation, not the processes for creating your visualisations.
    
### Raw Data Spreadsheet link : 
[https://curtin-my.sharepoint.com/:x:/r/personal/21569498_student_curtin_edu_au/Documents/Sales%20Orders.xlsx?d=w475def7f80b64d3aa2981c793f059db9&csf=1&web=1&e=pkHKyO]




## Analysis to address the respective questions

[The Power BI File](https://github.com/gycellaaa/Analyics/blob/main/A2_PowerBI.pbix)

[1. What are the top 3 stores by total net sales amount for each of the years 2021-2022?]( What-are-the-top-3-stores-by-total-net-sales-amount-for-each-of-the-years-2021-2022?)  

## Table of Contents
- [1. What are the top 3 stores by total net sales amount for each of the years 2021?](#1-what-are-the-top-3-stores-by-total-net-sales-amount-for-each-of-the-years-2021)
- [2. Are there months in which sales of a particular product in any of the states are significantly higher than others?](#2-are-there-months-in-which-sales-of-a-particular-product-in-any-of-the-states-are-significantly-higher-than-others)
- [3. Which sales team has the highest profit margin?](#3-which-sales-team-has-the-highest-profit-margin)
- [4. Which warehouse(s) should be shut down?](#4-which-warehouses-should-be-shut-down)
- [5. Do cities with a higher population have higher profit?](#5-do-cities-with-a-higher-population-have-higher-profit)

## 1. What are the top 3 stores by total net sales amount for each of the years 2021-2022?

* Visualisation
![1. What are the top 3 stores by total net sales amount for each of the year 2021](https://github.com/user-attachments/assets/cd2b6b5d-61fa-45ce-a19b-4916b9469bd4) 

![1.2. What are the top 3 stores by total net sales amount for each of the year 2022?](https://github.com/user-attachments/assets/0f5b6f7f-ad81-4c15-8b4c-676197ff3194)

* Steps
Step 1.	Delete the irrelevant columns: 1.2 lat, 1.2 lng, iso2, iso 3, and ID. The ID doesn't represent stores id

Step 2.	renamed column 1 = to be stores ID, as data scanned from the Store_ID in the Sales Data makes more sense. 
Instead of using the Store ID as reference, it would be more appropriate to transform the Store ID as the City names as it would be easier for stakeholders to understand better the stores represented by the City.

Step 3. I adjusted few of the data types accordingly

Step 4. Add a conditional column to transform the Discount Band to the Discount Band Percentage per the description to change the value of Nil to %, LOW to 1%, MED to 2% and HI to 5%. 

Step 5. In order to find out the find out the total net sales amount, we need to calculate the Total Gross Sales amount. I use the Custom Column option to add a new column to multiply the Order Quantity and the Item Price in the sales data. 

Step 6. Create a column to calculate the Discount band Multiplied with the Total Gross Sales amount. 
Named the column of this multiplication as 
    
    "Discount Total" = Total Gross Sale= [Total Gross Sale] *[Discount Band Percentage]

Step 7.  Finally, The Total Net Sales across the total Gross Sales and the Discount Total for all rows in the table. 
The formula to calculate the Total Net Sale(s) amount using the Measure function: 

    Total Net Sales = SUM('Sales Data'[Total Gross Sales]) - SUM('Sales Data'[Discount Total])

* Description 
The visualisation displays a clustered bar chart “Top 3 stores according to their total net sales”, 
as well as a slicer that consists the options of the year 2021 and 2022.
The option for Clustered bar chart for this specific analysis is to mainly promotes comparison of the total net sales made by the different stores. 
Each column’s length corresponds to the net sales amount, and the additonal value indicated by the end of each bar assissts with the precise of the total net sales amount for each store rather than stressing the reader’s eyes to navigate each amount, and instead, focusing on the main insight of the chart.
When one of the slicer’s year option is chosen, it enabels simple comparison of the total net sales made by the three stores within the dedicated year.
With an integrated tooltip as a storytelling function that provides a compact view of the store, net sales and the year when navigating through specific value. Not only is assists with data filter, it provides a straightforward user-friendly interface for data exploration. It functions to tell a story and guide the reader for quick data-driven decison making. 

* Example analysis 
The three stores of the year 2021 is:  Canberra with net sales of 294k, Lanceston store with net sales of 302k, Toowomba with net sales of 298k.

* Assumption: 
Additonally, I have decided to refer the store name by it’s City, since each Store ID is column from Store data is dedicated to their different cities. Not only it would be more human-readable, 
the reference to the city would also enable further analysation of which store of the city has made the total net sales from.

## 2. Are there months in which sales of a particular product in any of the states are significantly higher than others?

Since this visual contains many datasets, I decided that it is efficient to provide one of the scenario analysis. 

* Visualisation 
![2. Are there months in which sales of a particular product in  any of the states are significantly higher than others?](https://github.com/user-attachments/assets/7b8d83f7-8ac2-4aee-bb14-b406d208ad3c)

* Steps 
Step 1. Changed the name of the column: admin_name to States, for a better indication of the states. 

Step 2. Created the new column for the Total Net Sale of each product to enable Sales Median calculation (this is different with the Total Net Sale(s) since the Total Net Sale only focus each product’s net sales instead of the net sales across all of the summed up net sales and all summed up discount total)

    Total Net Sale = [Total Gross Sales]-[Discount Total]

Step 3. Created a new measure for the Sales Median 

    Sales Median = CALCULATE(MEDIAN('Sales Data'[Total Net Sale]))

* Example analysis: 
Assuming that the reader wants to check the Accessories net sales of the state Queensland in the year 2022 as well as comparing the Accessories sales with the Bar Tools sales. 

From this analysis, we can conclude that the Accessories sales the Queensland state does not make sales from January to May. 
However, there’s significant sales from the month of December by 10.3k, and made more sales by 8.6k compared to the other months. 
While the month of November made only 5.6k sales and less sales by 2.6k compared to the rest of the month’s performance. 
Additionally, the Bar Tool sales in June, July and October is higher than the sales of Accessories. 

* Explanation 

The visualisation displays a line and column clustered chart “Total Net Sasles of product by Months”  to determine the months in which sales of specific product in the different states shows the significant variances  from overall net sales performance. 
The reason I use Line and clustered column chart is that not only it depicts the trend over months 

X-axis representing the months overtime for the paritcular year, 
Y-axis indicates the Total Net Sales amount. 
And the Line Y-axis is used to functions as the Net Sales median of product’s performance with the rest of the month. This enables comparison of product performance for specific year with the overall product’s net sale for the whole years.

On the other hand, there is slicer indicated by the Year that would display the month ranges in tlne and column chart, a  slicer of Product Name for the reader to narrow down into the  particular product. 
And lastly a slicer for reader to navigate through the various states. 

Additionally, the tooltip function is used to indicate the month, product name, and total sales when navigating through specific point of chart after all the slicer options are chosen.

* Assumption:
Assuming that the total net sales median would be used for the stakeholders as further analysis when comparing through the specific product’s total net sales in the chosen year (that indicates the sales of the months), with the product’s total net sales from the rest of the months performance. Further the decision making based on the given performance of specific product’s particular year with the performance for the rest of the years. 

The question does not indicate the year of requested months, therefore I decided to add the slicer to choose the specific year’s months. This enable more and complete analysis given the whole data. 




## 3. Which sales team has the highest profit margin?

* Visualisation
![3. Which sales team has the highest profit margin?](https://github.com/user-attachments/assets/d40fd3e5-7367-413e-aaa2-a202ca7f7860)

* Steps
Step 1. Add a new measure to calculate the average profit margin for each sales team 

    Average Profit Margin = AVERAGEX('Sales Data', 'Sales Data'[Profit Margin])

Step 2.	Create a Rank measure per the average profit margin:

    Rank by Profit Margin = RANKX(ALL('Sales Team'), [Average Profit Margin],,DESC)


* Explanation: 
This visualisation displays the table of “Sales Team Ranking”, with columns of Sales Team, Rank by Profi Margin and the Average Profit Margin.
I used the table as the data that is adopted to create the visualisation as it addresses the question that do not require many dataset and it is easier to understand. 

To address the question, reader would be able to tell which of the sales team that performs from the best to the wost as the sales team rows corresponds to their rank that is based on their profit margin percentage (from over the total net sales amount). Additionally. The color-coded rows that clearly indicates the corresponding rank and profit margin. 
As the Rank column  is sorted in descending order, this is used for a clear indication of the rank performance from each sales team as following ther Profit margin. 

* Assumption: I assumed that the calculation of Profit margin would be the Total Net Sales – Sale cost / Total Net Sales, as this is a common expression to calculate the Profit Margin. 

* Example analysis:
Thus the answer of this question is the Jonathan Hawking sales team as the team is ranked first with the profit margin of 38%. 
While the lowest performing sales team is Shaw Wallace ranked by 28 with the profit margin of only 35.5%. 


## 4. Which warehouse(s) should be shut down?

* Visualisation
![4. Which warehouse(s) should be shut down?](https://github.com/user-attachments/assets/c9e6498e-7567-47fc-9243-8a19cb62e7d0)

* Steps
Step 1.	Firstly, in the Store data, remove the DeliverDate ad ShipDate columns as this would not be relevant for this analysis. 

Step 2.	Add a new measure to calculate the Total Profit        

    Total Profit = SUM('Sales Data'[Net Sales Amount]) - SUM('Sales Data'[Sale Cost])


* Explanation 

The visualisation indicates Stacked Column chart for total Profit, and the total Net Sales made by the respective warehouse.
I use the stacked column chart as I want to visually demonstrate that the both profit and sales are both crucial considerations to shut down the warehouse limited to the provided datasets. Besides profit, the total net sale is also a crucial value provided by the warehouses. 

The X-Axis representing the Warehouse codes that corresponds to the respective net sales and profit,
Y-axis that contains the total net sales and total profit. 
The darker green bars on the chart indicates the total net sales made per warehous, while the lighter green bars indicates the total profit made by each warehouse.
To make the decision of which warehouse to shut down, the reader can determine whether to prioritise making profit or the net sales, and therefore decided which of the warehouse to shut down. 

* Example analysis: the stakeholder prioritizes profit, therefore the warehouse to shut down is WARE-NBV1002. (reminder: since this is a limited data and thus, in reality, this is not the only data we rely to calculate the worth of each warehouse)

## 5. Do cities with a higher population have higher profit?

* Visualisation
![5. Do cities with a higher population have higher profit?](https://github.com/user-attachments/assets/139313c7-5cb0-4d4b-b2dd-dbaf08d5cbee)

* Step
#### (Though not directly related to data transformation, the visualisation adds up to create the relevant data). 
 
 Step 1. Using the R Script visual to add a line trend & precise coordinates: 

    library(ggpubr)
    ggscatter(dataset, x = "population", y = "Total Profit",
    add = "reg.line", conf.int = TRUE) +
    stat_cor(label.x = 1000000, label.y = 300000, size = 6, color = "red") +
    stat_regline_equation(label.x = 3000000, label.y = 300000, size = 6, color = "blue",
    aes(label = paste(..eq.label.., sep = "~~~")))



* Explanation: 
The first chart indicates a correlation plot with an integrated coding of R-Studio, as this software enable to add a correlation line to visually indicate relationship and R=-0.18, p = 0.35 to statistically indicate the relationship’s strength (correlation coefficient) between Population and the Total Profit.
Therefore, we can determine whether there is a strong indication that when Profit increases, Population increase?
Additionally, the y=24000-0.002x that indicates of the equation of the regression line, useful when there is additional data to calculate the specific value. 

Additional second chart contains the red shading within the chart, useful to indicate where most of the total profit and population lays on. This helps to visually answer where or not there is any correlation at all. 
X-axis indicating the total profits.
Y-axis indicating the population.  

* Example analysis: 
Using the R=-0.18, p = 0.35 to indicate if there is relationship, since it is -0.18.then there is no correlation between City and population at all. 


## Conclusion

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present except column named "Arrival Delay".
- Step 5 : For calculating average delay time, null values were not taken into account as only less than 1% values are null in this column(i.e column named "Arrival Delay") 
- Step 6 : In the report view, under the view tab, theme was selected.
- Step 7 : Since the data contains various ratings, thus in order to represent ratings, a new visual was added using the three ellipses in the visualizations pane in report view. 
- Step 8 : Visual filters (Slicers) were added for four fields named "Class", "Customer Type", "Gate Location" & "Type of travel".
- Step 9 : Two card visuals were added to the canvas, one representing average departure delay in minutes & other representing average arrival delay in minutes.
           Using visual level filter from the filters pane, basic filtering was used & null values were unselected for consideration into average calculation.
           
           Although, by default, while calculating average, blank values are ignored.
- Step 10 : A bar chart was also added to the report design area representing the number of satisfied & neutral/unsatisfied customers. While creating this visual, field named "Gender" was also added to the Legends bucket, thus number of customers are also seggregated according the gender. 
- Step 11 : Ratings Visual was used to represent different ratings mentioned below,

  (a) Baggage Handling

  (b) Check-in Services
  
  (c) Cleanliness
  
  (d) Ease of online booking
  
  (e) Food & Drink
  
  (f) In-flight Entertainment

  (g) In-flight Service
  
  (h) In-flight wifi service
  
  (i) Leg Room service
  
  (j) On-board service
  
  (k) Online boarding
  
  (l) Seat comfort
  
  (m) Departure & arrival time convenience
  
In our dataset, Some parameters were assigned value 0, representing those parameters are not applicable for some customers.

All these values have been ignored while calculating average rating for each of the parameters mentioned above.

- Step 12 : In the report view, under the insert tab, two text boxes were added to the canvas, in one of them name of the airlines was mentioned & in the other one company's tagline was written.
- Step 13 : In the report view, under the insert tab, using shapes option from elements group a rectangle was inserted & similarly using image option company's logo was added to the report design area. 
- Step 14 : Calculated column was created in which, customers were grouped into various age groups.

for creating new column following DAX expression was written;
       
        Age Group = 
        
        if(airline_passenger_satisfaction[Age]<=25, "0-25 (25 included)",
        
        if(airline_passenger_satisfaction[Age]<=50, "25-50 (50 included)",
        
        if(airline_passenger_satisfaction[Age]<=75, "50-75 (75 included)",
        
        "75-100 (100 included)")))
        
Snap of new calculated column ,

![Snap_1](https://user-images.githubusercontent.com/102996550/174089602-ab834a6b-62ce-4b62-8922-a1d241ec240e.jpg)

        
- Step 15 : New measure was created to find total count of customers.

Following DAX expression was written for the same,
        
        Count of Customers = COUNT(airline_passenger_satisfaction[ID])
        
A card visual was used to represent count of customers.

![Snap_Count](https://user-images.githubusercontent.com/102996550/174090154-424dc1a4-3ff7-41f8-9617-17a2fb205825.jpg)

        
 - Step 16 : New measure was created to find  % of customers,
 
 Following DAX expression was written to find % of customers,
 
         % Customers = (DIVIDE(airline_passenger_satisfaction[Count of Customers], 129880)*100)
 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred business class
 
 ![Snap_Percentage](https://user-images.githubusercontent.com/102996550/174090653-da02feb4-4775-4a95-affb-a211ca985d07.jpg)

 
 - Step 17 : New measure was created to calculate total distance travelled by flights & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(airline_passenger_satisfaction[Flight Distance])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap_3](https://user-images.githubusercontent.com/102996550/174091618-bf770d6c-34c6-44d4-9f5e-49583a6d5f68.jpg)
 
 - Step 18 : The report was then published to Power BI Service.
 
 
![Publish_Message](https://user-images.githubusercontent.com/102996550/174094520-3a845196-97e6-4d44-8760-34a64abc3e77.jpg)

# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://user-images.githubusercontent.com/102996550/174096257-11f1aae5-203d-44fc-bfca-25d37faf3237.jpg)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://user-images.githubusercontent.com/102996550/174074051-4f08287a-0568-4fdf-8ac9-6762e0d8fa94.jpg)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Customers = 129880

   Number of satisfied Customers (Male) = 28159 (21.68 %)

   Number of satisfied Customers (Female) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Male) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (Female) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Baggage Handling - 3.63/5
    b) Check-in Service - 3.31/5
    c) Cleanliness - 3.29/5
    d) Ease of online booking - 2.88/5
    e) Food & Drink - 3.21/5
    f) In-flight Entertainment - 3.36/5
    g) In-flight service - 3.64/5
    h) In-flight Wifi service - 2.81/5
    i) Leg room service - 3.37/5
    j) On-board service - 3.38/5
    k) Online boarding - 3.33/5
    l) Seat comfort - 3.44/5
    m) Departure & arrival convenience - 3.22/5
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 15.09
      b) Average delay in departure(minutes) - 14.71
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Class
 
 1.1) 47.87 % customers travelled by Business class.
 
 1.2) 44.89 % customers travelled by Economy class.
 
 1.3) 7.25 % customers travelled by Economy plus class.
 
         thus, maximum customers travelled by Business class.
 
 ### Age Group
 
 2.1)  21.69 % customers belong to '0-25' age group.
 
 2.2)  52.44 % customers belong to '25-50' age group.
 
 2.3)  25.57 % customers belong to '50-75' age group.
 
 2.4)  0.31 % customers belong to '75-100' age group.
 
         thus, maximum customers belong to '25-50' age group.
         
### Customer Type

3.1) 18.31 % customers have customer type 'First time'.

3.2) 81.69 % customers have customer type 'returning'.
       
       thus, more customers have customer type 'returning'.

### Type of travel

4.1) 69.06 % customers have travel type 'Business'.

4.2) 30.94 % customers have travel type 'Personal'.

        thus, more customers have travel type 'Business'.
