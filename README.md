# ¡Palabras! — Mi barrio en español

Application d'espagnol pour le collège (5e, 4e, 3e), par BROT2YOU. Gratuite, sans compte, progression enregistrée sur l'appareil.

## Déploiement (GitHub Pages)

1. Supprimer de l'ancien dépôt tous les anciens fichiers du dossier `assets/` (ceux aux noms cassés : `accueil-barrio-pop.png. .PNG`, `logo-palabras.png..PNG`, `planche-icones.png.png`…).
2. Déposer à la racine `index.html`, `README.md`, `.nojekyll` et le dossier `assets/`.
3. Aucune autre dépendance (seules les polices Google Fonts sont chargées, avec repli système).

## Contenu

- 13 lieux répartis sur 3 rues (Calle del Sol 5e, Calle de las Flores 4e, Paseo de la Luna 3e)
- 6 voisins guides (Madrid, Mexico, Séville, Buenos Aires, Bogotá, Lima), chacun avec l'accent de son pays si la voix existe sur l'appareil
- 282 mots avec phrase d'exemple traduite
- 13 épisodes dialogués (8 répliques + 3 questions de compréhension)
- 13 fiches de grammaire (explication, tableau, exemples, 6 exercices), une par lieu, en progression spiralaire
- 7 jeux : FR → ES, ES → FR, écoute, écriture (avec clavier d'accents), article, phrase à remettre dans l'ordre, défi mélangé
- Révisions espacées (6 cases : 1, 2, 4, 8, 16 jours), cartes de lieux (argent / or), cartes culture des voisins à débloquer
- Réglages d'accessibilité : police Lexend, taille du texte, espacement, vitesse de la voix

## Modifier le contenu

Tout le contenu est dans le bloc `<script type="application/json" id="palabras-data">` de `index.html`.

- **Ajouter un mot** : l'ajouter **à la fin** de la liste `palabras` du lieu (l'identifiant d'un mot est sa position ; insérer au milieu décalerait la progression des élèves). Format : `["el mot", "traduction", "emoji", "Phrase d'exemple.", "Traduction de l'exemple."]`. Pour un nom qui ne doit pas aller dans le jeu des articles (comme *el agua*), ajouter `{"nog": 1}` en 6e élément.
- **Variantes** : séparer par ` / ` (`"el coche / el auto"`) ; toutes les formes sont acceptées dans le jeu d'écriture.
- **Ressources** : les capsules culturelles sont rédigées dans l'appli ; on peut y ajouter des liens vers des documents authentiques.

## Remplacer les illustrations

Déposer un nouveau fichier **avec le même nom** dans `assets/` :

- `p-mateo.webp`, `p-valentina.webp`, `p-diego.webp`, `p-lucia.webp`, `p-pablo.webp`, `p-sofia.webp` : portraits (carrés, ~300 px)
- `i-*.webp` : icônes des lieux et menus (carrées, ~160 px)
- `u-*.webp` : boutons d'interface
- `accueil.webp` (paysage), `accueil-mobile.webp` (portrait), `logo.webp` (fond transparent)

## Audio

L'appli utilise la voix espagnole de l'appareil si elle existe. Sinon, elle bascule sur une voix espagnole en ligne (service de synthèse de Google Traduction, non officiel, connexion nécessaire). Elle ne lit jamais l'espagnol avec une voix française : si aucune des deux n'est disponible, elle affiche comment installer une voix espagnole. Réglages : Source de la voix (Automatique / Appareil / En ligne) et bouton Tester la voix.

## Technique

Un seul fichier HTML, JavaScript ES5 (compatible anciens iPad/iPhone), données en JSON, `localStorage` (clé `palabras-v3`), export / import de la progression en fichier JSON.
