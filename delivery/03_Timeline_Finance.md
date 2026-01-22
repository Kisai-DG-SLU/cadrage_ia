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

## 3. Analyse Financière (Estimation)

### Coûts d'Implémentation (One-shot / CapEx)
*Basé sur un coût moyen journalier (TJM) de 600€.*
- **Phase POC** : ~20k€ (Staffing réduit).
- **Phase MVP & Scale** : ~130k€ (Équipe complète sur 4 mois).
- **Total CapEx** : **~150k€**.

### Coûts Récurrents (OpEx / Run) - Azure
*Estimation basée sur le simulateur Azure (Usage modéré).*
- **Compute (AML + App Service)** : ~600€ / mois.
- **Storage & AI Search** : ~300€ / mois.
- **Maintenance Humaine (Run)** : ~2000€ / mois.
- **Total OpEx** : **~2900€ / mois** (~35k€ / an).

## 4. Calcul du ROI & Rentabilité
**Hypothèses Marketing** : Augmentation du CA e-commerce estimée à **+400k€ / an**.

| Année | Coûts Cumulés | Gains Cumulés | Solde (Cash Flow) |
| :--- | :--- | :--- | :--- |
| **Année 0 (Dev)** | 150 000 € | 0 € | -150 000 € |
| **Année 1** | 185 000 € | 400 000 € | +215 000 € |
| **Année 2** | 220 000 € | 800 000 € | +580 000 € |

**Break-even Point (Point mort)** : Atteint environ **6 mois** après la mise en production.
**ROI à 2 ans** : **> 250%**.
