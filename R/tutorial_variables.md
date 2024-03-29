test
================
Ugo
2023-07-31

``` r
# Variables:
# As mentioned, we often need some number (eg a concentration), some table (eg table of differentially expressed genes), information (eg the name of a protein) etc. to be saved in R to be able to use them later in the analysis. This is where variables come into play, and now we’ll see how to create them, how to reuse them, and what kinds of variables exist.

# To create a variable we write name_of_the_variable <- what_to_save (you can either use = instead of <-, even if the former is usually used for declaring arguments in a function, but we’ll see it later).
# Now, write this to the console, click Return/send on the keyborard, and see what happens:

myvar <- 5
```

``` r
# On the console nothing happens, but something appeared in the window called Environment (if yours is different, it may be that there is the “List” view setting instead of “Grid” in the blue box, you can change it to your liking). Here in details the info given for each variable:

# Name: name of the variable
# Type: type of the variable (don’t worry, we’ll see in a minute what this means)
# Length:: the length of the variable (how many items it contains)
# Size: how much memory that variable occupies
# Value: the value of our variable

#If we want to create multiple variables with the same value we can do this:

var1 <- var2 <- var3 <- 20

print(var1)
```

    ## [1] 20

``` r
print(var2)
```

    ## [1] 20

``` r
print(var3)
```

    ## [1] 20

``` r
# Using a variable:
# Ok, but once stored, how to we use a variable? Easy, we just need to type it in the console (or start writing the first letters of its name and press Tab to show RStudio suggestions). If, for example, we want to calculate the power of our variable we should write:

print(myvar) #check the variable
```

    ## [1] 5

``` r
myvar ** 2 #calculate the power of 2
```

    ## [1] 25

``` r
myvar ^ 2 #calculate the power of 2
```

    ## [1] 25

``` r
# And here is the result (to elevate to the power we can either use ** or ^).
```

``` r
# And what if we want to store this result? As before:

myvar_power <- myvar ^ 2
print(myvar_power)
```

    ## [1] 25

``` r
# Here we use print() function, but in R we can also just write the name of the variable to see it.
```

``` r
# Variable names:

# As in everything, even in naming variables there are rules and guidelines. Don’t be scared, they are simple and will make your life easier, let’s see them together.
# Rules:

# Variable name CANNOT start with a character other than a letter
# Variable name can contain both letters and numbers (case sensitive, uppercase and lowercase matter)
# Variable name may contain as special characters only the dot . or the underscore _
# Guidelines:

# Since the name of the variable must be useful, its name must suggest something: for example, the variable myvar was previously defined, whose meaning is equal to 0 (so avoid these names), while myvar_power is more indicative, as it tells us that it is raised to a power
# Variables are normally written in lowercase letters, except for those you want to remain constant in your analysis, which in other languages are written in uppercase (this does not make them immutable, but suggests this feature within the script)
# Use underscores rather than periods as special characters in variable names if you can
# If the variable name contains more than one word, you can separate them with an underscore (as in the example) or use the camel case (myvarPower) or the Pascal case (MyvarPower)
# Be consistent within the script: if you decide to use the Pascal case, always use the Pascal case in that script
```

``` r
# Overwriting variables:
# Attention! Variables can be overwritten (unrecoverable action).
# To override a variable, simply assign that variable a new value:

print(myvar)
```

    ## [1] 5

``` r
myvar <- 9
print(myvar)
```

    ## [1] 9

``` r
# Now myvar is equal to 9, and there is no way back…
# This feature is useful for saving space and not cluttering up too much with variables that are okay to change often, but it can be risky. So be careful when naming variables.
```

``` r
# List all variables:
# A useful way to avoid overwriting an important variable is to list the variables. We know that in RStudio they are all present in the Environment window, but what if we weren’t in RStudio but elsewhere (for example in the terminal)?
# The answer is simple, let’s use the ls() function

ls()
```

    ## [1] "myvar"       "myvar_power" "var1"        "var2"        "var3"

