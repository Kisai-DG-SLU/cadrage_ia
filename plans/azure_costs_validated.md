# Calculs Détaillés des Coûts Azure - Validés avec Tarifs Officiels

## Sources des Prix
- **Azure Pricing Calculator** (France Centre, février 2026)
- **Site Microsoft Azure** : https://azure.microsoft.com/fr-fr/pricing/
- **Prix vérifiés** pour les services pertinents

## 1. Prix Unitaires Validés (France Centre)

### Azure App Service
| Famille | Plan | Specs (vCPU / RAM) | Prix Horaire | Prix Mensuel (Est.) |
| :--- | :--- | :--- | :--- | :--- |
| **BASIC (Dev/Test)** | **B1** | 1 vCPU / 1.75 Go | 0,015 € | **11,00 €** |
| | **B2** | 2 vCPU / 3.5 Go | 0,029 € | **21,17 €** |
| | **B3** | 4 vCPU / 7 Go | 0,059 € | **43,07 €** |
| **PREMIUM V2 (Old)** | **P1v2** | 1 vCPU / 3.5 Go | 0,107 € | **78,11 €** |
| | **P2v2** | 2 vCPU / 7 Go | 0,214 € | **156,22 €** |
| | **P3v2** | 4 vCPU / 14 Go | 0,428 € | **312,44 €** |
| **PREMIUM V3 (Standard)** | **P0v3** | 1 vCPU / 4 Go | 0,073 € | **53,17 €** |
| | **P1v3** | 2 vCPU / 8 Go | 0,146 € | **106,35 €** |
| | **P2v3** | 4 vCPU / 16 Go | 0,292 € | **212,69 €** |
| | **P3v3** | 8 vCPU / 32 Go | 0,583 € | **425,39 €** |
| **PREMIUM V3 (Mémoire)** | **P1mv3** | 2 vCPU / 16 Go | 0,175 € | **127,75 €** |
| | **P2mv3** | 4 vCPU / 32 Go | 0,350 € | **255,50 €** |
| | **P3mv3** | 8 vCPU / 64 Go | 0,699 € | **510,27 €** |
| | **P4mv3** | 16 vCPU / 128 Go | 1,399 € | **1 021,27 €** |
| | **P5mv3** | 32 vCPU / 256 Go | 2,797 € | **2 041,81 €** |

| Phase | Choix Retenu | Coût Mensuel | Justification CTO | Options Rejetées & Raisons |
| :--- | :--- | :--- | :--- | :--- |
| **1. POC** | **Basic B1** | **11,00 €** | Option la moins chère permettant un environnement stable ("Always On") avec support SSL personnalisé. | **Free/Shared** : Éliminés à cause des "Cold Starts" (latence de démarrage) inacceptables pour une démo.<br>**Premium** : Surdimensionnés pour une phase sans utilisateurs réels. |
| **2. MVP** | **Premium P1v3** | **106,35 €** | Le standard d'entrée pour une API Python. Les **2 vCPU** sont cruciaux pour gérer la concurrence des requêtes. Permet l'Autoscaling et les "Deployment Slots" (Mise à jour sans coupure). | **P0v3 (53€)** : Éliminé car 1 seul vCPU crée un goulot d'étranglement immédiat si un traitement IA bloque le thread.<br>**Série MV3 (Mémoire)** : Éliminée car l'API est limitée par le CPU, pas par la RAM. Payer plus pour 16 Go de RAM est inutile. |
| **3. SCALE** | **Premium P2v3** | **212,69 €** | Doublement de la capacité de calcul (**4 vCPU**) pour encaisser le trafic. | **P3 / P4 / P5** : Stratégie de "Scale Horizontal" privilégiée. Mieux vaut avoir deux instances P2 (Load Balancing / Haute Dispo) qu'une seule instance P3. Au-delà de ce coût (>500€), une migration vers Kubernetes (AKS) serait étudiée. |

| Phase | Option Choisie | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Basic B1** | **11,00 €** | Suffisant pour dev (1 vCPU / 1.75 Go). Les options B2/B3 sont superflues. |
| **MVP** | **Premium P1v3** | **106,35 €** | Standard de Prod (2 vCPU / 8 Go). Meilleur ROI que la V2 (obsolète). Les instances PM ne sont pas requises (pas de besoin RAM fort). |
| **SCALE**| **Premium P2v3** | **212,69 €** | Doublement de capacité (4 vCPU). On privilégie l'ajout d'instances P2 plutôt que de monter sur du P4/P5 hors de prix. |

