# FoodScan AI

Petit projet frontend pour analyser l'état des aliments à l'aide d'un modèle Teachable Machine et afficher les résultats sous forme de barres.

Fichiers principaux
- [index.html](index.html)
- [scanner.html](scanner.html)
- [css/reset.css](css/reset.css)
- [css/style_index.css](css/style_index.css)
- [css/style_landing.css](css/style_landing.css)
- [js/model-runner.js](js/model-runner.js) — contient la fonction exportée [`model-runner.setupModel`](js/model-runner.js)
- [js/bar-graph.js](js/bar-graph.js) — contient les fonctions exportées [`bar-graph.setupBarGraph`](js/bar-graph.js) et [`bar-graph.updateBarGraph`](js/bar-graph.js)

Démarrage rapide (serveur local)
1. Depuis la racine du projet, lancer un serveur simple :
   $ python3 -m http.server 8000
2. Ouvrir la page scanner dans le navigateur hôte :
   $BROWSER http://localhost:8000/scanner.html

Utilisation
- La page [scanner.html](scanner.html) charge les bibliothèques TFJS et Teachable Machine depuis les CDN.
- Le modèle Teachable Machine utilisé est défini ici : la constante `URL` dans [scanner.html](scanner.html). Remplacez-la par l'URL de votre modèle si nécessaire.
- Flux principal :
  - [`bar-graph.setupBarGraph`](js/bar-graph.js) récupère la metadata et construit les barres.
  - [`model-runner.setupModel`](js/model-runner.js) charge le modèle et écoute l'upload d'image.
  - Lorsque l'image est uploadée, [`bar-graph.updateBarGraph`](js/bar-graph.js) met à jour l'affichage.

Points d'attention
- Les scripts s'appuient sur des imports de modules ES (`type="module"`). Servir via HTTP est recommandé (pas d'ouverture directe file://).
- TFJS inclus est une version ancienne dans [scanner.html](scanner.html) — mettre à jour si besoin.
- Le preview d'image est géré dans [scanner.html](scanner.html) (élément `#selectedImage`) tandis que la prédiction est réalisée dans [js/model-runner.js](js/model-runner.js).

Contribuer
- Modifier le modèle : mettre à jour la variable `URL` dans [scanner.html](scanner.html).
- Ajouter des styles : éditer les fichiers dans `css/`.
- Ajouter des visualisations : éditer `js/bar-graph.js`.

Licence
- Projet personnel / prototype. Ajouter une licence si nécessaire.
