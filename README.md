# NLP and Clustering of Board Games and their Reviews 

## Objective

1. Retrieve a dataset through an API.

2. Apply a Natural Language Processing (NLP) model on the dataset.

3. Use a clustering model to group the data.

4. Analyze the resulting clusters.

5. Draw conclusions based on the interpretation of the clusters.
</br></br>
---
### Data source

Board games reviews and information will be retrieved from the website https://boardgamegeek.com/ from an [API](https://boardgamegeek.com/xmlapi) .
</br></br>
Here is the various information retrieved with the API:

| Game information retrieved      | 
|---------------|
| **Username** |
| **Rating** |
| **Comment**|
| **Game Name** | 
| **Mechanics** | 
| **Min Players** | 
| **Max Players** | 
| **Min Playtime** | 
| **Max Playtime** | 
| **Age** | 
| **Average Rating** | 
| **Wanting Count** | 
| **Wishing Count** | 
| **Description** | 
| **Categories** | 

</br></br>
The retrieved data can be found here [Dataset](data/games_comments.csv)

---
### Step 1: Data Cleaning,

Data cleaning is crucial for data analysis. The cleaned data can be found here [Cleaned Dataset](data/games_comments_clean.csv)

1. Missing values will be replaced or discarded.
2. A language column will be created based on the language used for the comment.
</br></br>

---
### Step 2 : Data Analysis

Data Analysis is necessary to understand 
   - the dataset
   - the various trends
   - the distribution
   - the range
     
of the various information available in the dataset.

</br></br>

---
### Step 3 : NLP - BERT Sentiment

A NLP model, most precisely BERT - Sentiment, will be used to convert the comments to a rating score from 1 to 10.
</br></br>
The new produce Sentiment rating will be useful, since 25% of users did not provide a rating along with their comment.
</br></br>
Some other NLP were tested as well
  - NLP Summarization model (BERT Summarizer)
  - NLP Summarization model (BART Summarizer)
  - NLP keywords model (KeyBERT Sentence Transformer)

However, due to a lack of time no further investigation was done on those three additional NLP.
</br></br>
The data with the added Sentiment rating can be found here [Dataset with Sentiment](data/games_comments_sentiment_summarized.csv) 

</br></br>
Here is an overview of the performance of the BERT Sentiment NLP in comparison to the available ratings.

![](graph/Class_report.png)
</br></br>
Here is an overview of the distribution of the BERT Sentiment NLP in comparison to the available ratings.

![](graph/SentimentvsRating.png)

What might explain the overall poor performance of the BERT Sentiment NLP is that the usual rating is from 1 to 5. However, the rating of the board game site range from 1 to 10. Therefore, we are not comparing apples with apples here.
</br></br>

---
### Step 4 : Clustering with KMeans

To simplify the clustering model and get a minimal amount of clusters to analyze, we only used the numerical columns of the dataset.
</br></br>
Here are the columns that were used with the KMeans model.

| Column       |
|--------------- |
| min_players    |
| max_players    |
| minplaytime    |
| maxplaytime    |
| age            |
| ratings_avg    |
| count_wanting  |
| count_wishing  |
| Sentiment      |

</br></br>
Here is the Elbow Analysis perform on the dataset, to find the right K values. 

![](graph/ElbowKmeans.png)
</br></br>
The KMeans model was used with a K value of eight. Thus, returning 8 clusters for our dataset to analyze further. 
</br></br>
Here is the distribution of the 8 clusters.

![](graph/Distribution_Cluster.png)


</br></br></br>
<center>

---
### Results


| Cluster | Interpretation for Games| Cluster | Interpretation for Games|
| :---------: |----------------| :---------: |----------------|
| 0       | - Pre-teens</br>- Short play time</br>- Low to high ratings</br>- Average popularity               | 4       | - Teens & Adults</br>- Short to long play time</br>- High ratings</br>- Average popularity                |
| 1       | - Teens & Adults </br>- Moderate play time</br>- Moderate ratings</br>- Low popularity                | 5       | - Teens & Adults</br>- Long play time</br>- High ratings</br>- Highest popularity                 |
| 2       | - Pre-teens</br>- Moderate play time</br>- Moderate ratings</br>- High popularity                | 6       | - Mid-Teens & Adults</br>- Longest play time</br>- Highest ratings</br>- Low popularity                |
| 3       | - Kids</br>- Very short play time</br>- Low ratings</br>- Unpopular                | 7       | - Teens & Adults</br>- Moderate play time</br>- Low to high ratings</br>- Lowest popularity                |

</br></br>
Principal Component Analysis was used to reduce our dataset to 2 dimension for visualisation.

![](graph/PCA_2d_comments.png)


</br></br>




    





