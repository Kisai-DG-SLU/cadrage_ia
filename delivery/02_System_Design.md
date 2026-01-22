# System Design & Architecture Azure - Projet Fashion-Insta

## 1. Vue d'Ensemble de l'Architecture (End-to-End)
L'architecture repose sur un pipeline de recherche de similarité visuelle industrialisé sur **Microsoft Azure**.

### Flux de données (Inférence Temps Réel)
1. **Frontend (Mobile App)** : L'utilisateur envoie une photo.
2. **API Gateway / App Service** : Réception de l'image et routage.
3. **Inférence (Extracteur d'Embeddings)** : Un modèle (ex: ResNet50) déployé sur **Azure Machine Learning** transforme l'image en vecteur numérique (embedding).
4. **Vector Search (Recherche)** : Interrogation d'**Azure AI Search** pour trouver les N articles les plus proches vectoriellement dans le catalogue.
5. **Enrichissement & Réponse** : Récupération des métadonnées (prix, lien, stock) et renvoi à l'utilisateur.

## 2. Cartographie des Services Azure

| Brique Technique | Service Azure Sélectionné | Justification |
| :--- | :--- | :--- |
| **Stockage Images** | **Azure Blob Storage** | Stockage scalable et économique des images catalogue et logs utilisateurs. |
| **Extraction de Vecteurs** | **Azure Machine Learning (Endpoints)** | Déploiement managé du modèle de Computer Vision avec autoscaling. |
| **Moteur de Recherche** | **Azure AI Search (Vector Search)** | Support natif de la recherche vectorielle (HNSW) et intégration facile. |
| **Orchestration API** | **Azure App Service (Python/FastAPI)** | Hébergement de l'API de recommandation, simple à maintenir. |
| **Pipeline de Données** | **Azure Data Factory** | Ingestion et synchronisation régulière du catalogue produits. |
| **Monitoring** | **Azure Monitor & App Insights** | Suivi des performances de l'API et de la latence d'inférence. |
| **Sécurité** | **Azure Key Vault** | Gestion sécurisée des secrets et clés d'API. |

## 3. Matrice des Rôles & Responsabilités (RACI)

| Brique / Tâche | Data Engineer | Data Scientist | ML Ops |
| :--- | :---: | :---: | :---: |
| **Ingestion Catalogue (Blob/ADF)** | **Responsable** | Consulté | Informé |
| **Entraînement & Optimisation Algo** | Informé | **Responsable** | Consulté |
| **Déploiement Endpoints (AML)** | Consulté | Soutien | **Responsable** |
| **Configuration Azure AI Search** | **Responsable** | Consulté | Soutien |
| **Développement API (App Service)** | Soutien | Consulté | **Responsable** |
| **Monitoring & Latence** | Informé | Consulté | **Responsable** |

## 4. Scalabilité et Performance
- **Passage à l'échelle** : Utilisation d'**Azure Kubernetes Service (AKS)** si le trafic dépasse les capacités d'App Service (estimé > 100 req/s).
- **Latence** : Mise en cache des embeddings des articles les plus populaires via **Azure Cache for Redis** pour réduire la charge sur le moteur de recherche.
