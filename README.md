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
    - [WhatMakesaHit?](#What-Makes-a-Hit?)
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
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from math import *
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
####
---
## Key Insights and Analysis
####
---
## Temporal Trends in Music Releases
####
---
## Musical Attributes and Popularity
####
---
## Audience Preferences
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


