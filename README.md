# Multiple-Linear-Regression-Analysis
A repo on how to perform multiple linear regression analysis. I have used a sample heart disease data that analyses the relationship between heart disease, biking and smoking.

### A. Loading the Dataset to R studio by importing to text (base)
- Get the summary of the heart.data dataset to check that it has been read correctly.
```
summary(head.data)
```

### B. Ensuring that our data meets the main assumptions

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

```
plot(heart.disease ~ smoking, data=heart.data)
```
![heartdisease-smoking](https://github.com/Marx-wrld/Multiple-Linear-Regression-Analysis/assets/105711066/e291b653-fefe-4176-acb8-d6e59ff32803)

### C. Performing Linear Regression Analysis

- Checking if there's a linear relationship between biking to work, smoking, and heart disease in our imaginary survey of 500 towns.

```
heart.disease.lm<-lm(heart.disease ~ biking + smoking, data = heart.data)

summary(heart.disease.lm)
```
### D. Checking for Homoscedasticity

- Before proceeding with data visualization, we need to ensure that our models fit the homoscedasticity assumption of the linear model.

```
par(mfrow=c(2,2))
plot(heart.disease.lm)
par(mfrow=c(1,1))
```
![homoscedasticity](https://github.com/Marx-wrld/Multiple-Linear-Regression-Analysis/assets/105711066/e82bce39-8892-4bf1-b2e0-5f31aef7e3b5)

### E. Visualizing the results with a graph

- Plotting the relationship between biking and heart disease at different levels of smoking. Smoking will be treated as a factor with three levels, just for the purposes of displaying the relationships in our data.

1. Creating a new dataframe with the information needed to plot the model
```
plotting.data<-expand.grid(
  biking = seq(min(heart.data$biking), max(heart.data$biking), length.out=30),
    smoking=c(min(heart.data$smoking), mean(heart.data$smoking), max(heart.data$smoking)))
```

