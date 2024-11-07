# Hi, guys! Welcome back to my advanced programming journal. 
## Today, I am going to show you an exploratory data analysis (or EDA in other term) on a dataset containing information about popular tracks on most streamed spotify songs 2023 entitled "Spotify's Most Played All-Time: For You". Sounds fun, right?
The idea behind the "For You" title is to create a space where people can reconnect with the music and artists that helped them through 2023—a kind of "For You Playlist" designed for nostalgia. This project is meant to be a way for people to revisit and remember the songs that carried them through challenging times, capturing the music that might otherwise be forgotten but still holds a special place in their hearts, as someone who has been through so much the past year.
### Jessie Mae Domingo of 2ECE-D, at your service! Feel free to use my project as your reference for your new playlist.


#### :warning: Here are the General Objectives that I want to meet as we dive into our Spotify Playlist Exploration.
##### :thought_balloon: Examine the dataset's structure.
To understand its layout, noting any missing values and checking data types. 
This will give an initial sense of the variables available.

##### :thought_balloon: Provide Summary Statistics.
Like the number of streams, release dates, and musical attributes 
(e.g., BPM, danceability) to provide an overview of the data.

##### :thought_balloon: Uses Visualizations.
Such as bar charts, histograms, and scatter plots to identify 
trends and patterns. Ensure that each chart is clearly labeled for easy interpretation.

##### :thought_balloon: Analyze Correlations.
To reveal relationships between different features. Look into connections between 
streams and musical characteristics like tempo, energy, or playlist presence.

##### :thought_balloon: Draw Insights and Make Recommendations.
Based on your analysis regarding tracks, artists, or music trends. 
Highlight elements that may help understand what makes a track popular.

### :envelope_with_arrow: Documentation
##### I've documented the step-by-step process I made in building our new playlist for the year based on genres, moods, and popular patterns. I took into consideration my milestones, realizations, errors encountered, metholodigies in comments within my code, and my successful code with respect to our objectives. Moreover, you'll be seeing my pre-made visualization, and thought processes that shapes this journey from data to discovery.
#### :label: Disclaimer! 
I began this exploratory project on November 4, 2024, and decided to document every error, insight, and successful code solution along the way, recording the date and time for each step. Before consolidating everything into a final file, I created this repository to narrate the journey of completing the project, offering a detailed story of the process from start to finish.

### :round_pushpin: Date Started: November 04, 2024 :mantelpiece_clock: 9:24 PM
##### Starting on Day One! As I reviewed the instructions, I could already tell this project would be time-intensive for I am not a coding gods, just kidding! I began with an initial dataset overview, downloading and loading the CSV file into Jupyter Notebook. Recalling techniques from my work on Experiment 3 with Pandas, I gave it a shot, but quickly ran into an error that made me feel lazy in continuing the code so I tried examining wether I missed any punctuation possible but nothing really changed that's why I closed the application and decided to continue it after my class that day which is LAVA and Elecs Physics.

##### :triangular_flag_on_post: Error 1: Overview of Dataset 
Errors and Realization.ipynb; Cell #2. 
##### import pandas as pd 
##### spotify = pd.read_csv('spotify-2023.csv')
##### spotify['track_name']
###### Even though I uploaded the csv already on the same location of my errors ipynb, I could not call any track name in the spotify-2023.csv file. 

### :round_pushpin: Date Started: November 05, 2024 :mantelpiece_clock: 10:45 PM
#### 


