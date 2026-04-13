# Churn Prediction — Telco Customer Churn

> 🇬🇧 [English](#english) · 🇫🇷 [Français](#français)

---

## English

Customer churn prediction using classical machine learning.
Built on the Telco Customer Churn dataset (IBM / Kaggle).

### Context

The goal is to predict whether a telecom customer is likely to churn (cancel their subscription),
using demographic and account data available at the time of analysis.

Churn is a binary classification problem:
- **Churn** — customer left the company
- **No Churn** — customer stayed

### Dataset

- Source: [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- 7043 rows, 21 columns → 7032 after cleaning
- Key features: tenure, MonthlyCharges, TotalCharges, Contract, PaymentMethod, InternetService...
- Target column: `Churn` (Yes / No)

### Cleaning

- `TotalCharges` stored as string due to 11 rows containing a whitespace character `' '` (new customers with no billing history)
- Converted to `float64` using `pd.to_numeric(errors='coerce')` → 11 NaN values revealed → removed with `dropna()`

### Pipeline

```
churn_analysis.ipynb   → Full analysis: EDA, preprocessing, feature engineering, model training
```

### Models

| Model | Accuracy | Churn F1 | Churn Recall |
|-------|----------|----------|--------------|
| Logistic Regression (`class_weight=balanced`) | 72.14% | 0.60 | **0.78** |
| Random Forest (`class_weight=balanced`) | **75.69%** | 0.51 | 0.48 |
| XGBoost (`scale_pos_weight`) | 73.85% | 0.58 | 0.68 |

> Best recall: Logistic Regression — detects 78% of churners. Best accuracy: Random Forest.

### Stack

Python · Pandas · Scikit-learn · XGBoost · Jupyter

### Author

Clément Schmitt — [LinkedIn](https://www.linkedin.com/in/clement-schmitt/)

---

## Français

Prédiction du churn client par machine learning classique.
Basé sur le dataset Telco Customer Churn (IBM / Kaggle).

### Contexte

L'objectif est de prédire si un client d'un opérateur télécom va résilier son abonnement (churn),
en s'appuyant sur des données démographiques et de compte disponibles au moment de l'analyse.

Le churn est un problème de classification binaire :
- **Churn** — le client a quitté l'entreprise
- **No Churn** — le client est resté

### Dataset

- Source : [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- 7043 lignes, 21 colonnes → 7032 après nettoyage
- Features principales : tenure, MonthlyCharges, TotalCharges, Contract, PaymentMethod, InternetService...
- Colonne cible : `Churn` (Yes / No)

### Nettoyage

- `TotalCharges` stockée en string en raison de 11 lignes contenant un espace `' '` (nouveaux clients sans historique de facturation)
- Convertie en `float64` via `pd.to_numeric(errors='coerce')` → 11 valeurs NaN révélées → supprimées avec `dropna()`

### Pipeline

```
churn_analysis.ipynb   → Analyse complète : EDA, preprocessing, feature engineering, entraînement
```

### Modèles

| Modèle | Accuracy | F1 Churn | Recall Churn |
|--------|----------|----------|--------------|
| Logistic Regression (`class_weight=balanced`) | 72.14% | 0.60 | **0.78** |
| Random Forest (`class_weight=balanced`) | **75.69%** | 0.51 | 0.48 |
| XGBoost (`scale_pos_weight`) | 73.85% | 0.58 | 0.68 |

> Meilleur recall : Logistic Regression — détecte 78% des churners. Meilleure accuracy : Random Forest.

### Stack

Python · Pandas · Scikit-learn · XGBoost · Jupyter

### Auteur

Clément Schmitt — [LinkedIn](https://www.linkedin.com/in/clement-schmitt/)
