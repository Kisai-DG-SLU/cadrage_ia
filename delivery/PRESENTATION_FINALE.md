---
marp: true
theme: gaia
paginate: true
backgroundImage: url('images/background.png')
style: |
  /* IMPORT POLICES */
  @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&family=Montserrat:wght@600;800&display=swap');

  /* VARIABLES */
  :root {
    --color-bg: #fdfbf7; 
    --color-text: #2d3436;
    --color-primary: #2c3e50; /* Bleu Foncé */
    --color-accent: #6c5ce7; 
    --color-orange: #E65100;  /* Orange */
  }

  /* CONFIGURATION GENERALE */
  section {
    font-family: 'Lato', sans-serif;
    font-size: 24px;
    color: var(--color-text);
    background-color: var(--color-bg);
    
    /* SECURITE LOGO HAUT GAUCHE */
    padding-top: 100px;
    padding-bottom: 40px;
    padding-left: 70px;
    padding-right: 70px;
    
    /* Centre tout verticalement par défaut */
    display: flex;
    flex-direction: column;
    justify-content: center; 
    align-items: center;
    position: relative; /* Nécessaire pour le positionnement absolu des enfants */
  }

  /* --- TYPOGRAPHIE --- */
  h1, h2, h3 {
    font-family: 'Montserrat', sans-serif;
    text-transform: uppercase;
    letter-spacing: -1px;
    text-align: center;
    width: 100%;
  }

  /* H1 STANDARD (Toutes les slides sauf la 1ère) */
  section:not(.lead) h1 {
    font-size: 1.3em;
    color: var(--color-primary);
    border-bottom: 3px solid var(--color-accent);
    padding-bottom: 10px;
    margin-bottom: 40px;
    margin-top: 0; 
  }

  /* H1 SPÉCIAL SLIDE 1 */
  section.lead h1 {
    font-size: 2.5em; 
    color: var(--color-primary);
    border: none;
    margin-bottom: 20px;
    line-height: 1.1;
  }

  /* H2 (Sous-titres) */
  h2 {
    font-size: 0.9em;
    color: var(--color-orange);
    margin-top: 0;
    margin-bottom: 20px;
  }

  /* H3 (Titres de blocs) */
  h3 {
    font-size: 0.9em;            
    color: var(--color-primary); 
    margin-bottom: 15px;
  }
   
  /* LOGO (Coin haut gauche) */
  section::before {
    content: ' ';
    position: absolute;
    top: 10px;
    left: 10px; 
    width: 90px;
    height: 90px;
    background-image: url('images/logo_projet.png');
    background-size: contain;
    background-repeat: no-repeat;
    opacity: 0.8;
  }

  /* --- SPECIFIQUE SLIDE 1 --- */
  /* Bloc texte aligné à gauche en bas */
  .intro-text-left {
    position: absolute; /* Force le positionnement hors du flux centré */
    bottom: 40px;       /* Distance du bas */
    left: 70px;         /* Distance de la gauche (aligné avec le padding) */
    text-align: left;
    font-size: 0.9em;
    color: var(--color-text);
    z-index: 10; /* S'assure qu'il est au-dessus au cas où */
  }

  /* --- STRUCTURES --- */
  .columns { display: grid; grid-template-columns: 40% 60%; gap: 0; width: 100%; }
  .columns div { display: flex; flex-direction: column; align-items: center; padding: 0 30px; }
  .columns div:last-child { border-left: 2px solid #dcdde1; }

  /* Staff Grid */
  .staff-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; margin-bottom: 30px; width: 100%; }
  .staff-list { list-style: none; padding: 0; margin: 0; }
  .staff-item { margin-bottom: 12px; display: flex; align-items: center; }

  /* Icones */
  .ico { font-size: 28px; margin-right: 12px; display: inline-block; }
  .ico-black { filter: grayscale(100%) brightness(0%); opacity: 0.8; }
  .ico-gold { filter: sepia(100%) saturate(1000%) hue-rotate(20deg) brightness(90%); }

  /* POC Grid */
  .poc-grid { display: grid; grid-template-columns: repeat(2, 1fr); grid-template-rows: repeat(2, 1fr); gap: 20px; height: 450px; width: 100%; }
  .poc-card { position: relative; padding: 25px; border: 1px solid rgba(0,0,0,0.1); border-radius: 12px; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; background-color: rgba(255,255,255,0.7); overflow: hidden; }
  .poc-card::before { content: ""; position: absolute; top: 0; left: 0; width: 100%; height: 100%; background-size: cover; background-position: center; opacity: 0.15; z-index: 0; }
  .img-obj::before { background-image: url(images/objectif.png); }
  .img-per::before { background-image: url(images/perimetre.png); }
  .img-dat::before { background-image: url(images/donnees.png); }
  .img-liv::before { background-image: url(images/livrable.png); }
  .poc-card h2, .poc-card p { position: relative; z-index: 1; }

  /* UTILITAIRES */
  .center-img { display: block; margin: 0 auto; text-align: center; }
  .custom-list { list-style: none; padding: 0; margin: 0; width: 100%; }
  .custom-list li { display: flex; align-items: flex-start; margin-bottom: 25px; width: 100%; }
  .custom-list img { margin-right: 20px; margin-top: 5px; flex-shrink: 0; }

  /* Tech Comparison */
  .tech-comparison { display: grid; grid-template-columns: 1fr 1fr; width: 100%; margin-top: 20px; }
  .tech-header { padding: 15px; font-family: 'Montserrat', sans-serif; font-weight: 800; font-size: 1.1em; text-align: center; }
  .header-a { background-color: #d1e8e2; color: #2c3e50; border-right: 2px solid #2d3436; }
  .header-b { background-color: #bdc3c7; color: #2c3e50; }
  .tech-body { padding: 30px; display: flex; flex-direction: column; gap: 25px; }
  .tech-item { display: flex; align-items: center; gap: 15px; }
  .tech-item span { font-size: 0.9em; line-height: 1.2; }
  .border-right { border-right: 2px solid #2d3436; }
   
  /* --- STYLE RGPD --- */
  .rgpd-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 30px;
    margin-top: 40px;
    margin-bottom: 40px;
    text-align: center;
  }
  .rgpd-col { display: flex; flex-direction: column; align-items: center; }
  .rgpd-img { height: 120px; width: auto; margin-bottom: 20px; }
  .rgpd-title { font-family: 'Montserrat', sans-serif; font-size: 1.1em; font-weight: 800; margin-bottom: 15px; color: #2d3436; }
  .rgpd-text { font-size: 0.9em; line-height: 1.3; color: #2d3436; }

  /* --- STYLE CONCLUSION --- */
  .concl-grid {
    display: grid;
    grid-template-columns: 55% 45%; 
    gap: 40px;
    align-items: center;
    margin-top: 20px;
    width: 100%;
  }

  /* Liste des items avec coches */
  .check-item { display: flex; align-items: center; margin-bottom: 30px; text-align: left; }
  .check-icon { width: 55px; height: auto; margin-right: 20px; flex-shrink: 0; }
  .check-text { font-size: 1em; line-height: 1.2; color: #000; }

  /* Boîte de Validation */
  .validation-box {
    border: 4px solid #ff8a65;
    background: linear-gradient(to bottom right, #ffffff, #fbe9e7);
    padding: 30px 20px;
    box-shadow: 0 10px 25px rgba(255, 138, 101, 0.3);
    text-align: center;
    color: #000;
  }

  /* Logo de fin */
  .footer-logo-block {
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  /* LOGO FIN AGRANDI */
  .logo-fin {
    width: 280px; 
    margin-bottom: 10px;
  }
  .brand-text { font-family: 'Montserrat', sans-serif; font-weight: 800; letter-spacing: 1px; text-transform: uppercase; font-size: 0.8em; color: #2c3e50; }

---
# Du style à l'achat<br>L'IA Comme moteur de conversion

## Cadrage Stratégique - Projet Fashion-Insta

<div class="center-img">

![width:650px](images/page1.png)

<br>
<br>
<br>
<br>
</div>

<div class="intro-text-left">
  <strong>Projet :</strong> Recommandation Vestimentaire par IA<br>
  <strong>Auteur :</strong> Damien GUESDON, AI Engineer<br>
  <strong>Date :</strong> Février 2026
</div>

<!--
Section 1 : Titre & Introduction (Slide 1)

 Bonjour. Je suis Damien, Ingénieur IA et Chef de Projet sur cette initiative.
 Nous sommes aujourd'hui réunis pour parler d'accélération.
 
 Fashion-Insta est un leader de la mode, mais l'expérience client digitale doit franchir un cap.
 L'objectif de cette présentation est de valider le lancement d'un POC (Proof of Concept) visant à transformer la façon dont les clients découvrent les produits.
 
 Nous allons voir comment l'IA peut transformer une simple inspiration visuelle en acte d'achat immédiat, de manière rentable, techniquement maîtrisée et juridiquement sécurisée.




💡 Antisèche (Q&A) :
• Pourquoi vous ? : "Je porte la vision technique tout en assurant l'alignement avec les enjeux business d'Alicia (VP Product)."
• Pourquoi maintenant ? : "La technologie est mature (Embeddings/Vision) et les concurrents prennent de l'avance. Le coût d'entrée a baissé, c'est le moment d'y aller." 

-->

---

# Le Constat : Une friction coûteuse

<div class="columns">
<div>

### Le Problème
        
<p align="center">
  <img src="images/perte30.png" width="300px" />
</p>

</div>
<div>

### L'Opportunité
        
<ul class="custom-list">
  <li>
    <img src="images/voit.png" width="40px"> 
    <span><strong>Mutation mobile</strong> :<br>Capturer l'intention d'achat instantanément.</span>
  </li>
  <li>
    <img src="images/concu.png" width="40px"> 
    <span><strong>Retard stratégique</strong> :<br>Combler l'écart avec les leaders.</span>
  </li>
  <li>
    <img src="images/vision.png" width="40px"> 
    <span><strong>Vision</strong> :<br>Devenir le "Shazam de la mode".</span>
  </li>
</ul>

</div>
</div>

<!--
Section 2 : Contexte & Enjeux (Slide 2)

 Partons d'un constat simple mais douloureux :
 Aujourd'hui, quand un client voit un style qui lui plaît dans la rue ou sur Instagram.
 Il cherche... et souvent, il trouve son bonheur dans une autre enseigne, ou pire, il abandonne.
 
 Pourquoi ? Parce que décrire un vêtement avec des mots clés ('robe rouge fleurie') est laborieux et imprécis. Les chiffres du marketing sont clairs : 30% de perte de conversion potentielle à cause de cette friction.

 L'ambition ici est de supprimer cette barrière pour devenir le 'Shazam de la mode' :
 je vois, je scanne, j'achète.
 
 L'enjeu est de rattraper le retard technologique pour capturer cette intention d'achat instantanée.



💡 Antisèche (Q&A) :
• D'où vient le chiffre de 30% ? : "Ca nous vient de Gartner, qui stipulait en 2017 que les marques adoptant précocement la recherche visuelle et vocale augmenteraient leur chiffre d'affaires numérique de 30 %. Ce chiffre est encore accepté comme une norme aujourd'hui, je l'ai donc pris en référence"
• Google Lens ne fait pas déjà ça ? : "Si, mais Google renvoie vers tous les sites. Nous voulons garder le client dans notre écosystème et notre stock." 
-->

---

# La Solution : Une expérience "Scan & Shop" instantanée

<div class="center-img">

![width:900px](images/tel-to-panier.png)

</div>
<br>

## **Fluidité absolue.** On ne cherche plus, on trouve.

<!--
Section 3 : La Mission / Concept (Slide 3)

 Concrètement, quelle est la promesse ? Elle tient en une phrase : 
 'Prenez une photo, nous trouvons le style.'
 
 L'utilisateur n'a plus besoin de décrire. Il uploade une photo. En moins d'une demi-seconde (500ms), l'IA analyse la coupe, la texture, la couleur, et lui propose les produits Fashion-Insta les plus similaires disponibles en stock. 
 C'est simple pour l'utilisateur, mais derrière, c'est une technologie de pointe en Computer Vision qui sera déployée.



💡 Antisèche (Q&A) :
• Est-ce que ça marche avec des photos floues ? : "L'IA est robuste, mais il y a des limites. Le POC servira justement à tester ces cas 'in-the-wild' (conditions réelles)."
• C'est une app à part ? : "À terme, ce sera une fonctionnalité intégrée dans l'app existante. Pour le POC, ce sera un prototype web isolé." 
-->

---

# Impact Business : Un levier de croissance quantifié

<div class="center-img">

![width:900px](images/estimation.png)

</div>

## **Impact Total :** Potentiel cumulé de **936k€ sur 2 ans**.

<!--
Section 4 : Valeur Ajoutée IA (Slide 4)
 
 Ici l'IA est un levier de croissance.
 En réduisant le temps de recherche de plusieurs minutes à quelques millisecondes, on fluidifie le parcours.
 Les projections, basées sur les données 2024, estiment un gain de chiffre d'affaires de 468 000 € par an.
 Le marketting prévoit ainsi une hausse du panier moyen (+14% en e-commerce) et d'un effet de +4% sur la vente en magasin (effet de la pub sur la nouveauté de l'app, et affichage des dispo ds el magasin le plus proche)



💡 Antisèche (Q&A) :
• Les +14% semblent optimistes ? : "C'est une hypothèse basée sur les benchmarks du secteur (McKinsey 2025) qui observent entre +15% et +30% de conversion sur les parcours de recherche visuelle."
• Et si on fait moins ? : "Même avec la moitié de ces gains, le projet reste rentable (nous verrons le ROI plus loin)." 
-->

---

# Stratégie POC : "Fail fast, learn fast"

<div class="poc-grid">
  <div class="poc-card img-obj">
    <h2>Objectif</h2>
    <p>Valider la faisabilité technique du cœur algorithmique en <strong>4 semaines</strong>.</p>
  </div>
  <div class="poc-card img-per">
    <h2>Périmètre</h2>
    <p>Focus exclusif sur le moteur de recommandation (Back-end uniquement).</p>
  </div>
  <div class="poc-card img-dat">
    <h2>Données</h2>
    <p>Dataset de référence <strong>DeepFashion</strong> (~800k images) pour entraînement initial.</p>
  </div>
  <div class="poc-card img-liv">
    <h2>Livrable</h2>
    <p>Un prototype fonctionnel démontrant la pertinence des recommandations.</p>
  </div>
</div>

<!--
Section 5 : Objectifs du POC (Slide 5)

 Alors, on ne va pas déployer directement. on adopte une approche 'Fail fast, learn fast'. (si n doit se tromper, il faut el faire le plus tôt possible pour ne pas persister dans l'erreur.
 
 L'objectif de ce POC est donc de valider la faisabilité technique en 4 semaines.
 On se concentre uniquement sur le cœur du réacteur : l'algorithme de recommandation.
 (l'implémentation avec le frontend n'interviendra que ds les phases suivantes)

 On utilise le dataset DeepFashion (800 000 images) pour l'entraînement initial, couplé à un extrait de notre catalogue.
 À la fin du mois, le livrable est un prototype fonctionnel : on met une image, on voit si les résultats sont pertinents."



💡 Antisèche (Q&A) :
• Pourquoi 4 semaines ? : "C'est le temps standard pour entraîner un modèle et valider une hypothèse sans engager trop de budget (Sprint Agile)."
• Pourquoi DeepFashion et pas nos données ? : "Pour aller vite. Nos données ne sont pas encore toutes annotées pour l'entraînement IA. DeepFashion est le standard académique pour démarrer."
-->

---

# Choix Technologique : Performance industrielle vs Hype

<div class="tech-comparison">
  <div class="tech-header header-a">Approche A (Retenue) :<br>Embeddings</div>
  <div class="tech-header header-b">Approche B (Exploratoire) :<br>LLM Vision</div>
  <div class="tech-body border-right">
    <div class="tech-item">
      <span>🔍</span>
      <span><strong>Technologie :</strong> Vector Search (ResNet/ViT)</span>
    </div>
    <div class="tech-item">
      <span>⏱️</span>
      <span><strong>Latence :</strong> < 100ms (Ultra-rapide)</span>
    </div>
    <div class="tech-item">
      <span>$</span>
      <span><strong>Coût :</strong> Faible (CapEx)</span>
    </div>
  </div>

  <div class="tech-body">
    <div class="tech-item">
      <span>🔍</span>
      <span><strong>Technologie :</strong> GPT-5 Vision / Claude</span>
    </div>
    <div class="tech-item">
      <span>⏱️</span>
      <span><strong>Latence :</strong> > 2000ms (Trop lent pour mobile)</span>
    </div>
    <div class="tech-item">
      <span>$</span>
      <span><strong>Coût :</strong> Élevé (OpEx)</span>
    </div>
  </div>
</div>
<br>

## **Décision :** Priorité aux Embeddings pour garantir la fluidité et la rentabilité.

<!--
Section 6 : Approche Technique (Slide 6)

 Sur le plan technique, on a comparé deux routes. 
 L'Approche B : Utiliser les gros modèles type GPT-5 Vision. C'est impressionnant, mais c'est lent (> 2 secondes) et très cher à chaque requête.
 La solution retenue est l'Approche A : Les Embeddings. C'est une technologie mature de recherche vectorielle ultra-rapide (< 100ms) et beaucoup moins coûteuse.
 Pour l'utilisateur mobile, la fluidité est non-négociable. On peut garder les LLM uniquement en 'backup' pour des cas très complexes d'analyse de style, mais ce n'est pas le sujet du POC, le moteur principal sera vectoriel.



💡 Antisèche (Q&A) :
• C'est quoi un Embedding ? : "Imaginez que l'IA transforme une image en une liste de 512 chiffres (un code-barres unique). On compare ensuite ces chiffres mathématiquement pour trouver les plus proches. C'est instantané."
• Pourquoi GPT-5 est trop lent ? : "Il doit générer du texte pour décrire l'image, puis on cherche le texte. C'est une étape de trop pour du temps réel." 
-->

---

# Critères de Succès : Une évaluation scientifique

## **Hit@5** (Top-5 Accuracy)

<div class="center-img">

![width:900px](images/succes.png)

</div>

1.  **Technique** : Latence < 500ms.
2.  **Métier** : Validation experts > 80%.
3.  **Baseline** : Comparaison face à Mots-clés + Couleur.

<!--
Section 7 : Critères de Succès (Slide 7)

 La 'Star Metric' sur laquelle on jugera la réussite est le Hit@5.
 
 On commence par établir un test étalon avec une baseline analitique :
 Une simple recherche textuelle avec des tags + une correspondance de couleur, sur un échantillon d'entraînement.
 Et on évalue les prédictions de cette baseline.

 Puis on soumet le modèle au même échantillon, et on compare les résultats.
 
 Ainsi, à la question 'Est-ce que le produit recherché apparaît dans les 5 premiers résultats ?' la cible est d'atteindre 70% de pertinence technique.
 Mais surtout, il faut faire mieux que la baseline.
 Nous visons une amélioration statistiquement significative (+15 points).
 Enfin, le critère métier est crucial : un panel d'experts mode de chez Fashion-Insta devra valider 80% de recommandations.


💡 Antisèche (Q&A) :
• Pourquoi Hit@5 et pas Hit@1 ? : "Sur mobile, l'utilisateur voit facilement 4 à 6 produits. Si le bon est dedans, c'est gagné. Hit@1 est trop restrictif pour de la mode où le style est subjectif."

Pourquoi ces objectifs (70% / +15 pts / 80%) ?

- 70% (Performance Technique) : C'est le seuil de "confort utilisateur". En dessous, le moteur est perçu comme défaillant ; à 70%, il est jugé performant pour des requêtes mode souvent subjectives.
- +15 points (Gain vs Baseline) : Ce saut qualitatif justifie l'investissement IA. Une amélioration mineure ne rentabiliserait pas la complexité du modèle par rapport à une recherche SQL classique.
- 80% (Validation Experts) : L'œil humain juge la cohérence stylistique. Même si l'item n'est pas le bon (échec au Hit@5), la recommandation doit rester élégante et pertinente pour l'image de marque de Fashion-Insta.

La Baseline Analytique (Le Test Étalon)

- Méthode : Recherche par mots-clés (tags) couplée à un filtre de correspondance de couleur stricte (approche par règles métier sans IA).
- Rôle : Servir de point de comparaison "zéro" pour prouver la valeur ajoutée de l'IA.

Coûts et Mise en œuvre

- Technique : Faible (2-3 jours de dev). Utilisation de scripts Python simples pour automatiser le calcul sur l'échantillon.
- Métier : 1 à 2 journées de mobilisation du panel d'experts pour l'audit qualitatif.

• Qu'est-ce que la baseline ? : "C'est notre performance actuelle avec la recherche textuelle (TF-IDF) et la comparaison d'histogrammes de couleurs."
-->

---

# Planning & Ressources POC : Une équipe commando
<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/planning.png" width="900px" />
</div>

## Staffing & Budget
<div class="staff-grid">
  <div>
    <ul class="staff-list">
      <li class="staff-item">
        <span class="ico ico-black">👤</span>
        <span><strong>Data Scientist</strong> (100%)</span>
      </li>
      <li class="staff-item">
        <span class="ico ico-black">👤</span>
        <span><strong>Data Engineer</strong> (50%)</span>
      </li>
      <li class="staff-item">
        <span class="ico ico-black">👤</span>
        <span><strong>Tech Lead</strong> (20%)</span>
      </li>
      <li class="staff-item">
        <span class="ico ico-black">👤</span>
        <span><strong>MLOps</strong> (20%)</span>
      </li>
    </ul>
  </div>
  <div>
    <ul class="staff-list">
      <li class="staff-item">
        <span class="ico ico-gold">👤</span>
        <span><strong>VP Product</strong> (20%)</span>
      </li>
      <li class="staff-item">
        <span class="ico ico-gold">👤</span>
        <span><strong>CDP</strong> (20%)</span>
      </li>
      <li class="staff-item">
        <span class="ico ico-gold">👤</span>
        <span><strong>Experts Mode</strong> (10%)</span>
      </li>
    </ul>
  </div>
</div>

## **Budget POC Estimé :** ~13.7k€

<!--
Section 8 : Planning & Staffing (Slide 8)
 
 Pour tenir ce délai de 4 semaines, on utilise 4 ingés, en plus du VP et du CDP.
 
 Nous aurons besoin d'un Data Scientist à 100% pour le modèle, et d'un Data Engineer à 50% pour préparer les données. Le Tech Lead et le MLOps interviendront en support (20%) pour préparer l'architecture.
 Ces compétences ont été identifiées en interne, nous n'avons pas besoin de prestataires.
 Le coût de staffing pour ce POC est estimé à 13 700 €."



💡 Antisèche (Q&A) :
• A-t-on la disponibilité ? : "Oui, le planning a été pré-validé avec les managers d'équipe."
• Ingénieur IA Chef de Projet ? : "C'est moi-même (ou ressource interne), je suis compté dans l'effort mais mon coût est absorbé dans les frais de fonctionnement internes (selon la convention P11)." 

-->

---

# Architecture Cible : Scalabilité et Performance sur Azure

**Flux de données :**

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/archi.png" width="900px" />
</div>

<!--
Section 9 : Architecture Technique (Slide 9)

 L'architecture sera déployée sur Azure, notre partenaire Cloud, pour maintenir la compatibilité avec l'existant.
 C'est une architecture moderne et scalable.

1. L'image arrive depuis le smartphone via l'API.
2. Elle est transformée en vecteurs par Azure Machine Learning.
3. Le moteur Azure AI Search trouve les produits similaires, et la réponse est mise en cache par Redis pour économiser les calculs sur les résulats fréquents. Tout cela est sécurisé et hébergé en France.
4. L'avantage de cette architecture, c'est qu'elle est 'Serverless' : elle s'adapte automatiquement à la charge, qu'il y ait 10 ou 10 000 utilisateurs, c'est auto-scalable. Il faudra bien-sûr placer des alertes budgets, on verra ça plus tard dans la partie financière.



💡 Antisèche (Q&A) :
• Pourquoi Azure et pas AWS ? : "Fashion-Insta est déjà sur l'écosystème Microsoft. Cela facilite l'intégration (SSO, Sécurité, Facturation) et réduit le temps de setup."
• Redis ? : "C'est une mémoire cache ultra-rapide pour stocker les résultats fréquents et économiser des calculs."
-->

---

# Gouvernance Technique : Matrice RACI
*Rôle central du Tech Lead pour garantir la cohérence technique.*
| Domaine de Responsabilité | Tech Lead Data | Data Scientist | Data Engineer | MLOps |
| :--- | :---: | :---: | :---: | :---: |
| **Architecture & Gouvernance**<br>*(Design, Sécurité, Coûts, RGPD)* | **A** | C | C | C |
| **Data Pipelines & Search**<br>*(Ingestion Blob, Azure AI Search)* | **A** | C | **R** | I |
| **Cœur Algorithmique**<br>*(Entraînement, Optimisation)* | **A** | **R** | I | C |
| **Industrialisation**<br>*(Déploiement AML, API, Monitoring)* | **A** | C | C | **R** |

<!--
Section 10 : Rôles & Responsabilités (Slide 10)

 Pour garantir une exécution rapide et sans faille, on a clarifié qui fait quoi via cette matrice RACI.
 Le Data Scientist est responsable de la qualité du modèle (le cerveau).
 Le Data Engineer assure que les données arrivent bien (la tuyauterie).
 Le MLOps s'occupe de la mise en production (l'usine).
 Et le Tech Lead valide l'ensemble de l'architecture pour éviter la dette technique.
 
 Cette organisation décloisonne les équipes et responsabilise chacun sur son expertise."

Pour simplifier cette présentation, je me suis focalisé sur les 4 ingé IA, et les principales phases du POC.

R – Responsible (Réalisateur) : C'est la personne qui fait le travail. Elle exécute la tâche. (Exemple : l'informaticien qui configure Azure AI Search).
A – Accountable (Approbateur / Responsable) : C'est la personne qui rend des comptes. Elle valide le travail et s'assure qu'il est fait. Il ne peut y avoir qu'un seul "A" par tâche.
C – Consulted (Consulté) : Ce sont les personnes dont on a besoin de l'avis ou de l'expertise pour avancer. La communication est bidirectionnelle. (Exemple : les experts mode de Fashion-Insta pour la validation des recommandations).
I – Informed (Informé) : Ce sont les personnes que l'on tient au courant de l'avancement ou de la fin d'une tâche. La communication est unidirectionnelle. (Exemple : la direction financière pour le suivi des alertes budgets).


💡 Antisèche (Q&A) :
• Qui décide en cas de désaccord technique ? : "C'est le Tech Lead Data (Rôle 'Accountable' sur l'Architecture)."
• Le MLOps est-il nécessaire pour le POC ? : "Oui, à 20%, pour s'assurer que ce qu'on construit sera déployable ensuite. On prépare l'industrialisation dès le jour 1." 
-->

---

# Roadmap de Déploiement : De l'expérimentation à l'échelle

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/croissance.png" width="900px" />
</div>

<!--
Section 11 : Timeline (Slide 11)

 Le POC n'est que le départ. Voici la feuille de route.
 Mois 1 : Le POC dont nous parlons, pour valider la technique.
 Mois 2 à 4 : Si le POC est validé, le MVP (Produit Minimum Viable).
 C'est là qu'on connecte le système à l'App et au stock réel. On passe en production.
 Mois 5 et plus : Le Scale. On optimise, on encaisse la charge et on surveille la performance dans le temps, le drift,... C'est un déploiement progressif pour maîtriser les risques.


💡 Antisèche (Q&A) :
• Pourquoi 3 mois pour le MVP ? : "Il faut intégrer l'API au front-end mobile, gérer la sécurité, les tests de charge, et former le support client."
• Drift ? : "C'est la dérive du modèle. Si la mode change (été/hiver), l'IA doit être ré-entraînée. C'est prévu en phase Scale." 
-->

---

# Analyse Financière : Des coûts maîtrisés et validés
<div class="columns">
<div>

### CapEx (Investissement)
# 161.5k€
**Staffing sur 2 ans :**
<ul>
  <li>Data Scientist</li>
  <li>Engineer</li>
  <li>MLOps</li>
  <li>Tech LEAD</li>
</ul>
</div>
<div>

### OpEx (Azure & Run)
<p align="center">
  <img src="images/couts.png" width="500px" />
</p>
</div>
</div>
<br>

## **Total Investissement 2 ans :** ~292k€**
*(Basé sur Azure Pricing Calculator France Centre & TJM réels)*

<!--
Section 12 : Analyse Financière (Slide 12)

 Nous avons chiffré le projet sur 2 ans, sur la base des estimations du marketting.
 
 L'investissement initial de développement (CapEx) est de 161 500 €.
 Cela couvre le staffing de toute l'équipe du POC jusqu'au Scale.
 
 Les coûts de fonctionnement (OpEx), incluant l'infrastructure Azure et la maintenance humaine, sont très faibles au début et montent en puissance.
 
 Au total, sur 24 mois, le coût complet du projet est estimé à 292 000 €. Ces chiffres s'appuient sur les TJM réels de nos équipes et le calculateur officiel Azure.



💡 Antisèche (Q&A) :
• Le coût Azure semble faible ? : "Nous utilisons des instances managées et du serverless. On ne paie que ce qu'on consomme. Pour le POC, c'est à peine 230€."
• Maintenance Humaine ? : "Nous avons budgété 20% du temps d'un Data Scientist et d'un MLOps pour surveiller le modèle après le lancement." 
-->

---

# Rentabilité & ROI : Un projet autofinancé dès l'An 1
<div class="columns">
<div>
<h3 style="margin-top: 0;">Chiffres Clés</h3>
<ul style="list-style-type: none; padding: 0; text-align: center;">
  <li style="margin-bottom: 15px; font-size: 1.1em;">
    <strong>ROI 2 ans :</strong> <span style="color: #E65100; font-weight: 800;">220%</span>
  </li>
  <li style="margin-bottom: 15px; font-size: 1.1em;">
    <strong>Gains Est. :</strong> <span style="color: #2c3e50; font-weight: 800;">936k€</span>
  </li>
  <li style="margin-bottom: 15px; font-size: 1.1em;">
    <strong>Investissement :</strong> 292k€
  </li>
</ul>
</div>
<div>

<p align="center">
  <img src="images/roi.png" width="500px" />
</p>
</div>
</div>

<br>

## **Point Mort : 9 Mois** (Croisement des courbes Coûts Cumulés vs Gains Cumulés).

<!--
Section 13 : Rentabilité & ROI (Slide 13)

 Face à ces coûts, les gains sont significatifs.
 Avec 936k€ de revenus additionnels estimés sur 2 ans, le projet s'autofinance très vite.
 Le Retour sur Investissement (ROI) est de 220%.
 
 Le Point Mort (Break-even) est atteint au 9ème mois.
 Autrement dit : avant même la fin de la première année, le projet a remboursé son développement et commence à générer du profit net pour Fashion-Insta."
 
 Comme on est sur du serverless, le principal risque financier se situe sur un débordement de la durée pour la phase 2 (MVP), c'est la raison pour laquelle on a pris de la marge avec les 3 mois alloués.


💡 Antisèche (Q&A) :
• Et si on rate la cible marketing de moitié ? : "Le ROI reste positif (>100%). Le projet est très robuste financièrement."
• Quand commence-t-on à gagner de l'argent ? : "Dès le déploiement du MVP (Mois 4), les revenus rentrent. Ils couvrent le déficit initial au Mois 9." 
-->

---

# Risques & Conformité RGPD : Privacy by Design

<div class="rgpd-grid">

  <div class="rgpd-col">
    <img src="images/flou.png" class="rgpd-img">
    <div class="rgpd-title">Anonymisation à la<br>source</div>
    <div class="rgpd-text">Floutage automatique des visages + Crop vêtement.</div>
  </div>

  <div class="rgpd-col">
    <img src="images/passtockage.png" class="rgpd-img">
    <div class="rgpd-title">Zéro Persistance</div>
    <div class="rgpd-text">Aucune image brute conservée. Uniquement des vecteurs mathématiques.</div>
  </div>

  <div class="rgpd-col">
    <img src="images/souverain.png" class="rgpd-img">
    <div class="rgpd-title">Souveraineté</div>
    <div class="rgpd-text">Données isolées sur<br>Azure France.</div>
  </div>

</div>

## **Conformité totale :** Nous traitons des vêtements, pas des identités.

<!--
Section 14 : Conformité RGPD (Slide 14)

 Pour la sécurité et la conformité, nous appliquons le 'Privacy by Design'.
1. Zéro visage : Nous floutons automatiquement les visages avant analyse, et on crop sur les vetements pour éviter le bruit des fond d'image (noms de rues, etc..)
2. Zéro stockage sensible : Nous ne gardons pas les photos des utilisateurs. Nous les transformons en vecteurs (des suites de chiffres) qui sont irréversibles. On ne peut pas recréer la photo depuis le vecteur.
3. Souveraineté : Toutes les données restent sur nos instances Azure en France.

Pour le preprocessing (floutage et crop), il faudra développer un petit script python et faire appel à OpenCV (flou) et le modèle Yolov8. Tout ça sera fait pendant le POC.



💡 Antisèche (Q&A) :
• Utilisez-vous les photos pour entraîner l'IA ? : "Non, nous utilisons DeepFashion (dataset public) pour l'entraînement. Les photos clients servent uniquement à la recherche instantanée (inférence) et sont jetées ensuite."
• OpenAI a-t-il accès aux données ? : "Non, nous utilisons Azure OpenAI Service avec un contrat 'Enterprise' qui garantit que Microsoft n'utilise pas nos données pour ses modèles." 
-->

---

# Conclusion & Décision

<div class="concl-grid">

  <div>
    <div class="check-item">
      <img src="images/check.png" class="check-icon">
      <div class="check-text">
        <strong>Rentabilité Prouvée</strong><br>
        (ROI 220%)
      </div>
    </div>
    <div class="check-item">
      <img src="images/check.png" class="check-icon">
      <div class="check-text">
        <strong>Faisabilité Technique</strong><br>
        (Architecture Azure Scalable)
      </div>
    </div>
    <div class="check-item">
      <img src="images/check.png" class="check-icon">
      <div class="check-text">
        <strong>Sécurité Juridique</strong><br>
        (Privacy by Design)
      </div>
    </div>
  </div>

  <div class="validation-box">
    <h3 style="margin: 0 0 15px 0; color: #000; font-size: 1.1em; border: none; text-align: center;">
      Demande de validation :
    </h3>
    <p style="font-size: 1em; margin: 0 0 20px 0;">
      Budget POC (13.7k€ + Infra)
    </p>
    <p style="font-weight: 800; font-size: 1.1em; margin: 0;">
      Objectif : Lancement POC.
    </p>
  </div>

</div>

<div class="footer-logo-block">
  <img src="images/logofin.png" class="logo-fin">
</div>

<!--
Section 15 : Conclusion (Slide 15)

 Pour résumer : C'est un projet Rentable (ROI 220%),
 Réalisable (Technologie maîtrisée en 4 semaines)
 et Sûr (RGPD Compliant).
 
 L'équipe est prête, l'architecture est validée.
 Je sollicite aujourd'hui votre validation pour débloquer le budget de 13 700 € nécessaire au lancement du POC dès que possible. 
 
 Merci de votre attention, je suis à votre disposition pour vos questions."



💡 Antisèche (Q&A) :
• Quels sont les risques restants ? : "Le principal risque est la qualité des photos utilisateurs (trop sombres/floues). Le POC sert à mesurer ce risque précisément."
• Prochaine étape si Go ? : "Kick-off meeting lundi matin avec l'équipe Data pour lancer l'ingestion des données." 



💰 BUSINESS & ROI (Alicia)
"Vos gains (+14%) sont trop optimistes. Et si on fait que +2% ?"

✅ Réponse : "Le modèle est robuste car les coûts (OpEx) sont variables (Serverless). Si moins de trafic = moins de coûts Azure. Le point de rentabilité recule (de 9 à 20 mois) mais le projet reste bénéficiaire à terme."

"Intégration Mobile difficile (Dette technique) ?"

✅ Réponse : "Architecture API-First (découplée). L'app mobile ne fait qu'afficher un JSON. Buffer de 2 sprints prévu dans le planning MVP. Sécurité via Feature Flipping (désactivation à distance si bug)."

"Que se passe-t-il si l'IA ne trouve rien ?"

✅ Réponse : "Gestion par Seuil de similarité. Si score trop bas → Fallback (Repli) sur une recherche par catégorie/couleur ('Voici nos robes rouges populaires') pour sauver la vente."

🛠️ TECH & ARCHI (Denis)
"Pourquoi ResNet50 (CNN) et pas ViT (Transformer) ?"

✅ Réponse : "Priorité à la latence < 100ms sur mobile. ResNet est plus léger et mature. ViT est trop lourd pour le POC. Optimisation prévue : Quantification INT8 via format ONNX."

"DeepFashion (Studio) vs Photos Clients (Floues/Moches) ?"

✅ Réponse : "Problème de Domain Shift anticipé. Solution : Data Augmentation agressive pendant l'entraînement (ajout artificiel de bruit, flou, rotation, baisse luminosité)."

"Nouvelle collection chaque semaine : faut-il tout réentraîner ?"

✅ Réponse : "Non. Le modèle apprend le style, pas les produits. Nouveaux produits = Simple inférence (calcul vecteur) + Ajout dans l'index Azure AI Search. Coût négligeable, zéro downtime."

⚖️ RGPD & ÉTHIQUE (DPO)
"Floutage des visages : Où est-il fait ?"

✅ Réponse : "POC = Cloud (RAM éphémère) avec suppression immédiate et transit TLS 1.3. Cible MVP = Edge Computing (sur le téléphone via SDK ML Kit) pour que le visage ne sorte jamais."

"Biais du dataset (Mannequins minces uniquement) ?"

✅ Réponse : "Les Embeddings analysent le vêtement (texture/forme), pas le corps. Vigilance maintenue : pour le MVP, enrichissement du dataset avec des images plus inclusives/diversifiées."

"Microsoft (OpenAI) utilise-t-il nos données ?"

✅ Réponse : "Non. Contrat Azure OpenAI Service Enterprise : nos données sont isolées, restent en France, et ne servent pas à l'entraînement des modèles globaux."

🎩 POSTURE "CHEF DE PROJET"
Si question trop code/spécifique (ex: librairie exacte) :

🃏 Joker : "En tant que Lead, j'ai fixé la contrainte (ex: Quantification). J'ai délégué le choix de la librairie au MLOps expert de l'équipe pour garantir la compatibilité Azure."



"Et vous, Damien, où êtes-vous dans ce tableau ?", voici la réponse exacte :

"En tant qu'Ingénieur IA et Chef de Projet, je me situe au-dessus de cette matrice d'exécution technique.

Mon rôle est celui du Chef d'Orchestre (Project Governance) :

Je suis le lien entre le Métier (Alicia/Marketing) et cette équipe technique.

Je m'assure que le Tech Lead garantit la qualité du code (Accountable technique).

Je suis moi-même Accountable (Responsable final) du respect du planning, du budget et de la réponse au besoin métier.

Ce RACI détaille spécifiquement comment les experts techniques collaborent entre eux pour livrer les briques logicielles."

-->
