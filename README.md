# Group-1-Disney

## Project Overview: 

- In recent years the number of streaming sites has been increasing and with that we have access to an enormous amount of user data. 
- We know a users watch history, movie ratings and what other similar movies or genres they like. 
- Using this dataset, we want to predict user preferences and how to market certain products based on their interests. 
- Our ML model will be providing recommendations based on Disney franchises. But can be used with other streaming datasets as well.

## Why we selected this topic: 
We can use our project in a variety of business scenarios: -
###### Product Placement in stores
- Useful to companies like ToysRus, 
Assumption:  users who like Lion King also likes Toy Story.  Then placing Lion King merchandise beside Toy Story merchandise will result in increased sales. Since both movies fall under Adventure genre, we can suggest ToysRus to include adventure themed merchandise (adventure board games, action figures) and not just dolls. The outcome can also help in planning the placements of merchabndising alongside and planning the store outlook.
###### Customer Segmentation: 
- We can segment our customers into like minded groups. We can market more efficiently and target the right customers.
Assumption:  If a particular cluster of customers love the adventure genre, we can advertise more adventure themed merchandise or movies to them.
###### Disney Park revenue: 
- We can use our dataset to make informed decisions about the Disney Park rides 
- We can put Lion King & Toy Story themed rides beside each other. 
- In addition, as the movie genre was adventure. The rides can be designed to be more thrilling instead of easy going, as they will appeal more to an adventurous demographic.

## Decomposing the Task

Thinking from business point of view. Example of what our system can produce: -

1. Customer Segmentation

* With the data we have, we can “discover” user preferences and toys sales, and therefore use this information for ToysRus toy product placement. Eg: Lion King merchandise beside Toy Story merchandise as we discovered that people who like Lion King also like Toy Story. If the genre is both “Adventure”, then we can also suggest that the toy merchandise include something like “adventure game” and not just soft toys.

* With the customer segmentation, Disney new releases can be advertised on IMDB & Rotten Tomatoes to "look alike" customers. Therefore, Disney is spending the marketing ads funds in a targeted manner.

* Disney Park Revenue: - the same can be said about park. Fast pass for Lion King & Toy Story as the same people like both movies. OR let’s say both are under “Adventure” genre, then we can say, the new Toy Story in Disney Park should be an adventure ride and not like “It’s A Small World” ride.

* Disney Park Revenue: - We can use our dataset to make informed decisions about the Disney Park rides. We can put Lion King & Toy Story themed rides beside each other. In addition, as the movie genre was adventure. The rides can be designed to be more thrilling instead of easy going, as they will appeal more to an adventurous demographic.

## Questions the team hopes to answer with the data

1. How can we utilize users watch history data to help other companies with product placement?
2. Can we accurately predict user preferences and help companies market more effectively? Why or why not?

## Data Collection / Identify Data Source

