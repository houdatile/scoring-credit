# Crédit Scoring & Dashboard Interactif

## Description du projet

Ce projet a été réalisé pour **Prêt à dépenser**, dans le cadre du développement d’un **outil de scoring crédit**. L’objectif est de prédire la probabilité qu’un client rembourse son crédit, et de classer les demandes en **crédit accordé ou refusé**.

Pour renforcer la **transparence des décisions** et améliorer la connaissance client, un **dashboard interactif** a été développé à destination des chargés de relation client. Ce dashboard permet d’explorer les informations clients et d’interpréter les prédictions de manière intelligible pour des non-experts en data science.

Le projet inclut également la mise en production du modèle via une **API**, ainsi que le suivi du **Data Drift** en production à l’aide de la librairie **evidently**.

---

## Objectifs

1. Construire un **modèle de scoring** automatique pour prédire la probabilité de défaut de paiement d’un client.
2. Développer un **dashboard interactif** pour visualiser et interpréter les prédictions, et comparer un client avec un groupe similaire ou la population générale.
3. Mettre en œuvre une **pipeline MLOps** pour le suivi, le déploiement et la maintenance du modèle.
4. Détecter le **Data Drift** entre les données d’entraînement et les nouvelles données clients en production.

---

## Données utilisées

Les données proviennent de plusieurs sources clients et financières. Elles incluent :

* **Données comportementales** (historique des paiements, transactions, etc.)
* **Données externes** provenant d’institutions financières partenaires

> Les datasets principaux pour le développement et le test sont :
>
> * `application_train.csv` : données d’entraînement
> * `application_test.csv` : nouvelles données clients pour test/production

---

## Méthodologie

1. **Analyse exploratoire (EDA)**

   * Analyse des valeurs manquantes et des distributions
   * Identification des variables clés
   * Visualisation des corrélations

2. **Prétraitement et feature engineering**

   * Imputation des valeurs manquantes
   * Normalisation des variables
   * Encodage des variables catégorielles
   * Création de features métiers

3. **Modélisation**

   * Sélection des modèles de classification : Logistic Regression, Random Forest, XGBoost, LightGBM
   * Validation croisée et optimisation hyperparamètres via **GridSearchCV**
   * Gestion du déséquilibre des classes (ex : SMOTE, sur/sous-échantillonnage)
   * Optimisation d’un **score métier** tenant compte du coût différencié entre faux négatifs et faux positifs

4. **Interprétabilité**

   * Explications globales et locales via **SHAP** ou **LIME**
   * Visualisation des facteurs influençant la décision de crédit

5. **Déploiement**

   * API de prédiction exposée sur le cloud
   * Dashboard interactif développé avec **Streamlit**
   * Détection du **Data Drift** via **evidently**

---

## Fonctionnalités du Dashboard

* Visualiser le **score de crédit** et son interprétation par client
* Explorer les informations descriptives du client
* Comparer un client avec l’ensemble des clients ou un groupe similaire
* Interface intuitive pour les chargés de relation client, non experts en data science

---

## Technologies utilisées

* Python 3.x
* Pandas, NumPy, Scikit-learn, XGBoost, LightGBM
* Streamlit / Dash / Bokeh (dashboard interactif)
* Evidently (Data Drift)
* MLflow (tracking des modèles et expérimentations)
* Plateforme cloud : Heroku / Azure / PythonAnywhere

---

## Métriques et suivi

* **Précision, AUC, Accuracy** pour l’évaluation classique
* **Score métier** basé sur le coût différencié FN vs FP
* **Cross-Validation** pour fiabilité des modèles
* **Tracking via MLflow** pour reproduire les expérimentations

---

## Déploiement

1. L’API et le dashboard sont hébergés sur le cloud (Heroku/ASP F1/Azure).
2. Le dashboard interagit avec l’API pour les prédictions en temps réel.
3. La librairie **evidently** génère un tableau HTML pour détecter le Data Drift futur.

