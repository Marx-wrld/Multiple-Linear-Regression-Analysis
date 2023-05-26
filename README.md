# Multiple-Linear-Regression-Analysis
A repo on how to perform multiple linear regression analysis. I have used a sample heart disease data that analyses the relationship between heart disease, biking and smoking.

#### Loading the Dataset to R studio by importing to text (base)
- Get the summary of the heart.data dataset to check that it has been read correctly.
```
summary(head.data)
```

#### Ensuring our data meets the main assumptions

1. Independence of Observations - Using cors() function to check the relationship between our independent variables.

```
cor(heart.data$biking, heart.data$smoking)
```
2. Normality - Using the hist() function to test whether our dependent variable follows a normal distribution.                                                                                                                                            
```
hist(heart.data$heart.disease)
```
![hist](https://github.com/Marx-wrld/Multiple-Linear-Regression-Analysis/assets/105711066/c71a9656-9dff-48ad-bfe5-5635f4e4a5c2)

3. Linearity - Checking the two scatterplots both the biking and heart disease, and one for smoking and heart disease.

```
plot(heart.disease ~ biking, data=heart.data)
```
![heartdisease-biking](https://github.com/Marx-wrld/Multiple-Linear-Regression-Analysis/assets/105711066/d1d416a1-82d9-4c85-aa3e-335db0354b3e)
![heartdisease-smoking](https://github.com/Marx-wrld/Multiple-Linear-Regression-Analysis/assets/105711066/e291b653-fefe-4176-acb8-d6e59ff32803)

