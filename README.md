# Hi, guys! Welcome back to my advanced programming journal. 
## Today, I am going to show you an exploratory data analysis (or EDA in other term) on a dataset containing information about popular tracks on most streamed spotify songs 2023 entitled "Spotify's Most Played All-Time: For You". Sounds fun, right?
The idea behind the "For You" title is to create a space where people can reconnect with the music and artists that helped them through 2023—a kind of "For You Playlist" designed for nostalgia. This project is meant to be a way for people to revisit and remember the songs that carried them through challenging times, capturing the music that might otherwise be forgotten but still holds a special place in their hearts, as someone who has been through so much the past year.
### Jessie Mae Domingo of 2ECE-D, at your service! Feel free to use my project as a reference for your new playlist.

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

    import pandas as pd 
          
    spotify = pd.read_csv('spotify-2023.csv')
          
    spotify['track_name']
      
###### Even though I uploaded the csv already on the same location of my errors ipynb, I could not call any track name in the spotify-2023.csv file. 

### :round_pushpin: Date Continued: November 05, 2024 :mantelpiece_clock: 10:45 PM
#### After hours of letting procrastination take over, I finally decided it was time to get back to work. I researched the issue and found that encoding='utf-8' couldn’t decode certain special characters in the file. These characters aren't compatible with the default encoding used to read the file, causing the error. To solve this problem, the latin-1 is used because continuation byte is invalid. As a result of this, I came up with the successful code. After this first successful code, I proceeded with the next guide question.

#### :heavy_check_mark: How many rows and columns does the dataset contain?

    import pandas as pd 
    
    spotify = pd.read_csv("spotify-2023.csv", encoding='latin-1')
    
    num_rows,num_columns = spotify.shape
    
    then print.
##### :pencil2: The number of rows in the dataset is: 953
##### :pencil2: The number of columns in the dataset is: 24

#### :heavy_check_mark: What are the data types of each column? 
    data_types = spotify.dtypes
    
    print("Data types of each column:")
    
    print(data_types)
##### :pencil2: Data types of each column:
      track_name              object
      artist(s)_name          object
      artist_count             int64
      released_year            int64
      released_month           int64
      released_day             int64
      in_spotify_playlists     int64
      in_spotify_charts        int64
      streams                 object
      in_apple_playlists       int64
      in_apple_charts          int64
      in_deezer_playlists     object
      in_deezer_charts         int64
      in_shazam_charts        object
      bpm                      int64
      key                     object
      mode                    object
      danceability_%           int64
      valence_%                int64
      energy_%                 int64
      acousticness_%           int64
      instrumentalness_%       int64
      liveness_%               int64
      speechiness_%            int64
      dtype: object

#### :heavy_check_mark: Are there any missing values?

    missing_values = spotify.isnull().sum() 
    
    missing_values = missing_values[missing_values > 0] #
    
    print(f"Missing values in each column: \n{missing_values}")
##### :pencil2: Missing values in each column:
    in_shazam_charts    50
    key                 95
    dtype: int64

### :round_pushpin: Date Continued: November 05, 2024 :mantelpiece_clock: 1:05 AM
#### Moving on to the next guide question, the focus shifted to basic descriptive statistics. I started with calculating the mean, median, and mode, which I had practiced thoroughly in Experiments 1-2 and during a skills test retake. The coding went smoothly with no errors, so I continued to the next question on distribution by year and artist count. This part was manageable, and I decided to enhance it by adding a visualization chart using Matplotlib to better illustrate and support the answers derived from the code. In addition to this, no errors were met upon doing these two codes.

#### :heavy_check_mark: What are the mean, median, and standard deviation of the streams column?

    streams_mean = spotify['streams'].mean() 
    
    streams_median = spotify['streams'].median() 
    
    streams_standard_deviation = spotify['streams'].std() 
    
    
    print(f"Mean of streams: {streams_mean}")
    
    print(f"Median of streams: {streams_median}")
    
    print(f"Standard deviation of streams: {streams_standard_deviation}")
##### :pencil2: Mean of streams: 514137424.93907565
##### :pencil2: Median of streams: 290530915.0
##### :pencil2: Standard deviation of streams: 566856949.0388832

#### :heavy_check_mark: What is the distribution of released_year and artist_count? Are there any noticable trends or outliers?

    import matplotlib.pyplot as plt  
    
    plt.figure(figsize=(15, 10))
    
    plt.scatter(spotify['released_year'], spotify['artist_count'], color='#F765A3', alpha=1)
    
    
    plt.title('Distribution of Released Year and Artist Count')
    
    plt.xlabel('Released Year')
    
    plt.ylabel('Number of Artist')
    
    plt.grid(True)
##### :pencil2: The scatterplot as a result can be seen in my final code file. Spotify's Most Played All-Time.ipynb, Cell number 107.







