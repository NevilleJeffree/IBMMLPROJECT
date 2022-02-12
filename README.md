# SpaceX Project
- Data Collection API
- Data Collection with Web Scrapping
- Exploratory Data Analysis with SQL
- Exploratory Data Analysis (Python)
- Exploratory Data Analysis with Data Visualisation
- Interactive Visual Analytics with Folium
- Build a Dashboard Application with Plotly Dash

Project Background & Context
I predicted if the Falcon 9 first stage will land successfully. SpaceX advertises Falcon 9 rocket launches on its website, with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore, if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.

Problems?
• What factor will effect Falcon 9 to land successfully?
• Effect of each relationship with certain rocket variables will impact in determining the the success rate of a successful landing. 
• What condition have to be achieved to reach a higher success rate?

Methodology
1. Data collection using API & Web Scrapping (Wikipedia)
2. Data Wrangling (Transforming data for Machine Learning) One hot encoding data fields for Machine Learning and dropping irrelevant column.
3. Exploratory Data Analysis using SQL & Data Visualisation. 
4. Generate interactive visual with Folium & Plotly Dash. 
5. Perform predictive analysis using classification model.

Methodology:
Data Collection
1. Worked with SpaceX launch data gathered from SpaceX REST API.
2. The API provided us data about launches, including information about rocket used, payload delivered, launch specification, landing specification, landing outcomes.
3. The SpaceX REST API endpoints, or URL, starts with api.spacexdata.com/ v4/.
4. Another popular data source for obtaining Falcon 9 Launch data is web scraping Wikipedia using BeautifulSoup.

Web Scrapping & Cleaning
1. Getting response from HTML & status code
2. Creating BeautifulSoup Object
3. Finding tables
4. Getting column names
5. Creating dictionary to DataFrame
6. Exporting CSV

Data Wrangling
1. Calculate number of launches at each sites
2. Calculate number and occurence of each orbit
3. Calculate number and occurence of mission outcome per orbit type
4. Create landing outcome label from Outcome column
5. Export as CSV

Exploratory Data Analysis
Flight Number VS Launch Site
![image](https://user-images.githubusercontent.com/32995833/151301942-e14ff43e-e926-4ac7-9ebe-97a0dfcb3356.png)
1. With Class 0 is fail and Class 1 is sucess.
2. For launch site CCAFS SLC 40 we can see less fails starting around flight number 50
3. For launch site VAFB SLC 4E we can see there’s only one fail after flight number 20
4. For launch site KSC LC 39A we can see there’s no fail after flight number around 78.

Pay Load vs Launch Site
![image](https://user-images.githubusercontent.com/32995833/151302280-3cbca125-407c-4a9e-aa15-7523a3130e28.png)
There are no rockets launched for heavypayload mass(greater than 10000) for launch site VAFB-SLC.

Success Rate VS Orbit Type
![image](https://user-images.githubusercontent.com/32995833/151302352-61e49d6c-37a9-4700-909c-a9c14f8a2195.png)
Orbit GEO,HEO,SSO,ES-L1 has the best Success Rate 

Flight Number VS Orbit Type
![image](https://user-images.githubusercontent.com/32995833/151302434-4eb3dbbd-c1c6-40ce-8288-02d8447f2f10.png)
We can see that in the LEO orbit the Success appears related to the number of flights; on the other hand, there seems to be no relationship between flight number when in GTO orbit. 

Pay Load VS Orbit Type
![image](https://user-images.githubusercontent.com/32995833/151302616-2d8f89a3-1b6c-4a49-b87e-1830a01ccda3.png)
With heavy payloads the successful landing or positive landing rate are more for Polar, LEO and ISS.

Launch yearly success trends
![image](https://user-images.githubusercontent.com/32995833/151302747-ebfa2e88-7785-47f2-95ed-978ba29609f0.png)
We can observe that the success rate since 2013 kept increasing till 2020.

Exploratory Data Analysis with SQL
Unique Launch Site
![image](https://user-images.githubusercontent.com/32995833/151302893-1db5dfa8-25fa-4e72-be47-c972c1ff6b52.png)
Show all launch sites

Total payload mass carried by boosters launched by NASA(CRS)
![image](https://user-images.githubusercontent.com/32995833/151303235-de8a4c00-d11b-4fa2-8e5a-af174163c4b2.png)
Total pay load mass carried by NASA (CRS) is 45596 KG

Average Payload Mass by F9 v1.1
![image](https://user-images.githubusercontent.com/32995833/151303286-c83a1b0e-ea51-4a76-83af-751b5d8709fc.png)
Average Payload Mass by F9 v1.1 is 2534 KG

First Successfull Ground Landing Date
![image](https://user-images.githubusercontent.com/32995833/151303422-55147e15-3a52-4c74-b53b-2e7a30f34b66.png)
First Successful Ground Landing Date is on 2015-12-22

Successful Drone Ship Landing with Payload between 4000 and 6000
![image](https://user-images.githubusercontent.com/32995833/151303490-4400ed30-9300-4350-b444-ac1d8e4f22b7.png)

Rank the count of landing outcomes (such as Failure (drone ship) or Success (ground pad)) between the date 2010-06-04 and 2017-03-20, in descending order
![image](https://user-images.githubusercontent.com/32995833/151303924-f8db8bd4-e85c-426d-a872-9106c12f5da7.png)
1. Selecting to display landing outcome and count the amount of landing outcome.
2. With where landing outcome is LIKE 'Failure (drone ship)’ AND 'Success (ground pad)’
3. Group by landing outcome and order by total count by descending order

Launch Sites Proximities Analysis
All launch sites global map markers
![image](https://user-images.githubusercontent.com/32995833/151304123-967df095-b424-40a3-b511-007f0c8eac80.png)
1. All SpaceX launch sites are in the United States coastline.
2. Florida & California

Color labelled markers
![image](https://user-images.githubusercontent.com/32995833/151304302-43294c8f-6e5f-47d4-b863-5e643686557e.png)
![image](https://user-images.githubusercontent.com/32995833/151304340-8f7a55b6-3f88-4c2d-b2d6-6a9d520809a1.png)
Green markers shows successful landings and red marker shows failures

Launch Site distance to landmarks
![image](https://user-images.githubusercontent.com/32995833/151304408-8d4f5f35-8f74-4ca9-9700-81379bdb6253.png)

Success rate (mean) vs Orbit Type
![image](https://user-images.githubusercontent.com/32995833/151301548-b6f60cd0-3471-4d26-9fa9-0050756a254d.png)
From this bar graph we can see that orbit ES-L1, GEO, HEO, SSO has the highest success rate.

Dashboard with Plotly Dash
Pie chart for the launch site with highest launch success ratio 
![image](https://user-images.githubusercontent.com/32995833/151305176-55a5c576-6f4f-4277-81f8-c66fdc4a391d.png)

Predictive Analysis (Classification)
Decision Tree performs the best with 0.8893
![image](https://user-images.githubusercontent.com/32995833/151305192-85f44527-d178-4399-9a66-3c28f9ac256d.png)

Conclusion
1. Orbit ES-L1, GEO, HEO, SSO has highest success rate
2. Success rate for SpaceX launches has been increasing relatively with time and looks like soon they will reach the required target
3. KSC LC-39A has the most successful launches but increasing payload mass seems to have negative impact on success
4. Decision Tree Classifier is the best machine learning model for provided dataset
