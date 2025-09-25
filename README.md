# Symbolic-Regression

## Introduction

Symbolic Regression is a regression analysis technique, used to develop and find interpretable mathematical expressions. Symbolic Regression will be used to generate a mathematical equation known as a regressor. A regressor will be used to calculate the lugs produced in 1991 in the vineyard dataset. With the use of Genetic Programming a regressor will be generated using methods below.

## Dataset Used


The data set used in performing this algorithm has been obtained from Smoothing Methods in Statistics in pages 146-147. The data was retrieved from a vineyard on a small island in Lake Erie. The vineyard was divided into 52 rows, in accordance with the 52 observations in the data sets. Each observation having the yields of the harvests measured by the total number of lugs, in the years 1989 , 1990 and 1991 separated by row. A lug is a basket container used to carry the plucked grapes, which holds approximately 13.6078 kilograms of grapes.

The row numbers are  ordered naturally, with row number increasing in the notion from northwest to southeast.\cite{web:lang:stats} The original dataset has been split randomly with 70\% being the training set and 30\% being the testing set. 

### Dataset Statistics

Title of Data Set: 192 vineyard
Variables : 3 
Observations : 52 
Attribute Characteristics: Continuous 
Missing Values: No
Duplicate rows : 1 
Further data pre-processing was made, by dropping duplicates in the dataset.

## Data Representation

The regressor is represented as an expression tree. Each individual of the tree is made up of the root node that is randomly selected from the functional set and the leaf nodes that are randomly selected from either the terminal set or functional set, to create expressions. An expression tree is known for its flexibility.Expression trees make it easier for the information at nodes to be accessed and manipulated.

The initial population was generated using the growth method. The growth method generates a tree with an initial depth of n. In this report, the initial depth of the tree is 0, to start generating simple trees.

## Fitness Function

A fitness function is a function used to calculate and assign a non-negative value, to evaluate how best suited an individual of the population.
In order to calculate a fitness function , the use of the mean absolute error is used to evaluate each equation -individual of the population.
$$
  \text{MAE} = \frac{1}{n} \sum \limits _{i = 1} ^{n} | Y_{i} - \hat{Y}_{i} |
$$
where :
n is the population size
$Y_{i}$ is the Y target, which is the number of lugs yielded in 1991
$\hat{Y}_{i}$ is the predicted value of Y, number of lugs yielded in 1991

## Selection Methods

A selection method randomly selects two or more individuals in the population as parents for the next generation. In this report, tournament selection is the selection method of choice. For k individuals, a random number of individuals are selected, for n, number of parents. The individuals with the smallest fitness score is selected for reproduction.

## Genetic Operators 

### Elitism

Elitism is a genetic operator which is used to keep the individuals with the best fitness scores, for the next generation. 10\% of the population is selected during Elitism for the new population.

### Crossover Operator

Crossover is a genetic operator used to reproduce the selected parents. A random integer is generated as a point. Parents at that point will swap to create new individuals of the population.60\% is generated using the cross-over genetic operator.A stricter crossover is applied against the individuals. The individual's fitness score is evaluated, and where the individual's fitness score is more than that of the parent, crossover should occur again.

### Mutation Operator

In mutation a individual taken from the population.A random integer is generated as a point. A new individual will be generated and inserted at the point. 15% of the generation will be made up using the mutation operator.\\ A stricter mutation, where after mutation, the individual's fitness score is evaluated. In the case where the mutated individual's fitness score is more than that of the parent, mutation should occur again.

## Termination Criterion

The maximum number of tree depth, number of generations and population size made the termination criterion, in this report.

## Parameters

Population size: 500
A large population size is used to increase population diversity.

Crossover Rate: 80% 
Crossover is applied against the individuals, if the random float is less than the crossover rate, crossover should occur, if crossover doesn't occur the individual should be added as is to the new population.

Mutation Rate: 15%
Mutation is applied against the individuals, if the random float is less than the mutation rate, mutation should occur, if mutation doesn't occur the individual should be added as it is.

Elistism Rate: 5%

Maximum tree depth = 3 
To control the growth of the trees generated, a max tree depth is used. After multiple simulations, the tree depth of 3, grew trees that were manageable and weren't too large to create noise.

Initial Population Generation Method: Growth Method

Functional set: {+,-,/,*}
Basic mathematical operands are used, these operands are stored as strings in the array. This assists with the creation of an expression tree, which is more interpretable and a regressor can be stored.

Terminal set: {x1,x2,c}
The terminal set consists of x1 which represents $x_{1}$ for the number of lugs produced in the year 1989 and x2 which represents $x_{2}$  for the number of lugs produced in 1990. After trail and error, a constant,c, with the value of 2, seemed to generate a better regressor.

