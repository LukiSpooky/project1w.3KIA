# Film Revenue Prediction

## Projektbeschreibung
Dieses Projekt sagt den Umsatz (revenue) von Filmen basierend auf verschiedenen Informationen aus den TMDB- und IMDB-Datensätzen voraus.

## Ergebnisse
Das Modell liefert bereits gute Vorhersagen, zeigt jedoch leichte Überanpassung (Overfitting). Eine größere Datenmenge oder ausgewogenere Feature-Auswahl könnten die Generalisierbarkeit verbessern. 

## Name & URL
| Name        | URL                         |
|-------------|-----------------------------|
| Huggingface | [Huggingface Space](https://huggingface.co/spaces/huserluk/project1w.3KIA) |
| Code        | [GitHub Repository](https://github.com/LukiSpooky/project1w.3KIA)            |

## Datenquellen und verwendete Features
| Datenquelle        | Features                                  |
|--------------------|--------------------------------------------|
| [TMDB Movies](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata?select=tmdb_5000_movies.csv)        | budget, genres, popularity, release_date, runtime, vote_count, vote_average, etc. |
| [TMDB Credits](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata?select=tmdb_5000_credits.csv)       | cast, crew (Director)                     |
| [IMDB Ratings](https://www.kaggle.com/datasets/shubhamchandra235/imdb-and-tmdb-movie-metadata-big-dataset-1m)       | IMDB_Rating, Meta_score                   |

## Erzeugte Features
| Feature                  | Beschreibung |
|--------------------------|--------------|
| genres_onehot            | One-hot-Encoding der Genres |
| lead_actor               | Erster Schauspieler aus dem Cast |
| lead_actor_avg_revenue   | Durchschnittlicher Umsatz pro Hauptdarsteller |
| director_avg_revenue     | Durchschnittlicher Umsatz pro Regisseur |

## Modelltraining

### Datenmenge
Verfügbar waren 3.229 Filme nach Bereinigung.

### Datenaufteilung
Train/Test Split: 80/20

---

### Performance (bei schrittweisem Feature-Zuwachs)

| It. Nr | Modell            | R²     | MAE (Mio $) | RMSE (Mio $) | Features                                                                 | Bemerkung                                                  |
|--------|-------------------|--------|-------------|--------------|--------------------------------------------------------------------------|------------------------------------------------------------|
| 1      | Linear Regression | 0.668  | 50.56       | 94.09        | `['budget', 'popularity']`                                              | Gutes Basismodell, noch leichtes Underfitting              |
| 2      | Random Forest     | 0.687  | 48.19       | 91.30        | `['budget', 'popularity']`                                              | Leichtes Overfitting sichtbar                              |
| 3      | Random Forest     | 0.594  | 72.32       | 143.29       | `['budget', 'popularity']` auf bereinigtem Datensatz                    | Schwächer nach Bereinigung, Underfitting erkennbar         |
| 4      | Random Forest     | 0.612  | 70.01       | 141.52       | + `lead_actor_freq`                                                     | Kleine Verbesserung, Modell bleibt leicht Underfitting   |
| 5      | Random Forest     | 0.607  | 69.20       | 142.45       | + `genres` (One-Hot für 4 Genres)                                       | Keine klare Verbesserung, leichtes Underfitting             |
| 6      | Random Forest     | 0.709  | 52.93       | 122.46       | + `director_avg_revenue`                                                | Gute Generalisierung, kein Overfitting                     |
| 7      | Random Forest     | **0.761** | **44.01**   | **111.11**   | + `lead_actor_avg_revenue`                                              | Bestes Modell, gut generalisiert, kein Overfitting         |

---

## Fazit
Die besten Ergebnisse wurden mit Random Forest erzielt, nachdem genres sowie statistische Durchschnittswerte pro Regisseur und Schauspieler berücksichtigt wurden. Eine Ausweitung auf weitere Features wie Produktionsland oder Marketingbudget könnte das Modell weiter verbessern.
