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
##### Table 1.1. The Most Streamed Spotify Songs 2023 dataset
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

##### Table 2.0. The Column Data Types Overview
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

##### Table 2.1. Summary of Missing Values per Column
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

As shown in Table 2.1, the dataset has a **$\color{Pink}{total\ of\ 145\ missing\ values }$** across all columns.

---
## Key Insights and Analysis
#### This part dives into an in-depth analysis of the dataset, exploring key statistics, standout tracks, and release trends to uncover noticeable patterns and unique insights.
---
### Basic Descriptive Statistics
- #### Stream Stats
 A statistical breakdown of stream counts, where the calculated mean, median, and standard deviation of the streams column is presented.

- #### Release Trends
This visualization offers a snapshot of the annual release trends.
  
- #### Artist Frequency
Here, illustrate a plot that reveals the extent of collaboration in the music industry, showing the number of artists per track.

---
###  Top Performers
- #### Most Streamed Tracks
This section highlights the top-performing tracks, revealing the true music sensations.

- #### Top Artists
This section highlights the top 5 artists with the most tracks in the dataset, showcasing their popularity and influence.

---
## Temporal Trends in Music Releases
####
---

### Tracks Released Over Time
####

---

### Top Release Years
#### 

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

### Audience Preferences
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


