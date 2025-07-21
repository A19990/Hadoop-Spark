# 🎧 Spotify Songs Analysis with PySpark (1958–2019)

This project explores and analyzes music chart data using **Apache Spark**, focusing on weekly Billboard chart rankings enriched with **Spotify audio features**. The dataset contains over **277,000 entries** and represents **24,000 unique songs** charted between **1958 and 2019**.

## 📊 Dataset Overview

The dataset includes detailed metadata for each song and week, such as:

- **Chart position** (weekly and peak)
- **Performer(s)** and song title
- **Spotify features**: danceability, energy, loudness, tempo, etc.
- **Custom genre tags** and track popularity
- **Timestamps**, **duration**, and **explicit flag**

Primary key: `WeekID` + `SongID`

## 🔧 Tasks and Objectives

### 1. Data Ingestion
- Load CSV using Spark with schema inference and malformed row handling.
- Ensure proper handling of quoted fields and encoding issues.

### 2. Data Cleaning and Enrichment
- Convert `WeekID` to `DateType`.
- Compute:
  - Length of song titles
  - Number of performers per song (splitting on `" & "`)
  - Extract `year` and `month` from dates

### 3. Top 10 Chart Analytics
- Analyze unique songs in Top 10 per month and year.
- Create pivot tables showing monthly Top 10 counts.
- Calculate average Top 10 presence per year.

### 4. Performer Insights
- Aggregate total Top 10 weeks per song using window functions.
- Explode collaborations to attribute performance to individual artists.
- Identify top performers across all years.

### 5. Clustering Songs (K-Means)
- Select 10 audio features for clustering:
  `danceability`, `energy`, `loudness`, `mode`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`
- Normalize features using `MinMaxScaler`.
- Apply `KMeans` with k=10 clusters.
- Analyze cluster characteristics by computing medians per feature and year.

## 🧰 Technologies Used

- **Apache Spark (PySpark)**
- **Spark SQL** and **Window Functions**
- **Spark MLlib** for clustering and scaling
- **Google Cloud Storage** (data source)
- **Pandas** (final summary exports)
