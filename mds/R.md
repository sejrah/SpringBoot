# R is case sensitive

# clear the entire workspace
rm(list = ls())

# removes two variables
rm(a,b)

# special keyword pi
pi

# Data types
# Decimals values like 4.5 are called numerics.
# Natural numbers like 4L are called integers. Integers are also numerics.
# Boolean values (TRUE or FALSE) are called logical.
# Text (or string) values are called characters.

# 0.3 is converted to TRUE
var2 <- 0.3
var2_log <- as.logical(var2)
var2_log
[1] TRUE
*****************************************************
poker_vector1 <- c(140, -50, 20, -120, 240)
names(poker_vector1) <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")

poker_vector2 <- c(Monday = 140, -50, 20, -120, 240)

roulette_vector1 <- c(-24, -50, 100, -350, 10)
days_vector <- names(poker_vector1)
names(roulette_vector1) <- days_vector

roulette_vector2 <- c(-24, -50, 100, -350, 10)
names(roulette_vector2) <- "Monday"

> poker_vector1
   Monday   Tuesday Wednesday  Thursday    Friday 
      140       -50        20      -120       240
> poker_vector2
Monday                             
   140    -50     20   -120    240
> roulette_vector1
   Monday   Tuesday Wednesday  Thursday    Friday 
      -24       -50       100      -350        10
> roulette_vector2
Monday   <NA>   <NA>   <NA>   <NA> 
   -24    -50    100   -350     10
> days_vector
[1] "Monday"    "Tuesday"   "Wednesday" "Thursday"  "Friday"

vector subsetting
some_vector <- c(140, -50, 20, -120, 240)
some_vector_midvalues <- some_vector[c(2,4)] 				# incorrect if you want to select 2nd to 4th value; correct if you want to select 2nd and 4th only
some_vector_midvalues <- some_vector[c(2,3,4)] 				# correct
some_vector_midvalues <- some_vector[2:4] 					# correct
some_vector_midvalues <- some_vector["Tuesday":"Friday"] 	# incorrect
some_vector_midvalues <- some_vector[c("Tuesday","Thursday","Friday"] 	# correct
some_vector_endweek <- some_vector["Thursday","Friday"] 	# correct
some_vector_endweek <- some_vector[c("Thursday","Friday")] 	# correct
some_vector_endweek <- some_vector[c(FALSE,TRUE)] 			# incorrect
some_vector_endweek <- some_vector[c(FALSE,TRUE,FALSE,FALSE,FALSE)]	# correct


poker_vector <- c(140, -50, 20, -120, 240)
selection_vector <- poker_vector > 0 			# profitable days_vector
poker_profits <- poker_vector[selection_vector] # assign amounts of profitable days to new vector

# Select amounts for profitable roulette days: roulette_profits
roulette_profits <- roulette_vector[roulette_vector > 0]

# Sum of the profitable roulette days: roulette_total_profit
roulette_total_profit <- sum(roulette_profits)

# Number of profitable roulette days: num_profitable_days
num_profitable_days <- sum(roulette_vector > 0)
*****************************************************
Matrices
# Star Wars box office in millions (!)
box <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8) #1st, 3rd and 5th are US sales

# Create star_wars_matrix
star_wars_matrix <- matrix(box, byrow=TRUE, ncol=2)
*****
# Star Wars box office in millions (!)
new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)

# Create star_wars_matrix
star_wars_matrix <- rbind(new_hope, empire_strikes, return_jedi)
*****
# Star Wars box office in millions (!)
new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)
star_wars_matrix <- rbind(new_hope, empire_strikes, return_jedi)

# Name the columns and rows of star_wars_matrix
colnames(star_wars_matrix) <- c("US", "non-US")
rownames(star_wars_matrix) <- c("A New Hope", "The Empire Strikes Back", "Return of the Jedi")

col <- c("US", "non-US")
row <- c("A New Hope", "The Empire Strikes Back", "Return of the Jedi")
star_wars_matrix <- matrix(c(new_hope, empire_strikes, return_jedi), 
                           byrow = TRUE, nrow = 3, dimnames = list(row, col))

# Calculate the worldwide box office: worldwide_vector
worldwide_vector <- rowSums(star_wars_matrix)
# Bind the new variable worldwide_vector as a column to star_wars_matrix: star_wars_ext
star_wars_ext <- cbind(star_wars_matrix, worldwide_vector)

# Combine both Star Wars trilogies in one matrix: all_wars_matrix
all_wars_matrix <- rbind(star_wars_matrix, star_wars_matrix2)

# Total revenue for US and non-US: total_revenue_vector
total_revenue_vector <- colSums(all_wars_matrix)
*****
# Select all US box office revenue
star_wars_matrix[,"US"]

