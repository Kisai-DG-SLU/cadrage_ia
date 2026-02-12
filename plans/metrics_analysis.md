# Analyse des Métriques et Critères de Succès - Fashion-Insta

## 1. Définition de la "Star métrique Hit 5"

### Contexte
La "Star métrique Hit 5" (également appelée "Top-5 Accuracy" dans les documents existants) est la métrique principale pour évaluer la performance du système de recommandation visuelle.

### Définition Formelle
**Hit@5 (Top-5 Accuracy)** : Pourcentage de requêtes où l'article cible (ou un équivalent fonctionnellement similaire) apparaît dans les 5 premières recommandations retournées par le système.

### Méthodologie de Calcul
```
Hit@5 = (Nombre de requêtes avec article cible dans le top-5) / (Nombre total de requêtes) × 100%
```

### Processus d'Évaluation
1. **Dataset de test** : Utilisation d'un sous-ensemble annoté du catalogue Fashion-Insta (~1000 images)
2. **Requêtes simulées** : Pour chaque image de test, le système doit retrouver l'article correspondant dans le catalogue
3. **Critère de succès** : L'article cible doit être dans les 5 résultats retournés par la recherche vectorielle
4. **Équivalence fonctionnelle** : Acceptation d'articles "équivalents" (même catégorie, couleur similaire, style proche) validés par un expert mode

### Valeur Cible
- **Objectif POC** : Hit@5 > 70%
- **Objectif Production** : Hit@5 > 85%

### Justification
- **Top-5** : Correspond à l'interface utilisateur typique qui affiche 5 recommandations maximum
- **70%** : Niveau acceptable pour un POC démontrant la faisabilité technique
- **Validation humaine** : Les 30% restants peuvent être améliorés par des ajustements algorithmiques

## 2. Baseline Observée (à mesurer)

### Approche de Référence (Baseline)
Pour challenger le modèle IA, nous établissons une baseline empirique basée sur des méthodes non-IA :
1. **Recherche textuelle TF-IDF** : Utilisation des tags/métadonnées des produits avec pondération TF-IDF
2. **Similarité couleur par histogramme** : Matching par distance d'histogramme de couleurs (RGB/HSV)
3. **Combinaison hybride** : Score pondéré optimisé des deux méthodes

### Méthodologie de Mesure
La baseline sera mesurée empiriquement sur le dataset Fashion-Insta (~500 images annotées) :
- **Dataset de validation** : Sous-ensemble représentatif du catalogue Fashion-Insta
- **Métrique** : Hit@5 calculé sur les mêmes requêtes que celles utilisées pour l'évaluation IA
- **Protocole** : Double-blind evaluation pour éviter les biais
- **Outils** : Scikit-learn pour TF-IDF, OpenCV pour l'analyse d'histogramme

### Critère de Succès Révisé
Le modèle IA doit démontrer une amélioration significative par rapport à la baseline mesurée :
- **Amélioration minimale** : Hit@5(IA) > Hit@5(baseline) + 15 points de pourcentage
- **Significativité statistique** : Test statistique (p < 0.05) pour valider l'amélioration
- **Objectif absolu** : Atteindre au moins 70% de Hit@5 (valeur cible maintenue)

### Phase d'Évaluation
- **Phase 1 (Semaine 1)** : Établir la baseline mesurée (recherche textuelle + similarité couleur)
- **Phase 2 (Semaine 2-3)** : Évaluer le modèle IA et comparer avec la baseline
- **Phase 3 (Semaine 4)** : Analyser les résultats et documenter l'amélioration

## 3. Critères de Succès Complets du POC

### Critères Techniques
1. **Performance** : Hit@5 > 70% sur dataset de validation
2. **Latence** : Temps de réponse < 500ms (p95)
3. **Scalabilité** : Support de 100 requêtes simultanées
4. **Intégration** : API fonctionnelle avec Azure AI Search

### Critères Métier
1. **Validation experte** : > 80% des recommandations jugées pertinentes par panel d'experts mode
2. **Facilité d'utilisation** : Interface de démonstration intuitive pour le COMEX
3. **Intégration catalogue** : Support d'au moins 10 000 produits dans l'index

### Critères Opérationnels
1. **Documentation** : Rapport technique complet avec méthodologie d'évaluation
2. **Reproductibilité** : Code versionné et pipeline déployable
3. **Coût contrôlé** : Budget POC respecté (< 20k€)

## 4. Plan d'Évaluation

### Phase 1 : Préparation (Semaine 1)
- Constitution du dataset de test annoté (500 images)
- Définition des critères d'équivalence fonctionnelle
- Mise en place de l'environnement d'évaluation

### Phase 2 : Évaluation (Semaine 2-3)
- Tests sur 3 approches :
  1. Baseline (recherche textuelle)
  2. Modèle IA (embedding + vector search)
  3. Validation humaine (panel d'experts)
- Calcul des métriques : Hit@5, Hit@1, Precision@5, Recall@5

### Phase 3 : Analyse (Semaine 4)
- Comparaison statistique des résultats
- Identification des cas d'échec et axes d'amélioration
- Recommandations pour la phase MVP

## 5. Recommandations pour la Mesure

### Outils d'Évaluation
- **Framework** : Scikit-learn pour calcul des métriques
- **Visualisation** : Matplotlib/Seaborn pour analyse des résultats
- **Tracking** : MLflow pour suivi des expériences

### Métriques Complémentaires
1. **Hit@1** : Précision de la première recommandation
2. **Mean Average Precision (MAP@5)** : Qualité globale du ranking
3. **NDCG@5** : Qualité du classement avec pondération
4. **Diversity Score** : Variété des recommandations

### Processus de Validation
- **Double-blind evaluation** : Experts ne connaissant pas l'origine des recommandations
- **Score de pertinence** : Échelle de 1 à 5 pour chaque recommandation
- **Analyse qualitative** : Revue des cas limites et edge cases

