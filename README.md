# DataKilqProject



This report is based on the Sales Performance of a particular Organization.

The dataset has 5 tables including the Customer profile, Returns Table, Product profile, Store info, and Transaction details. It was first loaded into SQL and then brought into Power bi for analysis via Power query. The dataset is clean so only a little cleaning is done to it.
The datatypes and all properly checked and then load into the power bi desktop page. After that modeling (not the fashion modeling 😝) is considered. This data has / forms a snowflake schema (in small English it does not form a star) Or better still say not all the dimension table is Directly connected to the Fact table. Now that modelling is done I went on to do my Analysis.
For this project, some questions are laid out already and I did be going through how I solved some of them. 
Firstly we are asked to look for Gross Sales which is the Quantity Supplied * Unit Price. N:B - Quantity Supplied is on the transaction table while the Unit price is on the product profile table, So I created a DAX function 

Gross_Sales = SUMX(Transactions_detail, Transactions_detail[Quantity_Supplied] *  RELATED(Product_Profile[Unit_Price])) . to get my gross sales .

The second question says -- Look for Revenue which is Gross sales - Discount sales. N: B - Both are in my transaction table .

So, I did this using the measure -- Revenue = Transactions_detail[Gross_Sales] - Transactions_detail[Discount Value]

Let's take another question which says Revenue and their growth (MOM) -- First I create a previous month's revenue using ...Prev month 

Revenue = CALCULATE([Revenue], DATEADD('Calender Table'[Date], -1, MONTH))


![](https://github.com/SaobanLateefat/Data
kliq/blob/master/HomeDash.PNG)



and then to get the MOM I used      MOM %(R) = DIVIDE([Revenue] - [Prev month Revenue], [Prev month Revenue] * 100)
to get my Month of Month.

There are plenty of DAX calculations there but let me just stop here. After the whole analysis, I then went ahead to create my Report using appropriate visuals/charts to represent my stuff.







