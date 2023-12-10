# Yelp Reviews
# Data Warehousing Project
Samantha Soto 
![image](https://github.com/samanthasotoo/Yelp/assets/42002045/39c0bbe2-6854-4ad1-af6b-ed3e41673ba1)


## Description
This project focuses on creating a sophisticated data warehousing solution tailored for analyzing Yelp Reviews. It aims to gather, transform, and store extensive Yelp Reviews data for in-depth behavioral analysis. The primary objective is to establish a central repository for insights into user behavior patterns, facilitating effective business intelligence and trend analysis. For the purposes of this project, I have only decided to look into categorical and numerical features instead of actual text data. 

## Business Problem 

The project addresses the need for a comprehensive understanding of user behavior related to Yelp Reviews. Key questions include determining peak times for review submissions, trends in user engagement, and the historical growth of Yelp's popularity. By analyzing these aspects, businesses can gain valuable insights into customer engagement patterns, enabling them to tailor their marketing and operational strategies more effectively.



## Business Impact

- Risks: Managing user-generated data entails ensuring accuracy, privacy, and compliance with data protection regulations.
- Costs: The dynamic and voluminous nature of Yelp Reviews necessitates robust infrastructure for real-time data processing and substantial storage capacity.
- Benefits: Analyzing user behavior trends from Yelp Reviews can inform businesses about peak engagement times, user preferences, and the effectiveness of their services or products. This knowledge can lead to improved customer service strategies, targeted marketing campaigns, and overall enhanced user experience.


## Business Persona 

This data warehouse serves business analysts, marketers, and decision-makers who seek to understand and leverage user engagement patterns. By accessing a centralized source of analyzed user behavior, these professionals can make informed decisions to optimize their services and align them with user preferences and peak engagement periods. Further, market researchers can analyze trends in customer preferences & behaviors across categories and geographical locations. In addition, policy makers and urban planners can analyze trends in business popularity and customer preferences, they can make informed decisions about urban development, zoning, and local economic policies.

## The Data 

The Yelp Academic Dataset is publicly available on their website yelp.com/dataset/download. The data consists of 4 files: business, review, tip and user. Each of these files hold information on business attributes (such as location and categories), review counts, tips left by users on a business and user information. The dataset is quite large (it is about 8 GB total) and requires a good amount of computing power and datahandling in order to load into a datawarehouse. 

## Methods

- Dimensional Modeling: creating a fact & dimension tables to model our data and to help us better understand the relationships between them.
  - dBSchema was used
  - <img width="1005" alt="Screenshot 2023-12-09 at 6 22 17 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/0b6cb383-109c-4931-a229-66cde1d4ab6c">  
- Extract, Transform, Load (ETL) Processes for Data Integration

### Extract:

- Download the dataset from yelp.com/dataset/download & run a python script to unzip the file.
- Python & Boto3 was used to upload my data to Amazon Web Services Storage (S3)


### Transform: 
- Python & Boto3 (Python was used to transform my data, making sure all data types matched the schema & dropping anything unneccesary). We utilized Pandas to make any transformations (split up the original CSV file into dimensions) & then uploaded the individual dimensions back to S3 in CSV format.
 

### Load: 

- I loaded my data into Amazon Web Services Datawarehouse (AWS Redshift Serverless), we had a predefined schema because of our dbSchema.
- I performed combination of both drag and drop and automation to upload dimensions files to Datawarehouse from S3 bucket. 
- My data was running into errors while loading to AWS Redshift Serverlesss so I tried loading into Google BigQuery, which was more seamless.
- I eventually was able to connect to AWS Redshift using my Python script.


### Visualization:

- We utilized Tableau to create visualizations using csv as the serving data.
- The Tableau workbook is uploaded [here](https://github.com/Pupat3l/OTC_4400/blob/main/Tableau/OTC_Engineers.twb)
- Following are the visualization created:

#### Yelp Reviews Use Over time
!<img width="936" alt="Screenshot 2023-12-09 at 7 24 48 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/3a25fb9b-40c5-4355-84a3-82ac0a3db044">

- Plotted above is the amount of reviews written by users over the year along with a forecast as to how many reviews will be published in the coming years. As you can see, the number of reviews dropped drastically in 2020, this correlates to the global pandemic and having to be on lockdown for the whole year. 


### Popular Days to Write Reviews
!<img width="1123" alt="Screenshot 2023-12-09 at 7 29 15 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/7dfad98e-94d1-4973-9cfb-75faa0edd696">

- The visualization above shows the most common days to publish reviews is on Sunday. This makes sense because it is the world's day to unwind and reflect on the week that has just passed. 

### Most Reviews by State
!<img width="265" alt="Screenshot 2023-12-09 at 7 58 37 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/846eb54d-bb94-4f11-8cf1-fa9fdc2fde9a">

- The visualization above shows the most reviews by state, as you can see most reviews are from PA. This is obviously because the yelp dataset does not have reviews from all states, but there might be the most in PA since it is closer to NYC. 

### Ratings Based on WiFi
!<img width="320" alt="Screenshot 2023-12-09 at 8 05 02 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/b20084db-a0d1-4307-917d-293c65408492">

Image above shows star ratings based on whether or not they have WiFi and if it is paid. Paid WiFi has lower ratings. 

### Dashboard combining all visualization
!<img width="993" alt="Screenshot 2023-12-09 at 7 57 15 PM" src="https://github.com/samanthasotoo/Yelp/assets/42002045/04bf5bd0-9863-436a-ba9b-efd3133838e9">

- The Dashboard is an interactive visualization that shows real-time updates of all visualization from above. 

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
