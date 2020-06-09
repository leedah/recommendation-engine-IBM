# Recommendation Engine with IBM

Analyzes the interactions that users have with articles on the [IBM Watson Studio platform](https://www.ibm.com/cloud/watson-studio), and makes recommendations to them about new articles they might like. 

## Features

### 1. Exploratory Data Analysis

Explore the data to understand the number of users, articles, and information about the interactions that take place. Visual and descriptive statistics to understand the interactions between users and articles in the dataset.


### 2. Rank Based Recommendations

Finds the most popular articles simply based on the most interactions. Since there are no ratings for any of the articles, it is easy to assume the articles with the most interactions are the most popular. These are then the articles we recommend to new users (or anyone depending on what we know about them).

- `get_top_articles(n, df)`: returns the top article titles from df
- `get_top_article_ids(n, df)`: returns the top article ids

### 3. User-User Based Collaborative Filtering

In order to build better recommendations for the users of IBM's platform, we look at users that are similar in terms of the items they have interacted with. These items are then be recommended to the similar users, providing more personal recommendations for the users.

- `create_user_item_matrix(df)`: returns the user_item matrix 
- `find_similar_users(user_id, user_item)`: returns a list of the users in order from most to least similar
- `get_article_names(article_ids, df)`: returns the article names associated with list of article ids
- `get_user_articles(user_id, user_item)`: returna the ids and names
- `user_user_recs(user_id, m)`: returns top m recommendations for this user_id  
- `get_top_sorted_users(user_id, df=df, user_item=user_item)`: returns the `neighbors_df`, a pandas dataframe with the following columns:
  - `neighbor_id`: a neighbor user_id
  - `similarity`: measure of the similarity of each user to the provided user_id
  - `num_interactions`: the number of articles viewed by the user
- `user_user_recs_part2(user_id, m)`: improvement of the `user_user_recs function`. Instead of arbitrarily choosing when we obtain users who are all the same closeness to a given user, we choose the users that have the most total article interactions before choosing those with fewer article interactions. Instead of arbitrarily choosing articles from the user where the number of recommended articles starts below m and ends exceeding m, we choose articles with the articles with the most total interactions before choosing those with fewer total interactions. This ranking should be what would be obtained from the top_articles function above.


### 4. Content Based Recommendations (TODO)

Given the amount of content available for each article, there are a number of different ways in which someone might choose to implement a content based recommendations system. Using NLP, we can develop a content based recommendation system.

- `plot_accuracy(u,s,vt)`: plots the accuracy vs the the number of latent features for the U, Σ, and Vtranspose matrices of the SVD.
- `create_test_and_train_user_item(df_train, df_test)`: Returns the following:
  - `user_item_train`: a user-item matrix of the training dataframe (unique users for each row and unique articles for each column)
  - `user_item_tes`: a user-item matrix of the testing dataframe (unique users for each row and unique articles for each column)
  - `test_idx`: all of the test user ids
  - `test_arts`: all of the test article ids

### 5. Matrix Factorization

A machine learning approach to building recommendations. Using the user-item interactions, build out a matrix decomposition. 
Using the decomposition, ywe get an idea of how well you can predict new articles an individual might interact with. 

### 6. Extras & Concluding

A discussion about the results, as well as a method to test how well your recommendation engine is working in practice.
