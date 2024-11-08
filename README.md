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

##### :memo: Realization: Overview of Dataset
###### UnicodeDecodeError: 'utf-8' codec can't decode bytes in position 7250-7251: invalid continuation byte. I conducted a research for it and the encoding='ut-8' can't decode the special characters included in the file. The file contains characters that are not compatible with the default encoding that is being used to read the file.

        import pandas as pd
        
        spotify = pd.read_csv("spotify-2023.csv", encoding='latin-1')# reading the file of spotify-2023
        
        print (spotify['track_name'])
###### Upon reviewing the csv file, I realized that there are special characters. With moments of researching and experimenting I could not figure it out. But after searching, I used the Latin-1 for reading the csv file I saw in the stackoverflow method.

### :round_pushpin: Date Continued: November 05, 2024 :mantelpiece_clock: 10:45 PM
#### After hours of letting procrastination take over, I finally decided it was time to get back to work. I researched the issue and found that encoding='utf-8' couldn’t decode certain special characters in the file. These characters aren't compatible with the default encoding used to read the file, causing the error. To solve this problem, the latin-1 is used because continuation byte is invalid. As a result of this, I came up with the successful code. After this first successful code, I proceeded with the next guide question.

#### :heavy_check_mark: How many rows and columns does the dataset contain?

        import pandas as pd 
        
        pd.set_option('display.max_rows', None) 
        
        spotify = pd.read_csv("spotify-2023.csv", encoding='latin-1')
        
        
        num_rows,num_columns = spotify.shape # to get the number of rows and columns in the csv file
        
        print(f'The number of rows in the dataset is: {num_rows}') # total number of rows
        
        print(f'The number of columns in the dataset is: {num_columns}') # total number of columns

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

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 1:05 AM
#### Moving on to the next guide question, the focus shifted to basic descriptive statistics. I started with calculating the mean, median, and mode, which I had practiced thoroughly in Experiments 1-2 and during a skills test retake. The coding went smoothly with no errors, so I continued to the next question on distribution by year and artist count. This part was manageable, and I decided to enhance it by adding a visualization chart using Matplotlib to better illustrate and support the answers derived from the code. In addition to this, no errors were met upon doing these two codes.

##### :triangular_flag_on_post: Error 1: Basic Descriptive Statistics

        streams_mean = spotify['streams'].mean() # .mean is used to get the mean.
        
        streams_median = spotify['streams'].median() # .median is used to get the median.
        
        streams_standard_deviation = spotify['streams'].std() # .std is used to get the standard deviation
        
        
        print(f"Mean of streams: {streams_mean}")
        
        print(f"Median of streams: {streams_median}")
        
        print(f"Standard deviation of streams: {streams_standard_deviation}")
        
###### The streams canonot be processed because there is a letter inside the csv file, in the streams column.

#### :heavy_check_mark: What are the mean, median, and standard deviation of the streams column?

        spotify['streams'] = pd.to_numeric(spotify['streams'], errors='coerce') 
        
        
        #errors='coerce' is used as a error handler wherein if the values aren't numbers, it will be ignored.
        
        
        
        streams_median = spotify['streams'].median() # .median is used to get the median.
        
        streams_standard_deviation = spotify['streams'].std() # .std is used to get the standard deviation
        
        
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
##### :pencil2: The scatterplot as a result can be seen in my final code file. Spotify's Most Played All-Time.ipynb, Cell number ____. Examining the yearly release counts provides insight into the music industry's activity levels over time. A high concentration of releases in recent years may suggest that digital platforms have made it easier for artists to distribute their music. With the use of scatter plot determines that the number of artists with multiple releases increases significantly from the 2000s with the highest count in recent year. 

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 2:40 AM
#### After spending a couple of hours coding for the second bullet point, I moved on to the third guide question. Surprisingly, I managed to complete it with almost no issues. While I did encounter minor errors—like a missing closing parenthesis, incorrect capitalization, and typos—they were minor enough that I didn’t add them to my ‘errors and realizations’ notebook, as they didn’t seem significant enough to document.

#### :heavy_check_mark: Which track has the highest number of streams? Display the top 5 most streamed track?

        import matplotlib.pyplot as plt
        
        top_tracks = spotify.nlargest(5, 'streams')[['track_name', 'streams']]
        
        
        plt.figure(figsize=(15,5))
        
        plt.bar(top_tracks['track_name'], top_tracks['streams'], color='#E27BB1')
        
        plt.xlabel("Track Name")
        
        plt.ylabel("Streams")
        
        plt.title("Top 5 Most Streamed Track", fontsize=15)
        
        plt.show()
