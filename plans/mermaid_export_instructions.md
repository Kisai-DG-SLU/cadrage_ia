# Instructions pour l'Export des Diagrammes Mermaid

## Contexte
Les diagrammes Mermaid dans la présentation (`delivery/05_Presentation_Slides.md`) et les documents d'architecture doivent être exportés en images PNG pour éviter les problèmes de connectivité lors de la présentation.

## Diagrammes à Exporter

### 1. Diagramme d'Architecture Principal
**Fichier source** : `plans/architecture_diagram.md`
**Code Mermaid** :
```mermaid
flowchart TD
    subgraph Frontend
        A[Application Mobile<br/>iOS/Android] --> B[SDK Azure Mobile Apps]
    end

    subgraph API Layer
        B --> C[Azure API Management<br/>Gateway & Rate Limiting]
        C --> D[Azure App Service<br/>FastAPI Python]
    end

    subgraph Processing Layer
        D --> E[Azure Machine Learning<br/>Endpoint d'inférence]
        E --> F[Embedding Vector<br/>512 dimensions]
    end

    subgraph Search Layer
        F --> G[Azure AI Search<br/>Vector Index HNSW]
        G --> H[Azure Cache for Redis<br/>Cache des résultats fréquents]
    end

    subgraph Data Layer
        I[Azure Blob Storage<br/>Images catalogue] --> J[Azure Data Factory<br/>Pipeline d'ingestion]
        J --> K[Azure SQL Database<br/>Métadonnées produits]
        L[Azure Key Vault<br/>Secrets & Clés] --> D
        L --> E
    end

    subgraph Monitoring & Security
        M[Azure Monitor<br/>Application Insights] --> N[Dashboards<br/>Alertes]
        O[Azure RBAC<br/>IAM] --> P[Azure Defender<br/>Security Center]
    end

    subgraph Output
        H --> Q[API Response<br/>Top-5 produits]
        K --> Q
        Q --> R[Frontend Mobile<br/>Affichage résultats]
    end

    style A fill:#e1f5fe
    style D fill:#f3e5f5
    style E fill:#e8f5e8
    style G fill:#fff3e0
    style K fill:#fce4ec
```

### 2. Diagramme de la Présentation (Slide 9)
**Fichier source** : `delivery/05_Presentation_Slides.md` (lignes 37-75)
**Code Mermaid** : Identique au diagramme ci-dessus

## Méthodes d'Export

### Méthode 1 : Utilisation de mermaid.ink (En ligne)
1. Copier le code Mermaid (sans les backticks ```)
2. Aller sur https://mermaid.ink/
3. Coller le code dans l'éditeur
4. Télécharger l'image SVG ou PNG
5. Sauvegarder dans `delivery/images/mermaid/architecture_diagram.png`

### Méthode 2 : Utilisation de mermaid-cli (Local)
```bash
# Installation
npm install -g @mermaid-js/mermaid-cli

# Création du répertoire
mkdir -p delivery/images/mermaid

# Export du diagramme
mmdc -i plans/architecture_diagram.mmd -o delivery/images/mermaid/architecture_diagram.png -t neutral
```

### Méthode 3 : Utilisation de l'API mermaid.ink (Script)
```python
import requests
import base64
import zlib

def encode_mermaid_to_url(mermaid_code):
    compressed = zlib.compress(mermaid_code.encode('utf-8'))
    encoded = base64.urlsafe_b64encode(compressed).decode('utf-8')
    return f"https://mermaid.ink/svg/{encoded}"

# Téléchargement
url = encode_mermaid_to_url(mermaid_code)
response = requests.get(url)
with open('architecture_diagram.png', 'wb') as f:
    f.write(response.content)
```

## Fichiers à Mettre à Jour

Après export des images, mettre à jour les fichiers Markdown suivants :

### 1. `delivery/05_Presentation_Slides.md`
**Remplacer** :
```mermaid
...code...
```

**Par** :
```
![Architecture Azure](images/mermaid/architecture_diagram.png)
```

### 2. `delivery/PRESENTATION.md`
**Remplacer** :
```
![Mermaid Architecture](https://mermaid.ink/svg/pako:eNqNUstuwjAQ/BVrTy0S8YI4VKmAtidUatUrN/YmWMW2vIdAKfLvXSePhKBeepjZ2Zkd27vEqREkoRyPd/YAnayZEnidbeZ0sy/YGrZpEq/ZskmSeM3W6Zqts8SR6SR6ZDZJniSrSRIr6/QieWQuSZZkdZos6Trbi-SR6ZDZJlknWZImSbok6yxZZ/uS/CDZJNkjWZMscZbkWZpkiZsk6ZOsksSR6SSZJDNJkmRN0qZpmqRp6iRJkjVJkySuSZp0TdKn65KkWZp0XfK9ZImS9EmW9EmW9EnW9EnWDAmS9Emm9Emm9Ek29Emm9Ek2JMmQpE+ypU+yZUiypU+ypU+yIUkLJFuGtE/SAtkyJO2T7BkS_AV_ADZshA)
```

**Par** :
```
![Architecture Azure](images/mermaid/architecture_diagram.png)
```

## Structure des Fichiers Résultants

```
delivery/
├── images/
│   ├── mermaid/
│   │   ├── architecture_diagram.png
│   │   └── presentation_diagram.png
│   ├── background.png
│   └── logo_projet.png
├── 05_Presentation_Slides.md
└── PRESENTATION.md
```

## Avantages de l'Export Local

1. **Fiabilité** : Pas de dépendance à une connexion internet
2. **Performance** : Chargement instantané des images
3. **Contrôle** : Versioning des images avec le code
4. **Portabilité** : Présentation fonctionne hors ligne
