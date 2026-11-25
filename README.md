
# 26006200-BAKARY-TRAORE-FIN-G3

# Projet F16 – Loi d'Okun

## 1. Présentation du projet

Ce projet étudie la relation entre la croissance économique et la variation du taux de chômage aux États-Unis, dans le cadre de la loi d'Okun.

La loi d'Okun décrit une relation généralement négative entre la croissance de la production économique et l'évolution du chômage.

## 2. Problématique

**Dans quelle mesure la croissance économique suffit-elle à réduire durablement le chômage aux États-Unis ?**

## 3. Objectif

L'objectif principal est d'analyser la relation entre la croissance trimestrielle du PIB réel et la variation du taux de chômage américain à l'aide d'une régression linéaire simple.

L'étude vise également à :

- Évaluer les performances prédictives du modèle.
- Comparer le modèle à une référence naïve.
- Examiner la significativité statistique du coefficient estimé.
- Étudier la stabilité de la relation au cours du temps.
- Identifier les limites du modèle.

## 4. Sources et description des données

Les données économiques proviennent de la base **FRED (Federal Reserve Economic Data)**, publiée par la Federal Reserve Bank of St. Louis.

### Sources des données

- **PIB réel américain (GDPC1) :** https://fred.stlouisfed.org/series/GDPC1
- **Taux de chômage américain (UNRATE) :** https://fred.stlouisfed.org/series/UNRATE

**Date d'extraction :** 20 novembre 2026.

**Période étudiée :** 1990Q2 à 2026Q3.

Le PIB réel est disponible à une fréquence trimestrielle, tandis que le taux de chômage est mensuel. Les observations mensuelles du chômage sont donc transformées en moyennes trimestrielles afin d'harmoniser les fréquences.

Le jeu de données final comporte **144 observations et 5 variables**, sans valeurs manquantes ni doublons.

### Variables utilisées

| Variable | Description | Rôle |
|---|---|---|
| GDP_Growth | Croissance trimestrielle non annualisée du PIB réel (%) | Explicative (X) |
| Delta_UNRATE | Variation trimestrielle du taux de chômage (points de pourcentage) | Cible (Y) |
| PIB_reel | Niveau du PIB réel américain | Variable de calcul |
| taux_chomage | Taux de chômage trimestriel moyen (%) | Variable de calcul |
| trimestre | Identifiant de la période trimestrielle | Variable temporelle |

### Formules de calcul

La croissance trimestrielle non annualisée du PIB réel est calculée comme suit :

\[
GDP\_Growth_t =
\left(\frac{PIB_t}{PIB_{t-1}}-1\right)\times100
\]

La variation trimestrielle du taux de chômage est calculée par différence entre deux trimestres successifs :

\[
Delta\_UNRATE_t = U_t-U_{t-1}
\]

## 5. Méthodologie

L'étude repose sur un algorithme de **régression linéaire simple**, utilisant un seul prédicteur : la croissance trimestrielle du PIB réel.

Le protocole expérimental comprend les étapes suivantes :

- Préparation, nettoyage et exploration des données.
- Construction d'un Pipeline de régression linéaire avec scikit-learn.
- Séparation chronologique des données : 80 % pour l'entraînement et 20 % pour le test.
- Validation chronologique en cinq plis avec TimeSeriesSplit.
- Recherche du meilleur paramétrage avec GridSearchCV.
- Construction d'une référence naïve fondée sur la moyenne historique calculée sur les données d'entraînement.
- Calcul des métriques de performance : MAE, MSE et R².
- Construction et interprétation de la courbe d'apprentissage.
- Présentation d'exemples de prédictions sur les données de test.
- Analyse de l'inférence statistique avec erreurs-types robustes HAC.
- Test de Breusch-Godfrey pour examiner l'autocorrélation des résidus.
- Analyse de la stabilité du coefficient sur deux sous-périodes.

La séparation chronologique permet de respecter l'ordre temporel des observations et d'éviter l'utilisation d'informations futures pour entraîner le modèle.

## 6. Environnement de travail

Le projet a été réalisé avec Python dans Google Colab.

Les principales bibliothèques utilisées sont :

| Bibliothèque | Version |
|---|---|
| Pandas | 2.2.3 |
| NumPy | 2.4.6 |
| Matplotlib | 3.10.0 |
| Seaborn | 0.13.2 |
| Scikit-learn | 1.6.1 |
| Statsmodels | 0.15.0 |

Les dépendances nécessaires à la reproduction du projet sont répertoriées dans le fichier `requirements.txt`.

## 7. Structure du dépôt GitHub