##### :pencil2: You can view the bar graph visualization in my "Spotify's Most Played All Time" notebook Cell Number _______, as I couldn’t include an image here. In summary, the track with the highest number of streams is Blinding Lights, with the top five most-streamed tracks being Blinding Lights, Shape of You, Someone You Loved, Dance Monkey, and Sunflower from Spider-Man: Into the Spider-Verse.

#### :heavy_check_mark: Who are the top 5 most frequent artists based on the number of tracks in the dataset?

        import matplotlib.pyplot as plt
        
        artist_counts = spotify['artist(s)_name'].str.split(', ').explode().value_counts() 
        
        
        top_artists = artist_counts.nlargest(5) #.nlargest is used to get the highest number of frequent artist
        
        
        plt.figure(figsize=(10, 5))
        
        plt.bar(top_artists.index, top_artists.values, color='#E5A0C6')
        
        plt.xlabel("Artist Name")
        
        plt.ylabel("Number of Tracks")
        
        plt.title("Top 5 Artists by Number of Tracks", fontsize=15)
        
        plt.show()
##### :pencil2: The bar graph visualization can be found in Cell Number ___ of my "Spotify's Most Played All Time" notebook, as I wasn't able to include an image here. In summary, the top 5 Artists by Number of Tracks are: Bad Bunny that has 40 tracks, Taylor Swift that has 38 tracks, The Weeknd that has 37 tracks, SZA that has 23 tracks, and Kenrick Lamar that also has 23 tracks.

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 4:30 AM
#### After wrapping up the third bullet, I took a half-hour study break to recharge. Feeling refreshed, I decided to tackle one more bullet point since it’s my online week and I can sleep in a bit with my classes starting later in the day. After a bit of deliberation, I managed to complete a portion of the temporal trend guide question before calling it a night. I had no error in making this because this is only about making a visualization using matplotlib and a simple analysis of the graph for an explanation to the question provided.

#### :heavy_check_mark: Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year?

        import matplotlib.pyplot as plt
        
        
        plt.figure(figsize=(15, 5))
        
        plt.hist(spotify['released_year'], bins=50)
        
        plt.xlabel('Year')
        
        plt.ylabel('Tracks Released')
        
        plt.title('Tracks Released per Year')
        
        plt.show()
##### :pencil2: The given graph can be seen on my notebook names "Spotify's Most Played All-Time". 

        from 1930 to 1954, there are no tracks released.

        in 1954-1958: 5 tracks released. 
        
        in 1958-1962: 2 tracks released.
        
        in 1962-1966: 3 tracks released.
        
        in 1966-1970: 3 tracks released.
        
        in 1970-1974: 2 tracks released.
        
        in 1974-1978: 2 tracks released.
        
        in 1978-1982: 3 tracks released. 
        
        in 1982-1986: 9 tracks released.
        
        in 1986-1990 there are no tracks released.
        
        in 1990-1994: 4 tracks released.
        
        in 1994-1998: 5 tracks released.
        
        in 1998-2002: 15 tracks released.
        
        in 2002-2006: 7 tracks released.
        
        in 2006-2010: 10 tracks released.
        
        in 2010-2014: 46 tracks released.
        
        in 2014-2018: 62 tracks released.
        
        in 2018-2022: 594 tracks released.
        
        in 2022-present: 175 track released.

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 11:08 AM
#### Welcome to a new day of insights and progress in our documentation journey! In this part, I continued the 4th bullet, Temporal Trends. 

#### :heavy_check_mark: Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

        monthly_counts = spotify['released_month'].value_counts().sort_index()
        
        
        month = {1: 'January', 2: 'February', 3: 'March', 4: 'April', 5: 'May', 6: 'June', 
                     7: 'July', 8: 'August', 9: 'September', 10: 'October', 11: 'November', 12: 'December'}
                     
        
        monthly_counts.index = monthly_counts.index.map(month)
        
        
        
        plt.figure(figsize=(15, 5))
        
        plt.bar(monthly_counts.index, monthly_counts.values)
        
        plt.xlabel('Month')
        
        plt.ylabel('Tracks Released')
        
        plt.title('Tracks Released per Month')
        
        plt.show()