### Azure AI Search

| Niveau | Specs (Stockage / Index) | Coût Mensuel (730h) |
| :--- | :--- | :--- |
| **Gratuit** | 50 Mo stockage / 3 Index max | **0,00 €** |
| **Basic** | 2 Go stockage / 15 Index max | **61,73 €** |
| **Standard S1** | 25 Go stockage / 50 Index max | **205,36 €** |
| **Standard S2** | 100 Go stockage / 200 Index max | **821,43 €** |
| **Standard S3** | 200 Go stockage / 200 Index max | **1 642,87 €** |
| **Optimisé L1** | 1 To stockage / 10 Index max | **2 346,34 €** |
| **Optimisé L2** | 2 To stockage / 10 Index max | **4 692,07 €** |

| Phase | Option Choisie | Coût Mensuel | Justification CTO | Options Rejetées & Raisons |
| :--- | :--- | :--- | :--- | :--- |
| **1. POC** | **Basic** | **61,73 €** | Le Basic est le premier niveau professionnel stable. Il permet d'indexer jusqu'à 2 Go, ce qui est nécessaire pour stocker les vecteurs IA. | **Gratuit** : Rejeté car limité à **50 Mo** et **3 index**. C'est insuffisant pour un corpus documentaire avec Embeddings.<br>**Standard S1** : Trop cher (205€) pour un simple test fonctionnel. |
| **2. MVP** | **Basic** | **61,73 €** | Suffisant pour démarrer la production tant que le volume de données reste modéré (< 2 Go). Meilleur ROI pour le lancement. | **Standard S1 (205€)** : Le saut de prix (x3) n'est pas justifié au lancement sans un volume de données ou un trafic justifiant des ressources dédiées supérieures. |
| **3. SCALE** | **Standard S1** | **205,36 €** | Nécessaire pour la performance quand le trafic augmente (meilleur CPU dédié aux calculs) et pour dépasser les 2 Go de stockage (passe à 25 Go). | **Standard S2 (821€)** : Éliminé. Le coût est quadruplé par rapport au S1. Il est préférable d'ajouter des réplicas S1 pour gérer la charge (Scaling Horizontal) plutôt que de passer au S2, sauf besoin impératif de 100 Go de stockage. |

### Azure Machine Learning

| Catégorie | Description Technique | Cas d'usage pour ton Projet IA |
| :--- | :--- | :--- |
| **General Purpose** (Usage Général) | **Ratio Équilibré** (1 vCPU pour 4 Go RAM). Processeurs standards. | **Développement & Orchestration.** Idéal pour les Notebooks Jupyter, l'exploration de données et les environnements de test. C'est le "couteau suisse". |
| **Compute Optimized** (Optimisé Calcul) | **Ratio CPU Élevé** (1 vCPU pour 2 Go RAM). Processeurs haute fréquence. | **Inférence CPU (Production).** Quand le modèle est entraîné et doit juste répondre vite aux requêtes API. Moins cher que le GPU pour des modèles classiques. |
| **Memory Optimized** (Optimisé Mémoire) | **Ratio RAM Élevé** (1 vCPU pour 8+ Go RAM). | **Traitement de Données (Big Data).** Nécessaire si tu manipules d'énormes Dataframes (Pandas/Spark) en mémoire avant l'entraînement. Rarement utile pour l'inférence simple. |
| **GPU** (Processeur Graphique) | **Accélération Matérielle.** Présence de cartes NVIDIA (Tesla, A100, etc.). | **Deep Learning & LLM.** Obligatoire pour l'*entraînement* de réseaux de neurones ou l'*inférence* de gros modèles (GenAI / LLM) qui rameraient sur un CPU. |
| **Storage Optimized** | **I/O Disque Élevé.** Gros débit de lecture/écriture. | **Base de Données / NoSQL.** Peu pertinent pour le nœud de calcul (Compute) ML, plutôt réservé aux clusters de stockage. |

