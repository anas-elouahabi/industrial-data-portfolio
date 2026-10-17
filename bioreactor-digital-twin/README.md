# Jumeau Numérique Prédictif pour Bioréacteur (Processus Fed-Batch CHO-K1)

**Auteur :** Anas EL OUAHABI
**Domaine :** Génie des Procédés Industriels et Pharmaceutiques | Modélisation Statistique Appliquée

---

## Présentation du Projet
Ce projet est une application web interactive de type **Jumeau Numérique (Digital Twin)** conçue pour l'industrie biopharmaceutique. Il simule un processus de culture cellulaire Fed-Batch (cellules CHO-K1) sur 14 jours pour la production d'anticorps monoclonaux (mAbs).

L'objectif de cet outil est de fournir un tableau de bord MS&T (Manufacturing Science and Technology) permettant d'appliquer les principes de **Quality by Design (QbD)**. Il permet aux ingénieurs d'ajuster virtuellement les Paramètres Critiques de Procédé (CPP) et de prédire instantanément les Attributs Critiques Qualité (CQA) grâce à une modélisation statistique avancée, évitant ainsi des tests physiques longs et coûteux.

## Fonctionnalités Principales
* **Simulation en Temps Réel :** Prédiction instantanée de la viabilité cellulaire et du rendement (Titer) en fonction des paramètres d'entrée.
* **Interface MS&T Interactive :** Manipulation des CPP (pH, Température, Oxygène Dissous, Glucose Feed) via un tableau de bord intuitif.
* **Évaluation de la Qualité (OOS) :** Vérification automatique du respect des spécifications de qualité (cibles logistiques atteintes, produit dans les normes).
* **Modélisation Statistique Appliquée :** Utilisation de modèles de régression multivariable (XGBoost) pour capturer la dynamique non-linéaire du bioréacteur.

## Architecture Technique
L'application repose sur une architecture client-serveur découplée :

1. **Front-End (Interface Opérateur) :** 
   * Développé en **React / Next.js**.
   * Gère l'expérience utilisateur et l'envoi des requêtes API sans effectuer de calculs lourds localement.
2. **Back-End (Moteur de Calcul) :**
   * Développé en **Python / FastAPI**.
   * Héberge l'API REST et exécute les calculs de prédiction statistique en quelques millisecondes.
3. **Modèle de Prédiction :**
   * Modèle hybride intégrant des équations théoriques de génie des procédés et des modèles statistiques (XGBoost).

## Instructions d'Installation et d'Exécution

Pour exécuter ce projet localement, vous devez lancer le serveur Back-End (Python) et le serveur Front-End (Node.js) simultanément.

### 1. Démarrer le Back-End (Moteur de calcul Python)
Ouvrez un terminal dans le dossier racine du projet et exécutez :
```bash
# Activation de l'environnement virtuel (si applicable)
# Installation des dépendances
pip install -r requirements.txt

# Lancement de l'API FastAPI avec Uvicorn
python -m uvicorn main:app --reload
