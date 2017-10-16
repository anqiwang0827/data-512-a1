# Monthly Traffic Data on English Wikipedia Project
## DATA 512 A1 Data Curation
The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from July 1 2008 through September 30 2017. Full steps are documented to ensure the project is fully reproducible by others: from data collection to data analysis

To reproduci the result of the project, you will need to clone this repository into your computer.

First, let me explain all the different moving parts that make up the python project, and all the elements which allow us to effectively share it with others, test it, document it, and track its evolution.

We recommend using conda to install matplotlib and other such libraries to ensure smooth running of the module.

## Organization of the  project

The project has the following structure:  
   * data-512-a1 
     * |- README.md  
     * |- LICENSE  
     * |- ProgrammingStep  
        * |- hcds-a1-data-curation.ipynb 
        * |- Visualization
     * |- Data 
        * |- Source Data
        * |- Final Data

In the following sections we will examine these elements one by one. First,let's consider the core of the project which is the hcds-a1-data-curation.ipynb in hcds-a1-data-curation.ipynb/ProgrammingStep folder 

## ProgrammingStep
### hcds-a1-data-curation.ipynb 
In this jupyter notebook, detailed steps are documented and presented for you to combine data Wikipedia traffic from two different Wikimedia REST API endpoints (Pageviews & Pagecounts) into a single dataset, perform some simple data processing steps on the data, and then analyze that data.

There are three steps to compelete the project.
Step 1: Data acquisition
    Collect data from two different API endpoints, the Pagecounts API for access to desktop and mobile traffic and Pageviews API for access to desktop, mobile web, and mobile app traffic from Wikipedia from 2008 to 2016. Execute codes in Step 1 will collect data for all months from aboth APIs in the Jupyter Notebook and then save the raw resuls into 5 separate Json Source data files.
Step 2: Data processing
    After data is collected from the Pageviews API, combine the monthly values for mobile-app and mobile-web to create a total mobile traffic count for each month. For all data, separate the value of timestamp into year and month. And combine all data into a final single CSV file with headers.
Step 3: Analysis
    Visualize the dataset created from previous step toa . time series graph. The visualizationwill track three traffic metrics: mobile traffic, desktop traffic, and all traffic (mobile + desktop)

#### How to use the Jupyter Notebook
After the Jupyter Notebook is downloaded, run through the notebook.
The module will then output:
1) 5 source data files in JSON format.
2) 1 final data file in CSV format.
3) 1 .png image of the visualization.

### Visualization
1 .png image of the visulization will be saved after executing hcds-a1-data-curation.ipynb 

## Data
license of the source data:         
Data was gathered from the Wikimedia REST API, Wikimedia Foundation, 2017. CC-BY-SA 3.0   
Relevant API documentation:  
https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts
https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews    
API endpoints:  
https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end    
https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end   
Wikimedia Foundation terms of use:    
https://wikimediafoundation.org/wiki/Terms_of_Use/en  

### Source Data
Collect data from two different API endpoints, the Pagecounts API and the Pageviews API.

The legacy Pagecounts API provides access to desktop and mobile traffic data from January 2008 through July 2016.
The Pageviews API provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017.

After executing Jupyter Notebook Step 1, 5 JSON source data files will be saved with following naming covention:  
pageviews_mobile-web_201507-201709.json                    
pageviews_mobile-app_201507-201709.json  
pageviews_desktop_201507-201709.json   
pagecounts_mobile-site_200801-201607   
pagecounts_desktop-site_200801-201607   

### Final Data
After saving raw data as JSON files, several processing steps needed on the data.

For data collected from the Pageviews API, combine the monthly values for mobile-app and mobile-web to create a total mobile traffic count for each month.
For all data, separate the value of timestamp into four-digit year (YYYY) and two-digit month (MM) and discard values for day and hour (DDHH).
Combine all data into a single CSV file with the following headers:

Column	 Value   
year	   YYYY	2008-2017       
month	   MM	  1-12   
pagecount_all_views	num_views   
pagecount_desktop_views	num_views   
pagecount_mobile_views	num_views   
pageview_all_views	num_views  
pageview_desktop_views	num_views   
pageview_mobile_views	num_views   

After executing Jupyter Notebook Step 1, a final data file will be saved as en-wikipedia_traffic_200801-201709.csv.

## Important Notes
1) We're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders. The Pageview API (but not the Pagecount API) will use filter by agent=user.
2) There is a 13 month period in which both APIs provide traffic data
