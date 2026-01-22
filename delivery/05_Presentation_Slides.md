# Plan de Présentation COMEX - Projet Fashion-Insta

## Slide 1 : Titre & Introduction
- **Contenu** : Logo Fashion-Insta, Titre "Cadrage Stratégique : Recommandation Vestimentaire par IA", Nom de l'AI Engineer.
- **Objectif** : Poser le cadre institutionnel.

## Slide 2 : Contexte & Enjeux
- **Contenu** : Mutation du e-commerce mode, besoin de réduire la friction entre l'inspiration (photo) et l'achat (catalogue).
- **KPI Actuel** : Taux de conversion à améliorer.

## Slide 3 : La Mission (Le Concept)
- **Contenu** : "Prenez une photo de vos habits favoris, nous trouvons le style correspondant dans notre catalogue."
- **Technologie** : IA Multi-modale et Visual Search.

## Slide 4 : Valeur Ajoutée de l'IA
- **Contenu** : Gain de temps utilisateur, augmentation du panier moyen, personnalisation de l'expérience d'achat.
- **Chiffre Clé** : +400k€ de CA estimé par an (Marketing).

## Slide 5 : Objectifs du POC (Proof of Concept)
- **Contenu** : Valider la faisabilité technique en 4 semaines.
- **Livrable** : Un prototype démontrant la pertinence des recommandations.

## Slide 6 : Approche Technique POC
- **Contenu** : Extraction d'Embeddings (Vecteurs) vs LLM Vision.
- **Dataset** : Utilisation de DeepFashion (800k images).

## Slide 7 : Critères de Succès du POC
- **Contenu** : Top-5 Accuracy > 70%, Latence < 500ms. Validation métier par experts mode > 80%.

## Slide 8 : Planning & Staffing POC
- **Contenu** : 4 semaines. 1 Data Scientist (100%), 1 Data Engineer (50%). Coût estimé : 20k€.

## Slide 9 : System Design Target (Azure)
- **Contenu** : Schéma End-to-End. Ingestion (Blob) -> Processing (AML) -> Search (Azure AI Search) -> API (App Service).

## Slide 10 : Rôles & Responsabilités
- **Contenu** : Matrice RACI. Collaboration entre Data Engineers, Scientists et MLOps pour l'industrialisation.

## Slide 11 : Timeline de Livraison (Feuille de Route)
- **Contenu** : POC (M1) -> MVP (M4) -> Scale (M5). Déploiement progressif avec feedback continu.

## Slide 12 : Analyse Financière (Budget)
- **Contenu** : CapEx (150k€) pour le dev. OpEx (2.9k€/mois) pour le run (Azure + Maint).

## Slide 13 : Rentabilité & ROI
- **Contenu** : Point mort à 6 mois. ROI à 2 ans > 250%. Courbe de rentabilité positive dès l'année 1.

## Slide 14 : Conformité RGPD & Sécurité
- **Contenu** : Privacy by Design. Floutage auto des visages, Crop intelligent. Isolation des données sur Azure France.

## Slide 15 : Conclusion & Décision
- **Contenu** : Un projet à fort ROI, techniquement maîtrisé et conforme RGPD.
- **Appel à l'action** : "Validation du budget POC pour lancement immédiat."
