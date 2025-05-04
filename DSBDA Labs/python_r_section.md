# Part B - Python & R Programming FAQ

## Transpose in R
Converts rows to columns and vice versa using `t()` function.

## Sorting Algorithms in R
Quick sort, merge sort, insertion sort, heap sort accessible via `sort()`, `order()`, and `arrange()`.

## Adding Datasets in R
Use `rbind()` for rows, `cbind()` for columns, or `merge()` for joining by keys.

## Memory Limit in R
Determined by OS and hardware; check with `memory.limit()` and modify using `memory.limit(size)`.

## Reading CSV in R
Use `read.csv("filename.csv")` or `read_csv()` from readr package.

## Writing R Commands
Type directly in R console or script files (.R) and execute with `source()`.

## Sorting Function in R
`sort()` for vectors, `order()` for obtaining indices, `arrange()` from dplyr for dataframes.

## Merging Dataframes
Use `merge(df1, df2, by="key_column")` or `dplyr::left_join()`, `right_join()`, `inner_join()`.

## Array Words in Decreasing Frequency
```r
words <- c("apple", "banana", "apple", "orange", "banana", "apple")
sort(table(words), decreasing=TRUE)
```

## which() Function
Returns indices of elements meeting a condition.
```r
which(x > 5)  # Returns indices where x is greater than 5
```

## subset() Function
Extracts subsets of data meeting specified conditions.
```r
subset(df, age > 30 & gender == "M")
```

## Data Analysis Tools
R, Python, Tableau, Power BI, Excel, SQL, SAS, SPSS, Stata, and Jupyter Notebooks.

## Common Data Analysis Problems
Missing data, outliers, inconsistent formatting, data quality issues, and insufficient sample size.

## Packages Function Groups
- caret: train(), confusionMatrix(), createDataPartition()
- e1071: svm(), naiveBayes(), tune()
- caTools: sample.split(), LogitBoost()
- class: knn(), knn.cv()
- gmodels: CrossTable(), fit.contrast()

## Handling Missing Values
Use `na.omit()`, `na.rm=TRUE`, `complete.cases()`, or imputation with `mice` package.

## Log Linear Models in R
Create using `glm()` function with family=poisson.

## K-Nearest Neighbor
Classification algorithm that predicts based on majority class of k-closest training examples.
```r
library(class)
knn(train, test, cl, k=3)
```

## Replace Missing Values with Mean
```r
replace_na_with_mean <- function(x) {
  x[is.na(x)] <- mean(x, na.rm=TRUE)
  return(x)
}
```

## Histogram Function
`hist(x, main="title", xlab="x-axis", col="color")`.

## Supervised vs Unsupervised Learning
Supervised uses labeled data for prediction; unsupervised finds patterns in unlabeled data.

## MapReduce in R
Use packages like rmr2 or SparkR with appropriate configuration.

## Text Data Processing Techniques
Tokenization, stemming, lemmatization, TF-IDF, word embeddings, and sentiment analysis.

## Creating Area Chart
```r
plot(x, y, type="n")
polygon(c(x, rev(x)), c(y, rep(0, length(y))), col="blue")
```

## Creating Heat Map
```r
heatmap(matrix_data, col=heat.colors(20), Colv=NA, scale="column")
```

## Creating Correlogram
```r
library(corrplot)
corrplot(cor(data), method="circle")
```

## Plotting Geographical Map
```r
library(maps)
map("world")
points(longitude, latitude, col="red")
```

## Plotting Entire Data
```r
plot(dataframe)  # Basic scatterplot matrix
```
Or use:
```r
library(GGally)
ggpairs(dataframe)  # Advanced visualization of all variables
```