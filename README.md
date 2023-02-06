# Python-Correlation

In this project I started by exploring a dataset of movies and their gross revenue in relationship to
their budget. The initial tools that I decided to use are pandas, numpy, matplotlib, and seaborn.

After doing a bit of cleaning and plugging the data into a scater plot and adding a regression line
I realized that the methods employed weren't producing anything useful so a different approach was
decided upon, in this case some basic machine learning algorithms. 

For fun I decided to let ChatGPT guide me along the journey of trying to predict whether or not a movie
would be profitable based on several features including the movies rating, budget, company, etc..
The first thing that was suggested by ChatGPT was linear regression, which improved upon a simple
scatter plot with a line through it, but still wasn't all that useful. Having looked at that regression
line the profitability of movie production appeared to be predictable around 50%. I decided to try
another regression technique in spite of this. The elected method was Gradient Boost Regression
which output a similar result, though the mean absolute error improved a bit.

After that I thought it would be fun to build out a Neural Network with tensorflow
and see how that panned out in comparison to GBR. The resulting error metric indicated worse 
prediction results than the GBR. Some hyperparameter tuning might be able to bring it more in line with
the MAE that the gradient boost was coming up with, but that seemed like a moot endeavor.

Since predicting the gross revenue with the data seemed to be a bit of a stretch I decided to reframe the
question from a more practical standpoint. Can we predict if an upcoming movie is going to be profitable?
I decided on a simple classification model and dropped some fields that wouldn't be helpful or available 
until after the hypothetical movie was released(eg critic rating, gross revenue, year released). I added
a feature that I called profitability by dividing gross by budget and that provided a numerical value where
anything greater than one was profitable.

The next step that I took was to run through some Recursive Feature Elimination in order to figure out which 
features are weighted heaviest in determining whether or not a movie will make a profit. I decided that trying
K-Nearest Neighbor would be an ok choice. I first tried training the model with all the available features that
would be available prior to a film's release. That yeilded a 63.2% accuracy rate when it came to predictions,
not great. Having already run through the RFE and determined that the best 3 features for predicting whether a movie 
will be profitable I trimmed down the features to just those three and ran it through the same algorithm - 63.11%.
I iterated this technique two more times trying the best two features and then the best feature. The biggest difference
between the best and worst prediction accuracies was only about 1.5% and the best results came from having a greater
number of features available to predict from.

The conclusion that I came to with this is that even with the ideal setup of budget, genre, company, director, writer,
etc.. Making and monetizing a movie is only about as succesful as flipping a coin.