##### :pencil2: The graph is available in my notebook titled "Spotify's All-Time Most Played Tracks."

    On the month of January, there's approximately 135 tracks released which is the highest among all months.
    
    On the month of February, there's 60 tracks relased.
    
    On he month of March, there's approximately 85 tracks released.
    
    On the month of April, there's approximately 65 tracks released.
    
    On the month of May, there's 130 tracks released.
    
    On the month of June, there's approximately 85 tracks released.
    
    On the month of July, there's 60 tracks released.
    
    On the month of August, there's approximately 50 tracks released.
    
    On the month of September, there's approximately 55 tracks released.
    
    On the month of October, there's approximately 88 tracks released.
    
    On the month of November, there's 80 tracks released.
    
    On the month of December, there's approximately 89 tracks released.

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 3:18 PM
#### This part of the project took the most time because I struggled with how to approach the coding, especially since the CSV file lacks a 'genre' column. I thought about asking my professor if it was acceptable to modify the file, but I ultimately refrained, knowing that it wouldn't be appropriate. Additionally, when I started working on the fifth task, I encountered an error right away because I wasn’t sure which type of graph to use, especially given the reference to "correlation." After arranging the error, I immediately thought of a realization upon checking my error and analyzing the result it comes with.

##### :triangular_flag_on_post: Error 1: Genres and Music Characteristics

    sorted_danceability = spotify['danceability_%'].sort_values()
    
    sorted_energy = spotify['energy_%'].sort_values()
    
    dance_energy_corr = spotify['danceability_%'].corr(spotify['energy_%'])
    
    
    plt.scatter(dance_energy_corr)
    
    plt.grid(True)
    
    plt.show()

###### I wanted to see if the correlation could be printed in here but I had a hard time determining the y requirement for scatter plot. But instead if using scatter plot, I used the bar chart.

##### :memo: Realization: Genres and Music Characteristics

    unsorted_dance_energy_corr = spotify['danceability_%'].corr(spotify['energy_%'])
    
    unsorted_valence_acous_corr = spotify['valence_%'].corr(spotify['acousticness_%'])
    
    sorted_dance_energy_corr = spotify['danceability_%'].sort_values().corr(spotify['energy_%'].sort_values())
    
    sorted_valence_acous_corr = spotify['valence_%'].sort_values().corr(spotify['acousticness_%'].sort_values())
    
    
    print(sorted_dance_energy_corr)
    
    print(unsorted_dance_energy_corr)
    
    print(sorted_valence_acous_corr)
    
    print(unsorted_valence_acous_corr)

##### :pencil2: This is the result:

    0.198094848376257
    0.19809484837625715
    -0.08190727483082764
    -0.08190727483082758

###### I realized that sorting the danceability and energy correlation, as well as the valence and acoustic correlation, would not change the output numbers. However, in graphs, the sorted one provides a much cleaner visualization of data.

#### :heavy_check_mark: Examine the correlation between streams and musical attributes like bpm, danceability_% and energy_%. Which attributes seem to influence streams the most?
##### This has 8 different codes that's why I separated them all for better visualization.

#### :one: Correlation for streams and bpm

    streams_bpm_correl = spotify['streams'].corr(spotify['bpm'])
    
    
    plt.scatter(spotify['streams'],spotify['bpm'])
    
    plt.title(f'Streams and Bpm: (r = {streams_bpm_correl})')
    
    plt.xlabel('Score')
    
    plt.ylabel('Percentage of Bpm')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and bpm is -0.0024379081382717954 which indicates a no relation.

#### :two: Correlation for streams and danceability

    streams_danceability_correl = spotify['streams'].corr(spotify['danceability_%'])
    
    
    plt.scatter(spotify['streams'], spotify['danceability_%'])
    
    plt.title(f'Streams and Danceability: (r = {streams_danceability_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Danceability')
    
    plt.grid(True)
    
    plt.show()
    
##### :pencil2: The correlation between streams and danceability is -0.10545688369141913 which indicates a no relation.

#### :three: Correlation for streams and energy

    streams_energy_correl = spotify['streams'].corr(spotify['energy_%'])
    
    
    plt.scatter(spotify['streams'], spotify['energy_%'])
    
    plt.title(f'Streams and Energy: (r = {streams_energy_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Energy')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and energy is -0.02605148836424894 which indicates a no relation.

#### :four: Correlation for streams and valence

    streams_valence_correl = spotify['streams'].corr(spotify['valence_%'])
    
    
    plt.scatter(spotify['streams'], spotify['valence_%'])
    
    plt.title(f'Streams and Valence: (r = {streams_valence_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Valence')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and valence is -0.040831367495159455 which indicates a no relation.

#### :five: Correlation for streams and acousticness

    streams_acousticness_correl = spotify['streams'].corr(spotify['acousticness_%'])
    
    
    plt.scatter(spotify['streams'], spotify['acousticness_%'])
    
    plt.title(f'Streams and Acousticness: (r = {streams_acousticness_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Acousticness')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and acousticness is -0.004484652700684083 which indicates a no relation.

