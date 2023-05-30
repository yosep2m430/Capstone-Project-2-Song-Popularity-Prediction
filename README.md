# Spotify_Popularity_Predictions
![image](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/assets/102874665/f009e0de-4040-4d6f-873d-15e15799c8e0)

* Spotify is a continuously growing audio streaming platform serving both artists and listeners worldwide. Our goal is to predict the popularity of songs given their audio features to supplement Spotify’s recommendation system. *
**1. Data Wrangling**
In  [Data Wrangling.ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Data%20Wrangling.ipynb), the audio feature dataset for top charting songs from 1921 to 2021 is aggregated to explore audio features’ relationships and patterns throughout the years. More specifically, there were three datasets used:
  - US 1921- 2020 dataset: contains audio data for popular songs in 1921-2020 broken down into 20 features: danceability, valence, energy, tempo, loudness, speechiness, instrumentalness, liveness, acousticness, popularity, song name, artist name, song id, artist id, explicitness, duration, release date, key, mode (musical mode), and time signature.
  - US 2021 dataset (df_US21): contains data for top 1255 songs in 2021. Titles and artists were used to query from Spotify Web API.
  - Spotify US 2021 dataset(US21): contains audio data queried from Spotify Web API. This contained the same audio features contained in the US 1921-2020 dataset. 


**2. Exploratory Data Analysis**
In [Exploratory Data Analysis (EDA).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Exploratory%20Data%20Analysis%20(EDA).ipynb), the relationships between audio features and the relationships between user, tracks, and playlists are explored.

![Uploading image.png…]()
We first explored how different audoio features changed from 1921- 2021s. Songs were high in acousticness around the 1920s-1950s. The acousticness started showing downward trend from then on. Valence and danceability values show close resemblance through the 1920s-1960s. They then show slight divergence, but both with upward trends until the 1990s. Valence and danceability then shows another divergence, with danceability increasing, while valence decreasing. Energy remains consistent throughout the 1920s-1950s, staying around 0.3. It then experienced constant upward trend until 2020s. Liveness stays consistent around 0.2 throughout the 1920s-2020s. Instrumentalness hovers around 0.2-0.4 between the 1920-1950, then decreases until the 1970s, then stays around 0.1 until 2020.

![Uploading image.png…]()
The heatmap shows that while there weren't any features with significant correlation with song popularity, we had some features with noticeable correlations with each other.
Strong positive correlations:
energy: loudness (0.75)

Moderate positive correlations:
loudness: duration (0.55)
acousticness: duration (0.51)
valence: danceability (0.55)
speechiness: danceability (0.53)
valence: energy(0.4)

Strong negative correaltions:
energy: acousticness (-0.72)

Moderate negative correlations:
loudness: acousticness (-0.52)
acousticness: popularity (-0.37)

**3. Modeling** 
First, regression models were explored to predict song popularities. Regression models yielded poor performance as they attempt to predict songs' exact placements on chart. It made more intuitive sense to predict song popularities based on classifications. 
In [Modeling- Part 1(Regression).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Modeling-%20Part%201(%20Regression).ipynb), Linear Regression model, Random Forest Regressor, and Gradient Boosting Regressor are explored.
In [Modeling- Part 2(Classification).ipynb](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features-Capstone-2-/blob/main/Modeling-%20Part%202(Classification).ipynb), Random Forest Classifier, and K-Nearest Neighbors Classifier models are explored.
Among them the best model is the K-Nearest Neighbors Classifier, which has the test score (accuracy) of 0.82.

**4. Future Improvements**
If there were data and opportunity available, I would be interested in the following:
- Exploring the relationship between streams of songs and artists’ standing in different social media- Aside from “how good” a song is, a song’s popularity can be impacted by its artist’s status. Some people may initially listen to a song only because it is released by their favorite artists and grow to like it, because they listened to it so often. 
- Focusing on individual genres of songs and developing models that predict popularity using audio features within each genre- one may be able to better predict popularity after training the model with genre specific data. Current model is trained on songs from a number of different genres. This can hinder model performance, as different genres each have characteristic audio features. 


**5. Project Report**
[Final Project Report](https://github.com/yosep2m430/Predicting-Song-Popularity-Using-Audio-Features/blob/main/Final%20Project%20Report.pdf)

