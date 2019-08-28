# Capstone Project 2
Kiva loan delay analysis.

---
### Goal of the project:
Build a book recommendation system for users, using Goodreads.com dataset with almost 6 million ratings done by 50K+ users for 10K+ books.

<br>

**Method and Results:** 
The built recommendation system works as follows:
 - First, we built a matrix factorization algorithm using ALS (Alternating Least Squares) in order to get implicit feedback. In other words, an algorithm that could predict if the user read a certain book or not, regardless of his opinion of the book. This could be seen as an attempt to study user behavior, in the sense that it tries to predict general/implicit preferences. The test score was pretty good, with a mean AUC of 0.96.
 - Using that implicit behavior as an extra feature, we then started to build the recommendation system by testing several algorithms and predict the user rating (explicit behavior). This was made after doing an initial feature selection, which was mainly based on the previous exploratory data analysis phase. Although the one with better results was a Voting Classifier ensemble using 3 of the models, I chose to go with the Light Gradient Boosting (LightGBM) algorithm, which got similar but much faster results.
 - Then, through principal component analysis (PCA), Recursive Feature Elimination (RFE) and also considering the feature importances obtained when testing the Random Forest Classifier, further feature selection was made, reducing the chosen features to 7.
 - After that, the chosen model was tuned on 4 major parameters. Then, since the usage of all these parameters can usually result in poor estimates of the individual class (rating) probabilities, we went further to perform probability calibration using sklearn's CalibratedClassifierCV. This was important for the next step. The final model got an RMSE score of 1.08 and an average AUC of 0.66.
 - The recommendations were based using the highest scoring probabilities of having a rating equal to 5 - the highest score a book can have. After testing with other methods, this one got better results. Against the test dataset it got an average error of 0.5, in terms of rating points. This means that the 8 recommended books were, on average, 0.5 rating points below the 8 highest rating books of the user, that is, on what would be a perfect score (error 0).
.

### Files:

| File                                                         |    Description                                   |
| ------------------------------------------------------------ | ----------------------------------------------   |
| [Capstone Project 2_ Project Proposal.pdf](https://github.com/MigBap/Springboard-Capstone-Project-II/blob/master/Capstone%20Project%202_%20Project%20Proposal.pdf)                                         |       Project proposal                           |
| [book_recommendations_goodreads.ipynb](https://github.com/MigBap/Springboard-Capstone-Project-II/blob/master/book_recommendations_goodreads.ipynb)                              |       All code in one file                       |
| [Capstone Project 2 - Final Presentation.pptx](https://github.com/MigBap/Springboard-Capstone-Project-II/blob/master/Capstone%20Project%202%20-%20Final%20Presentation.pptx)                                      |       PowerPoint presentation                    |
| [Capstone Project 2_ Final Report.pdf](https://github.com/MigBap/Springboard-Capstone-Project-II/blob/master/Capstone%20Project%202_%20Final%20Report.pdf)                          |       Final report: Pdf document                |
                  |

<br>
