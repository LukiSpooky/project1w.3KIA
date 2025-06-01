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
| TMDB Movies        | budget, genres, popularity, release_date, runtime, vote_count, vote_average, etc. |
| TMDB Credits       | cast, crew (Director)                     |
| IMDB Ratings       | IMDB_Rating, Meta_score                   |

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

| It. Nr | Modell           | R² | MAE (Mio $) | RMSE (Mio $) | Features | Bemerkung |
|--------|------------------|----|-------------|---------------|----------|-----------|
| 1      | Linear Regression | 0.43 | 134.6 | 195.7 | `['budget']` | Starkes Underfitting |
| 2      | Random Forest     | 0.57 | 110.3 | 168.4 | `['budget']` | Leichtes Overfitting |
| 3      | Random Forest     | 0.65 | 93.1 | 150.7 | + `popularity` | Noch Overfitting |
| 4      | Random Forest     | 0.72 | 74.5 | 128.6 | + Genres OneHot | Modell verbessert sich |
| 5      | Random Forest     | 0.78 | 42.3 | 106.0 | + lead_actor_avg_revenue, director_avg_revenue | Bestes Ergebnis |

---

## Fazit
Die besten Ergebnisse wurden mit Random Forest erzielt, nachdem genres sowie statistische Durchschnittswerte pro Regisseur und Schauspieler berücksichtigt wurden. Eine Ausweitung auf weitere Features wie Produktionsland oder Marketingbudget könnte das Modell weiter verbessern.

## Referenzen
- [TMDB API](https://www.themoviedb.org/documentation/api)
- [IMDb Datasets](https://www.imdb.com/interfaces/)
- Scikit-learn Dokumentation
