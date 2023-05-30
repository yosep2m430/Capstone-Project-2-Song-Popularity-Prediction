# Spotify_Popularity_Predictions
![image](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/assets/102874665/f009e0de-4040-4d6f-873d-15e15799c8e0)

*Spotify is a continuously growing audio streaming platform serving both artists and listeners worldwide. Our goal is to predict the popularity of songs given their audio features to supplement Spotify’s recommendation system.*

## 1.Data

A wonderful CSV file containing audio feature data for 1921- 2020 top charting songs was sourced from:

https://www.kaggle.com/datasets/ektanegi/spotifydata-19212020

Another CSV file containting data for top charting songs in 2021 was sourced from:

https://www.kaggle.com/datasets/sashankpillai/spotify-top-200-charts-20202021


## 2. Data Wrangling

In  [Data Wrangling.ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Data%20Wrangling.ipynb), the audio feature dataset for top charting songs from 1921 to 2021 is aggregated to explore audio features’ relationships and patterns throughout the years. After ensuring there was no null values, I dropped track names and artist names from the data as they could be identified using song ID. 

The Spotify 2021 top charting songs dataset sourced from Kaggle did not have desired audio data. However, we obtained the track titles and artist names to get a comprehensive list of top 2021 songs to build our own dataset. I wrote a function that uses the track title and artist name to retrieve audio data from Spotify Web API.
I used the function to query audio data from Spotify's RESTful API to build a dataset containing the same audio features contained in 1921-2020 dataset. Track Name, Artist', type, uri, track_href, analysis_url, and id were removed from the queried dataset to match features contained in 1920-2020 dataset.

## 3. Exploratory Data Analysis

In [Exploratory Data Analysis (EDA).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Exploratory%20Data%20Analysis%20(EDA).ipynb), the relationships between audio features and the relationships between user, tracks, and playlists are explored.

<img width="916" alt="image" src="https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/assets/102874665/e60d242e-9b06-4c77-808b-37dafc82c762">

We first explored how different audoio features changed from 1921- 2021s. Songs were high in acousticness around the 1920s-1950s. The acousticness started showing downward trend from then on. Valence and danceability values show close resemblance through the 1920s-1960s. They then show slight divergence, but both with upward trends until the 1990s. Valence and danceability then shows another divergence, with danceability increasing, while valence decreasing. Energy remains consistent throughout the 1920s-1950s, staying around 0.3. It then experienced constant upward trend until 2020s. Liveness stays consistent around 0.2 throughout the 1920s-2020s. Instrumentalness hovers around 0.2-0.4 between the 1920-1950, then decreases until the 1970s, then stays around 0.1 until 2020.

<img width="918" alt="image" src="https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/assets/102874665/a225a179-ce8c-405c-9b20-9c78be9e977f">

The heatmap shows that while there weren't any features with significant correlation with song popularity, we had some features with noticeable correlations with each other:

**Strong positive correlations:<br>**
 energy: loudness (0.75)

**Moderate positive correlations:<br>**
 loudness: duration (0.55) <br>
 acousticness: duration (0.51)<br>
 valence: danceability (0.55)<br>
 speechiness: danceability (0.53)<br>
 valence: energy(0.4)

**Strong negative correaltions:<br>**
 energy: acousticness (-0.72)

**Moderate negative correlations:<br>**
 loudness: acousticness (-0.52)<br>
 acousticness: popularity (-0.37)

## 4. Modeling 

First, regression models were explored to predict song popularities. Regression models yielded poor performance as they attempt to predict songs' exact placements on chart. It made more intuitive sense to predict song popularities based on classifications. 

The dataset was balanced before it was used, with most songs with low popularity, followed by medium, then by high popularity. This is intuitive, because there aren't as many popular songs as there are non-popular songs (otherwise, there will be much more financial stability in music industry!). However, any imbalance in dataset will tamper with the accuracy of our model. The dataset was upsampled.

### Models
In [Modeling- Part 1(Regression).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Modeling-%20Part%201(%20Regression).ipynb), Linear Regression model, Random Forest Regressor, and Gradient Boosting Regressor are explored.

In [Modeling- Part 2(Classification).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Modeling-%20Part%202(Classification).ipynb), Random Forest Classifier, and K-Nearest Neighbors Classifier models are explored.

Among them the best model is the K-Nearest Neighbors Classifier, which has the test score (accuracy) of 0.82.

## 5. Future Improvements

If there were data and opportunity available, I would be interested in the following:
- Exploring the relationship between streams of songs and artists’ standing in different social media- Aside from “how good” a song is, a song’s popularity can be impacted by its artist’s status. Some people may initially listen to a song only because it is released by their favorite artists and grow to like it, because they listened to it so often. 
- Focusing on individual genres of songs and developing models that predict popularity using audio features within each genre- one may be able to better predict popularity after training the model with genre specific data. Current model is trained on songs from a number of different genres. This can hinder model performance, as different genres each have characteristic audio features. 


## 6. Project Report

[Final Project Report](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/blob/main/Final%20Project%20Report.pdf)

