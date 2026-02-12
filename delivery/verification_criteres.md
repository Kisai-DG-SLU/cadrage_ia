# Vérification finale des critères d'auto-évaluation

## Tableau de vérification détaillé

### Compétence 1 : Présenter le projet data et expliquer ses choix

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 1 | Je me suis assuré que chaque diapositive respecte les principes de l'accessibilité. | ✅ Complètement traité | Lignes 449-457 | "Conformité WCAG 2.1 AA pour toutes les diapositives", "Contraste des couleurs vérifié (ratio > 4.5:1)", "Texte alternatif pour toutes les images et diagrammes", "Structure hiérarchique claire (titres H1-H3)", "Compatibilité avec les lecteurs d'écran" |
| 2 | J'ai adapté mon niveau de détail et la terminologie au public visé (COMEX, métiers, techniques). | ✅ Complètement traité | Lignes 82-105, 107-126, 140-147 | Notes pour COMEX avec antisèches techniques et business, adaptation du niveau de détail selon le public |
| 3 | J'ai justifié clairement mes choix techniques et méthodologiques, en lien avec les besoins métiers. | ✅ Complètement traité | Lignes 173-193, 149-169, 130-147 | "Priorité aux Embeddings pour la performance" avec justification métier (latence < 100ms vs > 2000ms), justification du dataset DeepFashion |
| 4 | J'ai explicité les rôles et responsabilités des profils Data dans le cadrage. | ✅ Complètement traité | Lignes 264-282, 222-240 | Tableau "Rôles & Responsabilités (MVP)" avec attribution claire des briques techniques |
| 5 | J'ai démontré ma compréhension des différentes phases projet (PoC, MVP, Run) et de leurs objectifs. | ✅ Complètement traité | Lignes 151-169, 286-316, 320-338 | "Durée : 4 semaines. Objectif Central : Démontrer la faisabilité technique du coeur algo", "Mois 1 : POC (Faisabilité). Mois 2-4 : MVP (Industrialisation). Mois 5 : Scale (Monitoring & Drift)" |

### Compétence 2 : Définir les modalités de réalisation et de suivi du projet data et le planifier

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 6 | J'ai proposé une timeline comportant au moins 3 phases distinctes : PoC, MVP, Run. | ✅ Complètement traité | Lignes 286-291 | "- **Mois 1 : POC** (Faisabilité).\n- **Mois 2-4 : MVP** (Industrialisation).\n- **Mois 5 : Scale** (Monitoring & Drift)." |
| 7 | Pour chaque phase, j'ai identifié au moins 3 tâches clés cohérentes. | ✅ Complètement traité | Lignes 292-304 | **MVP** : 5 tâches (intégration e-commerce, déploiement API, monitoring, formation, A/B testing)<br>**Run/Scale** : 5 tâches (optimisation, extension catégories, retours utilisateurs, scaling, maintenance)<br>**POC** : Sourcing -> Dev -> Eval -> Demo |
| 8 | J'ai respecté une succession logique des étapes. | ✅ Complètement traité | Lignes 222-240, 286-304 | Timeline logique : "Sourcing -> Dev -> Eval -> Demo" pour le POC, puis MVP avec intégration progressive, puis Run avec optimisation |

### Compétence 3 : Identifier de nouvelles opportunités, solutions ou pratiques dans le champ de la data et les diffuser

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 9 | J'ai sélectionné un jeu de données d'images cohérent avec la problématique métier. | ✅ Complètement traité | Lignes 156-157, 168-169 | "Dataset : **DeepFashion**." avec justification "dataset académique de référence, garantissant une base d'entraînement solide" |
| 10 | J'ai proposé une approche technique d'analyse d'image alignée avec l'état de l'art. | ✅ Complètement traité | Lignes 175-182 | "**Approche A (Embeddings)** : **ResNet / ViT**" avec "Technologie : ResNet / ViT" et justification "ultra-rapide (moins de 100ms)" |
| 11 | J'ai comparé avec au moins une autre approche technique et ai expliqué pourquoi elle est plus ou moins pertinente. | ✅ Complètement traité | Lignes 175-193 | Comparaison complète entre "Approche A (Embeddings)" et "Approche B (LLM Vision)" avec explications "Latence : **< 100ms** vs > 2000ms", "Coût : **Faible (CapEx)** vs Élevé (OpEx)" |

### Compétence 4 : Conduire les actions et les échanges entre les parties prenantes du projet data

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 12 | J'ai attribué les briques techniques à des profils Data pertinents. | ✅ Complètement traité | Lignes 264-282 | Tableau avec attribution claire : "Data Pipeline → Data Engineer (Lead) avec MLOps (Soutien)", "Modèle IA → Data Scientist (Lead) avec Tech Lead (Soutien)", "API & Déploiement → MLOps (Lead) avec Data Engineer (Soutien)" |
| 13 | Je me suis assuré que les taux de staffing, tâches et durées des phases étaient cohérents. | ✅ Complètement traité | Lignes 222-240, 236-240 | "Ressources (34 J.H) : 1 Data Scientist (100%), 1 Data Engineer (50%), 1 VP Product (20%)" avec note "Validation de cohérence : TJM sourcés depuis P11_Profils_Data.pdf, plan de staffing aligné sur la complexité technique de chaque phase" |
| 14 | Je me suis assuré que les coûts one-shot et récurrents étaient cohérents. | ✅ Complètement traité | Lignes 342-360 | "CapEx (Développement) : **150 000 €**", "OpEx (Run) : **~2 900 € / mois**" avec détail "Azure Compute/Storage (900€), Maintenance humaine (2000€)" |
| 15 | J'ai estimé les gains financiers liés à l'augmentation des ventes, à partir des données marketing fournies. | ✅ Complètement traité | Lignes 134-136, 380-383 | "Hausse du CA estimée à **+1 800 000 € en 2 ans**" et note "Sources marketing : Estimations basées sur les données Fashion-Insta 2024 : CA total 10,4M€ (5,2M€ physique + 5,2M€ e-commerce), 950 000 visiteurs uniques e-commerce annuels" |
| 16 | J'ai comparé les coûts et les gains cumulés afin d'identifier une date de rentabilité claire. | ✅ Complètement traité | Lignes 364-383 | "Point mort : Atteint à **M+3**", "ROI à 2 ans : **> 300%**" avec graphique ROI Chart |
| 17 | J'ai planifié des instances de gouvernance projet (ex : copil) adaptées à chaque phase. | ✅ Complètement traité | Lignes 320-338 | **POC** : Réunion hebdomadaire technique + daily standup<br>**MVP** : Comité de pilotage bimensuel + revue mensuelle KPIs<br>**Run/Scale** : Revue trimestrielle stratégique + audit semestriel |