| Série (Sigle) | Signification & Hardware | Rôle dans ton Architecture |
| :--- | :--- | :--- |
| **Série D** (Ex: Dsv3, Ddv4) | **"D" comme "Daily"**. C'est la gamme General Purpose standard. Le "s" signifie support du SSD Premium. Le "v3/v4" est la génération. | **Machine de Dev (POC).** C'est ce qu'on prend par défaut pour travailler. Une `Standard_D4s_v3` est parfaite pour coder. |
| **Série F** (Ex: Fsv2) | **"F" comme "Fast"**. Processeurs Turbo. Offre la puissance de calcul brute la moins chère du catalogue. | **Machine de Prod (MVP CPU).** Le meilleur choix pour servir ton modèle en production si tu n'as pas besoin de GPU. Une `Standard_F4s_v2` est très réactive. |
| **Série E** (Ex: Esv3) | **"E" comme "Extra Memory"**. Beaucoup de RAM pour peu de CPU. | **Réservé aux cas spécifiques.** Uniquement si ton script de pré-traitement plante avec une erreur "Out of Memory". |
| **Série NC** (Ex: NC_T4_v3) | **"N" comme "Nvidia"**. La lettre qui suit (C, D) indique le type de carte. **NC = Compute (Calcul)**. T4 = Carte Tesla T4. | **Inférence IA Lourde.** La `Standard_NC4as_T4_v3` est la moins chère des machines GPU. C'est la porte d'entrée pour faire tourner du Deep Learning pro. |
| **Série ND** (Ex: ND_A100) | **"D" comme "Deep Learning"**. Cartes très haut de gamme (A100). | **Entraînement Massif.** Hors budget pour un POC/MVP (>2000€/mois). À oublier pour l'instant. |

| Famille | Instance | Specs (vCPU / RAM) | Prix Horaire | Coût Mensuel (730h) |
| :--- | :--- | :--- | :--- | :--- |
| **GENERAL (Dev)** | **D2s v3** | 2 vCPUs / 8 Go | 0,094 € | **68,62 €** |
| | **D4s v3** | 4 vCPUs / 16 Go | 0,188 € | **137,24 €** |
| **COMPUTE (Prod)** | **F2s v2** | 2 vCPUs / 4 Go | 0,085 € | **62,05 €** |
| | **F4s v2** | 4 vCPUs / 8 Go | 0,169 € | **123,37 €** |
| | **F8s v2** | 8 vCPUs / 16 Go | 0,338 € | **246,74 €** |
| **GPU (IA Lourde)** | **NC4as T4 v3**| 4 vCPUs / 28 Go / 1 GPU | 0,515 € | **375,95 €** |
| | **NC8as T4 v3**| 8 vCPUs / 56 Go / 1 GPU | 0,735 € | **536,55 €** |

| Rôle dans l'Architecture | Instance Choisie | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC (Poste de Dév)** | **Standard_D4s_v3** | **137,24 €** | **Pourquoi D4s (16 Go) ?** La D2s (8 Go) est trop juste pour un environnement de développement moderne (VS Code Remote + Jupyter + Chargement des datasets en mémoire). 16 Go est le standard de confort pour ne pas perdre de temps. |
| **MVP (Serveur API)** | **Standard_F4s_v2** | **123,37 €** | **Pourquoi F4s (4 vCPU) ?** C'est le meilleur rapport performance/prix pour l'inférence. Les processeurs "F" sont plus rapides que les "D", ce qui réduit le temps de réponse de l'IA. 4 vCPUs permettent de gérer plusieurs utilisateurs en parallèle. |
| **Option GPU** | **Standard_NC4as_T4_v3**| **375,95 €** | **Le choix tactique.** C'est l'instance GPU la moins chère du marché Azure (avec une vraie carte Tesla T4). À réserver uniquement si le modèle est trop lent sur le CPU (F4s). |

### Azure Blob Storage
| Niveau d'accès (Tier) | Description | Prix Unitaire (Stockage) | Prix pour 10 Go (Test) |
| :--- | :--- | :--- | :--- |
| **HOT (Chaud)** | Données actives, accès fréquent (Latence ms). Pas de frais de lecture, stockage un peu plus cher. | **0,016 € / Go / mois** | **0,16 €** |
| **COOL (Froid)** | Données gardées min. 30 jours (Backups mensuels). Stockage moins cher, mais l'accès est facturé. | **0,009 € / Go / mois** | **0,09 €** |
| **ARCHIVE** | Données gardées min. 180 jours (Logs légaux). Stockage quasi-gratuit, mais récupération lente (heures) et payante. | **0,002 € / Go / mois** | **0,02 €** |

