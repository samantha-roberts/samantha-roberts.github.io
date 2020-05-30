---
title: "The Music Hall Project"
layout: splash
date: 2020-04-22
---
<h2><center>Description of the Project</center></h2>
<p>
  The Music Hall is a non-profit performing arts center located in Portsmouth, NH. Their passion is to inspire, educate and connect audiences through the power of live performances and on-screen programming. They aim to ignite creativity, purpose, and a sense of community. Their clients are the people of the Seacoast area. The Music Hall is comprised of two venues: The Historic Theatre and The Loft. This project focused on the performances for the Historic Theatre, which is an 895-seat theatre. Performances are artists from genres like Folk, Singer/Songwriter and Alternative. In general, audience member are people in their 50s or older, often referred to as the "white haired" crowd. The Music Hall is struggling with identifying artists that are within their range and that will be successful at their venue. Within their range means artists that book venues around the Music Hall's 900 seat capacity, and within their price range. The question that this project was trying to solve was can the Music Hall's artist selection be improved to ensure that they are booking more successes. 
</p>
<p>
  To conduct this project, there were many data sources that were explored to find predictors to help with creating a model. The useful data that was acquired came from Social Blade, Chartmetric and Google Demand. This data was then formatted and imputed in a replicable manner using Python, including determining the relevant success metric. The input data was then used to train a Random Forest model, which was then applied to a set of test artists who had not yet performed at the Music Hall, to generate a prediction of the level of success a given artist would have. The final Random Forest model used had a prediction accuracy rate of 86%.
There were two types of predictions that were conducted: a binary prediction (success/failure) and a range prediction, with the varying degrees of success (0-10%, 11-20%, etc. of ticket sales) being the prediction ranges.
</p>
<p>
  Since the original data set of Music Hall artists only had 100 rows, SMOTE was used to create synthetic data to help ensure that the model was not over/under fitting on the limited data. After the synthetic data was created, random forest modeling was able to be executed on the data set, for both prediction problems: binary and range. The final model that was used predicted the range of success a past Music Hall artist fell within. This model was then used to predict the range that a test artist would most likely fall within if they were to perform at the Music Hall. 
</p>
<br>
<br>
<h2><center>PowerPoint Presentation</center></h2>
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQ4esvNx_HrHxHurmV_mBkxTXrv2Jj2k3JyhAeBr3aH0hxo1h4NqflZZtNxlDfPtg/embed?start=false&loop=false&delayms=3000" frameborder="0" width="1280" height="749" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
<br>
<br>
<h2><center>Python Code for Modeling</center></h2>
 <center><img src="/images/mh1.PNG" width="800" height="800"></center>
 <center><img src="/images/mh2.PNG" width="800" height="800"></center>
 <center><img src="/images/mh3.PNG" width="800" height="800"></center>
 <center><img src="/images/mh4.PNG" width="800" height="800"></center>
 <center><img src="/images/mh5.PNG" width="800" height="800"></center>
 <center><img src="/images/mh6.PNG" width="800" height="800"></center>