### Compétence 5 : Identifier et évaluer les risques de la solution data en matière d'accessibilité, de sécurité et de développement durable

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 18 | J'ai identifié les risques liés à l'utilisation de données personnelles (nom, prénom, email, etc.) hors analyse d'image. | ✅ Complètement traité | Lignes 402-406 | "**Données personnelles structurées** :\n- Risque : Profils utilisateurs (nom, email, historique d'achats)\n- Solution : Pseudonymisation systématique, chiffrement des données au repos\n- Mesures : Audit régulier, conformité RGPD 'by design'" |
| 19 | J'ai repéré les risques spécifiques liés au transfert de données via des APIs publiques (vers LLM providers, etc.). | ✅ Complètement traité | Lignes 398-401 | "**Transfert de données via APIs publiques** :\n- Risque : Exposition d'images utilisateur à des fournisseurs LLM tiers\n- Solution : Architecture 'on-premise' avec modèles locaux, pas d'APIs externes pour le traitement d'images" |
| 20 | J'ai proposé des solutions adaptées : anonymisation des données structurées, choix technique sécurisé pour l'analyse d'image. | ✅ Complètement traité | Lignes 389-406 | "**Anonymisation** : Floutage auto des visages.", "**Crop Intelligent** : Focus vêtement uniquement.", "**Confidentialité** : Isolation Azure France.", "**Garantie DPO** : Zéro image brute stockée.", "**Solution** : Pseudonymisation systématique, chiffrement des données au repos", "**Solution** : Architecture 'on-premise' avec modèles locaux" |

### Compétence 6 : Effectuer un prototype de la solution afin d'en confirmer la faisabilité technique

| # | Critère | État | Référence | Citation/Description |
|---|---------|------|-----------|----------------------|
| 21 | Je me suis concentré sur la fonctionnalité principale du prototype. | ✅ Complètement traité | Lignes 153-158 | "**Objectif Central** : Démontrer la faisabilité technique du coeur algo.\n- **Périmètre** : \n    - Dataset : **DeepFashion**.\n    - Focus exclusif sur la brique de recommandation." |
| 22 | J'ai défini des critères de succès clairs et mesurables, en lien direct avec le besoin métier. | ✅ Complètement traité | Lignes 200-208 | "**Hit@5 (Top-5 Accuracy)** : Hit@5(IA) > Hit@5(baseline) + 15 points avec p < 0.05 (amélioration significative).\n- **Baseline mesurée** : Performance des méthodes non-IA (recherche textuelle TF-IDF + similarité couleur) sur dataset Fashion-Insta.\n- **Objectif minimal** : Atteindre au moins 70% de Hit@5 (valeur cible absolue).\n- **Latence d'inférence** : < 500ms (pour garantir la fluidité mobile).\n- **Acceptation Mode** : > 80% (Validation experts).\n- **Intégration Azure** : Pipeline cloud-ready." |
| 23 | Mon approche est réaliste. | ✅ Complètement traité | Lignes 151-169, 222-240 | "**Durée** : 4 semaines." avec justification "C'est le standard pour valider un 'noyau dur' technique sans s'éparpiller", "Ressources (34 J.H)" avec TJM réalistes |
| 24 | J'ai proposé un System Design structuré, avec au moins 5 briques techniques en plus de la fonctionnalité principale. | ✅ Complètement traité | Ligne 246, 244-260 | Diagramme Mermaid montre au moins 5 briques : Azure App Service, Azure AI Search, Azure Storage, Azure Functions, Azure Key Vault, Azure Monitor, etc. |
| 25 | Mes choix techniques sont cohérents et je peux les justifier. | ✅ Complètement traité | Lignes 173-193, 244-260 | "**Décision** : Priorité aux **Embeddings** pour la performance.\n- **Backup** : LLM Vision pour les cas complexes." avec justification "ultra-rapide (moins de 100ms)" |
| 26 | J'ai formalisé une méthodologie claire pour le PoC, alignée avec les contraintes métiers et techniques. | ✅ Complètement traité | Lignes 151-169 | "**Durée** : 4 semaines.\n- **Objectif Central** : Démontrer la faisabilité technique du coeur algo.\n- **Périmètre** : \n    - Dataset : **DeepFashion**.\n    - Focus exclusif sur la brique de recommandation." |
| 27 | J'ai démontré la faisabilité technique du projet via un System Design argumenté et illustré. | ✅ Complètement traité | Lignes 244-260, ligne 246 | "![Mermaid Architecture](...)" et "**Avantage** : Scalabilité automatique et sécurité Azure." |
