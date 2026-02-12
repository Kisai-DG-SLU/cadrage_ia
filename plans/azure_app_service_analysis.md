# Analyse Azure App Service : Consumption vs Premium vs Container

## Contexte
Pour le projet Fashion-Insta, nous devons héberger l'API de recommandation (FastAPI Python). Trois options principales sont envisageables sur Azure :
1. **Azure App Service - Consumption Plan** (Serverless)
2. **Azure App Service - Premium Plan** (Dédié)
3. **Azure Container Instances / AKS** (Conteneurs)

## Comparaison Détaillée

### 1. Azure App Service - Consumption Plan (Serverless)
**Caractéristiques** :
- Facturation à l'usage (par exécution)
- Scale automatique à zéro (cold start)
- Pas de gestion d'infrastructure
- Limites : 1.5 Go mémoire max, timeout max 10 minutes

**Avantages** :
- Coût optimal pour charges variables (POC, MVP)
- Pas de coût fixe lorsque l'API n'est pas utilisée
- Déploiement rapide via ZIP deploy ou GitHub Actions

**Inconvénients** :
- Latence de cold start (2-5 secondes) peut impacter l'expérience utilisateur
- Limitations mémoire pour traitement d'images lourdes
- Pas de garantie de performance élevée

**Coût estimé** :
- 1 million d'exécutions/mois : ~20€
- Stockage : 0.10€/Go/mois
- **Total estimé POC** : ~30-50€/mois

### 2. Azure App Service - Premium Plan (v3)
**Caractéristiques** :
- Instances dédiées (1 à 30 instances)
- Pas de cold start (instances toujours chaudes)
- Autoscaling basé sur métriques (CPU, mémoire, requêtes)
- Support des VNET, SSL personnalisé, déploiement slots

**Avantages** :
- Performance garantie (SLA 99.95%)
- Meilleure latence (<100ms)
- Mémoire jusqu'à 14 Go par instance
- Isolation réseau possible

**Inconvénients** :
- Coût fixe élevé (à partir de ~150€/mois pour P1v3)
- Surprovisionnement possible pour charges faibles

**Coût estimé** :
- P1v3 (1 vCPU, 3.5 Go RAM) : ~150€/mois
- P2v3 (2 vCPU, 7 Go RAM) : ~300€/mois
- P3v3 (4 vCPU, 14 Go RAM) : ~600€/mois
- **Total estimé MVP** : ~150-300€/mois

### 3. Azure Container Instances (ACI) / Azure Kubernetes Service (AKS)
**Caractéristiques** :
- Conteneurs Docker déployés
- ACI : serverless containers
- AKS : orchestration Kubernetes complète

**Avantages** :
- Flexibilité totale (choix d'image, ressources)
- Portabilité (multi-cloud)
- Scaling granulaire
- Intégration avec Azure DevOps

**Inconvénients** :
- Complexité opérationnelle plus élevée
- Coûts variables selon l'utilisation
- Nécessite expertise Kubernetes (pour AKS)

**Coût estimé** :
- ACI : ~0.000025€/vCPU-seconde + ~0.0000025€/Go-seconde
- Pour 1000 requêtes/jour (30s chacune) : ~15€/mois
- AKS : ~50€/mois pour cluster managé + coût des nœuds

## Recommandation pour Fashion-Insta

### Phase POC (4 semaines)
**Choix recommandé** : **Azure App Service - Consumption Plan**
- Justification :
  - Charge faible et irrégulière pendant le POC
  - Économique (coût quasi nul si peu d'utilisation)
  - Focus sur la validation fonctionnelle plutôt que performance
  - Déploiement simplifié pour l'équipe Data Science

### Phase MVP (12 semaines)
**Choix recommandé** : **Azure App Service - Premium Plan P1v3**
- Justification :
  - Charge prévisible avec pics modérés (100-1000 req/jour)
  - Latence constante nécessaire pour UX fluide
  - SLA professionnel requis pour production
  - Capacité d'autoscaling pour pics saisonniers (soldes, promotions)
  - Coût raisonnable pour une startup

### Phase Scale (après MVP)
**Choix recommandé** : **Azure Kubernetes Service (AKS)**
- Justification :
  - Trafic élevé (>100 req/s)
  - Besoin d'orchestration multi-microservices
  - Intégration avec Azure Machine Learning et autres services
  - Flexibilité pour déployer d'autres composants (batch processing, monitoring)

## Plan de Migration
1. **POC** : Déploiement sur Consumption Plan avec monitoring Application Insights
2. **MVP** : Migration vers Premium Plan P1v3 avec blue-green deployment
3. **Scale** : Refactoring vers AKS avec Helm charts et CI/CD GitOps

## Points d'Attention
- **Cold Start** : Pour Consumption Plan, prévoir une fonction warm-up si nécessaire
- **Sécurité** : Premium Plan permet l'intégration VNET pour isolation
- **Monitoring** : Application Insights disponible sur les trois options
- **Coûts cachés** : Bandwidth, Log Analytics, Backup (à inclure dans le budget)

## Conclusion
Pour Fashion-Insta, nous recommandons une approche progressive :
- **Court terme (POC)** : Consumption Plan pour validation rapide et économique
- **Moyen terme (MVP)** : Premium Plan P1v3 pour performance garantie
- **Long terme (Scale)** : AKS pour scalabilité et flexibilité maximale

Cette approche minimise les risques techniques et financiers tout en permettant une évolution graduelle.