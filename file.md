# K-Nearest Neighbors (KNN) Algorithm

The K-Nearest Neighbors (KNN) algorithm is a simple, instance-based learning method used for classification and regression. It classifies a data point based on how its neighbors are classified. Here’s a detailed explanation of the algorithm along with a use case.

#### How KNN Works

1. **Choose the number of neighbors \( k \)**: Determine the number of nearest neighbors to include in the majority voting process. The value of \( k \) is usually odd to avoid ties.
2. **Calculate distances**: For a given test instance, calculate the distance between the test instance and all the training instances. Common distance metrics include Euclidean distance, Manhattan distance, and Minkowski distance.

   - **Euclidean distance** (for instance, between points \( p = (p_1, p_2, ..., p_n) \) and \( q = (q_1, q_2, ..., q_n) \)) is:
     \[
     d(p, q) = \sqrt{(p_1 - q_1)^2 + (p_2 - q_2)^2 + ... + (p_n - q_n)^2}
     \]
3. **Identify nearest neighbors**: Sort all training instances by their distance to the test instance and select the \( k \) closest training instances.
4. **Voting (for classification)**: The class of the test instance is determined by the majority class among the \( k \) nearest neighbors.

   - For **regression**, the output value is the average of the values of the \( k \) nearest neighbors.
5. **Assign class or value**: Assign the most frequent class (or the average value for regression) among the \( k \) neighbors to the test instance.

#### Example Use Case: Movie Recommendation System

Consider building a movie recommendation system using KNN. The goal is to recommend movies to users based on their past ratings and similarities with other users.

##### Steps

1. **Data Preparation**:

   - Collect data on user ratings for various movies. This data can be represented in a matrix where rows represent users and columns represent movies.
   - Each entry in the matrix represents the rating a user has given to a particular movie.
2. **Define Distance Metric**:

   - Use a similarity measure like cosine similarity or Euclidean distance to measure how similar two users are based on their movie ratings.
   - For instance, with cosine similarity, the similarity between users \( A \) and \( B \) is:
     \[
     \text{similarity}(A, B) = \frac{\sum_i{r_{A,i} \cdot r_{B,i}}}{\sqrt{\sum_i{r_{A,i}^2}} \cdot \sqrt{\sum_i{r_{B,i}^2}}}
     \]
     where \( r_{A,i} \) and \( r_{B,i} \) are the ratings of users \( A \) and \( B \) for movie \( i \).
3. **Determine Number of Neighbors \( k \)**:

   - Choose \( k \), the number of similar users (neighbors) to consider for making a recommendation. Typical values might range from 5 to 20.
4. **Find Nearest Neighbors**:

   - For a target user \( U \), calculate the similarity between \( U \) and all other users.
   - Select the \( k \) users with the highest similarity scores.
5. **Make Recommendations**:

   - Aggregate the movie ratings from these \( k \) nearest neighbors.
   - Recommend movies that the target user has not rated yet but are highly rated by their nearest neighbors.

##### Benefits of Using KNN in This Use Case

- **Simplicity**: Easy to implement and understand.
- **Flexibility**: Can handle large datasets and works well with multi-class problems.
- **Adaptability**: Easily adapts to new data since it's a non-parametric method.

##### Example in Practice

Suppose we have the following user-movie rating matrix (simplified for illustration):

| User/Movie | Movie 1 | Movie 2 | Movie 3 | Movie 4 | Movie 5 |
| ---------- | ------- | ------- | ------- | ------- | ------- |
| User A     | 5       | 3       | 4       | NaN     | 1       |
| User B     | 4       | 2       | NaN     | 5       | 3       |
| User C     | NaN     | 4       | 3       | 4       | 5       |
| User D     | 3       | 5       | 4       | 2       | NaN     |
| User E     | 1       | 1       | NaN     | 3       | 2       |

To recommend movies to User A, we:

1. Calculate the similarity of User A with all other users.
2. Select the top \( k \) most similar users (e.g., Users B and C if \( k = 2 \)).
3. Recommend the movies that these similar users rated highly but User A hasn't watched (e.g., Movie 4 if Users B and C rated it highly).

In summary, the KNN algorithm is straightforward and effective, particularly in recommendation systems where it leverages the similarity between users or items to provide personalized recommendations.
