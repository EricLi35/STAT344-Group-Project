# STAT344-Group-Project

**Introduction:** 

**Objectives and Background:**

We are tired of spending our precious time watching bad movies. So, we are interested in finding out the average IMDB rating of a movie along with the proportion of movies that score above 65/100. This way we can figure out what an average movie looks like, and how many movies get a decently rated score of 65% or higher. If it turns out a decent proportion of movies get a score of 65% or higher then that tells us that there should be little to no reason to ever watch a movie that does not achieve that score. 

**Dataset:**

We obtained our dataset from Kaggle: <https://www.kaggle.com/datasets/ashpalsingh1525/imdb-movies-dataset/>. This dataset has nearly 10000 movies along with their title, score, genre, release date, etc. We choose this dataset because the dataset has lots of downloads and a high reliability score, it has the necessary columns we need (score and genre), and a large size so we can take sufficient sample sizes.

**Parameters of Interest:**

Our population is all movies. Our dataset from Kaggle has 9660 random movies from different genres, scores, and even languages, from which we will conduct further smaller sampling. 

Our parameters of interest are the IMDB rating score of a movie (our continuous parameter), and whether or not a movie scores above 65/100 (our binary parameter). 

**Sampling Methods:**

Our 2 sampling methods are SRS and stratified sampling. We choose SRS because we believe it is very intuitive and sufficient for our purposes. For stratified sampling our strata are the 19 different genres of movies. We decided to use the strata as different genres because from our understanding of movies and critic ratings, different genres should heavily impact the score of a movie. 

**Data Analysis:**

**Note:**

All of the calculations were done in R, with the R Code attached at the very end of this report after the conclusion. 

**Assumptions:**

For all of the following calculations, we are assuming that the data are all independent and identically distributed random variables (i.i.d). Also, that the data are normally distributed.

**Sample Size Calculation:**

First we need to figure out what sample size we should use for both the SRS and stratified sampling methods.

The 𝞭 (m.o.e) is chosen as 0.04, this is an assumption that we are happy with. The function we used is n = n0/(1+n0/N)  . FPC(finite parameter correction) was used because the ratio of sample size to population was bigger than 0.05. n0 = (Z/2)2 \*sguess2 /𝞭2  .  The p we calculated is the proportion of films rated above 65 in all films. p\*(1-p) is used to find sguess2 . We demand an accuracy of +- 4.0% points, 19 times out of 20.

The final sample size result we calculated for n0 is 597 and the n is 563. 

**SRS Estimates:**

**1st Parameter of Interest:**

To get the estimate for our first parameter of interest, the IMDB rating score of a movie (the continuous parameter), we took a random sample size of 563 and then found the mean rating = 64.229. Next, we used the standard error for continuous estimates formula and found the standard error for this estimate = 0.520. 

So, our 95% CI is 64.229 +/- 1.96\*0.520 = (63.210, 65.248)

**2nd Parameter of Interest:**

To get the estimate for our second parameter of interest, the proportion of movies that score about 65% (the binary parameter), we took a random sample size of 563 and then found the proportion of movies that scored above 65% = 0.499. Next, we used the standard error for binary estimates formula and found the standard error for this estimate = 0.020. 

So, our 95% CI is 0.499 +/- 1.96\*0.020 = (0.461, 0.539)

**SRS Interpretations:**

Through SRS, we see that the CI for our 1st parameter of interest is (63.210, 65.248). This means that the true mean IMDB score for the entire population of movies has a 95% probability of being within (63.210, 65.248). 

The CI for our 2nd parameter of interest is (0.461, 0.539). This means that the true proportion of movies that score above 65% for the entire population of movies has a 95% probability of being within (0.461, 0.539). 

What this means for our use case is discussed further in the conclusion.

**Advantages of SRS:**

- It is very intuitive and easy to understand/interpret

- The standard errors were relatively low, resulting in narrow CI

**Disadvantages of SRS:**

- It may be possible to get even lower standard errors with more appropriate methods, such as stratified sampling

**Stratified Sampling Estimates:**

