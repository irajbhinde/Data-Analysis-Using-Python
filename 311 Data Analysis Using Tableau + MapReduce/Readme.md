
## NYC 311 Data Analysis

The Data is downloaded from the NYC Open Data API

Here's the link to the website: 
https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9

And, API documentation: 
https://dev.socrata.com/foundry/data.cityofnewyork.us/fhrw-4uyv

For the ease of analysis, we will download data only for the year 2015, 2016 and 2017.

Script: Download API Data.ipynb - will download the data from the API and save it into the Folder Finals/Data/311_(Year).csv
Since, most of our analysis will be based of the following fields, the rest of the data is filtered out.

Fields taken into consideration include: 
- agency_name, borough, city, closed_date, complaint_type, created_date, descriptor, due_date, incident_zip, street_name , resolution_description


### Analysis1:

Since, I have used Plotly graphs are not visible in GitHub - as iFrames are not supported.
Visit the below link to see the interactive graph for Analysis1: http://nbviewer.jupyter.org/github/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/analysis/Analysis%201.ipynb

- Find the number of incidents reported each month by Borough for year 2015, 2016 and 2017 and plot their distribution    

Segregating the data by 5 Boroughs in NY - BRONX, BROOKLYN, MANHATTAN, QUEENS, STATEN ISLAND by month-year.
1. Read data from all 3 CSV's - 311_2015.csv, 311_2016.csv, 311_2017.csv and extract Borough and Created Date
2. Transform JSON Date to datetime and extract month and year information
3. Group the data by Borough, Month and Year and get the count of the incidents reported
4. Plot the information of all 3 years for each month using Plotly.

![A1G1_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis1_Graph1.png)

- Find the Top 10 Complaint Types and plot their distribution by Borough for years 2015, 2016 and 2017

Digging deeper to analyse the Boroughs, first we segregate the data by Borough, Complain_Type and Year.
1. Filter the data by the Top 10 Complaint_Types: 
 'HEAT/HOT WATER', 'Noise - Residential', 'UNSANITARY CONDITION','Blocked Driveway','Street Light Condition','Illegal Parking', 'Water   System','Street Condition','Sanitation Condition'
2. Count the total no.of incidents reported by Borough, Complaint_Type, Year
3. Count the no.of incidents reported for our Top 10 issues by Borough, Complaint_Type, Year
4. Find the difference between count of Total Issues and Top 10 Issues to get the count of Other Issues
5. Transform this data into Percentage and plot the % contribution of each complaint type by Year for each of the 5 Boroughs.

![A1G2_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis1_Graph2.png)

### Analysis 2:

Since, I have used Plotly graphs are not visible in GitHub - as iFrames are not supported.
Visit the below link to see the interactive graph for Analysis2: http://nbviewer.jupyter.org/github/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/analysis/Analysis%202.ipynb

- Finding the Top 10 City Zip codes where incidents are reported for Year 2017

1. Extract the data from 311_2017.csv for year 2017 and create a dataframe to read the Zip Code and the Complaint_Type
2. Count the values of Zip Code to find the count of incidents reported by zip code 
3. Get the top 10 zip codes with the highest no. of incidents reported 
4. Use Seaborn to plot the Top 10 Zip Codes with Highest Reported 311 Incidents - 2017

![A2G1_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis2_Graph1.png)

- Finding the highest reported complaint and its distribution by Percent

1. Index the Complaint_Type and get a unique count of each of the issues reported
2. Plot a line chart to see the Top 20 Complain_Type vs Count - 2017
3. To further analyze the complaint types we narrow down the top 10 complaint types and their % distribution as compared to the total issues reported.
4. Plot a Donut Graph of Complaints By Type and their % distribution - 2017

![A2G2_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis2_Graph2.png)

![A2G3_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis2_Graph3.png)

- Finding the highest reported issue for Top 25 Cities

1. Filter the data by City and Complaint Type and group them to find the sum 
2. Plot a bar chart to show the Most Reported Issue in Top 25 Cities - 2017

![A2G4_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis2_Graph4.png)

### Analysis3:

Since, I have used Plotly graphs are not visible in GitHub - as iFrames are not supported.
Visit the below link to see the interactive graph for Analysis3:
http://nbviewer.jupyter.org/github/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/finals/analysis/Analysis%203.ipynb

- From Analysis 2 we could derive that HEAT/HOT WATER is the highest reported incident. In this analysis we will try to dig further and find the average resolution time for this issue by each Borough for Years 2015, 2016 and 2017.

1. Load the data from all the 3 CSV files for year 2015, 2016 and 2017
2. Filter the data to extract 'created_date','closed_date','complaint_type','borough','resolution_description'
3. Transform the JSON dates to datetime and create new columns for Year and Months
4. Since, heat issues are valid in Winters and Early Spring which Includes months (Oct-May) we will filter the data for this period only
5. Also, we filter out the data wherein the complaint was resolved in the next heating season
6. Now, we can select only the cases where the closed date was in the same season as the created date. 
 And, Calculate Average Resolution Times
7. Plot the Average Resolution Time by Borough for Years 2014-2017 for HEAT issue 

![A3G1_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis3_Graph1.png)

- Create a WordCloud from the Resolution_Description Corpus of the data.

1. Load the Resolution_Description corpus from the CSV files
2. Perform NTLK and lemmatize the corpus to find the unique words and their frequency after removing the stop words
3. Create a wordcloud to see the most frequently used words in the corpus 

![A3G2_1](https://github.com/dhavalbhinde/bhinde_dhaval_spring2017/blob/master/Python%20Data/finals/images/Analysis3_Graph2.png)


### Addtional Instructions to Run the code
1. Install Plotly using 'pip install plotly'.
2. Install WordCloud using 'pip install wordcloud'
   If the installation fails for WordCloud - please follow: https://github.com/amueller/word_cloud/

### Data Related Instructions
1. Since, the original data is too heavy (~1.6Gb) to be loaded onto GitHub - the data can be downloaded onto the finals/data folder easily when you execute the Download API Data.ipynb notebook.
2. Please make sureyou have approximately 5GB of free space in the hard drive or else the request will fail.
3. To get the data_download_key please visit: https://data.cityofnewyork.us/profile/app_tokens
4. The CSV files under folder data are sample inputs only. Please download the complete data by running the Download API Data.ipynb notebook.
