# data-512-a2
A2: Bias in the Data
This folder contains information on analysing the done for identifying the bias in politician articles in wikipedia data for the Human Centered Data Science. The below location contains the details which were asked 
https://wiki.communitydata.science/Human_Centered_Data_Science_(Fall_2019)/Assignments#A2:_Bias_in_data 

Data sets used:
1. Page_Data.csv: this data was pulled from https://figshare.com/articles/Untitled_Item/5513449. The file contains the below columns which have been documented in the figshare. 

"page", containing the unsanitised page title.
"country", containing the sanitised country name, extracted from the category name;
"rev_id" which is the unique identifier for an article.

2. WPDS_2018_data.csv
This data set was picked from world population datasheet published by the Population Reference Bureau, https://canvas.uw.edu/courses/1319253/files/
The file contains 
Geography: Geography contains country and in Capitals the geography. There are 6 geographies in the file.
Populationmid-2018(millions): This has the mid-2018 population data for each of the country and geographies.

Final Dataset:
1. The final analysis was done from the file wp_wpds_politicians_by_country.csv. This file has the following columns:
"country	" - Name of the country
"article_name" - Title of the article
"revision_id" - unique id of the article
"article_quality" - score from Ores
"population" - population data from the WPDS file.


Steps taken
1. Cleanup down on the Page_Data: Articles starting with "Template:'were removed from the file.
2. Countries and Geographies were seperated so that at a feature date they can be combined. This was done in excel and the best way is to add another column with geography a country belongs to so that you now have 3 columns then mapping them will become easy else you will not know which country belongs to which geography.
3. For the page_data, gather all of the rev_id's and send them in chunks of 100 to the ores API to get a prediction. 
4. Once we have the data, seperate out the rev_id's for which we dont have any prediction from Ores, which were about 155 of the articles.
5. Then join this predicted rev_id using the country as a mapping to the population data and then get the final data. 
6. In the final data set I also removed all of the rows where we did not have the country mapping. Finally we ended with 44465 rows in the final file(wp_wpds_politicians_by_country.csv)
7. I tool the final fie and then used pivot table to get to the various different version of the tables which were requested. I have uploaded this excel with appropriate names for the tabs to understand what was done. Coverage and Relative quality was calculated for each of the country. I also claculated the coverage per person hence i multiplied the population provided with 1Million so that the coverage numnbers are per person.

License:
License used was the MIT License.


Additional Resources Used:
Ores: https://www.mediawiki.org/wiki/ORES
CLASSES PRODUCED BY oRES: https://en.wikipedia.org/wiki/Wikipedia:WikiProject_assessment#Grades
Used stackoverflow a lot to search for some of the code needed for getting the data through API and then writing into files.


