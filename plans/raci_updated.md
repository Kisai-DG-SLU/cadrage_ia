# Matrice RACI 

## Rôle Tech Lead Data
Le **Tech Lead Data** est responsable de :
- Supervision technique de l'ensemble du pipeline de données
- Décisions architecturales et choix technologiques
- Coordination entre Data Engineers, Data Scientists et ML Ops
- Validation des performances et de la scalabilité
- Gestion des risques techniques et de la dette technique
- Interface avec les parties prenantes métier et technique

## Matrice RACI Complète

| Brique / Tâche | Data Engineer | Data Scientist | ML Ops | Tech Lead Data |
| :--- | :---: | :---: | :---: | :---: |
| **Ingestion Catalogue (Blob/ADF)** | **R** | C | I | A |
| **Entraînement & Optimisation Algo** | I | **R** | C | A |
| **Déploiement Endpoints (AML)** | C | S | **R** | A |
| **Configuration Azure AI Search** | **R** | C | S | A |
| **Développement API (App Service)** | S | C | **R** | A |
| **Monitoring & Latence** | I | C | **R** | A |
| **Architecture & Design Technique** | C | C | C | **R** |
| **Gestion des Coûts Azure** | I | I | C | **R** |
| **Sécurité & Conformité RGPD** | C | C | C | **R** |
| **Plan de Reprise d'Activité** | C | I | C | **R** |
| **Documentation Technique** | C | C | C | **R** |
| **Revue de Code & Best Practices** | C | C | C | **R** |

## Légende
- **R** = Responsable (réalise la tâche)
- **A** = Accountable (approuve et est redevable)
- **C** = Consulté (donne son avis)
- **I** = Informé (tenu au courant)
- **S** = Soutien (assiste le responsable)

## Explications par Rôle

### Tech Lead Data (A)
- **Accountable** pour la majorité des tâches stratégiques
- Valide les décisions techniques et architecturales
- Assure la cohérence entre les différents composants
- Signe les décisions de déploiement en production

### Data Engineer (R pour ingestion, configuration)
- Responsable des pipelines de données (Azure Data Factory)
- Gère le stockage (Azure Blob Storage)
- Configure Azure AI Search (indexation)

### Data Scientist (R pour entraînement)
- Développe et optimise les modèles d'IA
- Valide les performances des algorithmes
- Gère la qualité des embeddings

### ML Ops (R pour déploiement, monitoring)
- Déploie les modèles sur Azure Machine Learning
- Met en place le monitoring et les alertes
- Gère la scalabilité des endpoints

## Implications pour le Projet Fashion-Insta
1. **Formation** : S'assurer que l'équipe comprend la matrice RACI
2. **Processus** : Mettre en place des réunions de coordination hebdomadaires
3. **Documentation** : Maintenir à jour les décisions architecturales
