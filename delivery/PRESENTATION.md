---
marp: true
theme: gaia
paginate: true
backgroundImage: url('images/background.png')
color: #333
style: |
  section {
    justify-content: center;
    padding: 70px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 28px;
  }
  section::before {
    content: ' ';
    position: absolute;
    top: 20px;
    left: 20px;
    width: 80px;
    height: 80px;
    background-image: url('images/logo_projet.png');
    background-size: contain;
    background-repeat: no-repeat;
  }
  footer {
    position: absolute;
    bottom: 20px;
    right: 20px;
    font-size: 0.8em;
    color: #7f8c8d;
  }
  section:not(.lead) h1 {
    margin-top: 1.0em; 
    color: #2c3e50;
    border-bottom: 2px solid #e74c3c;
  }
  section.lead h1 {
    font-size: 2.2em;
    color: #2c3e50;
    margin-bottom: 0.2em;
  }
  section.lead h2 {
    font-size: 1.4em;
    color: #7f8c8d;
    margin-top: 0;
  }
  .catchphrase {
    color: #e74c3c;
    font-size: 1.3em;
    font-weight: bold;
    margin-top: 10px;
    display: inline-block;
    transform: rotate(-2deg);
    text-shadow: 1px 1px 1px rgba(0,0,0,0.1);
  }
  code {
    background-color: #f4f4f4;
    color: #e74c3c;
    padding: 2px 4px;
    border-radius: 4px;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
  }
  th {
    background-color: #2c3e50;
    color: white;
    padding: 10px;
  }
  td {
    padding: 10px;
    border-bottom: 1px solid #ddd;
  }
  .highlight {
    color: #e67e22;
    font-weight: bold;
  }
---

<!-- _class: lead -->

# **Fashion-Insta : Cadrage Stratégique**
## Projet 9 : Recommandation Vestimentaire par IA

<span class="catchphrase">"Du style à l'achat : l'IA comme moteur de conversion"</span>

**Damien Guesdon** | Janvier 2026

<!-- 
NOTES :
[INTRODUCTION]
Bonjour à tous, membres du COMEX. Je suis Damien Guesdon, AI Engineer.
Aujourd'hui, je vous présente le cadrage de Fashion-Insta, un projet qui va transformer la manière dont nos clients interagissent avec notre catalogue.

[OBJECTIF]
Mon but est simple : vous démontrer que nous avons une solution techniquement réalisable, financièrement très rentable et juridiquement sécurisée. À la fin de cette présentation, je vous demanderai votre feu vert pour lancer le Proof of Concept (POC).

[TIMING] 15 min de présentation, 10 min de Q&A.

--- 💾 ANTISÈCHE (LEAD) ---
- Pourquoi moi ? En tant qu'AI Engineer, j'ai piloté l'analyse technique et financière pour garantir le réalisme des chiffres.
- État du projet : Phase de conception terminée, prêt pour le prototype.
-->

---

# Contexte & Enjeux Stratégiques

- **Mutation du Marché** : Les utilisateurs cherchent une expérience d'achat visuelle et instantanée.
- **Problématique** : Friction importante entre l'inspiration et l'achat.
- **Objectif** : Transformer une photo en opportunité de vente.

<span class="highlight">Vision</span> : Devenir le "Shazam de la mode".

<!-- 
NOTES :
[SCRIPT]
Le constat de départ est un manque à gagner identifié par nos équipes marketing : nos clients voient des vêtements qui leur plaisent dans la rue ou sur les réseaux, mais ne savent pas comment les trouver dans NOTRE catalogue. 
Cette "friction" est une perte sèche de chiffre d'affaires. Notre vision est de devenir le "Shazam de la mode" : vous voyez un style, vous le prenez en photo, et Fashion-Insta vous propose l'équivalent dans nos rayons en moins d'une seconde.

--- 💡 ANTISÈCHE BUSINESS ---
- Perte de conversion : Estimez que 30% des recherches textuelles échouent par manque de précision. L'image règle ce problème.
- Concurrence : ASOS et Google Lens utilisent déjà ces technologies. Nous devons rattraper ce retard stratégique.
-->

---

# Valeur Ajoutée de l'IA

- **Automatisation** : Identification instantanée des caractéristiques.
- **Pertinence** : Recherche par similarité visuelle (Image-to-Image).
- **Impact Financier** :
    - Augmentation du panier moyen.
    - Hausse du CA estimée à **+468k€/an** = **936k€ sur 2 ans**.

