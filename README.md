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

| It. Nr | Model            | R²     | MAE (Mio $) | RMSE (Mio $) | Features Used                           | Beschreibung                                |
|--------|------------------|--------|-------------|--------------|------------------------------------------|---------------------------------------------|
| 1      | Linear Regression| 0.67   | 71.3        | 129.0        | budget, popularity                       | Basis-Modell, Underfitting                  |
| 2      | Random Forest    | 0.72   | 58.2        | 117.4        | budget, popularity                       | Besser, aber noch etwas instabil            |
| 3      | Random Forest    | 0.74   | 51.7        | 111.8        | + genre one-hot (18 genres)              | Signifikante Verbesserung durch Genres      |
| 4      | Random Forest    | 0.78   | 42.3        | 106.0        | + director_avg_revenue                   | Director macht starken Einfluss aus         |
| 5      | Random Forest    | 0.78   | 42.2        | 106.0        | + lead_actor_avg_revenue                 | Lead Actor trägt kaum mehr zur Verbesserung bei |


---

## References  
Feature importance analysis and model evaluations are part of the Jupyter Notebook in this repository.
