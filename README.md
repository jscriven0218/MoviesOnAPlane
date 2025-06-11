![screens](https://github.com/user-attachments/assets/4107690e-7665-4459-a018-b0dadaf6a236)

# Movies on a Plane
Analysis by Jordan Scriven  

## Business Understanding
Here at ABC Airlines we are happy to provide the perk of movies in air during our flights.  But, as our library of movies is paid for by licensing, not views, and the cost is getting too high, we have been tasked to limit the movies available on a flight.  Concurrently, our userface will change and passengers will not simply type in a movie name, but we will recommend movies based on their prior movie ratings.

## Data Understanding

Data provided by MovieLens, a movie recommendation service, provides us with an individuals userID, list of seen movies and a user-specific rating for each of those movies.  This data is provided for all 610 passengers on our flight.

Each movie is rated on a 5-star scale.  The total rated movies amongst the 610 passengers is nearly 10,000 movies.

### Data Preparation
In a first step to make good recommendations, we remove any movie that has less than 5 reviews. Then, we normalize our ratings by using the mean rates for each user. Using the normalized ratings, we come up with a list of the 1,500 highest rated moves that will be our available movie set ready for recommending. This reduces the movies we have available from nearly 10,000 to 1,500 based on their ratings.

![RatingDist](https://github.com/user-attachments/assets/9f3d2221-dd7b-4bad-8f0a-998f78e5d9e6)

## Modeling
To model the recommendations, singular value decomposition (SVD) is a collaborative filtering which is the process of making recommendations based on the preferences of other similar users.  We utilize SVD by creating a matrix of rows representing each user and columns for each movie - with ratings, if reviewed, in the matrix.  We train our model on 70% of our total dataset.

## Evaluation

After fitting the model to our training dataset, we run the model with our testing dataset.  Those predicitons are compared to the actual testing dataset.  An RMSE of 0.8595 tells us that for a predicted rating, the real rating for that user and that movie, is within .8595.  While this is close to a point, it is generally considered a good score on a 5 point rating system.  Therfore, our model is a good predictor of ratings.

Using those predicted ratings, we rank the unwatched movies per user. The first top 5 recommended movies, that are also in the set of 1,500 that we have narrowed our library down to, are recommended to the user.

Top recommendations for user 256:
- Star Wars: Episode V - The Empire Strikes Back (1980) (Estimated rating: 4.66)
- Silence of the Lambs, The (1991) (Estimated rating: 4.50)
- Desperado (1995) (Estimated rating: 4.16)
- Speed (1994) (Estimated rating: 4.03)
- Independence Day (a.k.a. ID4) (1996) (Estimated rating: 3.90)

![StarWars](https://github.com/user-attachments/assets/ac82c4f9-f8d5-44b3-8db2-f03d00de8f01)

## Conclusion

Using a model to recommend movies to the passengers on our flights allows us to cut the cost of this service by only offering a subset of movies, while continuing to provide highly rated movies that fit with the passengers preferences.

### Limitations and Next Steps
The largest limitation to a recommendation model is the cold start problem.  While we have completed this analysis assuming we have the movie preferences and ratings of all passengers on our flights, it is not practical.  Without those to begin with, our model is at a loss.  One way to address this problem is using demographic data.  A passenger's information such as age and gender may connect them to users already in the data.

## Repository Navigation

* [.gitignore](.gitignore)
* [notebook.ipynb](Notebook.ipynb)
* [presentation.pdf](Presentation.pdf)
* [README.md](README.md)