# Select revenue for "A New Hope"
star_wars_matrix["A New Hope",]

# Average non-US revenue per movie: non_us_all
non_us_all <- mean(star_wars_matrix[,"non-US"])
  
# Average non-US revenue of first two movies: non_us_some
non_us_some <- mean(star_wars_matrix[1:2,"non-US"])

# All figures for "A New Hope" and "Return of the Jedi"
star_wars_matrix[c(1,3),]

# Select the US revenues for "A New Hope" and "The Empire Strikes Back"
star_wars_matrix[c(TRUE,TRUE,FALSE),c(TRUE,FALSE)]

# Select the last two rows and both columns
star_wars_matrix[c(FALSE,TRUE,TRUE),c(TRUE,TRUE)]

# Select the non-US revenue for "The Empire Strikes Back"
star_wars_matrix[c(FALSE,TRUE,FALSE),c(FALSE,TRUE)]

#selects the total revenue for the second, fourth and sixth movie in the matrix
all_wars_matrix[seq(2, 6, by = 2), "total"]
all_wars_matrix[c(F,T), "total"]

# Combine view_count_1 and view_count_2 in a new matrix: view_count_all
view_count_all <- cbind(view_count_1,view_count_2)

# Subset view counts for three loudest debaters: view_count_loud
view_count_loud <- view_count_all[,c("Rachel","Walter","Dave")]

# Use colSums() to calculate the number of views: total_views_loud
total_views_loud <- colSums(view_count_loud)

# Calculate the money that remains after subtracting the commission: remaining
remaining <- star_wars_matrix -(star_wars_matrix*commission_rates)

# Calculate income per film: remaining_tot
remaining_tot <- rowSums(remaining)

# Calculate profit
profit <- remaining_tot-budget
*****************************************************
Factors
# Definition of hand_vector
hand_vector <- c("Right", "Left", "Left", "Right", "Left")

# Convert hand_vector to a factor: hand_factor
hand_factor <-factor(hand_vector)

# Display the structure of hand_factor
hand_factor
[1] Right Left  Left  Right Left 
Levels: Left Right

str(hand_factor)
Factor w/ 2 levels "Left","Right": 2 1 1 2 1

my_vector <- c("L", "S", "L", "M", "M")

# Option 1
my_factor <- factor(my_vector)
levels(my_factor) <- c("Large", "Medium", "Small")

# Option 2
my_factor <- factor(my_vector,
                    levels = c("S", "M", "L"),
                    labels = c("Small", "Medium", "Large"))
					
# Defintion of survey_vector and survey_factor
survey_vector <- c("R", "L", "L", "R", "R")
survey_factor <- factor(survey_vector, levels = c("R", "L"), labels = c("Right", "Left"))

# Summarize survey_vector
summary(survey_vector)
   Length     Class      Mode 
        5 character character
		
# Summarize survey_factor
summary(survey_factor)
Right  Left 
    3     2
	
	# Definition of animal_vector and temperature_vector
animal_vector <- c("Elephant", "Giraffe", "Donkey", "Horse")
temperature_vector <- c("High", "Low", "High", "Low", "Medium")

# Convert animal_vector to a factor: animal_factor
animal_factor <- factor(animal_vector)

# Encode temperature_vector as a factor: temperature_factor
temperature_factor <- factor(temperature_vector, levels=c("Low", "Medium", "High"), labels=c("Low", "Medium", "High"), ordered=TRUE)

# Print out animal_factor and temperature_factor
animal_factor
[1] Elephant Giraffe  Donkey   Horse   
Levels: Donkey Elephant Giraffe Horse

temperature_factor
[1] High   Low    High   Low    Medium
Levels: Low < Medium < High



# Definition of survey_vector and survey_factor
survey_vector <- c("R", "L", "L", "R", "R")
survey_factor <- factor(survey_vector, levels = c("R", "L"), labels = c("Right", "Left"))

# First element from survey_factor: right
survey_factor[1]
[1] Right
Levels: Right Left

# Second element from survey_factor: left
survey_factor[2]
[1] Left
Levels: Right Left

# Right 'greater than' left?
survey_factor[1] > survey_factor[2]
Warning message: '>' not meaningful for factors
[1] NA




# Create speed_vector
speed_vector <- c("OK", "Slow", "Slow", "OK", "Fast")

# Convert speed_vector to ordered speed_factor
speed_factor <- factor(speed_vector, ordered=TRUE, levels=c("Slow","OK","Fast"))

# Print speed_factor
speed_factor
[1] OK   Slow Slow OK   Fast
Levels: Slow < OK < Fast

