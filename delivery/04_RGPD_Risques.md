# Risques & Gouvernance RGPD - Projet Fashion-Insta

## 1. Analyse de Conformité RGPD
Le projet traite des données hautement sensibles : des photographies d'utilisateurs ("In-the-wild"), pouvant contenir des visages, des lieux privés ou des attributs personnels.

| Principe RGPD | Application au Projet | Risques Identifiés |
| :--- | :--- | :--- |
| **Minimisation** | Seules les caractéristiques vestimentaires doivent être traitées. | Collecte involontaire de visages ou d'arrière-plans sensibles. |
| **Limitation des finalités** | Recommandation d'articles uniquement. | Détournement des photos pour du profilage marketing non consenti. |
| **Sécurité & Confidentialité** | Chiffrement et accès restreint. | Fuite de données ou accès par des tiers (APIs publiques). |
| **Droit des personnes** | Possibilité de supprimer ses photos. | Difficulté technique à purger les données dans les logs d'inférence. |

## 2. Stratégies de Mitigation & Data Privacy

### Technique d'Anonymisation "By Design"
Pour rassurer le DPO, nous implémentons un pipeline de **Pre-processing Privacy** :
1. **Floutage Automatique** : Détection et floutage systématique des visages et des plaques d'immatriculation via un modèle léger (ex: MTCNN) avant l'envoi à l'extracteur d'embeddings.
2. **Crop Intelligent** : Recadrage de l'image sur l'article vestimentaire détecté pour éliminer l'environnement (domicile, rue).
3. **Non-persistance** : Les images brutes ne sont jamais stockées. Seuls les vecteurs numériques (embeddings) non réversibles sont conservés pour l'amélioration du service.

### Garantie vis-à-vis des LLM Tiers
- **Azure OpenAI Service** : Utilisation des instances privées d'Azure. Microsoft garantit contractuellement que les données envoyées aux APIs (GPT-4o) **ne sont pas utilisées** pour entraîner leurs modèles globaux.
- **VPC / Private Link** : Tout le trafic reste au sein du réseau privé virtuel de Fashion-Insta sur Azure.

## 3. Gouvernance & Consentement
- **Opt-in Explicite** : Case à cocher spécifique avant chaque prise de photo expliquant le traitement.
- **Politique de Rétention** : Suppression automatique des métadonnées après 30 jours si l'utilisateur ne les enregistre pas dans ses favoris.
- **Information DPO** : Registre de traitement tenu à jour avec analyse d'impact (AIPD).

## 4. Arguments Clés pour le COMEX
1. **Zéro Image Stockée** : On ne garde que des "chiffres" (vecteurs), pas des photos.
2. **Privacy First** : Le floutage des visages est fait en local ou en entrée de pipeline.
3. **Souveraineté Azure** : Les données restent en Europe (Region France Central) et sous notre contrôle total.
