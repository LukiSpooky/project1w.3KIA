# Movie Revenue Prediction

## Project Description

Dieses Projekt sagt den erwarteten Box Office Revenue eines Films voraus – basierend auf Budget, Genre, Popularität, Bewertungen, Regisseur, Hauptdarsteller und weiteren Eigenschaften.

Das Ziel war, ein End-to-End Machine Learning Modell zu trainieren, evaluieren und als interaktive Web-App via Hugging Face Spaces zu deployen.

---

## Modellleistung

| Modell              | R²       | MAE (Mio. $) | RMSE (Mio. $) |
|---------------------|----------|--------------|----------------|
| Linear Regression   | 0.74     | 60.5         | 116.1          |
| Random Forest       | **0.78** | **42.3**     | **106.0**      |

**Random Forest** wurde für das Deployment gewählt.

---

## Model Inputs (Features)

| Feature | Beschreibung |
|--------|--------------|
| budget | Produktionsbudget in USD |
| popularity | Beliebtheitswert von TMDB |
| vote_average | Durchschnittliche Bewertung |
| vote_count | Anzahl Bewertungen |
| runtime | Filmlänge in Minuten |
| release_year | Erscheinungsjahr |
| director_avg_revenue | Durchschnittlicher Revenue des Regisseurs (Target-Encoding) |
| lead_actor_avg_revenue | Durchschnittlicher Revenue des Hauptdarstellers |
| genres (z. B. Action, Drama, Comedy, …) | One-Hot-Encoded Genre-Flags |

---

## Beispiel (Input für Gradio-App)

| Inputfeld | Beispielwert |
|-----------|---------------|
| Budget | 150_000_000 |
| Popularity | 35.0 |
| Vote Average | 7.8 |
| Vote Count | 3500 |
| Runtime | 140 |
| Release Year | 2022 |
| Director Avg Revenue | 420_000_000 |
| Lead Actor Avg Revenue | 380_000_000 |
| Genres | Action, Sci-Fi, Fantasy |

---

## Datenquellen

| Quelle | Beschreibung |
|--------|--------------|
| [TMDB Movies](https://drive.switch.ch/index.php/s/SgdbbF6MkF0fTly) | Film-Metadaten |
| [TMDB Credits](https://drive.switch.ch/index.php/s/j36PM3I1C0FaX3C) | Cast- & Crew-Daten |
| [IMDb + TMDB Kombidatensatz](https://drive.switch.ch/index.php/s/GknMWjEvz9VhuN4) | Bewertungen, Stars, Zusatzfeatures |

---

## Deployment

Das Modell wurde als interaktive Gradio-Webanwendung auf Hugging Face Spaces veröffentlicht.

| Name | Link |
|------|------|
| Web-App | [Hugging Face Space](https://huggingface.co/spaces/huserluk/project1w.3KIA) |
| Code | [GitHub Repository](https://github.com/LukiSpooky/project1w.3KIA/) |

---

## Autor

Luke Huser  
Modul: AI Applications (w.BA.XX.3KIA-WIN.XX)