Le dépôt est organisé de la manière suivante :

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
│   │   ├── PIB REEL USA trimestriel.csv
│   │   └── TAUX DE CHOMAGE DE USA mensuel.csv
│   │
│   └── processed/
│       └── donnees_finales_F16.csv
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
│   ├── 01_evolution_croissance_PIB.png
│   ├── 02_evolution_taux_chomage.png
│   └── 03_relation_croissance_chomage.png
│
├── rapport/
│
└── presentation/
```

### Description des dossiers

- `data/raw/` : données économiques brutes téléchargées depuis FRED.
- `data/processed/` : jeu de données final préparé pour la modélisation.
- `docs/` : consignes officielles, fiche du sujet et références bibliographiques.
- `notebooks/` : notebook principal contenant les traitements, les analyses et la modélisation.
- `figures/` : graphiques issus de l'exploration et de l'analyse des données.
- `rapport/` : documents du rapport final.
- `presentation/` : supports de présentation du projet.

## 8. Principaux résultats et limites

### Résultats du modèle optimisé

La recherche par validation chronologique a retenu une régression linéaire sans constante (`fit_intercept=False`).

Le coefficient estimé de la croissance du PIB réel est de **-0,1388**.

L'équation du modèle retenu est :

\[
\widehat{Delta\_UNRATE}
= -0,1388 \times GDP\_Growth
\]

Le modèle a été évalué sur 29 observations de test, après un entraînement sur 115 observations.

### Comparaison avec la référence naïve

| Indicateur | Régression optimisée | Référence naïve |
|---|---:|---:|
| MAE | 0,6199 | 0,6996 |
| MSE | 2,7676 | 3,7297 |
| R² | 0,2579 | -0,0001 |

La régression optimisée obtient de meilleures performances que la référence naïve sur les trois indicateurs.

Le coefficient de détermination R² de 0,2579 indique que le modèle explique environ 25,79 % de la variance de la variable cible sur l'échantillon de test.

### Validation chronologique

La validation chronologique en cinq plis a donné les résultats suivants pour le meilleur paramétrage :

- MAE moyenne de validation : **0,1703**.
- Écart-type de la MAE : **0,0710**.
- Meilleur paramétrage : régression sans constante.

### Analyse statistique et stabilité

L'analyse avec erreurs-types robustes HAC confirme la significativité statistique du coefficient estimé (p < 0,001).

Le test de Breusch-Godfrey révèle une autocorrélation des résidus. Cette dépendance temporelle constitue une limite du modèle. Les erreurs-types robustes HAC permettent de tenir compte de cette caractéristique dans l'inférence statistique.

L'analyse de stabilité sur deux sous-périodes donne les coefficients suivants :

| Sous-période | Coefficient |
|---|---:|
| 1990Q2 à 2004Q2 | -0,0718 |
| 2004Q3 à 2018Q4 | -0,2380 |

L'écart absolu entre les deux coefficients est de 0,1662. La relation reste négative, mais son intensité évolue au cours du temps.

### Conclusion et limites

Les résultats mettent en évidence une relation négative entre la croissance économique et la variation du chômage aux États-Unis, conformément au principe général de la loi d'Okun.

Cependant, la croissance économique ne suffit pas, à elle seule, à expliquer toutes les fluctuations du chômage.

Les principales limites de l'étude sont :

- L'utilisation d'un seul prédicteur économique.
- L'autocorrélation des résidus.
- La stabilité imparfaite du coefficient entre les sous-périodes.
- Les fluctuations exceptionnelles, notamment pendant la crise sanitaire de 2020, qui compliquent les prédictions.

## 9. Reproduction des résultats

Pour reproduire cette étude, suivre les étapes suivantes :

### 1. Récupérer le dépôt

Télécharger ou cloner le dépôt GitHub :

```bash
git clone https://github.com/bakary289/26006200-BAKARY-TRAORE-FIN-G3.git
```

### 2. Installer les dépendances

Se placer à la racine du dépôt et exécuter :

```bash
pip install -r requirements.txt
```

### 3. Ouvrir le notebook

Ouvrir le fichier :

`notebooks/F16_Loi_Okun_USA.ipynb`

Le notebook peut être exécuté dans Google Colab ou dans un environnement Jupyter.

### 4. Vérifier les données

Vérifier la présence des fichiers CSV bruts dans `data/raw/` et du jeu de données préparé dans `data/processed/`.

S'assurer que le répertoire de travail permet d'accéder à ces fichiers avec les chemins utilisés dans le notebook.

### 5. Exécuter l'analyse

Exécuter les cellules du notebook dans l'ordre chronologique, depuis l'importation des données jusqu'à l'évaluation et à l'interprétation du modèle.

Les tableaux, métriques et graphiques permettent de retrouver les principaux résultats présentés dans ce projet.

## Dépôt GitHub

Le code source, les données, le notebook et les documents du projet sont disponibles à l'adresse suivante :

https://github.com/bakary289/26006200-BAKARY-TRAORE-FIN-G3
```


