# data-sourcing-challenge
Module 6 Challenge

## Part 1: Access the New York Times API
    * Made a GET request to the NYT seach API using paging and periodically sleeping so as to avoid API query limits.
    * Utilized a try and except to retrieve and append review to the list of reviews.
    * Extracting the movie title from the "headline.main" required additional regex logic and data cleansing.
        ** Added addtional logic to handle both unicode characters regardless of the trailing word.
        ** Some extracted movie titles also required removing the "," from the title; this allowed for successfull lookups in the TMDB API.
    * The titles list consists of 199 extracted valid movie titles. the lone item being a "headline.main" value that didn't conform to the specified unicode character enclosed requirement.

## Part 2: Access the Movie Database API
    * Utilizing the titles list from above, I queried the movie database via a loop to retrieve the corresponding movie Id. which was later used to retrieve the movie details.
    * After successfully retrieving the movie Id. A call was made to the movie details API by passing path parameters to get the details.
    * A request counter was created to keep track of the API calls, and enabled the application to sleep after making 50 subsequent calls to the API service.
    * Upon successful movie details retrieval, the json object was parsed with the attributes of interest retrieved and stored in a local variable.

## Part 3: Merge and Clean the Data for Export
    * Merged the NYT reviews dataframe and the TMDB movies dataframe on the titles column.
    * Cleansed the "genres", "spoken_languages", and "production_countries" column data as requested. Also modified the datatypes of the cloumns to be of type string (str).
    * Deleted duplicated rows and reset the index of the merged dataframe.
    * Exported the data to a csv called "collected_data.csv".