We use the same sample size (n = 563) in the stratified sampling method compared with the sample size we used in the SRS sampling method. Then, we got sample size for each genres by using nd/n = Nd/N. 

**1st Parameter of Interest:**

The estimate of mean was calculated by function: ystr = h=1Hysh.ysh = (i = 1nhyi)/nh for each genre. 

The estimate of mean = 63.854

The standard error of the mean was calculated by function: s.e.(ystr) = i = 1Nh(Nh/N)2\*(1-nh/Nh)\*ssh2/nh . 

The standard error = 0.524

So, our 95% CI is 63.854 +/- 1.96\*0.524 = (62.827, 64.881)

**2nd Parameter of Interest:**

The estimate of proportion was calculated by function: pstr = h = 1H(Nh/N)\* psh. psh =(i = 1nhpi)/nh . 

The estimate of proportion = 0.478

The standard error of the proportion was calculated by function: s.e.(pstr) = h=1H(Nh/N)2\*(1-nh/Nh)\*(1-psh)\*psh/nsh.

The standard error of the proportion = 0.0192

So, our 95% CI is 0.478 +/- 1.96\*0.0192 = (0.440, 0.516)

**Stratified Sampling Interpretations:**

Through stratified sampling, we see that the CI for our 1st parameter of interest is (62.827, 64.881). This means that the true mean IMDB score for the entire population of movies has a 95% probability of being within (62.827, 64.881). 

The CI for our 2nd parameter of interest is (0.440, 0.516). This means that the true proportion of movies that score above 65% for the entire population of movies has a 95% probability of being within (0.440, 0.516). 

What this means for our use case is discussed further in the conclusion.

**Advantages of Stratified Sampling:**

- Honestly, we did not see any major benefits for this method because even the standard errors were very similar to SRS or even higher… I guess 1 advantage is that it shows off your stats skills more :) 

**Disadvantages of Stratified Sampling:**

- It is less intuitive and also more difficult to conduct compared to SRS

- Like said above, the standard error was only marginally smaller for the 2nd parameter of interest and for the 1st parameter of interest, the standard error was actually higher

  - The SE being so similar for both methods suggest that genre actually probably does not have a huge impact on the IMDB rating of a movie, so stratifying by genre is not a good decision. 

**Conclusion:**

In conclusion, both our sampling methods produced very similar results to one another. For our 1st parameter of interest, the average IMDB rating of a movie, the estimates and standard errors for SRS and stratified sampling are: 

Mean is 64.229 and SE is 0.520 for SRS, and Mean is 63.854 and SE is 0.524 for stratified sampling. This shows that an average movie is rated approximately 64 on IMDB, so for our initial purposes, if a movie is rated below this score it should likely be avoided. 

For our 2nd parameter of interest, the number of movies that get an IMDB score of 65% or higher, the estimates and standard errors for SRS and stratified sampling are: 

Mean is 0.499 and SE is 0.020 for SRS, and Mean is 0.478 and SE is 0.0192 for stratified sampling. This shows that roughly 50% of movies get a score of 65% or higher. This further shows that if a movie is not rated at least 65, it is probably not worth watching, since about half the movies are rated higher than 65. 

Additionally, the SE being so similar for both methods suggest that genre actually probably does not have a huge impact on the IMDB rating of a movie, so stratifying by genre is not a good decision. This was another really cool finding, because we initially thought that genre of movies have a huge impact on the score, and it is normal for certain genres like horror to be rated less just because it is a horror movie. However, if genre actually had a huge impact on the ratings of movies, then the stratified sampling should have resulted in significantly less SE.

**Further Discussions:**

We felt like our dataset was good for this report, as it was sufficiently large and random to accurately represent what the entire population of movies looks like. We felt like there were no limitations anywhere in our dataset or our methods, and all of the assumptions needed for the data analysis are valid assumptions. Furthermore, we believe that the conclusions from this report should be able to be generalized to the entire large population of movies. 

**Appendix/R Code:**

We used Google Colab, and made a PDF of our workspace. This PDF is attached starting on the next page. 
