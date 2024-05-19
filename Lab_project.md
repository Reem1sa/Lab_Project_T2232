DSC 200 Lab Project -Term 2232
================
2024-05-19

**Student Name:<insert your name here>**reem saud

**Student ID:<insert ID here>**2221002374

**Deadline:** 23:59 on Sunday, 19 May 2024

**Total Points:** 20

## Loading Packages

``` r
library(tidyverse)
library(openintro)
library(ggrepel)
```

## Tasks

\`1. (2 points)

``` r
# Count the number of pets
num_pets <- nrow(seattlepets)
num_pets
```

    ## [1] 52519

Write your narrative here

\`2. (2 points)

``` r
# Count the number of variables
num_variables <- ncol(seattlepets)
num_variables
```

    ## [1] 7

Write your narrative below

\`3. (2 points)

``` r
# Count the frequency of each species
species_count <- table(seattlepets$species)
species_count
```

    ## 
    ##   Cat   Dog  Goat   Pig 
    ## 17294 35181    38     6

Write your narrative here

\`4. (2 points)

``` r
# Count the frequency of each pet name
pet_name_frequency <- table(seattlepets$animal_name)

# Sort the frequency table in descending order
sorted_pet_names <- sort(pet_name_frequency, decreasing = TRUE)

# Display the top ten most common pet names
head(sorted_pet_names, 10)
```

    ## 
    ##    Lucy Charlie    Luna   Bella     Max   Daisy   Molly    Jack    Lily  Stella 
    ##     439     387     355     331     270     261     240     232     232     227

Write your narrative here

\`5. (2 points)

``` r
# Filter records for species Pig
pig_records <- filter(seattlepets, species == "Pig")

# Arrange the filtered records by pet names (animal_name)
sorted_pig_records <- arrange(pig_records, animal_name)

# Display the sorted pig records
sorted_pig_records
```

    ## # A tibble: 6 × 7
    ##   license_issue_date license_number animal_name species primary_breed
    ##   <date>             <chr>          <chr>       <chr>   <chr>        
    ## 1 2018-04-23         S116433        Atticus     Pig     Pot-Bellied  
    ## 2 2018-08-29         S146305        Coconut     Pig     Pot-Bellied  
    ## 3 2018-04-10         139975         Darla       Pig     Pot Bellied  
    ## 4 2018-07-27         731834         Millie      Pig     Pot-Bellied  
    ## 5 2018-08-29         S146306        Othello     Pig     Pot-Bellied  
    ## 6 2018-05-12         S141788        <NA>        Pig     Standard     
    ## # ℹ 2 more variables: secondary_breed <chr>, zip_code <chr>

Write your narrative here

\`6. (2 points)

``` r
# Select only pet name (animal_name) and primary breed for species Goat
goat_records <- select(filter(seattlepets, species == "Goat"), animal_name, primary_breed)

# Arrange the selected records by pet names (animal_name)
sorted_goat_records <- arrange(goat_records, animal_name)

# Display the sorted goat records
sorted_goat_records
```

    ## # A tibble: 38 × 2
    ##    animal_name     primary_breed
    ##    <chr>           <chr>        
    ##  1 Abelard         Miniature    
    ##  2 Aggie           Miniature    
    ##  3 Arya            Miniature    
    ##  4 Beans           Miniature    
    ##  5 Brussels Sprout Miniature    
    ##  6 Darcy           Miniature    
    ##  7 Fawn            Miniature    
    ##  8 Fiona           Miniature    
    ##  9 Gavin           Standard     
    ## 10 Grace           Miniature    
    ## # ℹ 28 more rows

Write your narrative here

\`7. (2 points)

``` r
library(dplyr)

# Concatenate animal_name and species into a single column named pet
seattlepets <- mutate(seattlepets, pet = paste(animal_name, species, sep = " - "))

# Select license_number and pet, then arrange by pet
sorted_records <- select(seattlepets, license_number, pet) %>%
                  arrange(pet)

# Display the sorted records
sorted_records
```

    ## # A tibble: 52,519 × 2
    ##    license_number pet                                     
    ##    <chr>          <chr>                                   
    ##  1 8001665        "\"Luci\" Lucia Rosalin Wicksugal - Dog"
    ##  2 896557         "\"Mama\" Maya - Cat"                   
    ##  3 S147119        "\"Mo\" - Cat"                          
    ##  4 353597         "'Alani - Cat"                          
    ##  5 S143106        "'Murca - Dog"                          
    ##  6 573722         "- - Cat"                               
    ##  7 S126229        "1 - Cat"                               
    ##  8 S126230        "2 - Cat"                               
    ##  9 133239         "30 Weight - Cat"                       
    ## 10 S142492        "7's - Dog"                             
    ## # ℹ 52,509 more rows

Write your narrative here

\`8. (2 points)

``` r
library(ggplot2)

