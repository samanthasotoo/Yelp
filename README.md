# Yelp Reviews
# Data Warehousing Project
Samantha Soto 

## Description
This project is a data warehousing solution designed to consolidate, transform, and store large volumes of OTC market data for analytical purposes. It aims to provide a centralized repository for business intelligence and reporting.

## Business Problem 

The Over-The-Counter (OTC) market refers to a decentralized trading environment, distinct from formal exchanges such as the NYSE or NASDAQ. It's a network where financial instruments, such as stocks, bonds, and derivatives, are traded directly between two parties without the oversight of an exchange. The OTC market is known to lack transparency & regulations; these variables can definitely contribute to higher potential returns but also comes with increased risks for buyers. 



## Business Impact

- Risks: Handling financial data is particularly tricky because we need to ensure strict secuirty measures to protect against data breaches and maintain privacy.
- Costs: OTC market data constantly updates. To handle constant updates, a robust IT infrastructure is needed, which can handle high volumes of data transactions in real-time. Significant amounts of storage is needed & it needs to be protected.
- Benefits: Analyzing the OTC market data can influence improved decision making processes and strategy developments for investors. Processing this data & storing it in a datawarehouse can act as a centralized repository for market data, including transaction prices, volumes, and counterparty details. This enhances transparency in price discovery. Further, analysts & stakeholders can look at historical data to discover patterns and they can further improve their investment strategies and risk management.  
  - A successful implementation of the datawarehouse & analysis capabilities can improve decision making effiency by 5-10%. This can increase a company's profits due to better trading & investment decisions. 

## Business Persona 

As mentioned, many can benefit from having access to this data in a centralized repository. Financial analysts and economists can use their data to forecast market trends, and advise on investments. This tool will also be immensely helpful to portfolio managers & traders who are the key decision makers and execute traders. This allows for real-time decision making, assessing risk more seamlessly -- this should lead to higher returns and effective portfolio diversification. 

## The Data 

OTC Market Data was provided by our professor who has permission to access it (the data is from OTC Markets Group). OTC Markets Group is an organization that specializes in collecting & distributing financial data for the OTC markets. The data we utilized for this project include the information on the securities and companies along with details on where these securities were traded. It also holds pricing information such as the closing bid & ask prices with their respective dates. 

Our data size is around 4 GB - this suggests that there is a lot to analyze and can be used to make informed decisions on investments. However, due to cost limitations (and computational resources), processing this amount of data is challenging. It requires more storage space and computing power to extract & transform this data. 

## Methods
- Dimensional Modeling: creating a fact & dimension tables to model our data and to help us better understand the relationships between them.
- The DbSchema can be found [Here](https://github.com/Pupat3l/OTC_4400/blob/main/DbSchema/OTC.dbs)

<img width="632" alt="DbSchema" src=https://github.com/Pupat3l/OTC_4400/blob/main/DbSchema/DbSchema.jpeg>

  
- Extract, Transform, Load (ETL) Processes for Data Integration
  Diagram:
  <img width="632" alt="Screenshot 2023-12-07 at 1 07 37 PM" src="https://github.com/Pupat3l/OTC_4400/assets/42002045/cddff691-aabf-4c1f-9838-7f7f2521bd97">

### Extract:
- Professor provided us the data source in the .CSV format.
- Python & Boto3 was used to upload our data from our local file system to Amazon Web Services Storage (S3)
  [Extract.py script](https://github.com/Pupat3l/OTC_4400/blob/main/ETL/Extract.py)

### Transform: 
- Python & Boto3 (Python was used to transform our data, making sure all data types matched our schema & dropping anything unneccesary). We utilized Pandas to make any transformations (split up the original CSV file into dimensions) & then uploaded the individual dimensions back to S3 in CSV format.
  [transform.py script](https://github.com/Pupat3l/OTC_4400/blob/main/ETL/transform.py)

### Load: 


- We loaded our data into Amazon Web Services Datawarehouse (AWS Redshift Serverless), we had a predefined schema because of our dbSchema.
- We performed combination of both drag and drop and automation to upload dimensions files to Datawarehouse from s3 bucket.
  [load.py_script](https://github.com/Pupat3l/OTC_4400/blob/main/ETL/load.py)

### Visualization:

- We utilized Tableau to create visualizations using csv as the serving data.
- The Tableau workbook is uploaded [here](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/OTC_Engineers.twb)
- Following are the visualization created:

#### Price Change over time
![Visualization 1](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/Price_Change.png)
- We created a visualization using Closing Best Ask Date and Price Change(calculation created in Tableau - Last Price - Open Price).
- The visualization shows the price change for each commodity in OTC Market over time in months(1-12)
- As you can see, December has the most negative price change and June has the most positive. Periodically Earnings report could be a reason for this change.
  
### Share Volume over time
![Visualization 2](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/Share_Volume.png)
- We created a visualization using Avg. Share Volume and Closing Inside Ask Price Date.
- The visualization shows Avg. Share Volume for each commodity in OTC Market over time in years. The y-axis is a logarithmic scale to view the data points better and the data can spread out more.
- As you can see, there is an upward trend for share volume over years which indicates that the market interest is growing.

### Bid-Ask spread over time
![Visualization 3](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/Bid_Ask_spread.png)
- We created a visualization using Closing Bid-Ask(calcualtion created in Tableau - Closing Bid Price - Closing Ask Price) and Closing Best Bid Date.
- The visualization shows the Bid-Ask spread of each commodity in OTC Market over time in terms of days/month.
- As you can see the values are negative which determines that people are good at negotiations. It also shows that on 8th day of the month, negotations are the best.

### Trading Volume vs Price Change over time
![Visualization 4](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/Trading_Volume_vs_Price_Changes.png)
- We created visualization using Price Change and Avg. Share Volume and Previous Close Date.
- The visualization shows the Avg. Share volume and Price Change for each commodity in OTC market over time in terms of years.
- As you can see Avg. Share volume and last price are moving in the same direction indicates a increasing demand of shares and market confidence.

### Dashboard combining all visualization
![Visualization 5](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/Dashboard.png)
- The Dashboard is an interactive visualization that shows real-time updates of all 4 visualization from above. There is also a filer in place for Status and Venue which helps visualize trends on different combinations of statuses and venues.

## Tools 

- Data Storage: AWS S3
- Data Processing: Python Scripts
- Visualization: Tableau  
- Data Orchestration [Work in Progress]: Automating data pipeline using Talend

## Getting Started
### Prerequisites
- [Python](https://www.python.com/) installed
- [Boto3] installed
- [Amazon S3] access
- [Amazon Redshift Serverless] access
- [Psycopg2] installed


# Yelp Reviews - CIS 4400