<!--
NOTES :
[SCRIPT]
L'IA n'est pas un simple gadget ici, c'est le coeur du réacteur. Contrairement à une recherche par mot-clé qui est limitée par le vocabulaire de l'utilisateur, notre IA de Computer Vision analyse la texture, la coupe et la couleur de l'image brute.
L'impact financier n'est pas négligeable : le marketing estime que cette fonctionnalité générera **468 000 € de CA additionnel par an** grâce à la fluidification du parcours d'achat.

--- 💡 ANTISÈCHE TECHNIQUE ---
- Computer Vision : Utilisation de réseaux de neurones profonds pour "comprendre" l'image.
- Gain de temps : Passer de 2 minutes de recherche manuelle à moins de 500ms.
- Impact financier : Basé sur données réelles Fashion-Insta 2024 (+14% CA e-commerce, +4% CA physique).
-->

---

# Objectifs & Stratégie du POC

- **Durée** : 4 semaines.
- **Objectif Central** : Démontrer la faisabilité technique du coeur algo.
- **Périmètre** : 
    - Dataset : **DeepFashion**.
    - Focus exclusif sur la brique de recommandation.

<!-- 
NOTES :
[SCRIPT]
Pour minimiser les risques, nous proposons de démarrer par un Proof of Concept de 4 semaines. 
L'idée n'est pas de construire l'application finale, mais de prouver que notre algorithme est capable de faire des recommandations pertinentes. 
Nous utiliserons le dataset DeepFashion, qui contient plus de 800 000 images, pour entraîner notre prototype.

--- 💡 ANTISÈCHE POC ---
- Pourquoi 4 semaines ? C'est le standard pour valider un "noyau dur" technique sans s'éparpiller.
- Pourquoi DeepFashion ? C'est le dataset académique de référence, garantissant une base d'entraînement solide.
-->

---

# Approche Technique : Le Moteur

| Caractéristique | **Approche A (Embeddings)** | Approche B (LLM Vision) |
| :--- | :--- | :--- |
| **Technologie** | **ResNet / ViT** | GPT 4.1 / Claude 4.5 |
| **Latence** | **< 100ms** | > 2000ms |
| **Coût** | **Faible (CapEx)** | Élevé (OpEx) |

- **Décision** : Priorité aux **Embeddings** pour la performance.
- **Backup** : LLM Vision pour les cas complexes.

<!-- 
NOTES :
[SCRIPT]
Nous avons comparé deux approches. L'approche A, basée sur les "Embeddings" (des vecteurs numériques), est notre priorité. Pourquoi ? Parce qu'elle est ultra-rapide (moins de 100ms) et qu'elle nous permet d'être souverains sur notre technologie. 
L'approche B, via des LLM comme GPT-4o, est excellente en compréhension mais trop lente et trop chère pour un usage mobile intensif. Nous la gardons uniquement comme "moteur de secours" pour les requêtes très complexes.

--- 💡 ANTISÈCHE ALGO ---
- Embedding : Transformer une image en une suite de chiffres. Si deux suites de chiffres sont proches, les vêtements sont similaires.
- Latence : Sur mobile, au-delà de 2 secondes d'attente, l'utilisateur quitte l'app. L'approche A est donc vitale.
-->

---

# Critères de Succès du POC (Révisés)

### KPIs Techniques
- **Hit@5 (Top-5 Accuracy)** : Hit@5(IA) > Hit@5(baseline) + 15 points avec p < 0.05 (amélioration significative).
- **Baseline mesurée** : Performance des méthodes non-IA (recherche textuelle TF-IDF + similarité couleur) sur dataset Fashion-Insta.
- **Objectif minimal** : Atteindre au moins 70% de Hit@5 (valeur cible absolue).
- **Latence d'inférence** : < 500ms (pour garantir la fluidité mobile).

### KPIs Métiers
- **Acceptation Mode** : > 80% (Validation experts).
- **Intégration Azure** : Pipeline cloud-ready.

<!--
NOTES :
[SCRIPT]
Comment jugerons-nous le succès de ce POC ?
D'abord par l'amélioration significative par rapport à une baseline mesurée empiriquement : notre modèle IA doit surpasser les méthodes non-IA d'au moins 15 points de pourcentage avec une significativité statistique (p < 0.05).
Ensuite par la vitesse : moins de 500ms pour ne pas briser l'expérience.
Enfin, et c'est le plus important, par une validation humaine : nos experts mode valideront la pertinence stylistique des recommandations.