# Create a bar plot of species counts
species_plot <- ggplot(seattlepets, aes(x = species)) +
                geom_bar() +
                labs(title = "Counts of Species", x = "Species", y = "Count") +
                theme(axis.text.x = element_text(angle = 45, hjust = 1))

# Display the plot
print(species_plot)
```

![](Lab_project_files/figure-gfm/unnamed-chunk-8-1.png)<!-- --> Write
your narrative here

\`9. (2 points)

``` r
top_10_names <- seattlepets %>% 
filter(animal_name %in% c( "Lucy"  , "Charlie" , "Luna" , "Bella" , "Max"    , 
                           "Daisy" , "Molly"   , "Jack" , "Lily"  , "Stella" ))
top_10_names
```

    ## # A tibble: 2,974 × 8
    ##    license_issue_date license_number animal_name species primary_breed          
    ##    <date>             <chr>          <chr>       <chr>   <chr>                  
    ##  1 2018-11-25         S120480        Charlie     Dog     Retriever, Labrador    
    ##  2 2018-11-03         829563         Max         Dog     Retriever, Labrador    
    ##  3 2018-10-29         732106         Lily        Cat     Domestic Shorthair     
    ##  4 2018-11-25         895808         Max         Cat     Domestic Shorthair     
    ##  5 2018-11-26         834841         Daisy       Dog     Terrier, American Pit …
    ##  6 2018-12-13         8003804        Charlie     Dog     Border Collie          
    ##  7 2018-11-06         S125292        Jack        Cat     Domestic Shorthair     
    ##  8 2018-11-01         835179         Stella      Dog     Retriever, Labrador    
    ##  9 2018-12-14         950094         Molly       Dog     Retriever, Labrador    
    ## 10 2018-11-24         S137301        Lucy        Dog     Hound                  
    ## # ℹ 2,964 more rows
    ## # ℹ 3 more variables: secondary_breed <chr>, zip_code <chr>, pet <chr>

\`a. What does the above code chunk do?

\`b. Plot the counts of the pet names (animal_name) in top_10_names

``` r
top_10_names <- seattlepets %>% 
filter(animal_name %in% c( "Lucy"  , "Charlie" , "Luna" , "Bella" , "Max"    , 
                           "Daisy" , "Molly"   , "Jack" , "Lily"  , "Stella" ))
top_10_names
```

    ## # A tibble: 2,974 × 8
    ##    license_issue_date license_number animal_name species primary_breed          
    ##    <date>             <chr>          <chr>       <chr>   <chr>                  
    ##  1 2018-11-25         S120480        Charlie     Dog     Retriever, Labrador    
    ##  2 2018-11-03         829563         Max         Dog     Retriever, Labrador    
    ##  3 2018-10-29         732106         Lily        Cat     Domestic Shorthair     
    ##  4 2018-11-25         895808         Max         Cat     Domestic Shorthair     
    ##  5 2018-11-26         834841         Daisy       Dog     Terrier, American Pit …
    ##  6 2018-12-13         8003804        Charlie     Dog     Border Collie          
    ##  7 2018-11-06         S125292        Jack        Cat     Domestic Shorthair     
    ##  8 2018-11-01         835179         Stella      Dog     Retriever, Labrador    
    ##  9 2018-12-14         950094         Molly       Dog     Retriever, Labrador    
    ## 10 2018-11-24         S137301        Lucy        Dog     Hound                  
    ## # ℹ 2,964 more rows
    ## # ℹ 3 more variables: secondary_breed <chr>, zip_code <chr>, pet <chr>

\`10. (2 points)

\`The below code plots the proportion of dogs with a given name versus
the proportion of cats with the same name. The 20 most common cat and
dog names are displayed. The diagonal line on the plot is the x = y
line; if a name appeared on this line, the name’s popularity would be
exactly the same for dogs and cats.

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## Warning in geom_image(mapping, data, inherit.aes = inherit.aes, na.rm = na.rm, : All aesthetics have length 1, but the data has 20 rows.
    ## ℹ Please consider using `annotate()` or provide this layer with data containing
    ##   a single row.
    ## All aesthetics have length 1, but the data has 20 rows.
    ## ℹ Please consider using `annotate()` or provide this layer with data containing
    ##   a single row.

![](Lab_project_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

\`What names are more common for cats than dogs? The ones above the line
or the ones below the line?

\`Answer here………The names that are more common for cats than dogs are
the ones above the diagonal line (x = y) on the plot.

\`Is the relationship between the two variables (proportion of cats with
a given name and proportion of dogs with a given name) positive or
negative? What does this mean in context of the data?

\`Answer here …..The relationship between the proportion of cats with a
given name and the proportion of dogs with the same name is negative. In
the context of the data, this negative relationship means that as the
proportion of cats with a given name increases, the proportion of dogs
with the same name tends to decrease, and vice versa. This suggests an
inverse relationship in the popularity of names between cats and dogs in
the dataset.