| Phase | Configuration Choisie | Coût Mensuel (Est. 10Go) | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Standard LRS - Tier HOT** | **~0,16 €** | On ne s'embête pas avec la gestion du cycle de vie. Tout est en "Hot" pour garantir la rapidité d'accès aux PDF pendant le développement. |
| **MVP** | **Standard LRS - Tier HOT** | **~1,00 €** *(avec marge)* | Le volume reste faible. Le Tier "Hot" est le plus sûr pour éviter les frais cachés de transaction/lecture sur les fichiers souvent consultés par les premiers utilisateurs. |
| **SCALE**| **Mixte (Hot + Lifecycle)** | **Variable** | Mise en place d'une politique automatique : les fichiers de plus de 30 jours passent automatiquement en **Cool** (0,009€) et les logs de plus de 6 mois en **Archive** (0,002€) pour optimiser la facture sur le long terme. |

### Azure Cache for Redis

| Famille | Instance | Specs (RAM / vCPU) | Prix Horaire | Coût Mensuel (730h) |
| :--- | :--- | :--- | :--- | :--- |
| **BASIC / BALANCED** | **Managed B0** | 0.5 Go / 2 vCPU | 0,015 € | **10,95 €** |
| *(Dev / Test)* | **Managed B1** | 1.0 Go / 2 vCPU | 0,031 € | **22,63 €** |
| | | | | |
| **STANDARD** | **Standard C1** | 1.0 Go / Répliqué | 0,068 € | **49,64 €** |
| *(Production)* | **Standard C2** | 2.5 Go / Répliqué | 0,136 € | **99,28 €** |
| | **Standard C3** | 6.0 Go / Répliqué | 0,272 € | **198,56 €** |

| Phase | Option Choisie | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Balanced B0** | **10,95 €** | **Pourquoi B0 ?** Pour le développement, on n'a pas besoin de SLA ni de réplication. 500 Mo (0.5 Go) suffisent largement pour stocker des sessions utilisateurs et quelques résultats de requêtes API. C'est 4x moins cher que le C1. |
| **MVP** | **Standard C1** | **49,64 €** | **Pourquoi C1 ?** En production, on doit garantir que le cache est toujours là. Le Tier Standard inclut la réplication des données. Si le serveur principal tombe, le secondaire prend le relais sans déconnecter les utilisateurs. |
| **SCALE**| **Standard C2** | **99,28 €** | **Pourquoi C2 ?** Uniquement si le monitoring montre qu'on utilise plus de 1 Go de RAM de cache (ce qui est beaucoup pour du texte). Sinon, on reste en C1. |

### Azure SQL Database

| Modèle | Tier / Performance | Specs & Stockage | Prix Horaire | Coût Mensuel (730h) |
| :--- | :--- | :--- | :--- | :--- |
| **BASIC** | **Basic** | 5 DTU / 2 Go | 0,007 € | **5,12 €** |
| **STANDARD** | **Standard S0** | 10 DTU / 250 Go | 0,0211 € | **15,41 €** |
| (Prod) | **Standard S1** | 20 DTU / 250 Go | 0,0422 € | **30,81 €** |
| | **Standard S2** | 50 DTU / 250 Go | 0,1055 € | **77,02 €** |
| | **Standard S3** | 100 DTU / 250 Go | 0,2110 € | **154,03 €** |
| **PREMIUM** | **Premium P1** | 125 DTU / 500 Go | 0,6541 € | **477,49 €** |
| (Haute Perf) | **Premium P2** | 250 DTU / 500 Go | 1,3082 € | **954,99 €** |
| **vCORE** | **Gen5 (2 vCore)** | 2 vCore / Flexible | *Variable* | **~365,00 €** *(Ton estimation)* |

