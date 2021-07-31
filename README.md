# Aggregate-Function-in-R--A-powerful-tool-for-data-frames

aggregate Function in R, In this tutorial, we are going to describe the aggregate function in R.

As the name indicate it’s aggregate the input data frame based on a given or specified function.

Let’s see the basic R syntax of an aggregate function.

aggregate(x = any_data, by = group_list, FUN = any_function)

The by an argument can list of columns and this is one of the main advantages of this function.

It can handle one or more columns of a data frame based on by parameter and FUN indicate function you can pass any kinds of functions here.

When we have different groups in our data frames the first steps is to calculate mean and sd.

Here we are going to explain simples examples of an aggregate function.

We are utilizing iris data frame for the aggregate calculations. Let’s load the data set into data frame ‘data’.

data <- iris
head(data) 
    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
 1          5.1         3.5          1.4         0.2  setosa
 2          4.9         3.0          1.4         0.2  setosa
 3          4.7         3.2          1.3         0.2  setosa
 4          4.6         3.1          1.5         0.2  setosa
 5          5.0         3.6          1.4         0.2  setosa
 6          5.4         3.9          1.7         0.4  setosa

aggregate Function in R- Examples

Example 1: Compute Mean by Group Using aggregate Function

LSTM Network in R » Recurrent Neural network »

aggregate(x = data[ , colnames(data) != "Species"],             
         by = list(data$Species),
          FUN = mean)
       Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
 1     setosa        5.006       3.428        1.462       0.246
 2 versicolor        5.936       2.770        4.260       1.326
 3  virginica        6.588       2.974        5.552       2.026

Example 2: Compute Sum by Group Using aggregate Function

aggregate(x = data[ , colnames(data) != "Species"],      
by = list(data$Species),
          FUN = sum)
      Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
 1     setosa        250.3       171.4         73.1        12.3
 2 versicolor        296.8       138.5        213.0        66.3
 3  virginica        329.4       148.7        277.6       101.3

Example 3: Compute SD by Group Using aggregate Function

aggregate(x = data[ , colnames(data) != "Species"],             
         by = list(data$Species),
          FUN = sd)
      Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
 1     setosa    0.3524897   0.3790644    0.1736640   0.1053856
 2 versicolor    0.5161711   0.3137983    0.4699110   0.1977527
 3  virginica    0.6358796   0.3224966    0.5518947   0.2746501

Sam way you can execute all other available functions while passing in FUN command.

Example 4: Applying aggregate Function to Data Containing NAs

data1<-data
data1[2,3]<-NA
aggregate(x = data1[ , colnames(data1) != "Species"], 
         by = list(data1$Species),
          FUN = mean)
       Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
 1     setosa        5.006       3.428           NA       0.246
 2 versicolor        5.936       2.770        4.260       1.326
 3  virginica        6.588       2.974        5.552       2.026

Here you can see Petal Length mean is not calculated because of NA values in data frame.

Example 5: Applying aggregate Function to Data Containing NAs with na.rm


aggregate(x = data1[ , colnames(data1) != "Species"],       
          by = list(data1$Species),
          FUN = mean,
          na.rm = TRUE)
          
       Group.1 Sepal.Length Sepal.Width Petal.Length Petal.Width
 1     setosa        5.006       3.428     1.463265       0.246
 2 versicolor        5.936       2.770     4.260000       1.326
 3  virginica        6.588       2.974     5.552000       2.026

Conclusion

Hope you have found the above information is useful. Here we discussed aggregate function to compute descriptive statistics by group and however many other better functions also available in terms of faster compilation.
