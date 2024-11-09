<h1 align="center">Python - Exploratory Data Analysis on Spotify 2023 Dataset
    
---

## Introduction

-  ### Project Overview

This project aims to **$\color{violet}{uncover\ the\ secrets\ behind\ music\ popularity}$** by conducting an exploratory data analysis (EDA) of the Most Streamed Spotify Songs 2023 dataset. The analysis will be conducted **$\color{violet}{using\ Python\ libraries}$** to process and visualize the data,providing a structured and insightful exploration of the dataset.

> [!TIP]
> To enhance your coding experience you can download the dataset available on Kaggle and following the code provided as you explore this repository. You can download the dataset [here](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023).

-  ### Objective
1. **$\color{crimson}{Explore\ the\ Dataset}$**
2. **$\color{crimson}{Summarize\ statistics}$** to give an overview of key metrics.
3. Use **$\color{crimson}{visual\ representations}$** to uncover trends and patterns.
4. **$\color{crimson}{Investigate\ correlations}$**  between specific columns.
5. **$\color{crimson}{Provide\ insights}$** or recommendations based on the analysis and interpretations gathered.

---
## Table of Contents
- [Introduction](#Introduction)
    - [Project Overview](#Project-Overview)
    - [Objective](#Objective)
- [Table of Contents](#Table-of-Contents)
- [Dataset Overview](#Dataset-Overview)
    - [Dataset Structure](#Dataset-Structure)
    - [Rows and Columns](#Rows-and-Columns)
- [Data Preprocessing](#Data-Preprocessing)
     - [Data Types](#Data-Types)
     - [Non-null Counts](#Non-null-Counts)
- [Key Insights and Analysis](#Key-Insights-and-Analysis)
    - [Basic Descriptive Statistics](#Basic-Descriptive-Statistics)
        - [Stream Stats](#Stream-Stats)
        - [Release Trends](#Release-Trends)
        - [Artist Frequency](#Artist-Frequency)
    - [Top Performers](#Top-Performers)
        - [Most Streamed Tracks](#Most-Streamed-Tracks)
        - [Top Artists](#Top-Artists)
- [Temporal Trends in Music Releases](#Temporal-Trends-in-Music-Releases)
    - [Tracks Released Over Time](#Tracks-Released-OverTime)
    - [Top Release Years](#Top-Release-Years)
- [Musical Attributes and Popularity](#Musical-Attributes-and-Popularity)
    - [What Makes a Hit?](#What-Makes-a-Hit?)
    - [The Rhythm and the Beat](#The-Rhythm-and-the-Beat)
    - [Mood Tones](#Mood-Tones)
- [Audience Preferences](#Audience-Preferences)
- [Advanced Analysis](#Advanced-Analysis)
    - [Key and Mode Analysis](#Key-and-ModeAnalysis)
    - [Frequent Artists in Playlists](#Frequent-Artists-in-Playlists)
- [Conclusion](#Conclusion)
- [License](#License)
- [Author](#$\mathbf{\color{lightblue}{Author}}$)
- [Version History](#Version-History)

---
## Dataset Overview
#### Before delving into the analysis, this section provides the overview of the dataset's structure and content, which is essential for analyzing the trends and patters.
---
- ### Dataset Structure

> [!IMPORTANT]
> Download the Most Streamed Spotify Songs 2023 dataset.
> * The following .csv file can be downloaded [here](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023)
  >###
>    NOTE: 
  >   Ensure that the following file is saved in the same directory as your Jupyter notebook so that the notebook can locate it.

#### After downloading the file, **$\color{lightblue}{utilize\ the\ following\ import\ conventions}$** to access the various libraries that will be used throughout the program.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

#### To enable the code to read the dataset, using encoding='latin-1' will help load the .csv file, and this function will store the data in the variable df.

```python
df = pd.read_csv('spotify-2023.csv', encoding='latin-1')
df
```
##### Table 1.1. The Most Streamed Spotify Songs 2023 dataset.
![image](https://github.com/user-attachments/assets/e54e02a3-15f8-4a55-b454-a7d4c5770009)

- ### Rows and Columns 
#### Table 1.0 provides a comprehensive overview of **$\color{lightgreen}{953}$** of Spotify's most-streamed songs with **$\color{lightgreen}{24}$** columns, containing their release dates, musical attributes, and platform performance, which will be used for further analysis.
  
---
## Data Preprocessing
#### Given the large amount of data, checking each column individually for completeness is challenging. This section outlines each column's data type and identifies any missing values to ensure the dataset's quality and reliability.
---
-  ### Data Types
To better understand the dataset, identifying the data types of each column is essential for selecting the most effective Python operations. This section provides a detailed breakdown of the dataset's structure.

Using dtypes function from pandas library, this will help indicate what are the data type stored in each column.

```python
data_types = df.dtypes
print("Data Types of Each Column:\n", data_types)
```

##### Table 2.0. The Column Data Types Overview.
| **$\color{Pink}{Column\ Name}$**     | **$\color{Pink}{ Data\ Type  }$**      |   
| ------------- |:-------------:| 
| track_name                        |    Object     | 
| artist(s)_name           |      Object        | 
| artist_count           |     int64     | 
| released_year            |     int64     | 
| released_month            |     int64      | 
|released_day           |     int64     | 
| in_spotify_playlists            |     int64     | 
| in_spotify_charts            |     int64      | 
| streams            |    Object      | 
| in_apple_charts           |    int64     | 
| in_apple_playlists          |     int64     | 
| in_deezer_playlists           |     Object    | 
| in_deezer_charts           |     int64     | 
|in_shazam_charts          |     Object   | 
| bpm          |   int64     | 
| key          |     Object      | 
| mode         |     Object     | 
|danceability_%           |    int64      | 
| valence_%|     int64      | 
| energy_%            |    int64      | 
| acousticness_%           |    int64      | 
| instrumentalness_%          |     int64      | 
| liveness_%          |     int64    | 
| speechiness_%          |    int64      | 

Table 2.0 indicates that the dataset includes two primary data types: **$\color{Pink}{int64\ for\ 17\ columns}$** containing numerical values, and **$\color{Pink}{object\ for\ 7\ columns }$** containing text or categorical information.

-  ### Non-null Counts
Recognizing missing values is key to ensuring data accuracy and minimizing potential errors. Here, a table displays the count of values present in each column.

By employing the .isnull() function, this code checks for missing values, and then the .sum() function totals all the number of missing values in each column. The outcome is stored in the variable missing_values.

```python
missing_values = df.isnull().sum()
print("\nMissing Values in Each Column:\n", missing_values)
```

This function displays the total missing values for each column.
```python
total_missing = missing_values.sum()
print(f"\nTotal Missing Values in the Dataset: {total_missing}")
```

##### Table 2.1. The Summary of Missing Values per Column.
| **$\color{Pink}{Column\ Name}$**     | **$\color{Pink}{ Number\ of\ Missing\ Values  }$**      |   
| ------------- |:-------------:| 
| track_name                        |   0     | 
| artist(s)_name           |     0       | 
| artist_count           |     0    | 
| released_year            |     0     | 
| released_month            |     0     | 
|released_day           |    0     | 
| in_spotify_playlists            |    0    | 
| in_spotify_charts            |   0      | 
| streams            |    0      | 
| in_apple_charts           |   0   | 
| in_apple_playlists          |     0    | 
| in_deezer_playlists           |     0    | 
| in_deezer_charts           |     0    | 
|in_shazam_charts          |     50  | 
| bpm          |   0    | 
| key          |    95     | 
| mode         |     0    | 
|danceability_%           |    0     | 
| valence_%|     0     | 
| energy_%            |    0     | 
| acousticness_%           |   0     | 
| instrumentalness_%          |     0     | 
| liveness_%          |    0    | 
| speechiness_%          |   0      | 

As shown in Table 2.1, the dataset has a **$\color{Pink}{total\ of\ 145\ missing\ values }$** across all columns, with the highest number of missing values found in  **$\color{Pink}{in_shazam_charts\ and\ key.}$** 

---
## Key Insights and Analysis
#### This part dives into an in-depth analysis of the dataset, exploring key statistics, standout tracks, and release trends to uncover noticeable patterns and unique insights.
---
## Basic Descriptive Statistics
- ### Stream Stats
 A statistical breakdown of stream counts, where the calculated mean, median, and standard deviation of the streams column is presented.

Given that the data type of the streams is an object, we can convert it to numeric using pd.to_numeric. This allows us to calculate the mean, median, and standard deviation using the .mean() function.

```python
mean_streams = pd.to_numeric(df['streams'], errors='coerce').mean()
median_streams = pd.to_numeric(df['streams'], errors='coerce').median()
std_streams = pd.to_numeric(df['streams'], errors='coerce').std()
```

This function displays the calculated mean, median, and standard deviation from the previous function.

```python
print("Descriptive statistics for streams")
print("Mean: ", mean_streams)
print("Median: ", median_streams)
print("Standard deviation: ", std_streams)
```
### Table 3.0. The Descriptive statistics for streams
| Metric             | Value                |
|--------------------|----------------------|
| $\mathbf{\color{Red}{Mean}}$  | 514137424.93907565      |
| $\mathbf{\color{orange}{Median}}$       | 290530915.0      |
| $\mathbf{\color{yellow}{Standard Deviation}}$ | 566856949.0388832 |

- ### Release Trends
This visualization offers a snapshot of the annual release trends.

```python
sns.set(style="whitegrid")
plt.figure(figsize=(10, 6))
sns.histplot(df["released_year"], bins=5, color="darkred")
```

```python
plt.xlabel("Released Year", fontsize=12)
plt.ylabel("Number of Tracks", fontsize=12)
plt.title("Distribution of Tracks Released Each Year", fontsize=14, fontweight="bold")
```

```python
eak_year = df["released_year"].value_counts()
max_count = peak_year.max()
peak_year = peak_year[peak_year == max_count].index.tolist()  # List of years with peak values
plt.axvline(x=peak_year, color='violet', linestyle='--', label=f'Peak Year: {peak_year}')
```

Dsiplays visual representation of how distribution of tracks were released each year.
```python
plt.legend(title="Peak Year")
plt.show()
```
### Figure 1.0. 
![image](https://github.com/user-attachments/assets/cd059c52-aed6-4fcc-895b-bc8de95a97da)


- ### Artist Frequency
Here, illustrate a plot that reveals the extent of collaboration in the music industry, showing the number of artists per track.

```python
sns.set(style="whitegrid")
plt.figure(figsize=(8, 6))
sns.countplot(y="artist_count", hue="artist_count", data=df, palette="Spectral", dodge=False, legend=False)
```


```python
plt.ylabel("Number of Artists per Track", fontsize=12)
plt.xlabel("Number of Tracks", fontsize=12)
plt.title("Distribution of Artist Count for Each Track", fontsize=14, fontweight="bold")
plt.show()
```

### Figure 1.1. 
![image](https://github.com/user-attachments/assets/b63d3bb1-2a0c-4e87-b1d4-3a9c7183351e)

---
##  Top Performers
- ### Most Streamed Tracks
This section highlights the top-performing tracks, revealing the true music sensations.

Since the 'streams' column is an object data type, it is necessary to convert it to numeric in order to use the nlargest function, which will be utilized to provide the top 5 most streamed tracks.

```python
df['streams'] = pd.to_numeric(df['streams'], errors='coerce')
most_streamed_tracks = df[['track_name', 'streams']].nlargest(5, 'streams')
```

```python
print("Top 5 Most Streamed Tracks:\n", most_streamed_tracks )
```

### Table 4.0. The Top 5 Most Streamed Tracks.
| $\mathbf{\color{Red}{#}}$       | $\mathbf{\color{Red}{Track\ Name}}$     |  $\mathbf{\color{Red}{Streams}}$       |  
| ------------- |:-------------:| :-------------:|
| 1          |     Blinding Lights      | 3.703895e+09|   
| 2          |     Shape of You    |3.562544e+09|   
|3            |     Someone You Loved      |  2.887242e+09|   
| 4            |     Dance Monkey      |  2.864792e+09|   
| 5            |    Sunflower - Spider-Man: Into the Spider-Verse      |2.808097e+09|   

- ### Top Artists
This section highlights the top 5 artists with the most tracks in the dataset, showcasing their popularity and influence.

By using the .value_counts() function, the code counts the frequency of each artist in the 'artist(s)_name' column. Then, by applying the .head(5) function, it gets the top 5 most frequently appearing artists based on the number of tracks.

```python
top_artists = df['artist(s)_name'].value_counts().head(5)
print("\nTop 5 most Frequent Artists by Number of Tracks:\n", top_artists)
```

### Table 4.1. The Top 5 most Frequent Artists by Number of Tracks.
|$\mathbf{\color{lightblue}{Artist\ Name}}$       | $\mathbf{\color{lightblue}{Track\ Count}}$     | 
| ------------- |:-------------:| 
| Taylor Swift        |     34     | 
| The Weeknd        |    22  | 
|Bad Bunny           |    19     |  
| SZA                |    19      |  
| Harry Styles          |    17     |

#### Table 4.1 reveals the collaborative dynamics within the music industry, showcasing how many times each unique combination of artists appears in the dataset, focusing on counting the frequency of artist pairings and group collaborations.

---
## Temporal Trends in Music Releases
#### To identify the golden era of music releases, we delved deeper into the data. By analyzing the distribution of releases across different years and months, we aim to uncover the peak years in the music industry.
---

### Tracks Released Over Time
The first stop in this section takes a deeper dive into analyzing the year that marked significant peaks in music releases, which identifies the key year that may have influenced the popularity and evolution of music over time.

Stored in the variable releases_per_year, the groupby() function groups the dataset that is in the values in the 'released_year' column. After grouping the values, using the .size() function it wil helps count the number of tracks released in each year.

```python
releases_per_year = df.groupby('released_year').size()
```

To analyze trends, the plt.figure() function is used to create a plot based on the values stored in the releases_per_year variable.

```python
plt.figure(figsize=(10, 6))
releases_per_year.plot(kind='area', color='pink', alpha=1)
```

Utilizing the .idxmax() function, this will find the year with the highest value in the graph.
```python
max_year = releases_per_year.idxmax() 
```
 

By using the .max() function, this will identify the highest value plotted in the graph.
```python
max_value = releases_per_year.max() 
```


This function will display the maximum values along with the corresponding year.
```python
plt.scatter(max_year, max_value, color='darkblue', s=100, zorder=5, label='Max Releases')
```

On the other hand, the following function helps the user understand the graph better by adding titles, x-labels, and y-labels.
```python
plt.title('Number of Tracks Released per Year (Max: ' + str(max_value) + ' in ' + str(max_year) + ')', fontsize=16, fontweight='bold')
plt.xlabel('Year')
plt.ylabel('Number of Tracks')
plt.xticks(rotation=45)
plt.grid(axis='y')
```

Displays the graph along with its legend.
```python
plt.legend()
plt.show()
```

### Figure 2.0. 
![image](https://github.com/user-attachments/assets/5f9f3b41-e813-427f-8ace-05d8547d6b79)

---

### Track Released per Month
Next, we investigate the seasonal trends in music releases, identifying the months that are most popular for artists to showcase their new tracks.

Similar to the previous code, the .value_counts() function is used to count the number of tracks released per month Then, by utilizing .sort_index(), it sorts the values by their index.
```python
releases_per_month = df['released_month'].value_counts().sort_index()
```

This function improves the user's comprehension of the graph by including titles, x-axis labels, and y-axis labels.
```python
plt.figure(figsize=(8, 6))
sns.barplot(x=releases_per_month.index, y=releases_per_month.values, palette="rainbow")
plt.title('Number of Tracks Released per Month', fontsize=16, fontweight='bold')
plt.xlabel('Month', fontsize=14)
plt.ylabel('Number of Tracks', fontsize=14)
plt.xticks(ticks=range(0,12), labels=['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'])
```

Displays the gathered values on the graph
```python
plt.show()
```

### Figure 2.1. 
![image](https://github.com/user-attachments/assets/587d4e85-59e2-42eb-8285-ea6aefee15ab)

--- 
## Musical Attributes and Popularity
In this section, we’ll take a look at what makes each track stand out and reach the top of the Spotify charts. Here, you’ll uncover the unique qualities that make these songs fan favorites, examining the connections between their musical attributes and streaming numbers. By understanding these factors, we can see why certain songs get so many streams and become big hits.
---

### What Makes a Hit?
#### Ever wonder how a song rockets to Spotify's top? Here, you can uncover the musical ingredients that make tracks climb the charts!

Stored in the correlation_with_streams variable, the .corr() function helps to find the correlation between the selected columns.
```python
correlation_with_streams = df[['streams', 'bpm', 'danceability_%', 'energy_%', 'valence_%',	'acousticness_%']].corr()
print("Correlation among Streams:\n", correlation_with_streams['streams'], "\n")
```

Aside from calculating the correlation, graphing the values aids in analyzing the relationship between them. Therefore, by using the plt function it provides visual representation of these values.
```python
plt.figure(figsize=(18, 15))
```

This graph shows the correlation between Streams and BPM.
```python
plt.subplot(2, 3, 1)
sns.regplot(x='bpm', y='streams', data=df, scatter_kws={'color': 'green'}, line_kws={'color': 'darkblue'})
plt.title('Streams vs. BPM')
```

This function illustrates the correlation between Streams and Danceability.
```python
plt.subplot(2, 3, 2)
sns.regplot(x='danceability_%', y='streams', data=df, scatter_kws={'color': 'orange'}, line_kws={'color': 'darkblue'})
plt.title('Streams vs. Danceability')
```

Provides a visual representation of the relationship between Streams and Energy.
```python
plt.subplot(2, 3, 3)
sns.regplot(x='energy_%', y='streams', data=df, scatter_kws={'color': 'yellow'}, line_kws={'color': 'darkblue'})
plt.title('Streams vs. Energy')
```

The graph depicts the connection between Streams and Valence.
```python
plt.subplot(2, 3, 4)
sns.regplot(x='valence_%', y='streams', data=df, scatter_kws={'color': 'pink'}, line_kws={'color': 'darkblue'})
plt.title('Streams vs. Valence')
```

Illustrates the correlation among Streams and Acousticness
```python
plt.subplot(2, 3, 5)
sns.regplot(x='acousticness_%', y='streams', data=df, scatter_kws={'color': 'violet'}, line_kws={'color': 'darkblue'})
plt.title('Streams vs. Acousticness')
```

Displays the Scatter Plot
```python
plt.show()
```
### Table 5.0. The Correlation of Musical Attributes among Streams
| Attribute        | Correlation              |
|------------------|--------------------------|
| streams          | 1.000000                 |
| bpm              | -0.002438                |
| danceability_%   | -0.105457                |
| energy_%         | -0.026051                |
| valence_%        | -0.040831                |
| acousticness_%   | -0.004485                |

Figure 3.0. The Correlation among Streams using Visual Representation
![image](https://github.com/user-attachments/assets/6909bec8-ec23-49dc-8449-fb504cc40d84)
![image](https://github.com/user-attachments/assets/def7353d-0066-4ed3-9bd9-6ca3af667323)

--
 
### The Rhythm and the Beat
#### Next, let's dive into the rhythm and beat! Calculating and plotting the correlation between Danceability and Energy to explore how these two atrributes come together and impact each other.

Similarly, the .corr() function calculates the correlation between the selected columns. Here, Correlation between Danceability and Energy.
```python
correlation_dance_energy = df['danceability_%'].corr(df['energy_%'])
print(f"Correlation between Danceability and Energy: {correlation_dance_energy:.2f}")
```

The correlation between Danceability and Energy is calculated to be  **$\color{orangered}{0.20}$** .

To better analyze the relationships between the selected columns,by utlizing the plt function this creates visual representation of their correlations.
```python
plt.figure(figsize=(12, 6))
```

Scatter plot for Danceability and Energy.
```python
plt.subplot(1, 2, 1) 
sns.regplot(x='danceability_%', y='energy_%', data=df, scatter_kws={'color': 'skyblue'}, line_kws={'color': 'darkblue'})
plt.title('Danceability vs Energy', fontsize=16)
plt.xlabel('Danceability (%)', fontsize=14)
plt.ylabel('Energy (%)', fontsize=14)
```

Displays the graph.
```python
plt.show()
```

Figure 3.1. 
![image](https://github.com/user-attachments/assets/9abb3a34-37f7-4498-a0a1-89c8f140ed9c)

---

### Mood Tones
#### Beyond the rhythm and beat, the mood of the track adds an extra spice. Here, we'll explore the correlation between Valence and Acousticness to see how these elements contribute to each other.

Likewise, we can use the .corr() function to find the relation between Valence and Acousticness.
```python
correlation_valence_acousticness = df['valence_%'].corr(df['acousticness_%'])
print(f"Correlation between Valence and Acousticness: {correlation_valence_acousticness:.2f}\n")
```

The correlation between Valence and Acousticness is computed to be $\color{orangered}{-0.08}$.

To better analyze the relationships between the selected columns,by utlizing the plt function this creates visual representation of their correlations.
```python
plt.figure(figsize=(12, 6))
plt.subplot(1, 2, 2)
sns.regplot(x='valence_%', y='acousticness_%', data=df, scatter_kws={'color': 'pink'}, line_kws={'color': 'darkred'})
plt.title('Valence vs Acousticness', fontsize=16)
plt.xlabel('Valence (%)', fontsize=14)
plt.ylabel('Acousticness (%)', fontsize=14)
plt.show()
```

Figure 3.2.
![image](https://github.com/user-attachments/assets/09b671a3-e072-4753-8ea2-8ce9957e180e)


---
## Audience Preferences
#### As we dive further into the data, we start to uncover where tracks are making their mark across different platforms. Let’s take a closer look at the trends and see which platform the audience's preferred the most!

By utilizing the .sum() function, it sums the values of the selected columns, which helps with comparison.
```python
popular_tracks = df[['in_apple_playlists', 'in_spotify_playlists','in_spotify_charts',  'in_deezer_playlists', 'in_deezer_charts']].sum()
print("The most Popular Tracks:\n", popular_tracks)
```
### Table 6.0. The Correlation of Musical Attributes among Streams
| Track Platform           | Popularity Count |
|--------------------------|------------------|
| in_apple_playlists       | 64625.0          |
| in_spotify_playlists     | 4955719.0        |
| in_spotify_charts        | 11445.0          |
| in_deezer_playlists      | 95913.0          |
| in_deezer_charts         | 2541.0           |

Sum the values for each platform
```python
popular_tracks = df.sum()

```

Create a DataFrame for plotting
```python
platforms = pd.DataFrame({
    'Platform': popular_tracks.index,
    'Track Count': popular_tracks.values
})
```

This function adjusts the size and adds design elements to the graph.
```python
plt.figure(figsize=(12, 6))
sns.set(style="whitegrid")
palette = sns.color_palette(["pink", "violet", "lightgreen", "orangered", "blue"])
graph = sns.barplot(data=platforms, x='Platform', y='Track Count', palette=palette, edgecolor='black')
```

The following functions are used to add labels to the graph.
```python
plt.xlabel('Platform', fontsize=14, fontweight='bold')
plt.ylabel('Number of Tracks', fontsize=14, fontweight='bold')
plt.title('Popular Tracks Across Platforms', fontsize=16, fontweight='bold', color='darkred')
plt.grid(axis='y', linestyle='--', alpha=0.7)
```

Show the plot
```python
plt.show()
```

Figure 4.0.
![image](https://github.com/user-attachments/assets/2cc78d87-f77c-47c3-bcd0-feb33e963dd6)

---
## Advanced Analysis
####

---

### Key and Mode Analysis
####

Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?
```python
streams_same_key = df.groupby(['key', 'mode'])['streams'].mean().reset_index()
print("Average Streams by Key and Mode:\n", streams_same_key, "\n")
```

Table 7.0 The Average Streams by Key and Mode

| Key  | Mode  | Average Streams        |
|------|-------|------------------------|
| A    | Major | 4.019603e+08           |
| A    | Minor | 4.173906e+08           |
| A#   | Major | 6.275336e+08           |
| A#   | Minor | 4.849231e+08           |
| B    | Major | 4.363336e+08           |
| B    | Minor | 5.825110e+08           |
| C#   | Major | 6.285883e+08           |
| C#   | Minor | 5.665252e+08           |
| D    | Major | 5.720180e+08           |
| D    | Minor | 3.425588e+08           |
| D#   | Major | 6.819623e+08           |
| D#   | Minor | 4.793647e+08           |
| E    | Major | 7.605963e+08           |
| E    | Minor | 5.083264e+08           |
| F    | Major | 5.279311e+08           |
| F    | Minor | 4.102836e+08           |
| F#   | Major | 4.175450e+08           |
| F#   | Minor | 5.954921e+08           |
| G    | Major | 4.929813e+08           |
| G    | Minor | 3.637593e+08           |
| G#   | Major | 5.458044e+08           |
| G#   | Minor | 3.219036e+08           |



Since the data type of the streams is an object, using .to_numeric function to convert 'streams' column to numeric.
```python
df['streams'] = pd.to_numeric(df['streams'], errors='coerce')  
```

Calculates the average among tracks with the same key or mode (Major vs. Minor).
```python
streams_same_key = df.groupby(['key', 'mode']).size().reset_index(name='Count')
```


Set the figure size and style
```python
plt.figure(figsize=(10, 6))
sns.set(style="whitegrid")
```


Create a scatter plot with different colors for each mode
```python
sns.scatterplot(data=streams_same_key, x='key', y='Count', hue='mode', palette='Set1')
```


Add labels and title
```python
plt.xlabel('Key', fontsize=14, fontweight='bold')
plt.ylabel('Average Streams', fontsize=14, fontweight='bold')
plt.title('Average Streams by Key and Mode (Major vs Minor)', fontsize=16, fontweight='bold', color='darkred')
```


Display the plot
```python
plt.legend(title='Mode')
plt.show()
```

Figure 5.0.
![image](https://github.com/user-attachments/assets/549710d0-62df-473d-b6d0-011bfdb8409e)

--- 

### Frequent Artists in Playlists
####

# Using .sum() function it sums up how many times the artist consistently appear in more playlists/charts.
top_artists = df.groupby('artist(s)_name')[['in_apple_playlists', 'in_spotify_playlists','in_spotify_charts','in_deezer_playlists','in_deezer_charts']].sum()
top_artists = top_artists.sort_values(by='in_spotify_playlists', ascending=False).head(10)
print("Most Frequently Appearing Artists:\n", top_artists_playlists)

Table 8.0. The Most Frequently Appearing Artists

| Artist(s) Name        | in Apple Playlists | in Spotify Playlists | in Spotify Charts | in Deezer Playlists | in Deezer Charts | Total Appearances |
|-----------------------|--------------------|-----------------------|-------------------|---------------------|------------------|-------------------|
| The Weeknd            | 1677               | 144053                | 180               | 2138.0              | 23               | 148071.0          |
| Taylor Swift          | 1796               | 132974                | 542               | 1708.0              | 58               | 137078.0          |
| Ed Sheeran            | 1448               | 128758                | 94                | 1702.0              | 43               | 132045.0          |
| Harry Styles          | 1741               | 110026                | 185               | 2483.0              | 76               | 114511.0          |
| Eminem                | 475                | 87331                 | 152               | 0.0                 | 12               | 87970.0           |
| Arctic Monkeys        | 241                | 84016                 | 190               | 1170.0              | 6                | 85623.0           |
| Coldplay              | 381                | 75716                 | 72                | 805.0               | 10               | 76984.0           |
| Avicii                | 407                | 68241                 | 42                | 0.0                 | 1                | 68691.0           |
| Dr. Dre, Snoop Dogg   | 283                | 65728                 | 0                 | 0.0                 | 2                | 66013.0           |
| Adele                 | 646                | 65049                 | 69                | 856.0               | 29               | 66649.0           |


# Sums the total number of appearances for each artist across all platforms.
top_artists['Total Appearances'] = top_artists.sum(axis=1)

# Set the overall design of the graph
plt.figure(figsize=(18, 6))
sns.set(style="whitegrid")
sns.barplot(data=top_artists, x='Total Appearances', y=top_artists_playlists.index, palette="viridis", edgecolor='black')
plt.bar_label(plt.gca().containers[0], fontsize=12, fontweight='bold', padding=5)

# Adds labels to the gaph.
plt.title('Top 10 Artists Consistently Appearing in Playlists/Charts', fontsize=14, fontweight='bold')
plt.xlabel('Total Appearances in Playlists/Charts', fontsize=12)
plt.ylabel('Artist Name', fontsize=12)
plt.grid(axis='x', linestyle='--', alpha=0.7)

# Show the plot
plt.show()

Figure 6.0.
![image](https://github.com/user-attachments/assets/42f78d77-d798-44a3-9fed-b84c0b63df21)

---
## Conclusion
####
---

## License 
#### Jupyter Notebook is a software licensed under the [BSD License](https://jupyter.org/governance/projectlicense.html). 

---

## Author

* Name: DOMINGO, Mariedel O.
* Section: 2ECE-A

---

## Version History

#### 1.00
* Created a repository.
#### 1.01
* Created a README file.
* Uploaded the supplemental file.
#### 1.02
* Deleted the file due to a mistake in the code.
#### 1.03
* Made some updates to the README file.
#### 1.04
* Uploaded the corrected supplemental file.