#### :six: Correlation for streams and instrumentalness

    streams_instrument_correl = spotify['streams'].corr(spotify['instrumentalness_%'])
    
    
    plt.scatter(spotify['streams'], spotify['instrumentalness_%'])
    
    plt.title(f'Streams and Instrumentalness: (r = {streams_instrument_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Instrumentalness')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and instrumentalness is -0.044902473175109724 which indicates a no relation.

#### :seven: Correlation for streams and liveness

    streams_liveness_correl = spotify['streams'].corr(spotify['liveness_%'])
    
    
    plt.scatter(spotify['streams'], spotify['liveness_%'])
    
    plt.title(f'Streams and Liveness: (r = {streams_liveness_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Liveness')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and liveness is-0.04833729577983244 which indicates a no relation.

#### :eight: Correlation for streams and speechiness

    streams_speechiness_correl = spotify['streams'].corr(spotify['speechiness_%'])
    
    
    plt.scatter(spotify['streams'], spotify['speechiness_%'])
    
    plt.title(f'Streams and Speechiness: (r = {streams_speechiness_correl})')
    
    plt.xlabel('Streams')
    
    plt.ylabel('Percentage of Speechiness')
    
    plt.grid(True)
    
    plt.show()

##### :pencil2: The correlation between streams and speechiness is -0.1123329964033855 which indicates a no relation.

#### :heavy_check_mark: Is there a correlation between danceablity_% and energy_%? How about valence_% and acousticness_%?

    dance_energy_correl = spotify['danceability_%'].corr(spotify['energy_%']) 
    
    valence_acous_correl =spotify['valence_%'].corr(spotify['acousticness_%']) 
    
    
    plt.scatter(spotify['danceability_%'],spotify['energy_%'])
    
    plt.title(f'Danceability and Energy: (r = {dance_energy_correl})')
    
    plt.xlabel('Percentage of Dance Ability')
    
    plt.ylabel('Percentage of Energy Perceived')
    
    plt.grid(True)
    
    plt.show()
    
    
    plt.scatter(spotify['valence_%'], spotify['acousticness_%']) # Sorted_valence is in the x-axis and the sorted_acousticness is in the y-axis
    
    plt.title(f'Valence and Acousticness Correlation: (r={valence_acous_correl})')
    
    plt.xlabel('Percentage of Valence')
    
    plt.ylabel('Percentage of Acousticness')
    
    plt.grid(True)

    plt.show()

##### :pencil2: Upon seeing the graph, we had an answer for the correlation between energy percent and dance ability which is 0.19809484837625715 which indicates a WEAK relationship between the two. Moreover, the correlation between valence percent and acousticness percent is -0.08190727483082758 which indicates that these two variables have NO relationship at all.

### :round_pushpin: Date Continued: November 06, 2024 :mantelpiece_clock: 11:30 PM
#### After spending hours working through countless trials and errors—often due to minor mistakes or moments of random creativity that sometimes led to syntax errors in the "Gender and Music Characteristics" section. I eventually moved on to tackling the "Platform Popularity" section. This took a bit more time, as I initially struggled with the second question. As a result, I ended up taking several TikTok breaks to recharge. Luckily, there's no massive syntax error that deserves to be seen in my error and realizaation ipynb in this section, only with closing or opening brackets, and my biggest enemy which is capitalization and mispelling.

#### :heavy_check_mark: How do numbers of tracks in spotify_playlist, spotify_charts, and apple_playlist compare?

    spotify_playlists_total = spotify['in_spotify_playlists'].sum()
      
    spotify_charts_total = spotify['in_spotify_charts'].sum()
      
    apple_playlists_total = spotify['in_apple_playlists'].sum()
      
        
    print(f"In Spotify playlists: {spotify_playlists_total}")
      
    print(f"In Spotify charts: {spotify_charts_total}")
      
    print(f"In Apple playlists: {apple_playlists_total}")

##### :pencil2: In Spotify playlists: 4955719
##### :pencil2: In Spotify charts: 11445
##### :pencil2: In Apple playlists: 64625

#### :heavy_check_mark: Which platform seems to be favor the most popular tracks?

    platforms = ['Spotify Playlists', 'Spotify Charts', 'Apple Playlists']
    
    totals = [spotify_playlists_total, spotify_charts_total, apple_playlists_total]
    
    
    plt.figure(figsize=(10, 5))
    
    plt.bar(platforms, totals, color='#E5A0C6')
    
    plt.xlabel('Platform')
    
    plt.ylabel('Total Appearances')
    
    plt.title('Platform that is most used for popular tracks')
    
    plt.show()

