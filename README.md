# 🎬 Movie Revenue Prediction

## Project Description  
Predicts box office revenue of movies using metadata from TMDB and IMDB, including genres, directors, and lead actors.

---

## Results  
The model shows signs of overfitting. While Random Forest performs better than Linear Regression, the available dataset of ~3200 movies may not generalize well across all genres, directors, and lead actors. More data or stronger regularization may improve results.

---

## Name & URL

| Name         | URL                              |
|--------------|-----------------------------------|
| Huggingface  | [Huggingface Space](https://huggingface.co/spaces/...) |
| Code         | [GitHub Repository](https://github.com/...) |
| Dataset      | [SwitchDrive Download](https://drive.switch.ch/...) |

---

## Data Sources and Features Used Per Source

| Data Source        | Features                                                             |
|--------------------|----------------------------------------------------------------------|
| TMDB Movies        | budget, genres, runtime, popularity, release_date, revenue          |
| TMDB Credits       | cast (lead actor), crew (director)                                   |
| IMDB-TMDB Mapping  | id linking between TMDB and IMDB                                     |

---

## Features Created

| Feature Name              | Description                                                     |
|--------------------------|-----------------------------------------------------------------|
| `lead_actor`             | Name of the top-billed actor (from cast list)                   |
| `lead_actor_avg_revenue` | Average revenue of all films led by the same actor             |
| `Director`               | Name of the film director                                       |
| `director_avg_revenue`   | Average revenue of all films by the same director              |
| `genres_list`            | List of genres per movie                                        |
| Genre columns (`Action`, `Drama`, etc.) | One-hot encoded genre flags                     |
| `release_year`           | Extracted from `release_date`                                  |

---

## Model Training

### Amount of Data  
~3200 movies after cleaning.

### Data Splitting Method  
80/20 Train/Test split.

---

## Performance

| Model             | R²     | MAE (USD)        | RMSE (USD)       | Notes           |
|------------------|--------|------------------|------------------|------------------|
| Linear Regression| 0.74   | ~60,509,000      | ~116,115,000     | Slight underfitting |
| Random Forest     | 0.78   | ~42,273,000      | ~106,045,000     | Better, but some overfitting |

---

## References  
Feature importance analysis and model evaluations are part of the Jupyter Notebook in this repository.
# 🎬 Movie Revenue Prediction

## Project Description  
Predicts box office revenue of movies using metadata from TMDB and IMDB, including genres, directors, and lead actors.

---

## Results  
The model shows signs of overfitting. While Random Forest performs better than Linear Regression, the available dataset of ~3200 movies may not generalize well across all genres, directors, and lead actors. More data or stronger regularization may improve results.

---

## Name & URL

| Name         | URL                              |
|--------------|-----------------------------------|
| Huggingface  | [Huggingface Space](https://huggingface.co/spaces/...) |
| Code         | [GitHub Repository](https://github.com/...) |
| Dataset      | [SwitchDrive Download](https://drive.switch.ch/...) |

---

## Data Sources and Features Used Per Source

| Data Source        | Features                                                             |
|--------------------|----------------------------------------------------------------------|
| TMDB Movies        | budget, genres, runtime, popularity, release_date, revenue          |
| TMDB Credits       | cast (lead actor), crew (director)                                   |
| IMDB-TMDB Mapping  | id linking between TMDB and IMDB                                     |

---

## Features Created

| Feature Name              | Description                                                     |
|--------------------------|-----------------------------------------------------------------|
| `lead_actor`             | Name of the top-billed actor (from cast list)                   |
| `lead_actor_avg_revenue` | Average revenue of all films led by the same actor             |
| `Director`               | Name of the film director                                       |
| `director_avg_revenue`   | Average revenue of all films by the same director              |
| `genres_list`            | List of genres per movie                                        |
| Genre columns (`Action`, `Drama`, etc.) | One-hot encoded genre flags                     |
| `release_year`           | Extracted from `release_date`                                  |

---

## Model Training

### Amount of Data  
~3200 movies after cleaning.

### Data Splitting Method  
80/20 Train/Test split.

---

## Performance

| Model             | R²     | MAE (USD)        | RMSE (USD)       | Notes           |
|------------------|--------|------------------|------------------|------------------|
| Linear Regression| 0.74   | ~60,509,000      | ~116,115,000     | Slight underfitting |
| Random Forest     | 0.78   | ~42,273,000      | ~106,045,000     | Better, but some overfitting |

---

## References  
Feature importance analysis and model evaluations are part of the Jupyter Notebook in this repository.
