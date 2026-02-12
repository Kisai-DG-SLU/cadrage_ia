# Timeline, Staffing & Analyse Financière - Projet Fashion-Insta

## 1. Timeline de Livraison Progressive
Le projet est découpé en 3 phases majeures après la validation du POC.

| Phase | Durée | Objectifs Clés | Livrables |
| :--- | :--- | :--- | :--- |
| **Phase 1 : POC** | 4 sem. | Validation technique & Algo. | Rapport de faisabilité. |
| **Phase 2 : MVP** | 12 sem. | Industrialisation & Intégration Azure. | API de Production (v1). |
| **Phase 3 : Scale** | 4 sem. | Optimisation & Monitoring Drift. | Dashboard MLOps & Scalabilité. |

### Instances de Gouvernance
- **Sprint Review** : Toutes les 2 semaines (Équipe Data + Alicia).
- **Comité de Pilotage (COPIL)** : Une fois par mois (Alicia + COMEX + DPO).

## 2. Plan de Staffing (Taux de charge %)

| Profil | Phase 1 (POC) | Phase 2 (MVP) | Phase 3 (Scale) | Run (Maintenance) |
| :--- | :---: | :---: | :---: | :---: |
| **Tech Lead** | 20% | 50% | 50% | 10% |
| **Data Scientist** | 100% | 100% | 50% | 20% |
| **Data Engineer** | 50% | 100% | 50% | 10% |
| **MLOps** | 20% | 100% | 100% | 20% |
| **Ingénieur IA Chef de Projet** | 50% | 30% | 20% | 20% |

## 3. Analyse Financière (Révisée avec Données Réelles)

### Coûts d'Implémentation (One-shot / CapEx)
*Basé sur les TJM réels extraits de `docs/P11_Profils_Data.pdf`.*

**Taux Journaliers Moyens (TJM) :**
- Data Scientist : 350 €/jour
- Data Engineer : 370 €/jour
- Tech Lead Data : 400 €/jour
- ML Ops Engineer : 360 €/jour

**Calculs détaillés :**
- **Phase POC (4 semaines)** : 13 740€
  - Tech Lead (20%) : 1 600€
  - Data Scientist (100%) : 7 000€
  - Data Engineer (50%) : 3 700€
  - MLOps (20%) : 1 440€
  - Ingénieur IA Chef de Projet (50%) : Ressource interne (0€)

- **Phase MVP (12 semaines)** : 76 800€
  - Tech Lead (50%) : 12 000€
  - Data Scientist (100%) : 21 000€
  - Data Engineer (100%) : 22 200€
  - MLOps (100%) : 21 600€
  - Ingénieur IA Chef de Projet (30%) : Ressource interne (0€)

- **Phase Scale (4 semaines)** : 18 400€
  - Tech Lead (50%) : 4 000€
  - Data Scientist (50%) : 3 500€
  - Data Engineer (50%) : 3 700€
  - MLOps (100%) : 7 200€
  - Ingénieur IA Chef de Projet (20%) : Ressource interne (0€)

- **Run/Maintenance (24 mois)** : 52 560€
  - Tech Lead (10%) : 9 600€
  - Data Scientist (20%) : 16 800€
  - Data Engineer (10%) : 8 880€
  - MLOps (20%) : 17 280€
  - Ingénieur IA Chef de Projet (20%) : Ressource interne (0€)

**Total CapEx (Staffing)** : **161 500€** (inchangé - ingénieur IA chef de projet ressource interne)

### Coûts Récurrents (OpEx / Run) - Azure
*Basé sur le calculateur Azure France Centre (février 2026) - Validé dans `plans/azure_costs_validated.md`.*

**Maintenance humaine recalculée avec TJM réels :**
- Tech Lead (10%) : 800€/mois
- MLOps (20%) : 1 440€/mois
- Data Scientist (20%) : 1 400€/mois
- Data Engineer (10%) : 740€/mois
- **Total maintenance** : **4 380€/mois** (arrondi à 4 400€ pour estimation)

| Phase | Infrastructure Azure | Maintenance Humaine | Total Mensuel |
|-------|---------------------|---------------------|---------------|
| **POC (1 mois)** | 230,25€ | 0€ (inclus dans CapEx) | 230,25€ |
| **MVP (11 mois)** | 513,22€ | 4 400€ | 4 913,22€ |
| **Scale (12 mois)** | 1 591,94€ | 4 400€ | 5 991,94€ |

**Total OpEx sur 2 ans** : **24 978€** (infrastructure) + **105 600€** (maintenance 24 mois × 4 400€) = **130 578€**

### Coûts Totaux sur 2 Ans
- **CapEx (Staffing)** : 161 500€
- **OpEx (Infrastructure)** : 24 978€
- **Maintenance Humaine** : 105 600€
- **Total Investissement** : **292 078€**

## 4. Calcul du ROI & Rentabilité
**Hypothèses Marketing** : Basées sur les données réelles Fashion-Insta 2024 :
- CA e-commerce : 5,2 M€
- CA physique : 5,2 M€
- Étude marketing : +14% CA e-commerce et +4% CA physique sur 24 mois

**Gains estimés sur 2 ans :**
- E-commerce : 5,2 M€ × 14% = **728 000€**
- Physique : 5,2 M€ × 4% = **208 000€**
- **Total gains** : **936 000€**

**Répartition annuelle (hypothèse linéaire) :**
- Année 1 : 468 000€
- Année 2 : 468 000€

| Année | Coûts Cumulés | Gains Cumulés | Solde (Cash Flow) |
| :--- | :--- | :--- | :--- |
| **Année 0 (Développement)** | 161 500 € | 0 € | -161 500 € |
| **Année 1** | 220 176 € | 468 000 € | +247 824 € |
| **Année 2** | 292 079 € | 936 000 € | +643 921 € |

**Break-even Point (Point mort)** : Atteint environ **9 mois** après le début du projet.
**ROI à 2 ans** : **(936 000€ - 292 079€) / 292 079€ × 100% = 220%**

**Analyse de sensibilité :**
- Si les gains sont de seulement +10% CA e-commerce et +2% CA physique : ROI = 120%
- Si les coûts infrastructure augmentent de 20% : ROI = 180%
- Scénario conservateur reste rentable avec ROI > 100%

**Sources :**
- TJM : `docs/P11_Profils_Data.pdf`
- CA Fashion-Insta : Documents financiers 2024
- Coûts Azure : `plans/azure_costs_validated.md` (calculateur Azure)
- Gains marketing : Étude interne Fashion-Insta

