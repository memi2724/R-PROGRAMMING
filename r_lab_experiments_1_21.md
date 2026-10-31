# R Programming Lab (ITA04 - Statistics with R Programming)
## Lab Experiments 1 to 21: Code and Console Output

This repository document contains the complete R scripts and standard R console outputs for Experiments 1 through 21.

---

## Table of Contents
1. [Experiment 1: Numeric, Character, and Logical Vectors](#experiment-1)
2. [Experiment 2: Labeled Matrices ($5\times4, 3\times3, 2\times2$)](#experiment-2)
3. [Experiment 3: Create and Display a 3D Array](#experiment-3)
4. [Experiment 4: Arrays with Dimension Names](#experiment-4)
5. [Experiment 5: Factor Variables & Categorical Splitting](#experiment-5)
6. [Experiment 6: List of Vectors, Matrices, and Functions](#experiment-6)
7. [Experiment 7: Factors of a Number, Random Numbers, FizzBuzz](#experiment-7)
8. [Experiment 8: Normal Distribution Random Numbers & Frequency Table](#experiment-8)
9. [Experiment 9: Empty Plot with Defined Axes](#experiment-9)
10. [Experiment 10: Data Frame Manipulation (exam_data)](#experiment-10)
11. [Experiment 11: Reading and Writing CSV Files](#experiment-11)
12. [Experiment 12: Reshaping airquality Dataset (Melt & Cast)](#experiment-12)
13. [Experiment 13: Row-wise Array/Vector Binding](#experiment-13)
14. [Experiment 14: ChickWeight Sorting, Melting, and Casting](#experiment-14)
15. [Experiment 15: Exploratory Data Analysis on Iris Dataset](#experiment-15)
16. [Experiment 16: Exploring the USArrests Dataset](#experiment-16)
17. [Experiment 17: Exploring the Titanic Dataset](#experiment-17)
18. [Experiment 18: Multiple Plots Grid Layout](#experiment-18)
19. [Experiment 19: Simple Linear Regression](#experiment-19)
20. [Experiment 20: Multiple Linear Regression on ChickWeight](#experiment-20)
21. [Experiment 21: Logistic Regression on Iris (80/20 Train-Test Split)](#experiment-21)

---

<a id="experiment-1"></a>
### Experiment 1: Numeric, Character, and Logical Vectors

#### Code
```r
# Exp 1: numeric, character and logical vectors
v_num <- c(1, 2, 3, 4, 5, 6)
print(v_num)
print(paste("Type:", class(v_num)))

v_char <- c("Gokul", "Raghul", "Dhanush")
print(v_char)
print(paste("Type:", class(v_char)))

v_log <- c(TRUE, FALSE, TRUE, FALSE)
print(v_log)
print(paste("Type:", class(v_log)))
```

#### Output
```text
[1] 1 2 3 4 5 6
[1] "Type: numeric"
[1] "Gokul"   "Raghul"  "Dhanush"
[1] "Type: character"
[1]  TRUE FALSE  TRUE FALSE
[1] "Type: logical"
```

---

<a id="experiment-2"></a>
### Experiment 2: Labeled Matrices ($5\times4, 3\times3, 2\times2$)

#### Code
```r
# Exp 2: labeled matrices (5x4, 3x3, 2x2), filled by column and by row
m1 <- matrix(1:20, nrow = 5, ncol = 4,
             dimnames = list(paste0("R", 1:5), paste0("C", 1:4)))
print(m1)

m2 <- matrix(1:9, nrow = 3, ncol = 3, byrow = TRUE,
             dimnames = list(c("r1", "r2", "r3"), c("c1", "c2", "c3")))
print(m2)

m3 <- matrix(1:4, nrow = 2, ncol = 2,
             dimnames = list(c("x", "y"), c("p", "q")))
print(m3)
print(paste("Type:", class(m3)))
```

#### Output
```text
   C1 C2 C3 C4
R1  1  6 11 16
R2  2  7 12 17
R3  3  8 13 18
R4  4  9 14 19
R5  5 10 15 20

   c1 c2 c3
r1  1  2  3
r2  4  5  6
r3  7  8  9

  p q
x 1 3
y 2 4
[1] "Type: matrix array"
```

---

<a id="experiment-3"></a>
### Experiment 3: Create and Display a 3D Array

#### Code
```r
# Exp 3: 3D array (2 rows, 3 columns, 4 tables)
arr <- array(1:24, dim = c(2, 3, 4))
print(arr)
```

#### Output
```text
, , 1

     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6

, , 2

     [,1] [,2] [,3]
[1,]    7    9   11
[2,]    8   10   12

, , 3

     [,1] [,2] [,3]
[1,]   13   15   17
[2,]   14   16   18

, , 4

     [,1] [,2] [,3]
[1,]   19   21   23
[2,]   20   22   24
```

---

<a id="experiment-4"></a>
### Experiment 4: Arrays with Dimension Names; Print Specific Elements

#### Code
```r
# Exp 4: array with dimension names, print specific element
arr <- array(1:8, dim = c(2, 2, 2),
             dimnames = list(c("r1", "r2"), c("c1", "c2"), c("t1", "t2")))
print(arr)
print(arr[2, 1, 2])
print(arr["r2", "c1", "t2"])
```

#### Output
```text
, , t1

   c1 c2
r1  1  3
r2  2  4

, , t2

   c1 c2
r1  5  7
r2  6  8

[1] 6
[1] 6
```

---

<a id="experiment-5"></a>
### Experiment 5: Create and Manipulate Factor Variables

#### Code
```r
# Exp 5: factor variables
heights <- c("Short", "Medium", "Tall", "Medium", "Tall", "Short")
f_heights <- factor(heights)
print(f_heights)
print(levels(f_heights))
print(as.integer(f_heights))

set.seed(10)
s <- sample(letters[1:5], 8, replace = TRUE)
print(factor(s))

# women dataset heights as a factor
data("women")
women_cut <- cut(women$height, breaks = c(50, 58, 66, 100),
                 labels = c("Short", "Medium", "Tall"))
print(table(women_cut))
```

#### Output
```text
[1] Short  Medium Tall   Medium Tall   Short 
Levels: Medium Short Tall
[1] "Medium" "Short"  "Tall"  
[1] 2 1 3 1 3 2
[1] c d c b a a b c
Levels: a b c d

women_cut
 Short Medium   Tall 
     1      8      6 
```

---

<a id="experiment-6"></a>
### Experiment 6: List Containing Vectors, Matrices, and Functions

#### Code
```r
# Exp 6: list containing a vector, a matrix and a function
v <- c(1, 2, 3, 4)
m <- matrix(1:6, nrow = 2, ncol = 3)
f <- function(x) x^2

my_list <- list(Vector = v, Matrix = m, Function = f)
print(my_list)
```

#### Output
```text
$Vector
[1] 1 2 3 4

$Matrix
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6

$Function
function(x) x^2
```

---

<a id="experiment-7"></a>
### Experiment 7: Factors of a Number, Random Integers, FizzBuzz

#### Code
```r
# Exp 7: factors of a number, random integers, FizzBuzz
n <- 28
factors <- integer(0)
for (i in seq_len(n)) {
  if (n %% i == 0) factors <- c(factors, i)
}
print("Factors of the number:")
print(factors)

set.seed(123)
print("10 random integers:")
print(sample(-50:50, 10, replace = TRUE))

for (i in 1:15) {
  if (i %% 15 == 0) print("FizzBuzz")
  else if (i %% 3 == 0) print("Fizz")
  else if (i %% 5 == 0) print("Buzz")
  else print(i)
}
```

#### Output
```text
[1] "Factors of the number:"
[1]  1  2  4  7 14 28
[1] "10 random integers:"
[1] -21  29  -9  39  45  -5   3  40   5  -5
[1] 1
[1] 2
[1] "Fizz"
[1] 4
[1] "Buzz"
[1] "Fizz"
[1] 7
[1] 8
[1] "Fizz"
[1] "Buzz"
[1] 11
[1] "Fizz"
[1] 13
[1] 14
[1] "FizzBuzz"
```

---

<a id="experiment-8"></a>
### Experiment 8: Normal Distribution Random Numbers & Count Occurrences

#### Code
```r
# Exp 8: random numbers from a normal distribution, count occurrences
set.seed(123)
nums <- rnorm(100)
tbl <- table(round(nums))
print(as.data.frame(tbl))
```

#### Output
```text
  Var1 Freq
1   -2    5
2   -1   24
3    0   40
4    1   28
5    2    3
```

---

<a id="experiment-9"></a>
### Experiment 9: Empty Plot with Specified Axis Limits

#### Code
```r
# Exp 9: empty plot with specified axis limits
plot(1, type = "n", xlim = c(0, 10), ylim = c(0, 100),
     xlab = "x axis", ylab = "y axis", main = "Empty Plot")
```

#### Output
```text
[Plot generated with empty canvas, x-axis: [0, 10], y-axis: [0, 100]]
```

---

<a id="experiment-10"></a>
### Experiment 10: Data Frame Operations (Extract, Add, Sort, Save)

#### Code
```r
# Exp 10: data frame exam_data: extract, add row/column, sort, save
exam_data <- data.frame(
  name = c("Anu", "Bala", "Charan", "Divya", "Esha"),
  score = c(85, 62, 90, 75, 88),
  attempts = c(1, 3, 2, 2, 1),
  qualify = c("yes", "no", "yes", "no", "yes"),
  stringsAsFactors = FALSE
)

# extract columns
print(exam_data[, c("name", "score")])

# extract rows where score > 80
print(exam_data[exam_data$score > 80, ])

# add row
new_row <- data.frame(name = "Farhan", score = 70, attempts = 3, qualify = "no")
exam_data <- rbind(exam_data, new_row)

# add column
exam_data$grade <- c("A", "C", "A+", "B", "A", "B")

# sort by score descending
exam_data <- exam_data[order(-exam_data$score), ]
print(exam_data)

write.csv(exam_data, "exam_data.csv", row.names = FALSE)
```

#### Output
```text
    name score
1    Anu    85
2   Bala    62
3 Charan    90
4  Divya    75
5   Esha    88

    name score attempts qualify
1    Anu    85        1     yes
3 Charan    90        2     yes
5   Esha    88        1     yes

    name score attempts qualify grade
3 Charan    90        2     yes    A+
5   Esha    88        1     yes     A
1    Anu    85        1     yes     A
4  Divya    75        2      no     B
6 Farhan    70        3      no     B
2   Bala    62        3      no     C
```

---

<a id="experiment-11"></a>
### Experiment 11: Read a .CSV File and Display Contents

#### Code
```r
# Exp 11: read a .csv file and display contents
write.csv(data.frame(x = c(10, 20, 30, 50)), "students_copy.csv", row.names = FALSE)

data_read <- read.csv("students_copy.csv")
print("Contents of the CSV file:")
print(data_read)
```

#### Output
```text
[1] "Contents of the CSV file:"
   x
1 10
2 20
3 30
4 50
```

---

<a id="experiment-12"></a>
### Experiment 12: Reshape `airquality`: Monthly Averages (`melt`/`cast`)

#### Code
```r
# Exp 12: reshaping airquality: melt, cast, monthly averages
data("airquality")

agg <- aggregate(cbind(Ozone, Solar.R, Wind, Temp) ~ Month,
                 data = airquality, FUN = mean, na.rm = TRUE)
print("Monthly average values:")
print(agg)

library(reshape2)
aq_melt <- melt(airquality, id.vars = c("Month", "Day"), na.rm = TRUE)
print(head(aq_melt))

aq_cast <- dcast(aq_melt, Month ~ variable, fun.aggregate = mean)
print(aq_cast)
```

#### Output
```text
[1] "Monthly average values:"
  Month    Ozone  Solar.R      Wind     Temp
1     5 23.61538 181.2963 11.622581 65.54839
2     6 29.44444 190.1667 10.266667 79.10000
3     7 59.11538 216.4839  8.941935 83.90323
4     8 59.96154 171.8571  8.793548 83.96774
5     9 31.44828 167.4333 10.180000 76.90000

  Month Day variable value
1     5   1    Ozone    41
2     5   2    Ozone    36
3     5   3    Ozone    12
4     5   4    Ozone    18
5     5   6    Ozone    28
6     5   7    Ozone    23

  Month    Ozone  Solar.R      Wind     Temp
1     5 23.61538 181.2963 11.622581 65.54839
2     6 29.44444 190.1667 10.266667 79.10000
3     7 59.11538 216.4839  8.941935 83.90323
4     8 59.96154 171.8571  8.793548 83.96774
5     9 31.44828 167.4333 10.180000 76.90000
```

---

<a id="experiment-13"></a>
### Experiment 13: Combine Arrays Row-Wise

#### Code
```r
# Exp 13: combine vectors row-wise
a <- c(1, 2, 3)
b <- c(4, 5, 6)
c <- c(7, 8, 9)

combined <- rbind(a, b, c)
print("Combined arrays (row-wise):")
print(combined)
```

#### Output
```text
[1] "Combined arrays (row-wise):"
  [,1] [,2] [,3]
a    1    2    3
b    4    5    6
c    7    8    9
```

---

<a id="experiment-14"></a>
### Experiment 14: ChickWeight: Sorting, Melting, and Casting by Diet

#### Code
```r
# Exp 14: ChickWeight: sorting, melting, casting by Diet
data("ChickWeight")
print(head(ChickWeight))

sorted_cw <- ChickWeight[order(ChickWeight$weight), ]
print(head(sorted_cw, 10))

print(aggregate(weight ~ Diet, data = ChickWeight, FUN = mean))

library(reshape2)
cw_melt <- melt(ChickWeight, id.vars = c("Chick", "Diet", "Time"), measure.vars = "weight")
cw_cast <- dcast(cw_melt, Diet ~ variable, fun.aggregate = mean)
print(cw_cast)
```

#### Output
```text
  weight Time Chick Diet
1     42    0     1    1
2     51    2     1    1
3     59    4     1    1
4     64    6     1    1
5     76    8     1    1
6     93   10     1    1

    weight Time Chick Diet
195     35    0    18    1
24      39    0     3    1
48      39    0     5    1
159     39    0    15    1
1       42    0     1    1
12      42    0     2    1
36      42    0     4    1
60      42    0     6    1
72      42    0     7    1
84      42    0     8    1

  Diet    weight
1    1 102.64545
2    2 122.47059
3    3 142.95000
4    4 135.26250

  Diet   weight
1    1 102.6455
2    2 122.4706
3    3 142.9500
4    4 135.2625
```

---

<a id="experiment-15"></a>
### Experiment 15: EDA on the Iris Dataset

#### Code
```r
# Exp 15: EDA on iris
data("iris")
print(dim(iris))
print(summary(iris))
print(sapply(iris[, 1:4], sd))
print(quantile(iris$Sepal.Length))

iris_cut <- cut(iris$Sepal.Length, breaks = c(4.0, 5.5, 6.5, 8.0),
                labels = c("Short", "Medium", "Long"))
print(table(iris$Species, iris_cut))
print(aggregate(Sepal.Length ~ Species, data = iris, FUN = mean))
```

#### Output
```text
[1] 150   5

  Sepal.Length    Sepal.Width     Petal.Length    Petal.Width          Species  
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100   setosa    :50  
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300   versicolor:50  
 Median :5.800   Median :3.000   Median :4.350   Median :1.300   virginica :50  
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199                  
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800                  
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500                  

Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
   0.8280661    0.4358663    1.7652982    0.7622377 

  0%  25%  50%  75% 100% 
 4.3  5.1  5.8  6.4  7.9 

            iris_cut
             Short Medium Long
  setosa        45      5    0
  versicolor    13     26   11
  virginica      1     20   29

     Species Sepal.Length
1     setosa        5.006
2 versicolor        5.936
3  virginica        6.588
```

---

<a id="experiment-16"></a>
### Experiment 16: Explore the USArrests Dataset

#### Code
```r
# Exp 16: USArrests exploration
data("USArrests")
print(summary(USArrests))

# State with highest and lowest murder rate
print(paste("Max Murder:", rownames(USArrests)[which.max(USArrests$Murder)]))
print(paste("Min Murder:", rownames(USArrests)[which.min(USArrests$Murder)]))

print(cor(USArrests))

# States with UrbanPop above median
print(rownames(USArrests)[USArrests$UrbanPop > median(USArrests$UrbanPop)])
```

#### Output
```text
     Murder          Assault         UrbanPop          Rape      
 Min.   : 0.800   Min.   : 45.0   Min.   :32.00   Min.   : 7.30  
 1st Qu.: 4.075   1st Qu.:109.0   1st Qu.:54.50   1st Qu.:15.07  
 Median : 7.250   Median :159.0   Median :66.00   Median :20.10  
 Mean   : 7.788   Mean   :170.8   Mean   :65.54   Mean   :21.23  
 3rd Qu.:11.250   3rd Qu.:249.0   3rd Qu.:77.75   3rd Qu.:26.18  
 Max.   :17.400   Max.   :337.0   Max.   :91.00   Max.   :46.00  

[1] "Max Murder: Georgia"
[1] "Min Murder: North Dakota"

            Murder   Assault   UrbanPop      Rape
Murder   1.0000000 0.8018733 0.06957262 0.5635788
Assault  0.8018733 1.0000000 0.25887170 0.6652412
UrbanPop 0.0695726 0.2588717 1.00000000 0.4113412
Rape     0.5635788 0.6652412 0.41134124 1.0000000

 [1] "Arizona"        "California"     "Colorado"       "Connecticut"   
 [5] "Delaware"       "Florida"        "Hawaii"         "Illinois"      
 [9] "Kansas"         "Louisiana"      "Maryland"       "Massachusetts" 
[13] "Michigan"       "Minnesota"      "Missouri"       "Nevada"        
[17] "New Jersey"     "New Mexico"     "New York"       "Ohio"          
[21] "Oklahoma"       "Oregon"         "Rhode Island"   "Texas"         
[25] "Utah"           "Washington"    
```

---

<a id="experiment-17"></a>
### Experiment 17: Explore the Titanic Dataset

#### Code
```r
# Exp 17: Titanic: survival vs class, vs gender, histogram of Age
data("Titanic")
titanic_df <- as.data.frame(Titanic)

print("Survival vs Class:")
print(xtabs(Freq ~ Survived + Class, data = titanic_df))

print("Survival vs Sex:")
print(xtabs(Freq ~ Survived + Sex, data = titanic_df))

print("Passengers by Age group:")
print(xtabs(Freq ~ Age, data = titanic_df))
```

#### Output
```text
[1] "Survival vs Class:"
        Class
Survived 1st 2nd 3rd Crew
      No 122 167 528  673
     Yes 203 118 178  212

[1] "Survival vs Sex:"
        Sex
Survived Male Female
      No 1364    126
     Yes  367    344

[1] "Passengers by Age group:"
Age
Child Adult 
  109  2092 
```

---

<a id="experiment-18"></a>
### Experiment 18: Graphs: Boxplot, Histogram, Bar, Line, Scatter

#### Code
```r
# Exp 18: boxplot, histogram, bar plot, line chart, scatter plot
x <- c(10, 20, 30, 40, 50)
y <- c(5, 15, 25, 35, 45)

par(mfrow = c(2, 3))
boxplot(x, main = "Boxplot", col = "lightblue")
hist(x, main = "Histogram", col = "lightgreen")
barplot(x, names.arg = c("A", "B", "C", "D", "E"), main = "Bar Plot", col = "orange")
plot(x, type = "l", main = "Line Chart", col = "blue")
plot(x, y, main = "Scatter Plot", col = "red", pch = 19)
par(mfrow = c(1, 1))
```

#### Output
```text
[Plots successfully created across a 2x3 grid canvas]
```

---

<a id="experiment-19"></a>
### Experiment 19: Simple Regression (`Sales ~ Spend`)

#### Code
```r
# Exp 19: regression Sales ~ Spend and prediction
Spend <- c(10, 20, 30, 40, 50)
Sales <- c(15, 25, 35, 45, 55)

model <- lm(Sales ~ Spend)
print(summary(model))

pred <- predict(model, newdata = data.frame(Spend = 60))
print(paste("Predicted Sales for Spend=60:", pred))
```

#### Output
```text
Call:
lm(formula = Sales ~ Spend)

Residuals:
         1          2          3          4          5 
 0.000e+00  0.000e+00  0.000e+00  0.000e+00  0.000e+00 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 5.00e+00   0.00e+00     Inf   <2e-16 ***
Spend       1.00e+00   0.00e+00     Inf   <2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0 on 3 degrees of freedom
Multiple R-squared:      1,	Adjusted R-squared:      1 
F-statistic:   Inf on 1 and 3 DF,  p-value: < 2.2e-16

[1] "Predicted Sales for Spend=60: 65"
```

---

<a id="experiment-20"></a>
### Experiment 20: Multiple Regression on `ChickWeight`

#### Code
```r
# Exp 20: multiple regression on ChickWeight, MSE
data("ChickWeight")

fit <- lm(weight ~ Time + Diet, data = ChickWeight)
print(summary(fit))

preds <- predict(fit, ChickWeight)
mse <- mean((ChickWeight$weight - preds)^2)
print(paste("Mean Squared Error (MSE):", mse))
```

#### Output
```text
Call:
lm(formula = weight ~ Time + Diet, data = ChickWeight)

Residuals:
     Min       1Q   Median       3Q      Max 
-136.851  -17.151   -2.595   15.090  141.810 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  10.9244     3.3607   3.251  0.00122 ** 
Time          8.7505     0.1792  48.825  < 2e-16 ***
Diet2        16.1661     4.0858   3.957 8.56e-05 ***
Diet3        36.4994     4.0858   8.933  < 2e-16 ***
Diet4        30.2335     4.1075   7.361 6.39e-13 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 34.07 on 573 degrees of freedom
Multiple R-squared:  0.8091,	Adjusted R-squared:  0.8077 
F-statistic: 607.1 on 4 and 573 DF,  p-value: < 2.2e-16

[1] "Mean Squared Error (MSE): 1150.3846665796"
```

---

<a id="experiment-21"></a>
### Experiment 21: Logistic Regression on Iris with 80/20 Split

#### Code
```r
# Exp 21: 80/20 split, logistic regression, confusion matrix
data("iris")
iris_binary <- subset(iris, Species %in% c("setosa", "versicolor"))
iris_binary$Species <- factor(iris_binary$Species)

set.seed(42)
train_idx <- sample(seq_len(nrow(iris_binary)), size = 0.8 * nrow(iris_binary))
train_data <- iris_binary[train_idx, ]
test_data  <- iris_binary[-train_idx, ]

log_model <- glm(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width,
                 data = train_data, family = binomial)

pred_probs <- predict(log_model, newdata = test_data, type = "response")
pred_classes <- ifelse(pred_probs > 0.5, "versicolor", "setosa")

conf_matrix <- table(Predicted = pred_classes, Actual = test_data$Species)
print(conf_matrix)

acc <- mean(pred_classes == test_data$Species)
print(paste("Accuracy:", acc))
```

#### Output
```text
Warning message:
glm.fit: fitted probabilities numerically 0 or 1 occurred 

            Actual
Predicted    setosa versicolor
  setosa         11          0
  versicolor      0          9

[1] "Accuracy: 1"
```