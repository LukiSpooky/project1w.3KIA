# Movie Revenue Predictor

Dieses Projekt sagt voraus, wie viel ein Film an den Kinokassen einspielen wird, basierend auf:

- Budget
- Popularität
- Bewertungen
- Hauptdarsteller & Regisseur
- Genre (One-Hot)
- u.a.

## Modell

- RandomForestRegressor (beste Performance mit R² ≈ 0.78)
- Trainingsdaten: Kombi aus TMDB & IMDb
- Features: numerisch & kategorisch (Target-Encoding, One-Hot)

## Deployment

Die App ist mit Gradio gebaut. Sie wird auf Hugging Face gehostet.

## Daten

Die Originaldaten sind aus Platzgründen auf SwitchDrive gehostet:

- [TMDB Movies](https://drive.switch.ch/index.php/s/SgdbbF6MkF0fTly)
- [TMDB Credits](https://drive.switch.ch/index.php/s/j36PM3I1C0FaX3C)
- [IMDb & TMDB](https://drive.switch.ch/index.php/s/GknMWjEvz9VhuN4)

## Beispiel

Budget: 150 Mio  
Genre: Action, Sci-Fi  
Erwarteter Umsatz: ~600 Mio

## Autor

Luke Huser  
Modul: End-to-End Machine Learning (w.3KIA)