#### Data Sources
- kaggle.com
Walt Disney Character Dataset
Contains data about Walt Disney characters
- kaggle.com
Walt Disney Movies
Walt Disney Movie dataset
- GroupLens
GroupLens Research has collected and made available rating data sets from the MovieLens web site ( The data sets were collected over various periods of time, depending on the size of the set.
- IMDB, the-numbers.com, Wikipedia & get the MovieLens movies.csv

## Data Preparation / Data Retrieval plan / Assemble and Clean Data

(NEED TO IMPROVE THIS PART)
- EDA: Exploratory Data Analysis
* Disney dataset: https://www.kaggle.com/maricinnamon/walt-disney-character-dataset 
- Data Preparation
- Data Specific Method: Content-based filtering
- 
#### Technical Flow Diagram
![Disney_Techical_Diagram](https://user-images.githubusercontent.com/93067732/161170074-14f3234e-5f84-410b-b2b8-eabd703e5680.png)

## Database Extract, Transform and Load
After exploration the data initially. We found that the data was incomplete, messy and did not yield good results after parsing through our first ML model. Furthermore, we have more than one business questions, therefore we need to implement more than one ML models to answer those questions. 
Due to the above, we decided to pivot and made the decision to scrape for the information from IMDB and Wikipedia for the most comprehensive and latest dataset.
With the newly scraped data from IMDB, we were able to use imdbId as our Primary Key and Foreign Key. This is also future proof as this imdbId will match to IMDB when we scrape for new information from IMDB in the future while eliminating potential data duplication. Therefore, the data integrity is preserved. 


![IMDB_scrape_code_snippet (1)](https://user-images.githubusercontent.com/93067732/163074976-bee17d7d-3d22-44f0-be28-33b509cced4b.png)

## ERD 

![Disney ERD](https://user-images.githubusercontent.com/93067732/163077392-571dd0fa-b0d5-4fb2-bcb4-bd115ccc7954.png)

## SQL

![Database_SQL_Join](https://user-images.githubusercontent.com/93067732/163075178-8634b72d-a200-453c-ae94-6442baf200a0.png)

#### Connect to SQL

![SQLAlchemy_Sending_Data](https://user-images.githubusercontent.com/93067732/163075291-2ad3c097-312d-4012-97ad-c3bce89dcb07.png)


#### SQL SCHEMA

```
CREATE TABLE movies (
	imdb_id varchar   NOT NULL PRIMARY KEY,
	title varchar   NOT NULL,
	year int   NOT NULL,
	rated varchar   NOT NULL,
	released date   NOT NULL,
	runtime int   NOT NULL,
	imdb_rating float   NOT NULL,
	imdb_votes int   NOT NULL,
	genres varchar   NOT NULL
	);

CREATE TABLE language_country (
	lc_id varchar   NOT NULL PRIMARY KEY,
	imdb_id varchar   REFERENCES movies (imdb_id),
	language archer   NOT NULL,
	country varchar   NOT NULL
	);

CREATE TABLE awards (
	awards_id varchar   NOT NULL PRIMARY KEY,
	imdb_id varchar   REFERENCES movies (imdb_id),
	awards archer   NOT NULL
	);

CREATE TABLE metascore (
	ms_id varchar   NOT NULL PRIMARY KEY,
	imdb_id varchar   REFERENCES movies (imdb_id),
	metascore varchar   NOT NULL
	);

CREATE TABLE gross_revenue (
	rev_id varchar   NOT NULL PRIMARY KEY,
	imdb_id varchar   REFERENCES movies (imdb_id),
	total_gross int   NOT NULL,
	inflation_adjusted_gross int   NOT NULL
	);
```

## Presentation

We initiated the presentation data in Google slides.
The presentation draft can be found in the following link below: 

https://docs.google.com/presentation/d/1bXQ0Cq8p2YGSmovvJoc0RRNRafFfXTP-7OJgANwXNB8/edit

## Tableau Dashboard

We created Tableau to give following visualizations, which helped us with greater insights of data and also improve our presentation that can be easily understandable by the investors.  

The Tableau dashboard link is below:

Disney's Revenue by Business Line - Dashboard:

https://public.tableau.com/app/profile/akinfolarin8600/viz/DisneysRevenuebyBusinessLine-Dashboard/DisneysRevenuebyBusinessLineDashboard?publish=yes

<img width="1174" alt="image" src="https://user-images.githubusercontent.com/93067732/161837263-029dc0b9-04d4-446a-a85d-b6f626b6b7b6.png">

### The Tableau dashboard link is below

Disney's Movies Revenue Dashboard:

https://public.tableau.com/app/profile/akinfolarin8600/viz/DisneyRevenueStory/DisneyRevenueStory?publish=yes

<img width="1103" alt="image" src="https://user-images.githubusercontent.com/93067732/161837388-9e4f60d2-5098-4e0d-bce9-2f559971bbc5.png">

## Machine Learning

We intend to use a Unsupervised Machine Learning model, specifically K-means clustering. We have a couple of questions to answer using the ML model, and know that by using historical data, we will see a relationship between a movies, user data, revenue etc to predict the user preference trends. 

### K-means Clustering Model

![K-Means Clustering](https://user-images.githubusercontent.com/93067732/163075597-9096c509-6624-4a32-9ad1-fab52de665be.gif)


#### Analysis & Visualization
While we have completed our first ML model using K-means clustering, while it fulfills what we need, one of the drawback of K-Means Cluster is the inability to understand why the different movies have been cluster together. Therefore we have decided to add another ML model to support and strengthen our initial K-means Cluster model. 

#### Elbow curve

![Elbow_Curve_Inertia](https://user-images.githubusercontent.com/93067732/163075460-8d1be328-fded-4476-9317-9ec77114b972.png)


### Nearest Neighbour
K Nearest Neighbour (KNN) algorithm can be used for both classification and regression problems. The KNN algorithm uses ‘feature similarity’ to predict the values of any new data points.

![Item_Based_KNN](https://user-images.githubusercontent.com/93067732/163075912-e0767b43-964e-4101-ad1d-ea6bfd7db3de.gif)


### Feature Engineering

From the dataset collected, we have selected these 4 values as our input features:
1. Genres
2. MPAA Ratings
3. IMDB Average Rating
4. IMDB Total Votes (which shows how many people have rated the movie)

Firstly, the dataset we have is imbalance and noisy. Therefore during data preprocessing stage, the outliers were binned for better performance.
* Genres was reduced from 29 to 22
* MPAA Rating was reduced from 14 to 8

In order for our ML model to process these features, we also need to encode and scale the features, please see below for what we did with each feature:
1. Genres - OneHotEncoder
2. MPAA Ratings - LabelEncoder
3. IMDB Average Rating - MinMaxScaler
4. IMDB Total Votes - MinMaxScaler


## Team Communication and Project Methodology

- Team Slack Channel
- Individual Slack Chat
- WhatsApp group
- Google Share Drive
- Zoom meetings
- Agile - Scrum