| Phase | Option Choisie | Coût Mensuel | Justification CTO | Options Rejetées & Raisons |
| :--- | :--- | :--- | :--- | :--- |
| **POC** | **Basic (5 DTU)** | **5,12 €** | Imbattable. Pour 5€/mois, on a une vraie base SQL relationnelle gérée, suffisante pour les tests fonctionnels et quelques utilisateurs. | **Standard S0 (15€)** : Pourquoi payer le triple pour un POC ? Le Basic fait le job.<br>**vCore (365€)** : Totalement hors sujet pour un POC. |
| **MVP** | **Standard S1** | **30,81 €** | Le standard de production. 20 DTU permettent de gérer la concurrence (plusieurs utilisateurs en même temps) sans ralentissement notable. | **Standard S0 (15€)** : Un peu juste en performance (IOPS) pour une mise en prod publique.<br>**Standard S3 (154€)** : On garde cette option sous le coude si le S1 sature (Upgrade en 1 clic). |
| **SCALE**| **Standard S3** | **154,03 €** | Quand le trafic augmente, on passe à 100 DTU. C'est le palier avant de basculer sur l'architecture vCore plus complexe. | **Premium P1 (477€)** : Trop cher. Si on a besoin de cette puissance, on basculera plutôt sur du vCore (365€) qui est plus flexible. |

### Azure Data Factory

| Famille | Type d'activité | Tarif Unitaire (France Central) | Coût Mensuel Est. |
| :--- | :--- | :--- | :--- |
| **PIPELINE (V2)** | **Orchestration** | ~ 0,84 € / 1000 exécutions | **< 1,00 €** (Négligeable) |
| *Serverless* | **Pipeline Activity** | 0,004 € / heure | **Variable** (Centimes) |
| | **Data Mouvement** | 0,210 € / heure | **Variable** (Selon volume) |
| | | | |
| **SSIS (Legacy)** | **Standard (4 Cores)** | 0,703 € / heure | **513,22 €** |
| *Serveur dédié* | **Enterprise (4 Cores)** | *Plus cher* | **> 1000 €** |

| Phase | Configuration Choisie | Coût Mensuel Est. | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Data Factory V2 (Pipeline)** | **~ 2,00 €** | On paie uniquement quand le pipeline tourne. Pour lancer quelques scripts Python et copier 10 fichiers par jour, le coût est dérisoire. |
| **MVP** | **Data Factory V2 (Pipeline)** | **~ 5,00 €** | Même en tournant toutes les heures, l'orchestration reste très bon marché. On utilise l'option "Azure IR" (le moins cher) et surtout pas "Managed VNET IR" (plus cher) pour l'instant. |
| **SCALE**| **Data Factory + Data Flow** | **Variable** | Si on doit manipuler des To de données, on activera les "Data Flows" (Clusters Spark à la demande). Mais pour démarrer, inutile de provisionner ça. |

### Azure Monitor

| Service | Unité de Facturation | Prix Unitaire (France Central) | Source |
| :--- | :--- | :--- | :--- |
| **Application Insights** | Ingestion de données | **2,31 € / Go** | |
| **Log Analytics** | Ingestion de journaux | **~1,92 € / Go** (Moyenne calculée sur 57,77€ pour 30Go) | |
| **Rétention Données** | Stockage | **Gratuit** (31 premiers jours) puis 0,10€/Go | |
| **Alertes (Log)** | Par signal surveillé | **1,26 € / signal** | |
| **Alertes (Metric)** | Par série chronologique | **0,13 € / série** | |
| **Notifications** | E-mails / Webhooks | **Gratuit** (Quota généreux inclus) | |

| Phase | Configuration Estimée | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Pay-as-you-go** | **~ 2,00 €** | On active Application Insights par défaut. Le volume de logs sera minime (< 1 Go/mois) pendant le développement. |
| **MVP** | **Standard (5 Go/mois)** | **~ 12,00 €** | **Ajustement réaliste.** Votre simulation à 57€ (30 Go) est très large. Pour un lancement MVP, 5 Go de logs suffisent amplement à tracer les erreurs et la performance sans gaspiller de budget. |
| **SCALE**| **Standard (30 Go/mois)** | **57,77 €** | **Configuration de votre capture.** Quand le trafic sera dense, on atteindra ce volume de 1 Go/jour. C'est le budget à prévoir pour la vitesse de croisière. |

### Azure Key Vault

| Type de ressource | Prix Unitaire | Coût pour un usage classique |
| :--- | :--- | :--- |
| **Opérations Standard** | **0,025 € / 10 000 transactions** | **< 0,01 €** (Négligeable) |
| *(Lecture de secrets)* | | |
| **Clés HSM (Premium)** | **0,84 € / clé / mois** | **0,84 €** (Si besoin de haute sécurité) |
| **Clés Avancées HSM** | **4,19 € / clé / mois** | **4,19 €** (Votre sélection actuelle) |
| **Certificats SSL** | **2,51 € / renouvellement** | **2,51 €** (Une fois par an) |

