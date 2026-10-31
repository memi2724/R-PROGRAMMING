# R Programming Lab (ITA04 - Statistics with R Programming)

Code and console output for each lab experiment. Scripts are in `scripts/`; saved outputs are in `outputs/`.

To regenerate every output: `Rscript run_all.R` (run from the repo root).

Experiments 9, 16, 17 and 18 produce plots; open those scripts in RStudio to view the graphs.

## Contents

- [Experiment 1: Create numeric, character and logical vectors](#01)
- [Experiment 2: Create labeled matrices (5x4, 3x3, 2x2)](#02)
- [Experiment 3: Create and display a 3D array](#03)
- [Experiment 4: Arrays with dimension names; print specific elements](#04)
- [Experiment 5: Create and manipulate factor variables](#05)
- [Experiment 6: List containing vectors, matrices and functions](#06)
- [Experiment 7: Factors of a number, random integers, FizzBuzz](#07)
- [Experiment 8: Normal distribution random numbers; count occurrences](#08)
- [Experiment 9: Empty plot with specified axis limits](#09)
- [Experiment 10: Data frame exam_data: extract, add, sort, save](#10)
- [Experiment 11: Read a .csv file and display contents](#11)
- [Experiment 12: Reshape airquality: monthly averages (melt/cast)](#12)
- [Experiment 13: Combine arrays row-wise](#13)
- [Experiment 14: ChickWeight: sorting, melting, casting by Diet](#14)
- [Experiment 15: EDA on the iris dataset](#15)
- [Experiment 16: Explore the USArrests dataset](#16)
- [Experiment 17: Explore the Titanic dataset](#17)
- [Experiment 18: Graphs: boxplot, histogram, bar, line, scatter](#18)
- [Experiment 19: Simple regression (Sales ~ Spend)](#19)
- [Experiment 20: Multiple regression on ChickWeight](#20)
- [Experiment 21: Logistic regression on iris with 80/20 split](#21)
- [Practice Question 1: If-else and arithmetic/boolean operators](#p01)
- [Practice Question 2: For loop: multiplication table](#p02)
- [Practice Question 3: While loop: sum of digits](#p03)
- [Practice Question 4: break and next](#p04)
- [Practice Question 5: Looping over a list](#p05)
- [Practice Question 6: Default argument values](#p06)
- [Practice Question 7: Explicit and implicit return](#p07)
- [Practice Question 8: Returning multiple values as a list](#p08)
- [Practice Question 9: Functions are objects](#p09)
- [Practice Question 10: Recursion: factorial](#p10)
- [Practice Question 11: Recursion: Fibonacci series](#p11)

<a id="01"></a>
## Experiment 1: Create numeric, character and logical vectors

**Code** (`scripts/01_vectors.R`)

```r
# Exp 1: numeric, character and logical vectors
a <- c(1, 2, 3, 4, 5, 6)
print(a)
print(paste("Type:", class(a)))

b <- c("Gokul", "Raghul", "Dhanush")
print(b)
print(paste("Type:", class(b)))

c1 <- c(TRUE, FALSE, TRUE, FALSE)
print(c1)
print(paste("Type:", class(c1)))
```

**Output**

```
[1] 1 2 3 4 5 6
[1] "Type: numeric"
[1] "Gokul"   "Raghul"  "Dhanush"
[1] "Type: character"
[1]  TRUE FALSE  TRUE FALSE
[1] "Type: logical"
```

<a id="02"></a>
## Experiment 2: Create labeled matrices (5x4, 3x3, 2x2)

**Code** (`scripts/02_matrices.R`)

```r
# Exp 2: labeled matrices (5x4, 3x3, 2x2), filled by column and by row
a <- matrix(1:20, nrow = 5, ncol = 4,
            dimnames = list(paste0("R", 1:5), paste0("C", 1:4)))
print(a)

b <- matrix(1:9, nrow = 3, ncol = 3, byrow = TRUE,
            dimnames = list(c("r1", "r2", "r3"), c("c1", "c2", "c3")))
print(b)

d <- matrix(1:4, nrow = 2, ncol = 2,
            dimnames = list(c("x", "y"), c("p", "q")))
print(d)
print(paste("Type:", class(b)))
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/02_matrices.txt` here._

<a id="03"></a>
## Experiment 3: Create and display a 3D array

**Code** (`scripts/03_array_3d.R`)

```r
# Exp 3: 3D array (2 rows, 3 columns, 4 tables)
a <- 1:24
arr <- array(a, dim = c(2, 3, 4))
print(arr)
```

**Output**

```
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

<a id="04"></a>
## Experiment 4: Arrays with dimension names; print specific elements

**Code** (`scripts/04_array_dimnames.R`)

```r
# Exp 4: array with dimension names, print specific element
a <- 1:8
b <- array(a, dim = c(2, 2, 2),
           dimnames = list(c("r1", "r2"), c("c1", "c2"), c("t1", "t2")))
print(b)
print(b[2, 1, 2])
print(b["r2", "c1", "t2"])
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/04_array_dimnames.txt` here._

<a id="05"></a>
## Experiment 5: Create and manipulate factor variables

**Code** (`scripts/05_factors.R`)

```r
# Exp 5: factor variables
a <- c("Short", "Medium", "Tall", "Medium", "Tall", "Short")
b <- factor(a)
print(b)
print(levels(b))
print(as.integer(b))

set.seed(10)
c1 <- sample(LETTERS[1:5], 8, replace = TRUE)
d <- factor(c1)
print(d)

# women dataset heights as a factor
h <- cut(women$height, breaks = c(0, 60, 66, 100), labels = c("Short", "Medium", "Tall"))
print(table(h))
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/05_factors.txt` here._

<a id="06"></a>
## Experiment 6: List containing vectors, matrices and functions

**Code** (`scripts/06_list.R`)

```r
# Exp 6: list containing a vector, a matrix and a function
a <- c(1, 2, 3, 4)
b <- matrix(1:6, nrow = 2, ncol = 3)
f <- function(x) x^2
mylist <- list(Vector = a, Matrix = b, Function = f)
print(mylist)
```

**Output**

```
$Vector
[1] 1 2 3 4

$Matrix
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6

$Function
function(x) x^2
```

<a id="07"></a>
## Experiment 7: Factors of a number, random integers, FizzBuzz

**Code** (`scripts/07_basic_tasks.R`)

```r
# Exp 7: factors of a number, random integers, FizzBuzz
n <- 12L
factors <- integer(0)
for (i in seq_len(n)) {
  if (n %% i == 0L) factors <- c(factors, i)
}
print("Factors of the number:")
print(factors)

set.seed(123)
print("10 random integers:")
print(sample(-50:50, 10, replace = TRUE))

for (i in 1:100) {
  if (i %% 15 == 0) print("FizzBuzz")
  else if (i %% 3 == 0) print("Fizz")
  else if (i %% 5 == 0) print("Buzz")
  else print(i)
}
```

**Output**

```
[1] "Factors of the number:"
[1]  1  2  3  4  6 12
[1] "10 random integers:"
 [1] -20  28   0 -37  16  -9  -1  -8  50 -37
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
[1] 16
[1] 17
[1] "Fizz"
[1] 19
[1] "Buzz"
[1] "Fizz"
[1] 22
[1] 23
[1] "Fizz"
[1] "Buzz"
[1] 26
[1] "Fizz"
[1] 28
[1] 29
[1] "FizzBuzz"
[1] 31
[1] 32
[1] "Fizz"
[1] 34
[1] "Buzz"
[1] "Fizz"
[1] 37
[1] 38
[1] "Fizz"
[1] "Buzz"
[1] 41
[1] "Fizz"
[1] 43
[1] 44
[1] "FizzBuzz"
[1] 46
[1] 47
[1] "Fizz"
[1] 49
[1] "Buzz"
[1] "Fizz"
[1] 52
[1] 53
[1] "Fizz"
[1] "Buzz"
[1] 56
[1] "Fizz"
[1] 58
[1] 59
[1] "FizzBuzz"
[1] 61
[1] 62
[1] "Fizz"
[1] 64
[1] "Buzz"
[1] "Fizz"
[1] 67
[1] 68
[1] "Fizz"
[1] "Buzz"
[1] 71
[1] "Fizz"
[1] 73
[1] 74
[1] "FizzBuzz"
[1] 76
[1] 77
[1] "Fizz"
[1] 79
[1] "Buzz"
[1] "Fizz"
[1] 82
[1] 83
[1] "Fizz"
[1] "Buzz"
[1] 86
[1] "Fizz"
[1] 88
[1] 89
[1] "FizzBuzz"
[1] 91
[1] 92
[1] "Fizz"
[1] 94
[1] "Buzz"
[1] "Fizz"
[1] 97
[1] 98
[1] "Fizz"
[1] "Buzz"
```

<a id="08"></a>
## Experiment 8: Normal distribution random numbers; count occurrences

**Code** (`scripts/08_normal_counts.R`)

```r
# Exp 8: random numbers from a normal distribution, count occurrences
set.seed(123)
x <- rnorm(100)
y <- table(round(x))
print(as.data.frame(y))
```

**Output**

```
  Var1 Freq
1   -2    4
2   -1   21
3    0   45
4    1   22
5    2    8
```

<a id="09"></a>
## Experiment 9: Empty plot with specified axis limits

**Code** (`scripts/09_empty_plot.R`)

```r
# Exp 9: empty plot with specified axis limits
plot(1, type = "n", xlim = c(0, 10), ylim = c(0, 100),
     xlab = "x axis", ylab = "y axis")
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/09_empty_plot.txt` here._

<a id="10"></a>
## Experiment 10: Data frame exam_data: extract, add, sort, save

**Code** (`scripts/10_dataframe.R`)

```r
# Exp 10: data frame exam_data: extract, add row/column, sort, save
exam_data <- data.frame(
  name     = c("Anu", "Bala", "Charan", "Divya", "Esha"),
  score    = c(85, 62, 90, 75, 88),
  attempts = c(1, 3, 2, 2, 1),
  qualify  = c("yes", "no", "yes", "no", "yes")
)
print(exam_data[, c("name", "score")])   # extract columns
print(exam_data[exam_data$score > 80, ]) # extract rows

exam_data <- rbind(exam_data,
                   data.frame(name = "Farhan", score = 70, attempts = 3, qualify = "no"))
exam_data$grade <- c("A", "C", "A+", "B", "A", "B")
exam_data <- exam_data[order(-exam_data$score), ]
write.csv(exam_data, "exam_data.csv", row.names = FALSE)
print(exam_data)
```

**Output**

```
(final printed data frame; the earlier extract steps print above it)
    name score attempts qualify grade
3 Charan    90        2     yes    A+
5   Esha    88        1     yes     A
1    Anu    85        1     yes     A
4  Divya    75        2      no     B
6 Farhan    70        3      no     B
2   Bala    62        3      no     C
```

<a id="11"></a>
## Experiment 11: Read a .csv file and display contents

**Code** (`scripts/11_read_csv.R`)

```r
# Exp 11: read a .csv file and display contents
write.csv(data.frame(x = c(10, 20, 30, 50)), "students_copy.csv", row.names = FALSE)
data <- read.csv("students_copy.csv")
print("Contents of the CSV file:")
print(data)
```

**Output**

```
[1] "Contents of the CSV file:"
   x
1 10
2 20
3 30
4 50
```

<a id="12"></a>
## Experiment 12: Reshape airquality: monthly averages (melt/cast)

**Code** (`scripts/12_airquality.R`)

```r
# Exp 12: reshaping airquality: melt, cast, monthly averages
data("airquality")
result <- aggregate(cbind(Ozone, Solar.R, Wind, Temp) ~ Month,
                    data = airquality, FUN = mean, na.rm = TRUE)
print("Monthly average values:")
print(result)

# melt / cast with reshape2 (install.packages("reshape2") if missing)
if (requireNamespace("reshape2", quietly = TRUE)) {
  library(reshape2)
  long <- melt(airquality, id.vars = c("Month", "Day"))
  print(head(long))
  wide <- dcast(long, Month ~ variable, fun.aggregate = mean, na.rm = TRUE)
  print(wide)
}
```

**Output**

```
[1] "Monthly average values:"
  Month    Ozone  Solar.R      Wind     Temp
1     5 24.12500 182.0417 11.504167 66.45833
2     6 29.44444 184.2222 12.177778 78.22222
3     7 59.11538 216.4231  8.523077 83.88462
4     8 60.00000 173.0870  8.860870 83.69565
5     9 31.44828 168.2069 10.075862 76.89655
```

<a id="13"></a>
## Experiment 13: Combine arrays row-wise

**Code** (`scripts/13_rbind.R`)

```r
# Exp 13: combine vectors row-wise
rm(list = ls())
a <- c(1, 2, 3)
b <- c(4, 5, 6)
c1 <- c(7, 8, 9)
d <- rbind(a, b, c1)
print("Combined arrays (row-wise):")
print(d)
```

**Output**

```
[1] "Combined arrays (row-wise):"
  [,1] [,2] [,3]
a    1    2    3
b    4    5    6
c1   7    8    9
```

<a id="14"></a>
## Experiment 14: ChickWeight: sorting, melting, casting by Diet

**Code** (`scripts/14_chickweight.R`)

```r
# Exp 14: ChickWeight: sorting, melting, casting by Diet
data("ChickWeight")
print(head(ChickWeight))
sorted <- ChickWeight[order(ChickWeight$weight), ]
print(head(sorted, 10))
print(aggregate(weight ~ Diet, ChickWeight, mean))

if (requireNamespace("reshape2", quietly = TRUE)) {
  library(reshape2)
  cw <- as.data.frame(ChickWeight)
  m <- melt(cw, id.vars = c("Chick", "Diet", "Time"), measure.vars = "weight")
  print(dcast(m, Diet ~ variable, fun.aggregate = mean))
}
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/14_chickweight.txt` here._

<a id="15"></a>
## Experiment 15: EDA on the iris dataset

**Code** (`scripts/15_iris_eda.R`)

```r
# Exp 15: EDA on iris
data("iris")
print(dim(iris))
print(summary(iris))
print(sapply(iris[, 1:4], sd))
print(quantile(iris$Sepal.Length))
print(aggregate(. ~ Species, iris, mean))

# pivot table and categorical grouping on Sepal.Length
iris$SepalCat <- cut(iris$Sepal.Length, breaks = c(0, 5.5, 6.5, 10),
                     labels = c("Short", "Medium", "Long"))
print(table(iris$Species, iris$SepalCat))
print(aggregate(Petal.Length ~ SepalCat, iris, mean))
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/15_iris_eda.txt` here._

<a id="16"></a>
## Experiment 16: Explore the USArrests dataset

**Code** (`scripts/16_usarrests.R`)

```r
# Exp 16: USArrests exploration
data("USArrests")
print(summary(USArrests))
print(rownames(USArrests)[which.max(USArrests$Rape)])  # state with most rape arrests
print(max(USArrests$Murder))
print(min(USArrests$Murder))
print(cor(USArrests))

print(rownames(USArrests)[USArrests$Assault > median(USArrests$Assault)])
print(rownames(USArrests)[USArrests$Murder <= quantile(USArrests$Murder, 0.25)])

par(mfrow = c(2, 2))
hist(USArrests$Murder, main = "Histogram of Murder", xlab = "Murder")
plot(density(USArrests$Murder), main = "Density of Murder")
plot(USArrests$Assault, USArrests$Murder, main = "Assault vs Murder",
     xlab = "Assault", ylab = "Murder")
barplot(head(USArrests$Murder, 10), names.arg = head(rownames(USArrests), 10),
        las = 2, main = "Murder (first 10 states)")
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/16_usarrests.txt` here._

<a id="17"></a>
## Experiment 17: Explore the Titanic dataset

**Code** (`scripts/17_titanic.R`)

```r
# Exp 17: Titanic: survival vs class, vs gender, histogram of Age
data("Titanic")
t <- as.data.frame(Titanic)

# weight by Freq so bars show people, not table rows
barplot(xtabs(Freq ~ Survived + Class, t), beside = TRUE, legend.text = TRUE,
        main = "Survival vs Class")
barplot(xtabs(Freq ~ Survived + Sex, t), beside = TRUE, legend.text = TRUE,
        main = "Survival vs Gender")

# Age in this dataset is Child/Adult only, so use a bar chart; a true
# age histogram needs the individual-level Titanic data (e.g. titanic package)
barplot(xtabs(Freq ~ Age, t), main = "Passengers by Age group")
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/17_titanic.txt` here._

<a id="18"></a>
## Experiment 18: Graphs: boxplot, histogram, bar, line, scatter

**Code** (`scripts/18_graphs.R`)

```r
# Exp 18: boxplot, histogram, bar plot, line chart, scatter plot
x <- c(10, 20, 30, 40, 50)
y <- c(5, 15, 25, 35, 45)
par(mfrow = c(2, 3))
boxplot(x, main = "Boxplot", col = "lightblue")
hist(x, main = "Histogram", col = "lightgreen")
barplot(x, main = "Bar Plot", col = "orange", names.arg = c("A", "B", "C", "D", "E"))
plot(x, type = "l", main = "Line Chart", col = "blue")
plot(x, y, main = "Scatter Plot", col = "red")
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/18_graphs.txt` here._

<a id="19"></a>
## Experiment 19: Simple regression (Sales ~ Spend)

**Code** (`scripts/19_simple_regression.R`)

```r
# Exp 19: regression Sales ~ Spend and prediction
Spend <- c(10, 20, 30, 40, 50)
Sales <- c(15, 25, 35, 45, 55)
model <- lm(Sales ~ Spend)
print(summary(model))
print(predict(model, data.frame(Spend = 60)))
```

**Output**

```
(prediction for Spend = 60)
 1
65
```

<a id="20"></a>
## Experiment 20: Multiple regression on ChickWeight

**Code** (`scripts/20_multiple_regression.R`)

```r
# Exp 20: multiple regression on ChickWeight, MSE
data("ChickWeight")
m <- lm(weight ~ Time + Diet, data = ChickWeight)
p <- predict(m)
print(mean((ChickWeight$weight - p)^2))
```

**Output**

```
[1] 1284.319
```

<a id="21"></a>
## Experiment 21: Logistic regression on iris with 80/20 split

**Code** (`scripts/21_logistic_iris.R`)

```r
# Exp 21: 80/20 split, logistic regression, confusion matrix
data("iris")
d <- subset(iris, Species %in% c("setosa", "versicolor"))
d$Species <- factor(d$Species)   # drop unused level

set.seed(42)
idx   <- sample(seq_len(nrow(d)), size = 0.8 * nrow(d))
train <- d[idx, ]
test  <- d[-idx, ]

m <- glm(Species ~ Petal.Length + Petal.Width, data = train, family = binomial)
prob <- predict(m, newdata = test, type = "response")
pred <- ifelse(prob > 0.5, "versicolor", "setosa")
print(table(Predicted = pred, Actual = test$Species))
print(paste("Accuracy:", mean(pred == test$Species)))
# Note: setosa/versicolor are perfectly separable, so glm warns that it did not converge.
```

**Output**

_Run `Rscript run_all.R`, then paste `outputs/21_logistic_iris.txt` here._

<a id="p01"></a>
## Practice Question 1: If-else and arithmetic/boolean operators

**Code** (`scripts/P01_ifelse_operators.R`)

```r
num <- 5
if (num > 0) {
  result <- "Positive"
} else if (num < 0) {
  result <- "Negative"
} else {
  result <- "Zero"
}
a <- 10
b <- 3
print(result)
print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a > b)
print(a == b)
print(a != b)
```

**Output**

```
[1] "Positive"
[1] 13
[1] 7
[1] 30
[1] 3.333333
[1] TRUE
[1] FALSE
[1] TRUE
```

<a id="p02"></a>
## Practice Question 2: For loop: multiplication table

**Code** (`scripts/P02_for_loop.R`)

```r
num <- 5
for (i in 1:10) {
  cat(num, "*", i, "=", num * i, "\n")
}
total <- 0
for (i in 1:10) total <- total + i
print(total)
```

**Output**

```
5 * 1 = 5
5 * 2 = 10
5 * 3 = 15
5 * 4 = 20
5 * 5 = 25
5 * 6 = 30
5 * 7 = 35
5 * 8 = 40
5 * 9 = 45
5 * 10 = 50
[1] 55
```

<a id="p03"></a>
## Practice Question 3: While loop: sum of digits

**Code** (`scripts/P03_while_loop.R`)

```r
num <- 1234
sum_digits <- 0
while (num > 0) {
  sum_digits <- sum_digits + num %% 10
  num <- num %/% 10
}
print(sum_digits)
```

**Output**

```
[1] 10
```

<a id="p04"></a>
## Practice Question 4: break and next

**Code** (`scripts/P04_break_next.R`)

```r
for (i in 1:10) {
  if (i == 3) next
  if (i == 8) break
  print(i)
}
```

**Output**

```
[1] 1
[1] 2
[1] 4
[1] 5
[1] 6
[1] 7
```

<a id="p05"></a>
## Practice Question 5: Looping over a list

**Code** (`scripts/P05_loop_list.R`)

```r
my_list <- list(a = 10, b = 20, c = 30)
for (item in my_list) print(item)
for (name in names(my_list)) cat(name, "=", my_list[[name]], "\n")
```

**Output**

```
[1] 10
[1] 20
[1] 30
a = 10
b = 20
c = 30
```

<a id="p06"></a>
## Practice Question 6: Default argument values

**Code** (`scripts/P06_default_args.R`)

```r
add_numbers <- function(a, b = 10) a + b
print(add_numbers(5))
print(add_numbers(5, 20))
```

**Output**

```
[1] 15
[1] 25
```

<a id="p07"></a>
## Practice Question 7: Explicit and implicit return

**Code** (`scripts/P07_return.R`)

```r
square_number <- function(x) x * x            # implicit return
cube_number <- function(x) return(x * x * x)  # explicit return
print(square_number(4))
print(cube_number(3))
```

**Output**

```
[1] 16
[1] 27
```

<a id="p08"></a>
## Practice Question 8: Returning multiple values as a list

**Code** (`scripts/P08_return_list.R`)

```r
calculate_stats <- function(x) {
  list(sum = sum(x), mean = mean(x), max = max(x), min = min(x))
}
print(calculate_stats(c(10, 20, 30, 40)))
```

**Output**

```
$sum
[1] 100

$mean
[1] 25

$max
[1] 40

$min
[1] 10
```

<a id="p09"></a>
## Practice Question 9: Functions are objects

**Code** (`scripts/P09_functions_objects.R`)

```r
my_function <- function(x) x + 1
print(class(my_function))
print(my_function(10))
another_function <- my_function
print(another_function(20))
```

**Output**

```
[1] "function"
[1] 11
[1] 21
```

<a id="p10"></a>
## Practice Question 10: Recursion: factorial

**Code** (`scripts/P10_factorial.R`)

```r
factorial_fun <- function(n) {
  if (n <= 1) return(1)
  n * factorial_fun(n - 1)
}
print(factorial_fun(5))
```

**Output**

```
[1] 120
```

<a id="p11"></a>
## Practice Question 11: Recursion: Fibonacci series

**Code** (`scripts/P11_fibonacci.R`)

```r
fibonacci <- function(n) {
  if (n == 0) return(0)
  if (n == 1) return(1)
  fibonacci(n - 1) + fibonacci(n - 2)
}
n <- 10
cat("Fibonacci Series using Recursion:\n")
for (i in 0:(n - 1)) cat(fibonacci(i), " ")
cat("\n")
```

**Output**

```
Fibonacci Series using Recursion:
0  1  1  2  3  5  8  13  21  34
```
