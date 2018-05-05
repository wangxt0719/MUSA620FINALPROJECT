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

For each time period, we have clipped the data to count points inside the City of Philadelphia only, and we have used the "sample" function in R to extract 20,000 sample points for each time period, because the very initial large data contents will slow the working process. After the data cleaning and reformating, we have 20000 device geological records for each time segment, total of 60,000 device records usec in the analyzing process.

## Building the Shiny Interactive App
The finished Shiny app contains three pages: The Animation Heat Map ; The Block Popularity Visualization Map and The Super Bowl Night Popular Club Visualization.

#### Page 1: Philadelphia People's Traveling Pattern Heat Map
![quicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic1.jpg)
In this page, we mapped the location of collected phone devices inside the City of Philadelphia. We use the Heat Map as a good way to display the density of devices in the spatial map. Through giving the background map a dark color, we could clearly observe, during the certain time period, each device's location in the map and people's density for certain region areas. 
In the app interface, users could choose different time period to check people's density for each region in different dates. 

#### Page 2: Block Popularity Visualization
In this page section, we choose to use Philadelphia's neighborhood map, sorting the device location data by using neighborhood as our calculation units. There are total of 318 neighborhood area in Philly. User could click each individual neighborhood area to closely check this neighborhood's detailed information - the crime rate; neighborhood population; the income level of this neighborhood... The neighborhood polygon map also follow the time lines - it displays the neighborhood's device density by using three time periods - before game; during the game and after the game. So that users could check the spatial pattern of device density during different time by using the neighborhood information as a reference. 
![qicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic2.jpg)
In the right corner of the page is the correlation scatter plot between different variables - when users choose different display factors from the two list "Select Feature to Plot" and "Select a Visualization Option", the plot will show the correlation plot of the two factors to decide if there's spatial coefficients. 

#### Page 3: Club Popularity
During the game time, people tend to visit bars in the town, gathering around the bar table, holding a beer and watching the exicted games. So we made a hypothesis that the bar will have much more visitors than usual. We have collected the geographic information of the top popular= bars in the City of Philadelphia, and we spatial join the bar area with devices map inside ArcMap, so that we can know during the game time, how many people gathered at which bars in town, and which one is the most popular bars for football fans.
We have dealed with the bar's visitor density by using two spatial scales - the large scale and the small scale.

The Large Scale Bar Map -The location of Most Popular 15 bars in Philadelphia (2018)
![quicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic3.jpg) 

The Small Scale Bar Map - The most popular bars in the Super Bowl night (bars with top 5 dense population)
In the center of each bar circle is the number of devices that fall into the bar area during the game time (how many people stay at the bar to watch the game)
![quicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic4.jpg)

After deciding which bar is the most popular one in the Super Bowl night, we are very curious about people's sentiments when they staying at the most popular bar of the night, so we use the rtweet package in R to collect 1000 tweets about the top 3 popular bars of the night and do a sentiment analysis to each of bars - so that we can see when people mentioned those bars in the Twitter, what's their feeling about the bar. We have extract the tweet text that contains emojis inside, so that we can see what emojis people mostly used when they talked about this bar. We made a table for the top five most popular emojis for each bar, and people can swich the table by choosing from the list. 
:+1:
![quicklook](https://github.com/wangxt0719/MUSA620FINALPROJECT/blob/master/pic5.jpg)


## Codes Behind the Screen 

#### Codes for Data Cleaning and Reformating
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