# Summarize speed_factor
summary(speed_factor)
Slow   OK Fast 
   2    2    1

   

# Definition of speed_vector and speed_factor
speed_vector <- c("Fast", "Slow", "Slow", "Fast", "Ultra-fast")
speed_factor <- factor(speed_vector, ordered = TRUE, levels = c("Slow", "Fast", "Ultra-fast"))

# Compare DA2 with DA5: compare_them
compare_them <- speed_factor[2] > speed_factor[5]

# Print compare_them: Is DA2 faster than DA5?
compare_them
[1] FALSE
*****************************************************
List

# Numeric vector: 1 up to 10
my_vector <- 1:10 
[1]  1  2  3  4  5  6  7  8  9 10

# Numeric matrix: 1 up to 9
my_matrix <- matrix(1:9, ncol = 3)
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9

# Factor of sizes
my_factor <- factor(c("M","S","L","L","M"), ordered = TRUE, levels = c("S","M","L"))
[1] M S L L M
Levels: S < M < L

# Construct my_list with these different elements
my_list <- list(my_vector, my_matrix, my_factor)
[[1]]
 [1]  1  2  3  4  5  6  7  8  9 10

[[2]]
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9

[[3]]
[1] M S L L M
Levels: S < M < L

> # Display structure of my_list
> str(my_list)


# select a single element from a list
shining_list[[1]]
shining_list[["title"]]
shining_list$title

# returns another list that contains the specified elements
shining_list[c(2,3)]
shining_list[c(F,T,T)]

# second component (Actors) and first element (Jack Nicholson)
shining_list[[2]][1]

*****
> shining_list
$title
[1] "The Shining"

$actors
[1] "Jack Nicholson"   "Shelley Duvall"   "Danny Lloyd"      "Scatman Crothers"
[5] "Barry Nelson"    

$reviews
[1] Good    OK      Good    Perfect Bad     Perfect Good   
Levels: Bad < OK < Good < Perfect

$boxoffice
               US Non-US
First release  39     47
Director's cut 18     14

> shining_list$boxoffice[1,2]
[1] 47

