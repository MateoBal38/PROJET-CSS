# README de rendu — Projet noté — Site vitrine d'un événement

## Groupe

| | |
|---|---|
| Nom du groupe | Baseline Conf |
| Membres (et rôle référent) | Mateo BAL (seul, tous les rôles) |
| Événement / thème | Conférence tech — « Baseline Conf », conférence CSS fictive, Lyon, 18-19 mars 2027 |
| Lien du dépôt Git | https://github.com/MateoBal38/PROJET-CSS |
| Convention de nommage | BEM : `.bloc`, `.bloc__element`, `.bloc--variante` ; utilitaires préfixés `u-` |

## Localisation des exigences

| Exigence | Élément attendu | Fichier:ligne | Commentaire (ce que ça fait, pourquoi) |
|---|---|---|---|
| 1. Architecture | Déclaration de l'ordre des `@layer` | `css/main.css:16` | Ordre déclaré une seule fois, avant les `@import`. |
| 1. Architecture | Tokens primitifs | `css/tokens.css:23` | Palette oklch, espacements, rayons, durées, polices. |
| 1. Architecture | Tokens sémantiques | `css/tokens.css:78` | Rôles (`--color-surface`, `--color-accent`…), seuls utilisés par les composants. |
| 1. Architecture | Nesting natif (exemple représentatif) | `css/components.css:473` | `.card` : `&:hover`, `@media` imbriqué, éléments `& .card__…` (3 niveaux max). |
| 2. Mise en page | `grid-template-areas` (mobile → desktop) | `css/layout.css:112` | Programme : `"titre" "jour1" "jour2"` devient `"titre titre" "jour1 jour2"` à 48rem. |
| 2. Mise en page | `subgrid` | `css/layout.css:155`, `css/components.css:476` | Les cartes intervenants partagent les lignes de la grille : image, titre, bio et lien sont alignés. |
| 2. Mise en page | Flexbox pour un composant | `css/layout.css:49`, `css/components.css:85` | En-tête et navigation en Flexbox avec `gap` et `flex-wrap`. |
| 3. Responsive | Première media query mobile-first | `css/layout.css:120` | `@media (width >= 48rem)`. |
| 3. Responsive | Typographie fluide `clamp()` | `css/tokens.css:121` | Tailles de texte et espacements de section en `clamp()`. |
| 3. Responsive | Container query (`container-type` + `@container`) et ses 2 contextes | `css/layout.css:174`, `css/components.css:575` ; contextes `index.html:329` et `index.html:372` | L'offre est empilée dans la grille et passe sur 3 colonnes dans le bandeau pleine largeur. |
| 3. Responsive | Test 320 px sans défilement horizontal (correctif principal) | `css/reset.css:43` | `fieldset { min-inline-size: 0 }` : la bascule de thème débordait. |
| 4. Sélecteurs | `:has()` pertinent | `css/components.css:637` | L'offre qui contient un badge est mise en avant automatiquement. |
| 4. Sélecteurs | `:is()` / `:where()` | `css/base.css:37`, `css/components.css:102` | `:where()` (spécificité nulle) sur les titres ; `:is()` factorise `:hover` et `:focus-visible`. |
| 5. Thème | `light-dark()` / `prefers-color-scheme` + `color-scheme` | `css/tokens.css:83` | `color-scheme: light dark` + `light-dark()` dans les tokens sémantiques. |
| 5. Thème (bonus technique) | Bascule CSS-only | `css/tokens.css:145` | Radios Auto / Clair / Sombre + `:root:has(#theme-dark:checked)`. |
| 6. Animations | Transition n°1 | `css/components.css:181` | Bouton : couleur + léger soulèvement. |
| 6. Animations | Transition n°2 | `css/components.css:491` | Carte : bordure + soulèvement au survol et au focus. |
| 6. Animations | `@keyframes` | `css/components.css:24` | `rise-in` : apparition du hero au chargement. |
| 6. Animations | `prefers-reduced-motion` | `css/components.css:182` | Les mouvements ne sont écrits que dans `no-preference` : rien ne bouge et rien ne reste invisible sinon. |
| 6. Animations (bonus technique) | Scroll-driven (`@supports`), View Transitions, `@starting-style`/popover… | `css/components.css:754` | `animation-timeline: view()` dans `@supports`. |
| 7. Accessibilité | Landmarks + hiérarchie de titres | `index.html:24` | header, nav, main, footer ; un seul h1 (`index.html:63`) ; h1 → h2 → h3 → h4. |
| 7. Accessibilité | `:focus-visible` | `css/base.css:95` | Anneau de 3px sur tous les éléments interactifs. |
| 7. Accessibilité | Contrastes AA vérifiés (outil + paires de couleurs testées, 2 thèmes) | `css/tokens.css:78` | Ratios calculés par script, 2 thèmes : texte/fond 18,6:1, texte secondaire ≥ 7:1, accent ≥ 5,5:1, bouton ≥ 6:1. |
| 7. Accessibilité | Images avec `alt` | `index.html:245` | `alt` descriptif sur chaque portrait ; décors en `aria-hidden`. |
| 8. Qualité | Résultat du validateur W3C | — | À COMPLÉTER |
| 8. Qualité | `!important` (aucun, ou utilitaire justifié) | — | Aucun `!important`. |

## Bonus technique revendiqué

| Fonctionnalité | Fichier:ligne | Explication (et repli prévu pour les navigateurs qui ne la gèrent pas) |
|---|---|---|
| Bascule de thème CSS-only | `css/tokens.css:145` | Le radio coché change `color-scheme` sur `:root`, donc tous les `light-dark()` basculent ; « Auto » suit le système. |
| Animation pilotée par le scroll | `css/components.css:754` | Dans `@supports` : Firefox ignore le bloc et affiche le contenu normalement. |

## JavaScript (facultatif, ≤ 20 lignes)

Aucun JavaScript.

## Déclaration d'usage d'outils d'IA

| Outil | Pour quoi faire (textes, explication d'une erreur, revue…) | Parties du code concernées |
|---|---|---|
| Claude Code | Review du code et coordination de la syntaxe | Tout le projet |
## Qui a fait quoi

| Membre | Principales contributions |
|---|---|
| Mateo BAL | Projet réalisé seul |

## Crédits

- Illustrations : SVG créés pour le projet (`img/`).
- Polices : Space Grotesk et JetBrains Mono, licence SIL Open Font License, via Google Fonts.
