# Analyse du Portefeuille Crédit — BNDE

Travail pratique d'exploration, de nettoyage et de profilage de données appliqué au portefeuille de crédit de la BNDE (Banque Nationale pour le Développement Économique, Sénégal).

## Objectifs

1. Explorer et comprendre les données du portefeuille de crédit
2. Nettoyer les données (doublons, valeurs manquantes, anomalies)
3. Identifier le profil des clients
4. Déterminer quels profils remboursent mal
5. Évaluer l'exploitabilité du dataset pour des analyses futures

## Contenu du dépôt

| Fichier | Description |
|---|---|
| [`Analyse_Portefeuille_Credit_BNDE.ipynb`](Analyse_Portefeuille_Credit_BNDE.ipynb) | Notebook principal : exploration, nettoyage et analyse du portefeuille |
| [`dataset_BNDE.csv`](dataset_BNDE.csv) | Jeu de données (séparateur `;`, encodage `latin1`) |
| [`dataset_BNDE.xlsx`](dataset_BNDE.xlsx) | Même jeu de données au format Excel |

## Données

503 lignes (500 clients après suppression des doublons) et 12 variables :

| Catégorie | Variables |
|---|---|
| Profil client | `Client_ID`, `Age`, `Region`, `Secteur_Activite`, `Revenu_Mensuel` |
| Conditions du crédit | `Montant_Credit`, `Duree_Mois`, `Taux_Interet`, `Nb_Credits_Anterieurs`, `Garantie` |
| Comportement de remboursement | `Retard_Paiement_Jours`, `Statut_Credit` (Bon / Douteux / Contentieux) |

## Méthodologie

1. **Chargement et exploration** : dimensions, types, valeurs uniques, statistiques descriptives
2. **Nettoyage**
   - Suppression de 3 doublons
   - Suppression de la variable `Age` (15 valeurs manquantes, faiblement corrélée aux autres variables)
   - Conversion de `Taux_Interet` (virgule décimale) en numérique
3. **Détection des anomalies**
   - 4 revenus mensuels négatifs (erreurs de signe probables)
   - 1 client (CLI0088) avec 980 jours de retard mais un statut « Bon », incohérent avec les normes BCEAO (> 360 jours)
   - 1 crédit de 95 000 000 FCFA pour un revenu de 225 000 FCFA (CLI0043, zéro en trop probable)
4. **Profilage des clients** : régions, secteurs d'activité, revenus, garanties, taux d'intérêt
5. **Analyse du risque** : statut de remboursement croisé avec le montant, le taux, le retard, la région, la garantie, le revenu et la durée
6. **Évaluation de l'exploitabilité** des données

## Principaux résultats

- **Taux de défaut combiné (Douteux + Contentieux) : 35,2 %** (324 Bon, 126 Douteux, 50 Contentieux)
- **Le retard de paiement est le signal de risque le plus fort** : les clients Contentieux ont les retards médians les plus élevés.
- **Montant, taux d'intérêt, garantie et durée ne distinguent pas les bons des mauvais payeurs.** Les taux moyens sont quasi identiques d'un statut à l'autre (12,8 % à 13,3 %), ce qui montre l'absence de prime de risque différenciée.
- **Un revenu élevé ne garantit pas le remboursement** : parmi les clients gagnant plus de 500 000 FCFA, 50 sont Douteux et 12 Contentieux.
- **Par région** : Dakar est la plus saine (67 % de bons payeurs), Kaolack a le taux de Contentieux le plus élevé (~13 %), Ziguinchor et Saint-Louis ont le plus de clients Douteux (≥ 28 %).
- **Qualité des données après nettoyage** : 500 lignes ; il reste des valeurs manquantes sur `Revenu_Mensuel` (20) et `Taux_Interet` (10).

## Exécution

```bash
git clone https://github.com/Matar18/TP-BNDE.git
cd TP-BNDE
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Analyse_Portefeuille_Credit_BNDE.ipynb
```

## Outils utilisés

- Python : pandas, numpy, matplotlib, seaborn
- Jupyter Notebook

## Auteur

Matar Ndoye
