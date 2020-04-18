# airbnb-price
# airbnb price prediction project 
# ensure analysisData.csv and scoringData.csv are in your working directory

# following code will read data and construct a simple model
data = read.csv('analysisData.csv')
model = lm(price~minimum_nights+review_scores_rating,data)

# read in scoring data and apply model to generate predictions
scoringData = read.csv('scoringData.csv')
pred = predict(model,newdata=scoringData)

# construct submision from predictions
submissionFile = data.frame(id = scoringData$id, price = pred)
write.csv(submissionFile, 'sample_submission.csv',row.names = F)