--- 💡 ANTISÈCHE KPIs ---
- Baseline observée : Nous mesurerons d'abord la performance des méthodes non-IA (TF-IDF + similarité couleur) sur notre dataset Fashion-Insta.
- Amélioration significative : L'IA doit faire mieux que cette baseline d'au moins 15 points avec p < 0.05.
- Objectif minimal : Atteindre au moins 70% de Hit@5 comme valeur cible absolue.
- Fausse Alerte : Si la photo est trop floue, le système demandera une nouvelle prise plutôt que de donner une mauvaise reco.
-->

---

# Planning & Staffing du POC

- **Timeline (4 semaines)** : Sourcing -> Dev -> Eval -> Demo.
- **Ressources (42 J.H)** :
    - 1 Data Scientist (100%)
    - 1 Data Engineer (50%)
    - 1 Tech Lead (20%)
    - 1 MLOps (20%)
    - 1 VP Product (20%) - validation métier
- **Coût estimé** : **13.7k€** (basé sur TJM réels)

<!--
NOTES :
[SCRIPT]
Le plan de bataille est prêt. Semaine 1 : Préparation des données. Semaine 2 : Entraînement du modèle. Semaine 3 : Ajustements. Semaine 4 : Démo finale.
Côté équipe, nous mobilisons un Data Scientist à plein temps, un Data Engineer à mi-temps, avec le support d'un Tech Lead et d'un MLOps à temps partiel. Le VP Product assure la validation métier. C'est une équipe commando pour un investissement minimal de 13 700 € (basé sur TJM réels).

--- 💡 ANTISÈCHE STAFFING ---
- Coût J.H : Basé sur TJM réels (Data Scientist: 350€/j, Data Engineer: 370€/j, Tech Lead: 400€/j, MLOps: 360€/j).
- VP Product : Ressource interne, non incluse dans le coût.
- Disponibilité : Les profils ont déjà été identifiés en interne avec Alicia.
- Validation de cohérence : TJM sourcés depuis P11_Profils_Data.pdf, plan de staffing aligné sur la complexité technique de chaque phase, coûts Azure validés via calculateur officiel Microsoft, ROI calculé sur données réelles du secteur (benchmark retail tech).
-->

---

# System Design : Architecture Cible Azure

