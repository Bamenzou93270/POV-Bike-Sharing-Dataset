# Bike Sharing – Prévision de la demande horaire

## Objectif

Ce projet vise à prédire la demande horaire de vélos pour la semaine suivante à partir des données Capital Bikeshare 2024–2025.

L’objectif est opérationnel : anticiper les pics de demande afin d’optimiser la planification des équipes (rééquilibrage, maintenance, support).

---

## Installation

Python 3.9+

Installer les dépendances :

pip install -r requirements.txt

---

## Données

Télécharger les fichiers mensuels 2024 et 2025 depuis :
https://capitalbikeshare.com/system-data

Placer tous les fichiers CSV dans un dossier `data/` à la racine du projet.

---

## Exécution

Lancer le notebook ou le script principal.

Le pipeline comprend :

- Chargement et concaténation des 24 mois  
- Nettoyage (dates manquantes, doublons, durées incohérentes)  
- Agrégation en série horaire continue  
- Feature engineering (variables calendaires + lags)  
- Split temporel strict  
- Baseline lag 168h  
- Entraînement RandomForest  
- Évaluation et analyse de robustesse  

---

## Résultats principaux (période test nov–déc 2025)

Baseline (lag 168h)
MAE ≈ 151  
sMAPE ≈ 34 %

RandomForest
MAE ≈ 116  
sMAPE ≈ 29 %  
MASE ≈ 0.77  

Amélioration d’environ 24 % par rapport à la baseline.

---

## Analyse rapide

- 9.56 % des heures présentent une erreur supérieure à 300 trajets  
- Sur Thanksgiving et Noël, le MAE monte à ≈ 336  
- Le modèle capture bien les patterns réguliers mais reste sensible aux événements exceptionnels  
