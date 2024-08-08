# Movie Recommender System

## Overview

The **Movie Recommender System** is designed to provide personalized movie recommendations based on user input. The system uses a content-based filtering approach, leveraging data from The Movie Database (TMDB) to identify similarities between movies. By analyzing various features such as genres, cast, crew, and keywords, the system can suggest movies that are closely related to a user's choice.

This project is an excellent starting point for understanding how recommendation systems work, particularly in the context of content-based filtering. The project is implemented in Python, and the code is organized to be modular and easy to understand.

## Table of Contents

- [Folder Structure](#folder-structure)
- [Setup Instructions](#setup-instructions)
- [Dataset Description](#dataset-description)
- [Model Implementation](#model-implementation)
- [Usage](#usage)
- [Future Work](#future-work)
- [Contributing](#contributing)
- [License](#license)

## Folder Structure

The project directory is organized as follows:

```plaintext
📁 C:\Users\Kartabya\PycharmProjects\movieRecommend/
  📄 app.py                      # Main application file
  📁 dataset/
    📄 tmdb_5000_credits.csv      # TMDB credits dataset (cast and crew information)
    📄 tmdb_5000_movies.csv       # TMDB movies dataset (movie metadata)
  📄 FolderStructure.ipynb        # Jupyter notebook explaining the folder structure
  📁 model/
    📄 movie_list.pkl             # Pickled file containing a list of movies
    📄 similarity.pkl             # Pickled file containing the similarity matrix
  📄 ModelImplementation.ipynb    # Jupyter notebook for model implementation details
  📄 requirements.txt             # List of dependencies needed to run the project
  📄 setup.sh                     # Shell script for setting up the environment
```

### Detailed File Descriptions

- **`app.py`:** This is the main application file that runs the movie recommender system. It loads the necessary data and models, and provides the user interface for interacting with the recommendation system.
  
- **`dataset/`:** This directory contains the datasets used in the project. 
  - **`tmdb_5000_credits.csv`:** Contains details about the cast and crew of the movies.
  - **`tmdb_5000_movies.csv`:** Contains metadata about the movies, including title, genres, and more.
  
- **`FolderStructure.ipynb`:** A Jupyter notebook that explains the project’s folder structure and the purpose of each file and directory.
  
- **`model/`:** This directory contains the serialized (pickled) model outputs.
  - **`movie_list.pkl`:** A list of movie titles extracted from the dataset.
  - **`similarity.pkl`:** A precomputed similarity matrix used to find similar movies.
  
- **`ModelImplementation.ipynb`:** A detailed Jupyter notebook that walks through the model implementation process, including data preprocessing, feature extraction, and similarity computation.
  
- **`requirements.txt`:** A text file listing all Python libraries and dependencies required to run the project. These can be installed using pip.
  
- **`setup.sh`:** A shell script to automate the setup process, ensuring that all dependencies are installed and the environment is correctly configured.

## Setup Instructions

Follow the steps below to set up the Movie Recommender System on your local machine:

### 1. Clone the Repository

Begin by cloning the repository to your local machine using Git:

```bash
git clone https://github.com/kartabyakrishna/movie-Recommend.git
cd movierecommend
```

### 2. Create a Virtual Environment

It's recommended to create a virtual environment to avoid conflicts with your global Python environment:

```bash
python3 -m venv venv
source venv/bin/activate   # On Windows, use `venv\Scripts\activate`
```

### 3. Install Dependencies

Next, install the necessary Python packages listed in `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 4. Run the Application

Finally, you can run the main application using:

```bash
streamlit run app.py
```

This will start the recommendation system, allowing you to input a movie and receive recommendations based on its similarity to other movies in the dataset.

## Dataset Description

The project utilizes two key datasets from TMDB (The Movie Database):

### 1. TMDB 5000 Movies Dataset (`tmdb_5000_movies.csv`)

- **Description:** This dataset contains metadata about 5000 movies. It includes information such as the title, genres, release date, runtime, and popularity of each movie.
- **Key Columns:**
  - `id`: Unique identifier for each movie.
  - `title`: The title of the movie.
  - `genres`: List of genres associated with the movie.
  - `overview`: A brief summary of the movie's plot.
  - `release_date`: The date when the movie was released.
  - `vote_average`: Average rating based on user votes.
  - `popularity`: A measure of the movie's popularity.

### 2. TMDB 5000 Credits Dataset (`tmdb_5000_credits.csv`)

- **Description:** This dataset provides details about the cast and crew for the movies listed in the TMDB 5000 Movies dataset. It includes information such as the actors, directors, and other crew members involved in each movie.
- **Key Columns:**
  - `movie_id`: A unique identifier that links this dataset to the movies dataset.
  - `cast`: A list of actors who appeared in the movie.
  - `crew`: A list of crew members, including directors and writers, who contributed to the movie.

**[Link to Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)**

You can find these datasets on Kaggle, where they are freely available for public use.

## Model Implementation

The recommender system model is built using a content-based filtering approach. The key steps involved in the model implementation are detailed below:

### 1. Data Preprocessing

- **Text Cleaning:** The movie titles, genres, and other text-based features are cleaned to remove any inconsistencies or noise.
- **Feature Extraction:** Features such as genres, keywords, cast, and crew are extracted from the datasets. These features are then combined into a single string for each movie.

### 2. Similarity Calculation

- **Vectorization:** The combined feature strings are converted into numerical vectors using techniques like TF-IDF (Term Frequency-Inverse Document Frequency).
- **Cosine Similarity:** The cosine similarity metric is used to calculate the similarity between movies. This metric measures the cosine of the angle between two vectors, which helps determine how similar the movies are based on their features.

### 3. Model Serialization

The movie list and similarity matrix are serialized using Python’s `pickle` module and stored in the `model/` directory. This allows the application to quickly load the precomputed data and make recommendations without recalculating the similarities each time.

For a step-by-step walkthrough of the model implementation, refer to the `ModelImplementation.ipynb` notebook.

## Usage

Once the application is running, you can input the name of a movie, and the system will provide a list of similar movies based on the calculated similarities. This can be useful for discovering new movies that match your preferences or for exploring movies similar to your favorites.

### Example Usage

1. **Input:** `Inception`
2. **Output:** A list of movies similar to "Inception", such as "Interstellar", "The Matrix", "Shutter Island", etc.

## Future Work

Here are some potential areas for improvement and extension of the project:

- **Incorporate Collaborative Filtering:** Integrate collaborative filtering to provide more personalized recommendations based on user behavior.
- **Enhance the Feature Set:** Include additional features such as user ratings, reviews, and box office performance to improve recommendation accuracy.
- **Web Interface:** Develop a user-friendly web interface using frameworks like Flask or Django to make the system more accessible to non-technical users.
- **Scalability:** Optimize the system for larger datasets and explore parallel processing techniques to handle more movies efficiently.
- **Error Handling:** Implement more robust error handling to manage edge cases and unexpected inputs.

## Contributing

Contributions are welcome! If you have suggestions for improvements or new features, feel free to fork the repository, make changes, and submit a pull request.

### Steps to Contribute

1. Fork the repository on GitHub.
2. Create a new branch for your feature or bugfix.
3. Make your changes and commit them with clear and descriptive commit messages.
4. Push your changes to your forked repository.
5. Open a pull request against the main branch of the original repository.

## License

This project is licensed under the MIT License. For more details, see the [LICENSE](LICENSE) file in the repository.