| Phase | Configuration Choisie | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Standard** | **~ 0,05 €** | On paie juste les transactions. Le stockage des secrets (mots de passe SQL, clés API OpenAI) est gratuit en Standard. |
| **MVP** | **Standard** | **~ 0,10 €** | Même avec 100 utilisateurs, le nombre de lectures de secrets reste faible (le backend les met en cache). Inutile de passer en Premium sauf exigence bancaire. |
| **SCALE**| **Premium (Optionnel)** | **~ 5,00 €** | Si on doit gérer des clés de chiffrement client (BYOK) avec sécurité matérielle (HSM), on ajoutera cette ligne à 4,19€. |

### Azure API Management

| Tier (Niveau) | Description | Prix Estimé (Vous) | VRAI Coût Mensuel (730h) |
| :--- | :--- | :--- | :--- |
| **Consommation** | Serverless. Payé à l'appel. 1M appels gratuits. Pas de portail développeur, démarrage à froid. | N/A | **0,00 €** |
| **Développeur** | Instance dédiée (non-SLA). Inclus le Portail Développeur et VNet. Idéal pour dev stable. | 0 € | **40,22 €** |
| **Basic** | Production entrée de gamme. Pas de VNet. | 130 € | **123,22 €** |
| **Standard (v2)** | Production robuste. (L'offre "v2" à 586€ est moins chère que la v1 à 731€). | 400 € | **586,07 €** |
| **Premium (v2)** | Haute dispo, Multi-région, VNet complet. | 1 600 € | **2 344,28 €** |

| Phase | Option Choisie | Coût Mensuel | Justification CTO |
| :--- | :--- | :--- | :--- |
| **POC** | **Consommation** | **~ 0,00 €** | **Pourquoi pas Développeur ?** Pour le POC, on veut valider les features. Le tier "Consommation" est gratuit et suffit pour exposer quelques endpoints. Si on a besoin du "Portail Développeur" pour tester la doc API, on passera au tier Développeur (40€), mais commençons gratuit. |
| **MVP** | **Basic** | **123,22 €** | **L'option équilibrée.** Offre une IP statique et des performances garanties (contrairement au Consommation). Suffisant pour gérer le trafic initial de *Sophia-Brain*. |
| **SCALE**| **Standard (v2)** | **586,07 €** | **Attention au saut de budget.** Quand le Basic sature, on passe au Standard v2 (moins cher que le v1). Le Premium (2300€) est totalement exclu sauf si on a une exigence bancaire de réseau privé (VNet) strict. |

## 2. Coûts Révisés par Phase (Consolidé)

### Phase POC (4 semaines)
**Configuration** : Environnement de développement stable ("Always On"), machine de dev puissante, stockage vectoriel de base.

| Service | Configuration Retenue | Coût Mensuel |
|---------|-----------------------|--------------|
| **Azure App Service** | Basic B1 (SSL inclus) | **11,00 €** |
| **Azure AI Search** | Basic (2 Go - Min. pour Vecteurs) | **61,73 €** |
| **Azure ML Compute** | Standard_D4s_v3 (Dev Station 16Go) | **137,24 €** |
| **Azure Blob Storage** | Hot Tier (10 Go) | **0,16 €** |
| **Azure Cache for Redis** | Basic B0 (0.5 Go) | **10,95 €** |
| **Azure SQL Database** | Basic (5 DTU) | **5,12 €** |
| **Azure Data Factory** | Pipeline Serverless (Est.) | **2,00 €** |
| **Azure Monitor** | App Insights (< 1 Go) | **2,00 €** |
| **Azure Key Vault** | Standard (Transactions) | **0,05 €** |
| **Azure API Management** | Consumption (Gratuit) | **0,00 €** |
| **TOTAL POC** | | **230,25 €** |

### Phase MVP (12 semaines)
**Configuration** : Production résiliente. Passage au Compute optimisé pour l'IA, sécurisation par API Management et redondance Redis/SQL.

| Service | Configuration Retenue | Coût Mensuel |
|---------|-----------------------|--------------|
| **Azure App Service** | Premium P1v3 (2 vCPU - Autoscaling) | **106,35 €** |
| **Azure AI Search** | Basic (2 Go - Suffisant lancement) | **61,73 €** |
| **Azure ML Compute** | Standard_F4s_v2 (Inférence Rapide) | **123,37 €** |
| **Azure Blob Storage** | Hot Tier (50 Go) | **1,00 €** |
| **Azure Cache for Redis** | Standard C1 (Répliqué - SLA) | **49,64 €** |
| **Azure SQL Database** | Standard S1 (20 DTU) | **30,81 €** |
| **Azure Data Factory** | Pipeline Serverless (Est.) | **5,00 €** |
| **Azure Monitor** | App Insights (Est. 5 Go logs) | **12,00 €** |
| **Azure Key Vault** | Standard | **0,10 €** |
| **Azure API Management** | Basic (IP Fixe + SLA) | **123,22 €** |
| **TOTAL MVP** | | **513,22 €** |

### Phase Scale (Trafic élevé)
**Configuration** : Doublement de la puissance de calcul, mise à l'échelle de la base de données et de l'indexeur IA, gestion avancée des API.

| Service | Configuration Retenue | Coût Mensuel |
|---------|-----------------------|--------------|
| **Azure App Service** | Premium P2v3 (4 vCPU) | **212,69 €** |
| **Azure AI Search** | Standard S1 (Perf + 25 Go) | **205,36 €** |
| **Azure ML Compute** | Standard_F8s_v2 (8 vCPU - Haute charge) | **246,74 €** |
| **Azure Blob Storage** | Mixte Hot/Cool (1 To) | **5,00 €** |
| **Azure Cache for Redis** | Standard C2 (2.5 Go) | **99,28 €** |
| **Azure SQL Database** | Standard S3 (100 DTU) | **154,03 €** |
| **Azure Data Factory** | Pipeline + Flux (Est.) | **20,00 €** |
| **Azure Monitor** | App Insights (Est. 30 Go logs) | **57,77 €** |
| **Azure Key Vault** | Premium (Optionnel - HSM) | **5,00 €** |
| **Azure API Management** | Standard v2 (Haute Perf) | **586,07 €** |
| **TOTAL SCALE** | | **1 591,94 €** |

## 3. Comparaison : Estimations Initiales vs Réalité (Calculateur)

| Phase | Estimation Initiale (Vieux Doc) | Coût Réel Validé (Nouveau) | Différence | Analyse |
|-------|-------------------|-------------------|------------|---------|
| **POC** | 224 € | **230 €** | + 2,6% | **Conforme.** L'ajout de Redis et SQL Basic est compensé par la précision des autres coûts. |
| **MVP** | 1 278 € | **513 €** | **- 60%** | **Optimisation Majeure.** Économies massives réalisées sur SQL (DTU vs vCore), Data Factory (Serverless vs SSIS) et ML (F-Series vs Cluster). |
| **Scale** | 3 668 € | **1 592 €** | **- 56%** | **Rationalisation.** L'architecture App Service P2v3 + SQL S3 suffit amplement. Pas besoin de Kubernetes ni de Premium SQL P2 hors de prix pour l'instant. |

## 4. Recommandations Finales pour le Budget

1.  **Réservation (Reserved Instances)** : Tous les prix ci-dessus sont en "Pay-as-you-go".
    * Dès que le MVP est stable (après 3 mois), passer en **Réservé 1 an** sur App Service, Redis et SQL fera baisser la facture MVP de **~30%** (soit un coût cible vers **360€/mois**).
2.  **La Sécurité SSIS** : L'audit a permis d'éliminer la ligne "SSIS" à 513€ qui était une erreur d'architecture. Data Factory en mode Pipeline ne coûte que quelques euros.
3.  **Souveraineté** : Tous ces coûts incluent le surcoût de la région **France Central** (obligatoire pour le projet).

## 5. Budget Total Révisé sur 2 Ans (Consolidé)

Grâce à l'optimisation des choix techniques, le budget infrastructure est divisé par deux par rapport aux premières estimations.

### Année 1 (Lancement)
* **POC (1 mois)** : 230,25 €
* **MVP (11 mois)** : 11 × 513,22 € = 5 645,42 €
* **Total Année 1 : ~ 5 876 €**

### Année 2 (Croissance)
* **Scale (12 mois)** : 12 × 1 591,94 € = 19 103,28 €
* **Total Année 2 : ~ 19 103 €**