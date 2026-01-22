# Cadrage du POC - Projet Fashion-Insta

## 1. Contexte & Valeur Ajoutée de l'IA
**Problématique** : Fashion-Insta veut booster ses ventes e-commerce en facilitant la découverte de produits à partir d'une photo prise par l'utilisateur.

**Valeur de l'IA** : 
- **Automatisation** : Identification instantanée des caractéristiques vestimentaires (coupe, couleur, style, matière).
- **Pertinence** : Recommandations basées sur la similarité visuelle (Image-to-Image) plutôt que sur une recherche textuelle souvent imprécise.
- **Engagement** : Expérience utilisateur "seamless" et ludique ("Shazam de la mode").

## 2. Approche Technique (Comparatif)

| Caractéristique | Approche A : Embedding & Vector Search | Approche B : Multi-modal LLM |
| :--- | :--- | :--- |
| **Technologie** | CNN (ResNet50) ou ViT (Vision Transformer) | GPT-4o-mini / LLaVA / Claude 3.5 Sonnet |
| **Fonctionnement** | Extraction de vecteurs de caractéristiques et recherche de voisins (FAISS/Milvus). | Description textuelle de l'image puis recherche sémantique dans le catalogue. |
| **Points Forts** | Latence très faible, coût d'inférence réduit, scalabilité. | Meilleure compréhension du "style" et des concepts abstraits (ex: "tenue bohème"). |
| **Points Faibles** | Sensible aux conditions de prise de vue (angle, lumière). | Coût élevé par requête, latence plus importante. |

**Recommandation pour le POC** : Privilégier l'**Approche A** (Embedding) pour sa rapidité et son coût, avec un test exploratoire sur l'**Approche B** pour les cas de styles complexes.

## 3. Données & Sourcing
- **Dataset de Référence** : **DeepFashion** ou **DeepFashion2** (contiennent des images de consommateurs et des images de catalogue pour l'entraînement à la similarité).
- **Catalogue Fashion-Insta** : Simulation d'un catalogue de ~10,000 articles (images + métadonnées).

## 4. Critères de Succès & Métriques
### Techniques (KPIs Data)
- **Top-5 Accuracy** : > 70% (l'article recherché ou un équivalent très proche doit être dans les 5 premiers résultats).
- **Latence d'inférence** : < 500ms (pour garantir la fluidité mobile).

### Métiers (KPIs Business)
- **Taux d'Acceptation** : Validation par un panel d'experts mode de la pertinence des recommandations (> 80%).
- **Facilité d'intégration** : Compatibilité avec l'écosystème Azure.

## 5. Ressources & Déroulé (Estimation)

### Timeline (4 semaines)
- **Semaine 1 : Sourcing & Setup**
    - Collecte et nettoyage du dataset DeepFashion.
    - Mise en place de l'environnement Azure (Storage & Compute).
- **Semaine 2 : Développement du Modèle**
    - Entraînement/Fine-tuning de l'extracteur d'embeddings.
    - Indexation du catalogue Fashion-Insta dans Azure AI Search.
- **Semaine 3 : Évaluation & Ajustements**
    - Tests de recherche de similarité sur photos "In-the-wild".
    - Benchmark comparatif avec LLM Vision (GPT-4o) pour les cas complexes.
- **Semaine 4 : Synthèse & Démonstration**
    - Finalisation des KPIs et rapport de faisabilité.
    - Création d'un prototype d'interface simplifiée pour démonstration COMEX.

### Staffing (Ressources Humaines)
| Profil | Taux de Staffing | Mission Clé |
| :--- | :--- | :--- |
| **Data Scientist** | 100% (20 j.h) | Développement modèle & Evaluation. |
| **Data Engineer** | 50% (10 j.h) | Pipeline de données & Infra Vector Search. |
| **Expert Mode / VP Product** | 20% (4 j.h) | Validation métier & Qualité des recos. |

**Total estimé** : 34 Jours-Hommes sur 1 mois calendaire.
