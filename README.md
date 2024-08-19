# Movie Recommender

This project is a content-based movie recommender system that uses various movie attributes like genres, keywords, cast, and crew to suggest similar movies. It leverages natural language processing techniques to create a movie recommendation engine based on cosine similarity.

## Project Structure

- **`movie_recommender.ipynb`**: Jupyter notebook containing the code for data preprocessing, feature extraction, and recommendation logic.
- **`movie_list.pkl`**: Serialized file containing the processed movie data.
- **`similarity.pkl`**: Serialized file containing the cosine similarity matrix.
- **`README.md`**: Documentation for the project.

## Dataset

The dataset used in this project is derived from the TMDB 5000 Movie Dataset, which consists of two CSV files:
- **`tmdb_5000_movies.csv`**: Contains movie details like budget, genres, homepage, release date, revenue, etc.
- **`tmdb_5000_credits.csv`**: Contains information about the cast and crew for each movie.

## How It Works

1. **Data Preprocessing**:
    - The `movies` and `credits` datasets are merged on the movie title.
    - Selected features such as `genres`, `keywords`, `cast`, and `crew` are extracted and converted from JSON-like structures to lists of relevant terms.
    - Non-essential characters (like spaces) in these terms are removed to avoid conflicts during feature extraction.
    - These lists are then concatenated to form a unified `tags` column.

2. **Feature Extraction**:
    - The `CountVectorizer` from `sklearn` is used to convert the `tags` column into a matrix of token counts.
    - The vocabulary size is limited to 5000 words, and English stop words are removed to focus on significant terms.

3. **Similarity Calculation**:
    - Cosine similarity is calculated between all movies using their vector representations.
    - This similarity matrix is then used to recommend movies based on the selected movie title.

4. **Recommendation**:
    - A function `recommend(movie)` is defined to return the top 5 movies most similar to the provided movie title.

## Usage

- **Recommending Movies**:
    - To get recommendations for a specific movie, run the `recommend(movie)` function with the desired movie title.
    - Example: `recommend('Gandhi')` will return a list of movies similar to *Gandhi*.

- **Running the Project**:
    1. Ensure you have the necessary packages installed (e.g., pandas, sklearn, etc.).
    2. Clone the repository and open the `movie_recommender.ipynb` notebook.
    3. Run the notebook cells to preprocess the data and generate recommendations.

- **Saving the Model**:
    - The project includes code to serialize and save the processed movie data and similarity matrix using `pickle`. These files (`movie_list.pkl` and `similarity.pkl`) can be loaded later for quick recommendations without re-running the entire notebook.

## Requirements

- Python 3.x
- pandas
- scikit-learn
- ast
- pickle

