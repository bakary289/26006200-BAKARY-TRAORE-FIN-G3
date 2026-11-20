# 26006200-BAKARY-TRAORE-FIN-G3
# Projet F16 – Loi d'Okun

## 1. Présentation du projet

Ce projet porte sur l'étude de la relation entre la croissance économique et le chômage aux États-Unis, dans le cadre de la Loi d'Okun.

## 2. Problématique

Dans quelle mesure la croissance économique suffit-elle à réduire durablement le chômage aux États-Unis ?

## 3. Objectif

Analyser la relation entre la croissance du PIB réel et l'évolution du taux de chômage aux États-Unis, puis examiner la stabilité de cette relation dans le temps.

## 4. Sources des données

Les données proviennent de FRED (Federal Reserve Bank of St) :

- PIB réel trimestriel : série `GDPC1`.
- Taux de chômage mensuel : série `UNRATE`.

Le taux de chômage mensuel sera transformé en moyenne trimestrielle afin d'harmoniser les fréquences.

## 5. Méthodologie

Le projet repose sur une régression linéaire simple, avec un seul prédicteur : la croissance du PIB réel.

La variable à expliquer sera la variation trimestrielle du taux de chômage.

Les analyses porteront notamment sur l'interprétation du coefficient de régression et sa stabilité dans le temps.

## 6. Environnement de travail

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Statsmodels

## 7. Structure du dépôt

- `data/raw/` : données brutes.
- `data/processed/` : données préparées.
- `docs/` : documentation du projet.
- `notebooks/` : notebook Google Colab.
- `figures/` : graphiques.
- `rapport/` : rapport final.
- `presentation/` : présentation finale.
- `requirements.txt` : dépendances Python.
- `DECLARATION_IA.md` : déclaration d'utilisation de l'IA.

## 8. Statut du projet

Projet en cours de réalisation. Les résultats seront ajoutés après les analyses.
