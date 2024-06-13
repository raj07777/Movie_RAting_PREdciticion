# Movie_RAting_PREdciticion

---

# Predicting IMDB Movie Ratings

by Rishav Raj

18th April 2024

---

## STEP 1: Fetch Movie Titles and Budgets

Retrieve a list of 5000 movie titles and their budgets from www.the-numbers.com. Save the data as 'movie_budget.json'.

```
$ scrapy crawl movie_budget -o movie_budget.json
```

---

## STEP 2: Obtain IMDB Movie Links

Load the movie titles from 'movie_budget.json' and search for their corresponding IMDB links. Save the results as 'fetch_imdb_url.json'.

```
$ scrapy crawl fetch_imdb_url -o fetch_imdb_url.json
```

---

## STEP 3: Scrape IMDB Movie Information

Scrape detailed information for over 5000 movies from IMDB using the links in 'fetch_imdb_url.json'. Save the data as 'imdb_output.json' and download movie posters.

```
$ scrapy crawl imdb -o imdb_output.json
```

---

## STEP 4: Face Recognition on Posters

Perform face recognition on the downloaded posters to count the number of faces. Save the results in 'image_and_facenumber_pair_list.json'.

```
$ python detect_faces_from_posters.py
```

---

## STEP 5: Generate Movie Metadata CSV

Combine data from 'imdb_output.json' and 'image_and_facenumber_pair_list.json' into a structured CSV file with 28 variables suitable for analysis in R or Pandas. The output file will be 'movie_metadata.csv' (approximately 1.5MB).

```
$ python parse_scraped_data.py
```

---

## STEP 6: Perform Analysis in RStudio

Load 'movie_metadata.csv' in RStudio and conduct Exploratory Data Analysis (EDA) and LASSO regression for predicting movie ratings.

```
$ > run RStudio
$ > load 'movie_rating_prediction.R'
```

---

This process outlines how to gather, process, analyze, and predict IMDB movie ratings using web scraping, image processing, and statistical modeling techniques.
