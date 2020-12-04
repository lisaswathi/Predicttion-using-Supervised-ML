# Predicttion-using-Supervised-ML
Prediction
library(Metrics)
install.packages("caret")
library(caret)
mydata = read.csv("student.csv",header=T) 
#predict the score(x) based on the hours spent(y)
#1. Plot a scatter plot
plot(mydata$Scores,mydata$Hours)
#A linear relationship is seen on the scatter plot
#2. Strength of correlation
cor(mydata$Scores,mydata$Hours)
#0.097 represents a strong and positive correlation between variables
#3. Simple Linear Regression model--lm-linear model
#y first and then x
r<-lm(Scores~Hours,data=mydata)
#4.Adding regression line--a-intercept,b-slope
abline(r)
names(r)
#5.fitted values
plot(mydata$Hours,r$fitted)
# create a list of 80% of the rows in the original dataset we can use for training
validation_index <- createDataPartition(mydata$Scores, p=0.80, list=FALSE)
# select 20% of the data for validation
validation <- mydata[-validation_index,]
# use the remaining 80% of data to training and testing the models
dataset <- mydata[validation_index,]
# take a peek at the first 5 rows of the data
head(dataset)
#to make predictions for x-score based on y-hours
predict(r,data.frame(Hours=9.25))
actual=21
predicted=27
result<-rmse(actual,predicted)
