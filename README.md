# 26006200-BAKARY-TRAORE-FIN-G3

# Projet F16 – Loi d'Okun

## 1. Présentation du projet

Ce projet étudie la relation entre la croissance économique et la variation du taux de chômage aux États-Unis, dans le cadre de la loi d'Okun.

## 2. Problématique

Dans quelle mesure la croissance économique suffit-elle à réduire durablement le chômage aux États-Unis ?

## 3. Objectif

Analyser la relation entre la croissance trimestrielle du PIB réel et la variation du taux de chômage américain à l'aide d'une régression linéaire simple.

L'étude examine également les performances prédictives du modèle, la significativité statistique et la stabilité du coefficient dans le temps.

## 4. Sources et description des données

Les données proviennent de la base FRED (Federal Reserve Economic Data).

- **PIB réel américain (GDPC1) :** https://fred.stlouisfed.org/series/GDPC1
- **Taux de chômage américain (UNRATE) :** https://fred.stlouisfed.org/series/UNRATE

**Date d'extraction :** 20 novembre 2026.

**Période étudiée :** 1990Q2 à 2026Q3.

Le taux de chômage mensuel est transformé en moyenne trimestrielle afin de l'aligner avec la fréquence du PIB réel.

Le jeu de données final comporte 144 observations et 5 variables, sans valeurs manquantes ni doublons.

### Variables principales

| Variable | Description | Rôle |
|---|---|---|
| GDP_Growth | Croissance trimestrielle non annualisée du PIB réel (%) | Explicative (X) |
| Delta_UNRATE | Variation trimestrielle du taux de chômage (points de pourcentage) | Cible (Y) |
| PIB_reel | Niveau du PIB réel | Variable de calcul |
| taux_chomage | Taux de chômage trimestriel moyen | Variable de calcul |

## 5. Méthodologie

L'étude repose sur une régression linéaire simple avec un seul prédicteur : la croissance trimestrielle du PIB réel.

Le protocole comprend :

- La préparation et l'exploration des données.
- La construction d'un Pipeline de régression linéaire.
- Une séparation chronologique entre entraînement (80 %) et test (20 %).
- Une validation chronologique en cinq plis avec TimeSeriesSplit et GridSearchCV.
- Une comparaison avec une référence naïve fondée sur la moyenne historique.
- Une courbe d'apprentissage et des exemples de prédictions.
- Une analyse statistique avec erreurs-types robustes HAC.
- Un test de Breusch-Godfrey et une analyse de stabilité du coefficient.

## 6. Environnement de travail

Le projet utilise Python et les bibliothèques suivantes :

| Bibliothèque | Version |
|---|---|
| Pandas | 2.2.3 |
| NumPy | 2.4.6 |
| Matplotlib | 3.10.0 |
| Seaborn | 0.13.2 |
| Scikit-learn | 1.6.1 |
| Statsmodels | 0.15.0 |

Les dépendances sont disponibles dans le fichier `requirements.txt`.

## 7. Structure du dépôt

```text
26006200-BAKARY-TRAORE-FIN-G3/
│
├── README.md
├── .gitignore
├── requirements.txt
├── DECLARATION_IA.md
│
├── data/
│   ├── raw/
│   └── processed/
│
├── docs/
│   ├── CC- Partie B- ML_finance-S7.md
│   ├── fiche_sujet_F16.md
│   └── references.md
│
├── notebooks/
│   └── F16_Loi_Okun_USA.ipynb
│
├── figures/
├── rapport/
└── presentation/
```

## 8. Principaux résultats et limites

Le modèle optimisé retient une régression linéaire sans constante, avec un coefficient estimé de -0,1388.

Sur les 29 observations de test, les performances obtenues sont :

| Indicateur | Régression optimisée | Référence naïve |
|---|---:|---:|
| MAE | 0,6199 | 0,6996 |
| MSE | 2,7676 | 3,7297 |
| R² | 0,2579 | -0,0001 |

La validation chronologique donne une MAE moyenne de 0,1703 et un écart-type de 0,0710.

L'analyse statistique avec erreurs-types HAC confirme la significativité du coefficient (p < 0,001). Toutefois, le test de Breusch-Godfrey révèle une autocorrélation des résidus.

L'analyse de stabilité montre également que l'intensité de la relation varie selon les sous-périodes étudiées.

Ces résultats confirment une relation négative entre croissance économique et variation du chômage, tout en montrant que la croissance seule ne suffit pas à expliquer toutes les fluctuations du marché du travail.

## 9. Reproduction des résultats

Pour reproduire l'étude :

1. Télécharger ou cloner le dépôt GitHub.
2. Installer les dépendances avec la commande :

```bash
pip install -r requirements.txt
```

3. Ouvrir le notebook `F16_Loi_Okun_USA.ipynb` dans Google Colab ou Jupyter.
4. Vérifier la disponibilité des fichiers de données dans les dossiers correspondants.
5. Exécuter les cellules dans l'ordre, de la préparation des données jusqu'à l'évaluation du modèle.

## Dépôt GitHub

https://github.com/bakary289/26006200-BAKARY-TRAORE-FIN-G3


