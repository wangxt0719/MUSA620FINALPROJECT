## MUSA620 FINAL PROJECT 
### - Super Bowl /Philly Eagle with Philadelphia
## Project Created By Fangnan Du / Xiaotong Wang
This is the ReadMe file for the MUSA 620's final project. The main focus of this project is about the data of Super Bowl 2018. The Super Bowl 2018 was played in Feb 2018 at U.S. Bank Stadium in Minneapolis, between the team New England Patriots and Philadelphia Eagles, and the Philadelphia Eagles finally beats the England Patriots, becoming the winner. The local residents of Philadelphia has huge passion toward the game. As Penn students we can personally feel the graet happiness that the city of Philadelphia has when our local team wins the great game. At the same time, our team has strong interest in people's activity pattern during the game period.
Through collecting the remote sensing data that people's phone generated from Feb 1 to Feb 5, our primary goal will be monitoring the people's movement and travel pattern through the game period inside the border of City Philadelphia. 
## Assignment Steps:
#### - Step 1 
Data Cleaning and Formating (R and ArcMap), geo-locate remote sensing points by three time period 
#### - Step 2
Using multiple ways to properly plot and display the cleaned dataset
#### - Step 3
Building a Leaflet map and Shiny app to allow users to visualize our analysis by visualizing data in the interactive map app

## Data Cleaning
For the initial data, there are total of 24039869 observation records. The initial data contains the longitude and latitude geological information for each remote sensing recording points and the time each point being recorded. 
We have seperated the five date into three time periods and we have plotted people's location in each time segment
- the time section before the game (Feb 1 to Feb 4 18:00 pm); 
- the time section during the game (Feb 4 18:00 pm - 22:00 pm);
- the time section after the game (Feb 4 22:00 pm - Feb 5)

For each time period, we have clipped the data to count points inside the City of Philadelphia only, and we have used the "sample" function in R to extract 20,000 sample points for each time period, because the very initial large data contents will slow the working process.
#### Basic Codes for Data Cleaning and Data Formating
```
during_game<- movement [18028750:18968862,]
before_small <- before[sample(nrow(before_small), 540113), ]
write.csv(before_small, "before_small.csv")
after_game <- movement[18968863:24039869,]
random_after <- after_game[sample(nrow(after_game),940113),]
write.csv(random_after,file = "random_after.csv")
write.csv(during_game,"during_game.csv")
write.csv(random_before,"random_before.csv")
```
## Building the Shiny Interactive App
The finished Shiny app contains three pages: The Animation Heat Map ; The Block Popularity Visualization Map and The Super Bowl Night Popular Club Visualization.

#### Page 1: Philadelphia People's Traveling Pattern Heat Map
![quicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic1.jpg)
In this page, we mapped the location of collected phone devices inside the City of Philadelphia. We use the Heat Map as a good way to display the density of devices in the spatial map. Through giving the background map a dark color, we could clearly observe, during the certain time period, each device's location in the map and people's density for certain region areas. 
In the app interface, users could choose different time period to check people's density for each region in different dates. 

#### Page 2: Block Popularity Visualization
![qicklook]