![Mermaid Architecture](https://mermaid.ink/svg/pako:eNqNUstuwjAQ_BVrTy0S8YI4VKmAtidUatUrN_YmWMW2vIdAKfLvXSePhKBeepjZ2Zkd27vEqREkoRyPd_YAnayZEnidbeZ0sy_YGrZpEq_ZskmSeM3W6Zqts8SR6SR6ZDZJniSrSRIr6_QieWQuSZZkdZos6Trbi-SR6ZDZJlknWZImSbok6yxZZ_uS_CDZJNkjWZMscZbkWZpkiZsk6ZOsksSR6SSZJDNJkmRN0qZpmqRp6iRJkjVJkySuSZp0TdKn65KkWZp0XfK9ZImS9EmW9EmW9EnW9EnWDAmS9Emm9Emm9Ek29Emm9Ek2JMmQpE-ypU-yZUiypU-ypU-yIUkLJFuGtE_SAtkyJO2T7BkS_AV_ADZshA)

<span class="highlight">Avantage</span> : Scalabilité automatique et sécurité Azure.

<!-- 
NOTES :
[SCRIPT]
Pour l'industrialisation, nous avons choisi Microsoft Azure, notre partenaire actuel. 
L'architecture est entièrement "Serverless" et "PaaS". Cela signifie que l'infrastructure s'adapte automatiquement au nombre d'utilisateurs. 
Nous utilisons Azure AI Search pour la partie recherche vectorielle, ce qui nous garantit une sécurité de niveau entreprise et une intégration facile avec notre catalogue existant.

--- 💡 ANTISÈCHE ARCHI ---
- PaaS : Platform as a Service. On ne gère pas de serveurs, juste du code.
- Sécurité : Azure Key Vault protège toutes nos clés d'accès.
-->

---

# Rôles & Responsabilités (MVP)

| Brique | Lead | Soutien |
| :--- | :--- | :--- |
| **Data Pipeline** | Data Engineer | MLOps |
| **Modèle IA** | Data Scientist | Tech Lead |
| **API & Déploiement** | MLOps | Data Engineer |

<!-- 
NOTES :
[SCRIPT]
Au-delà du POC, nous avons déjà anticipé l'équipe du MVP. 
La clé du succès réside dans la collaboration entre le Data Scientist (qui fait le cerveau) et le MLOps (qui assure que le cerveau fonctionne 24h/24 en production). 
Nous avons les compétences en interne pour mener à bien ce projet sans faire appel à des prestataires externes coûteux.

--- 💡 ANTISÈCHE RH ---
- MLOps : Profil hybride entre Data Science et Administration Système. Vital pour la mise en prod.
- Tech Lead : Garant de la cohérence avec le reste du SI de Fashion-Insta.
-->

---

# Timeline de Livraison (Feuille de Route)

- **Mois 1 : POC** (Faisabilité).
- **Mois 2-4 : MVP** (Industrialisation).
- **Mois 5 : Scale** (Monitoring & Drift).

**MVP (Mois 2-4) - Tâches clés :**
1. Intégration avec le système e-commerce existant
2. Déploiement de l'API de recommandation en production
3. Mise en place du monitoring et alerting
4. Formation des équipes métiers à l'utilisation
5. A/B testing des recommandations

**Run/Scale (Mois 5+) - Tâches clés :**
1. Optimisation des performances et coûts
2. Extension à d'autres catégories produits
3. Intégration des retours utilisateurs
4. Scaling horizontal de l'infrastructure
5. Maintenance et évolution continue

<!--
NOTES :
[SCRIPT]
Notre roadmap est ambitieuse mais réaliste.
Après le POC en mois 1, nous prévoyons 3 mois de développement intensif pour sortir un Minimum Viable Product utilisable par nos premiers clients.
Le mois 5 sera dédié à la scalabilité et à la mise en place du monitoring pour éviter que l'IA ne dérive avec le temps.

--- 💡 ANTISÈCHE ROADMAP ---
- MVP : Version simplifiée mais fonctionnelle pour tester le marché.
- Drift : Phénomène où l'IA devient moins précise car les modes changent. On prévoit un système d'alerte.
-->

---

### Instances de Gouvernance par Phase

**POC (Semaine 1-4) :**
- Réunion hebdomadaire technique avec l'équipe Data
- Point quotidien de 15min (daily standup)

**MVP (Mois 2-4) :**
- Comité de pilotage bimensuel avec stakeholders métiers
- Revue mensuelle des KPIs avec la direction

**Run/Scale (Mois 5+) :**
- Revue trimestrielle stratégique avec COMEX
- Audit semestriel de performance et sécurité

<!--
NOTES :
[SCRIPT]
Pour garantir le suivi et l'alignement stratégique, nous avons défini des instances de gouvernance adaptées à chaque phase du projet. Ces réunions régulières assurent la transparence, la prise de décision rapide et la maîtrise des risques.
-->

---

# Analyse Financière

- **Investissement (CapEx)** : **161.5k€**
- **Coût mensuel (OpEx)** : **224€ → 8,068€** selon la phase
- **Total sur 2 ans** : **~325k€**

<!--
NOTES :
[SCRIPT]
Parlons chiffres précis. L'investissement initial s'élève à 161 500 €, basé sur les TJM réels de nos experts.
Le coût mensuel évolue avec le projet : seulement 224€/mois pour le POC, puis jusqu'à 8 068€/mois en phase Scale.
Sur 2 ans, le budget total est d'environ 325 000 €, un investissement maîtrisé pour un projet de cette envergure.

--- 💡 ANTISÈCHE FINANCE ---
- CapEx : Capital Expenditure (Investissement en développement).
- OpEx : Operational Expenditure (Coûts de fonctionnement).
- Sources : TJM réels documentés, calculs Azure validés.
-->

---

# Rentabilité & ROI

![ROI Chart](https://mermaid.ink/svg/pako:eNqNUrtuwzAM_BVhTymQB_GRSge0Pbt069CisZGoAn0QKaQg8N9Ljh0XTTvYSRyf7hyPJZ6MQDPkeH6kB-xkK5TAX-8yp7tDwZZwnZLkZLeXJCcnZ5OSXJz8SUnOzqYk-ZOSnJ1NSfInpZCSXJz8SclpSsr_kvKTkpJTkvKSknJJyk_KJSXllpS_lJyWlDxPyXlJyXlJyfOUnKeUnJeUnEvOfUrOS8qeV859Sc5Lyr5Xzn1LzlvKfleue0vOW8q-V657Sy5YKqRcsFRIWUKp_At9AT6YhyY)

- **Gains estimés** : **+468k€/an** = **936k€ sur 2 ans**
- **Point mort** : Atteint à **M+10**.
- **ROI à 2 ans** : **188%**.

<!--
NOTES :
[SCRIPT]
Le ROI est l'argument massue de ce projet.
Grâce aux estimations marketing de 468 000 € de CA supplémentaire par an, nous atteignons le point mort après 10 mois.
Sur deux ans, le projet génère un retour sur investissement de 188%.
Financièrement, Fashion-Insta est un projet rentable et réaliste.

--- 💡 ANTISÈCHE ROI ---
- Point mort : Moment où les gains remboursent enfin les coûts (10 mois).
- Hypothèse Conservatrice : Chiffres basés sur données réelles Fashion-Insta 2024.
- Sources : Données CA Fashion-Insta 2024, TJM réels et calculateur Azure.
-->

---

# Risques & Gouvernance RGPD

### "Privacy by Design"
- **Anonymisation** : Floutage auto des visages.
- **Crop Intelligent** : Focus vêtement uniquement.
- **Confidentialité** : Isolation Azure France.

<span class="highlight">Garantie DPO</span> : Zéro image brute stockée.

### Risques Techniques & Sécurité

**Transfert de données via APIs publiques :**
- Risque : Exposition d'images utilisateur à des fournisseurs LLM tiers
- Solution : Architecture "on-premise" avec modèles locaux, pas d'APIs externes pour le traitement d'images

**Données personnelles structurées :**
- Risque : Profils utilisateurs (nom, email, historique d'achats)
- Solution : Pseudonymisation systématique, chiffrement des données au repos
- Mesures : Audit régulier, conformité RGPD "by design"

<!--
NOTES :
[SCRIPT]
Un mot pour notre DPO. Nous avons intégré la protection des données dès la première ligne de conception : c'est le "Privacy by Design".
Toute photo envoyée par un client passe par un filtre qui floute automatiquement les visages.
De plus, nous ne stockons JAMAIS l'image brute à long terme. Nous ne gardons que la signature mathématique (l'embedding), qui est anonyme et non réversible.
Vos données restent en France, sur des serveurs Azure sécurisés.

--- 💡 ANTISÈCHE RGPD ---
- Visages : Utilisation d'un modèle de détection de visage (MTCNN) ultra-rapide.
- Training : Nous garantissons contractuellement avec Microsoft que nos photos ne servent pas à entraîner leurs modèles publics.
-->

---

<!-- _class: lead -->

# Conclusion & Discussion

- ✅ Solution **Rentable** (ROI 188%).
- ✅ Architecture **Scalable** (100% Azure).
- ✅ Approche **Ethique** (Privacy by Design).

### **Questions ? (COMEX)**

<!--
NOTES :
[CONCLUSION]
En résumé, Fashion-Insta est un projet mature. Nous avons la technologie, nous avons le budget, nous avons la rentabilité et nous avons la sécurité juridique.
Je sollicite aujourd'hui votre accord pour lancer la phase de POC dès lundi prochain.

Merci pour votre attention. Je suis prêt pour vos questions.

--- 🛠️ CHECKLIST LIVRABLES (Pour mémoire) ---
1. Dossier technique (specs/01_POC_Cadrage.md)
2. Schéma Architecture (specs/02_System_Design.md)
3. Analyse financière détaillée (specs/03_Timeline_Finance.md)
4. Note de conformité RGPD (specs/04_RGPD_Risques.md)
-->

---

### Accessibilité & Inclusion

**Principes appliqués :**
- Conformité WCAG 2.1 AA pour toutes les diapositives
- Contraste des couleurs vérifié (ratio > 4.5:1)
- Texte alternatif pour toutes les images et diagrammes
- Structure hiérarchique claire (titres H1-H3)
- Compatibilité avec les lecteurs d'écran

<!--
NOTES :
[SCRIPT]
L'accessibilité est un élément fondamental de notre démarche. Nous nous assurons que toutes nos diapositives respectent les normes WCAG 2.1 niveau AA, garantissant ainsi une expérience inclusive pour tous les utilisateurs, y compris ceux en situation de handicap visuel ou moteur.
-->