> shining_list[[c(2,4)]]
[1] "Scatman Crothers"
*****
Extending list
$ as well as [[ can be used to select elements from lists; also be used to extend lists
shining_list$my_opinion <- "Love it!"
shining_list[["my_opinion"]] <- "Love it!"
shining_list <- c(shining_list, my_opinion = "Love it!")
c(shining_list, my_opinion = "Love it!", your_opinion = "Hate it!") # adds named components for each
c(shining_list, list(my_opinion = "Love it!", your_opinion = "Hate it!")) # equivalent to previous one
	   
c(shining_list, opinions = c("Love it!", "Hate it!")) # adds opinions1 and opinions2 components
*****************************************************
Data frames
# Print the first observations of mtcars
head(mtcars)

# Print the last observations of mtcars
tail(mtcars)

# Print the dimensions of mtcars
dim(mtcars)

planets_df <- data.frame(planets, type, diameter, rotation, rings)
str(planets_df)
'data.frame':	8 obs. of  5 variables:
 $ planets : Factor w/ 8 levels "Earth","Jupiter",..: 4 8 1 3 2 6 7 5
 $ type    : Factor w/ 2 levels "Gas giant","Terrestrial planet": 2 2 2 2 1 1 1 1
 $ diameter: num  0.382 0.949 1 0.532 11.209 ...
 $ rotation: num  58.64 -243.02 1 1.03 0.41 ...
 $ rings   : logi  FALSE FALSE FALSE FALSE TRUE TRUE ...

type_factor <- factor(type)
planets_df <- data.frame(planets, type_factor, diameter, rotation, rings, stringsAsFactors = FALSE)

names(planets_df) <- c("name", "type", "diameter", "rotation", "has_rings")

planets_df[planets_df$has_rings == TRUE, ]
subset(planets_df, subset = has_rings == TRUE)

# Planets that are smaller than planet Earth: small_planets_df
small_planets_df <- subset(planets_df, diameter < 1)

# Planets that rotate slower than planet Earth: slow_planets_df
slow_planets_df <- subset(planets_df, abs(rotation) > 1)

# add columns
my_df$new_column <- my_vec
my_df[["new_column"]] <- my_vec
my_df <- cbind(my_df, new_column = my_vec)

# Add observation
# Name pluto correctly
pluto <- data.frame(name="Pluto", type="Terrestrial planet", diameter=0.18, rotation=-6.38, has_rings=FALSE)

# Bind planets_df and pluto together: planets_df_ext
planets_df_ext <- rbind(planets_df, pluto)

# Sorting
a <- c(100,9,101)
order(a) # returns rank
[1] 2 1 3
a[order(a)] # returns ordered vector
[1]   9 100 101

# Create a desired ordering for planets_df: positions
positions <- order(planets_df$diameter, decreasing=TRUE)

# Create a new, ordered data frame: largest_first_df
largest_first_df <- planets_df[order(planets_df$diameter, decreasing=TRUE),]

# Print largest_first_df
largest_first_df

# Remove economic variables and add population
countries_df_dem <- countries_df[1:8,c(TRUE,TRUE,FALSE,FALSE,TRUE)]
countries_df_dem$population <- population

# Add brazil
names(brazil) <- c("name", "continent", "has_president", "population")
countries_df2 <- rbind(countries_df_dem, brazil)

# Sort by population
countries_df2[order(countries_df2$population, decreasing=TRUE),]
countries_df2

*****************************************************
Graphics
# Plot the genre variable of movies
plot(movies$genre)

# Plot the genre variable against the rating variable
plot(movies$genre, movies$rating)

hist(x, breaks = "Sturges")

# Create a histogram for rating
hist(movies$rating)

# Create a histogram for rating, with 20 bins
hist(movies$rating, breaks=20)

# movies is already pre-loaded

# Create a boxplot of the runtime variable
boxplot(movies$runtime)

# Subset the dateframe and plot it entirely
dateframe <-data.frame(movies$rating, movies$votes, movies$runtime)
plot(dateframe)

# Create a pie chart of the table of counts of the genres
# genre_table <- as.table(movies$genre)
genre_table <- table(movies$genre)
pie(genre_table)

# Subset salaries: salaries_educ 
salaries_educ <- subset(salaries, salaries$degree==3)

# Create a histogram of the salary column
hist(salaries_educ$salary, breaks=10)

plot(movies$votes, movies$runtime,
  main="Votes versus Runtime",
  sub="No clear correlation",
  xlab="Number of votes [-]",
  ylab="Runtime [s]")
  
# Customize the plot further
plot(movies$votes, movies$runtime,
     main = "Votes versus Runtime", col.main=604,
     xlab = "Number of votes [-]",
     ylab = "Runtime [s]",
     sub = "No clear correlation",
     pch=9,
     col="#dd2d2d")

plot(movies$votes, movies$year,
  main="Are recent movies voted more on?",
  xlab="Number of votes [-]",
  ylab="Year [-]",
  col="orange",
  pch=19,
  cex.axis=.80)
  
# Build a customized histogram
hist(movies$runtime,
  breaks=20,
  main="Distribution of Runtime",
  xlab="Runtime [-]",
  col="cyan",
  border="red",
  xlim = c(90, 220))

# Add the exp vector as a column experience to salaries
salaries$experience <- exp

# Filter salaries: only keep degree == 3: salaries_educ
salaries_educ <- subset(salaries, salaries$degree==3)

# Create plot with many customizations
plot(salaries_educ$exp, salaries_educ$salary,
  main="Does experience matter?", col.main="red",
  xlab="Work experience",
  ylab="Salary",
  col="blue",
  cex.axis=1.20)

  
  
# List all the graphical parameters
par()

# Specify the mfrow parameter
par(mfrow = c(2,1))

# Build two plots
plot(movies$votes, movies$rating)
hist(movies$votes)

# Build the grid matrix
grid <- matrix(c(1,2,3,3), nrow=2, ncol=2)

# Specify the layout
layout(grid)

# Build three plots
plot(movies$rating, movies$runtime)
plot(movies$votes, movies$runtime)
boxplot(movies$runtime)


# Build the grid matrix
grid <- matrix(c(1, 2, 3, 3), nrow = 2)

# Specify the layout
layout(grid)

# Customize the three plots
plot(movies$rating, movies$runtime, xlab="Rating", ylab="Runtime", pch=4)
plot(movies$votes, movies$runtime, xlab="Number of Votes", ylab="Runtime", col="blue")
boxplot(movies$runtime, border="darkgray", main="Boxplot of Runtime")

# Fit a linear regression: movies_lm
movies_lm <- lm(movies$rating ~ movies$votes)

# Build a scatterplot: rating versus votes
plot(movies$votes, movies$rating)

# Add straight line to scatterplot
abline(coef(movies_lm))

# Fit a linear regression (don't change)
movies_lm <- lm(movies$rating ~ movies$votes)

# Customize scatterplot
plot(movies$votes, movies$rating, main="Analysis of IMDb data", xlab="Number of Votes", ylab="Rating",col="darkorange",pch=15,cex=.7)

# Customize straight line
abline(coef(movies_lm), lwd=2, col="red")

# Add text
xco <- 7e5
yco <- 7
text(x=xco,y=yco,label="More votes? Higher rating!")

