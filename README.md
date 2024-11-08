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
    - [Platform Comparison](#Platform-Comparison)
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
|$\mathbf{\color{Red}{#}}$       | $\mathbf{\color{Red}{Track\ Name}}$     |  $\mathbf{\color{Red}{Streams}}$       |  
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

### Table 4.0. The Top 5 most Frequent Artists by Number of Tracks.
|$\mathbf{\color{lightblue}{Artist\ Name}}$       | $\mathbf{\color{lightblue}{Track\ Count}}$     | 
| ------------- |:-------------:| 
| Taylor Swift        |     34     | 
| The Weeknd        |    22  | 
|Bad Bunny           |    19     |  
| SZA                |    19      |  
| Harry Styles          |    17     |

Table 4.0 reveals the collaborative dynamics within the music industry, showcasing how many times each unique combination of artists appears in the dataset, focusing on counting the frequency of artist pairings and group collaborations.
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
####
---

### What Makes a Hit?
#### 

--
 
### The Rhythm and the Beat
#### 

---

### Mood Tones
####

---
## Audience Preferences
####
---

### Platform Comparison
####

---
## Advanced Analysis
####
---

### Key and Mode Analysis
####

--- 

### Frequent Artists in Playlists
####

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


