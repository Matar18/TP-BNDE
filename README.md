# Analyse du Portefeuille Crédit — BNDE

Travail pratique d'exploration, nettoyage et profilage de données appliqué au portefeuille de crédit de la BNDE (Banque Nationale de Développement Économique).

## Objectifs

1. Explorer et comprendre les données du portefeuille de crédit
2. Nettoyer les données (valeurs manquantes, anomalies)
3. Identifier le profil des clients
4. Déterminer quels profils remboursent mal
5. Évaluer l'exploitabilité du dataset pour des analyses futures

## Contenu du dépôt

| Fichier | Description |
|---|---|
| [`Analyse_Portefeuille_Credit_BNDE.ipynb`](Analyse_Portefeuille_Credit_BNDE.ipynb) | Notebook principal : exploration, nettoyage et analyse du portefeuille de crédit |
| [`BNDE_Presentation.pptx`](BNDE_Presentation.pptx) | Support de présentation des résultats |
| [`Pratiques.pdf`](Pratiques.pdf) | Document de référence / énoncé des travaux pratiques |
| [`dataset_BNDE.csv`](dataset_BNDE.csv) / [`dataset_BNDE.xlsx`](dataset_BNDE.xlsx) | Jeu de données du portefeuille de crédit |

## Méthodologie

Le notebook est structuré en plusieurs étapes :

1. **Import et chargement des données**
2. **Exploration initiale** du dataset (dimensions, types, valeurs uniques)
3. **Nettoyage des données** : valeurs manquantes, détection et traitement des anomalies (retards de paiement anormaux, montants de crédit incohérents avec le revenu)
4. **Profilage des clients** : secteurs d'activité, revenu mensuel, types de garantie, taux d'intérêt
5. **Analyse du risque de remboursement** : lien entre statut de remboursement et montant du crédit, taux d'intérêt, retard de paiement, région, garantie, revenu et durée du crédit
6. **Évaluation de l'exploitabilité** des données pour des analyses futures

## Outils utilisés

- Python (pandas, numpy, matplotlib, seaborn)
- Jupyter Notebook

## Auteur

Matar Ndoye
