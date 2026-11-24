
# Fiche du sujet F16 – Loi d'Okun

## 1. Identification du projet

- **Sujet :** F16 – Loi d'Okun
- **Étudiant :** Bakary Traoré
- **Code Apogée :** 26006200
- **Groupe :** FIN G3
- **Pays étudié :** États-Unis
- **Algorithme :** 1 – Régression linéaire simple

## 2. Contexte et problématique

La loi d'Okun décrit une relation négative entre la croissance économique et l'évolution du chômage. En période de croissance, le chômage tend généralement à diminuer, tandis qu'un ralentissement économique peut s'accompagner d'une hausse du chômage.

**Problématique :**

Dans quelle mesure la croissance économique suffit-elle à réduire durablement le chômage aux États-Unis ?

## 3. Objectif de l'étude

Étudier la relation entre la croissance trimestrielle du PIB réel et la variation trimestrielle du taux de chômage aux États-Unis, à l'aide d'une régression linéaire simple.

L'objectif est d'évaluer le pouvoir explicatif et prédictif de la croissance économique, ainsi que la stabilité du coefficient estimé.

## 4. Sources et données

Les données proviennent de la base FRED (Federal Reserve Economic Data).

- **PIB réel (GDPC1) :** https://fred.stlouisfed.org/series/GDPC1
- **Taux de chômage (UNRATE) :** https://fred.stlouisfed.org/series/UNRATE
- **Date d'extraction :** 20 novembre 2026.
- **Période d'étude :** 1990Q2 à 2026Q3.
- **Fréquence :** trimestrielle.
- **Nombre d'observations finales :** 144.

## 5. Variables utilisées

| Variable | Description | Rôle |
|---|---|---|
| GDP_Growth | Croissance trimestrielle non annualisée du PIB réel (%) | Explicative (X) |
| Delta_UNRATE | Variation trimestrielle du taux de chômage (points de pourcentage) | Cible (Y) |
| PIB_reel | Niveau du PIB réel américain | Variable de calcul |
| taux_chomage | Moyenne trimestrielle du taux de chômage | Variable de calcul |

Le taux de chômage mensuel est transformé en moyenne trimestrielle. La variation du chômage correspond à la différence entre deux moyennes trimestrielles successives.

La croissance du PIB est calculée selon la formule :

GDP_Growth = ((PIB_t / PIB_t-1) - 1) × 100

## 6. Préparation des données

Les données mensuelles du chômage sont agrégées en moyennes trimestrielles afin de les aligner avec la fréquence du PIB réel.

Les variables de croissance du PIB et de variation du chômage sont ensuite calculées. Les observations comportant des valeurs manquantes pour ces variables sont exclues.

Le jeu final comporte 144 observations et cinq variables, sans valeur manquante ni doublon.

## 7. Modélisation et évaluation

L'algorithme retenu est une régression linéaire simple avec un seul prédicteur : la croissance trimestrielle du PIB réel.

Le protocole comprend :
- Une séparation chronologique entre entraînement (80 %) et test (20 %).
- Une référence naïve fondée sur la moyenne historique de la variable cible.
- Une validation chronologique avec TimeSeriesSplit et GridSearchCV.
- Une courbe d'apprentissage.
- Une analyse de l'inférence statistique avec erreurs-types robustes HAC.
- Une vérification de la stabilité du coefficient sur deux sous-périodes.

Les principales métriques utilisées sont la MAE, la MSE et le coefficient de détermination R².

## 8. Limites et précautions

La relation entre croissance économique et chômage peut varier selon les périodes et les conditions économiques. Les crises exceptionnelles, notamment celle de 2020, peuvent entraîner des fluctuations difficiles à prévoir.

L'autocorrélation des résidus et la stabilité imparfaite du coefficient constituent également des limites de l'analyse.