##### :pencil2: With the given graph that has visualized in the notebook, we can easily tell that the Spotify playlist is the number one for streaming the popular tracks.

### :round_pushpin: Date Continued: November 07, 2024 :mantelpiece_clock: 10:40 AM
#### It took me quite a while to finish the last task because I burned out while working on the "Genres and Music Characteristics" section. I ended up continuing the work the next morning, pushing through with a tired mind. To make sure I approached the next part effectively, I decided to do some research for inspiration. However, I didn't want to rely only on external sources, so I also reached out to a few friends who’ve taken IT courses for their recommendations on how to tackle this section. Unfortunately, they weren't very experienced with graphing in Python. I tried diving into the last part for my first try but I had errors prior in coding.

##### :triangular_flag_on_post: Error 1: Advanced Analaysis

        import pandas as pd
        
        playlist_chart= ['in_spotify_playlists', 'in_spotify_charts', 
        
                          'in_apple_playlists', 'in_apple_charts', 
                          
                          'in_deezer_playlists', 'in_deezer_charts', 
                          
                          'in_shazam_charts']
                          
        
        spotify[playlist_chart] = pd.to_numeric(spotify[playlist_chart])
        
        print(spotify[playlist_chart])
        
###### pd.numeric is only applicable in single column only. In my case playlist_chart, I am trying to use it in multiple columns that is why it does not work.I need to put it in a listing process first and apply pd.numeric

##### :triangular_flag_on_post: Error 2: Advanced Analaysis

        import pandas as pd
        
        
        playlist_chart= ['in_spotify_playlists', 'in_spotify_charts', 
        
                          'in_apple_playlists', 'in_apple_charts', 
                          
                          'in_deezer_playlists', 'in_deezer_charts', 
                          
                          'in_shazam_charts']
                          
        
        
        spotify[playlist_chart] = spotify[playlist_chart].apply(pd.to_numeric, errors='coerce')
        
        print(spotify[playlist_chart])

###### I encountered another error due to not applying the error handler in playlist_chart. Error occured: File lib.pyx:2391, in pandas._libs.lib.maybe_convert_numeric() ValueError: Unable to parse string "2,445"

### :round_pushpin: Date Continued: November 07, 2024 :mantelpiece_clock: 3:38 PM
#### With so much going on in my mind as I tried to work through this part, I took advantage of some free time during class to continue coding. This time, I encountered a mix of errors and realizations before finally arriving at the correct solution.

##### :memo: Realization: Advanced Analysis

        import pandas as pd
        
        playlist_chart= ['in_spotify_playlists', 'in_spotify_charts', 
        
                          'in_apple_playlists', 'in_apple_charts', 
                          
                          'in_deezer_playlists', 'in_deezer_charts', 
                          
                          'in_shazam_charts']
        
                          
        spotify[playlist_chart] = spotify[playlist_chart].apply(pd.to_numeric)
        
        
        
        artist_totals = spotify.groupby('artist(s)_name')[playlist_chart].sum()
        
        
        
        artist_totals['Total_Appearances'] = artist_totals.sum(axis=0)

###### if I used axis=0 the display in the bar would be none because axis 0 refers in the columns.

#### :heavy_check_mark: Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?

    import matplotlib.pyplot as plt
    
    
    plt.figure(figsize=(12, 6))
    
    plt.bar(spotify['mode'], spotify['streams'])
    
    plt.title('Major vs. Minor')
    
    plt.xlabel('Mode')
    
    plt.ylabel('Average Streams\n')
    
    plt.show()



#### :heavy_check_mark: Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

    import pandas as pd
    import matplotlib.pyplot as plt
    
    
    playlist_chart= ['in_spotify_playlists', 'in_spotify_charts', 
    
                      'in_apple_playlists', 'in_apple_charts', 
                      
                      'in_deezer_playlists', 'in_deezer_charts', 
                      
                      'in_shazam_charts']
    
    
    spotify[playlist_chart] = spotify[playlist_chart].apply(pd.to_numeric, errors='coerce')
    
    
    artist_totals = spotify.groupby('artist(s)_name')[playlist_chart].sum()
    
    
    artist_totals['Total_Appearances'] = artist_totals.sum(axis=1)
    
    
    top10_artist = artist_totals.nlargest(10, 'Total_Appearances')
    
    
    
    plt.figure(figsize=(14, 8))
    
    plt.bar(top10_artist.index, top10_artist['Total_Appearances'], color='#E5A0C6')
    
    plt.xlabel("Artist")
    
    plt.ylabel("Total Appearances")
    
    plt.title("The Total Appearances of top 10 artist")
    
    plt.show()