``` r
# Here are our variables.
# Note how I called this command with the name function: we will cover this concept later, for now you just need to know that they exist and that they can be identified immediately by the fact that after the name there is a pair of round brackets.
```

``` r
# Delete variables:
# To delete a variable, use the rm() function and insert the variable to be deleted:

# create a variable
to_remove <- 1213

# list all variables
ls()
```

    ## [1] "myvar"       "myvar_power" "to_remove"   "var1"        "var2"       
    ## [6] "var3"

``` r
# delete just-created variable
rm(to_remove)

# list all variables
ls()
```

    ## [1] "myvar"       "myvar_power" "var1"        "var2"        "var3"

``` r
# As we see, in the second case the to_remove variable has been removed.
# What if I want to remove multiple variables? Let’s put multiple variable names inside the rm() function separated by commas:

# create various variables
to_remove <- 1213
to_remove2 <- 685

# list all variables
ls()
```

    ## [1] "myvar"       "myvar_power" "to_remove"   "to_remove2"  "var1"       
    ## [6] "var2"        "var3"

``` r
# delete just-created variables
rm(to_remove, to_remove2)

# list all variables
ls()
```

    ## [1] "myvar"       "myvar_power" "var1"        "var2"        "var3"

``` r
# The two variables have been removed.
# But looking closely at these codes, we see that some start with # and are not evaluated. What are they? These are the comments, i.e. messages that you will write in the scripts (and we will see later how to create them) to help you understand what you are doing. They are actual comments that you can add, and will not be “evaluated” as code as the line starts with #.
```

``` r
# Type of variables:
# Let’s see what are the basic types of variables that exist in R:

# Numeric: numbers, can be integer (whole numbers) or double (decimal numbers)
# Character: characters, therefore strings of letters (words, sentences, etc.)
# Boolean: TRUE or FALSE, are a special type of variable that R interprets in its own way, but super super super useful
# Factor: similar to character, but with peculiar features (and memory saving), often used for categorical variables such as male/female, heterozygous/wild-type
# We will see each type of variable in detail in next chapters. To find out what type a variable is we use the typeof() function:

typeof(myvar)
```

    ## [1] "double"

``` r
# We see that myvar is a double (although it is an integer value), this is because R basically interprets every number as a double, so as to increase its precision and the possibility of operations between various numbers without having type problems.
```

``` r
# Exercise 3.1:
# Create 3 variables indicating the weights of 3 mice.
mice_A <- 8
mice_B <- 10
mice_C <- 9

print(mice_A)
```

    ## [1] 8

``` r
print(mice_B)
```

    ## [1] 10

``` r
print(mice_C)
```

    ## [1] 9

``` r
# Exercise 3.2 Create the variable sum_weights as the sum of the weights of those 3 mice.

sum_weights <- (mice_A + mice_B + mice_C)
print(sum_weights)
```

    ## [1] 27

``` r
# Exercise 3.3 Create 4 other variables for other 4 mice that weight 20 g. Then you realize you did a mistake and you choose to delete 3 of them and change the fourth to 7.7.

mice_D <- mice_E <- mice_F <- mice_G <- 20

print(mice_D)
```

    ## [1] 20

``` r
print(mice_E)
```

    ## [1] 20

``` r
print(mice_F)
```

    ## [1] 20

``` r
print(mice_G)
```

    ## [1] 20

``` r
ls()
```

    ##  [1] "mice_A"      "mice_B"      "mice_C"      "mice_D"      "mice_E"     
    ##  [6] "mice_F"      "mice_G"      "myvar"       "myvar_power" "sum_weights"
    ## [11] "var1"        "var2"        "var3"

``` r
rm(mice_D, mice_E, mice_F)

ls()
```

    ##  [1] "mice_A"      "mice_B"      "mice_C"      "mice_G"      "myvar"      
    ##  [6] "myvar_power" "sum_weights" "var1"        "var2"        "var3"

``` r
mice_G <- 7.7
```
