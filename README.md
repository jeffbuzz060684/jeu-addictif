# jeu-addictif

**Néon Dodge** — un jeu d'arcade web en un seul fichier `index.html` : esquive les météores qui tombent, enchaîne les *near-miss* pour faire grimper ton multiplicateur de combo, et bats ton record. Zéro dépendance, zéro asset externe : graphismes néon, nébuleuse, particules, ondes de choc, sons et musique sont générés en direct par le navigateur (canvas 2D + WebAudio).

## Jouer

- **En ligne** : [https://jeffbuzz060684.github.io/jeu-addictif/](https://jeffbuzz060684.github.io/jeu-addictif/) (déployé automatiquement par GitHub Pages à chaque push sur `main`).
- **En local** : ouvre simplement `index.html` dans n'importe quel navigateur moderne.
- **Icône bureau** : dans Chrome/Edge, glisse l'icône 🔒 de la barre d'adresse sur le bureau pour créer un raccourci (avec la favicon du jeu).

## Contrôles

| Action | Contrôles |
|---|---|
| Se déplacer | `←` `→` ou `A` `D`, souris, ou toucher (glisser) |
| Démarrer / rejouer | `Espace`, `Entrée`, clic ou tap |
| Pause / reprendre | `P` ou bouton ⏸ en haut à droite |
| Son on/off | `M` ou bouton ♪ en haut à droite |
| Recommencer à tout moment | `R` |

## Règles

- Les météores tombent de plus en plus vite et nombreux : **nouveau niveau toutes les 12 s**, dérive sinusoïdale à partir du niveau 5, météores rapides à partir du niveau 4. La musique s'intensifie avec le niveau.
- Un météore qui te frôle = **near-miss** : +points et **combo +1**. Tous les 4 combos, le **multiplicateur augmente** (jusqu'à ×8). Tous les 8 combos : **bonus de série** « SÉRIE +… ».
- Le score augmente avec le temps de survie × multiplicateur.
- Power-ups : **B** bouclier (absorbe un impact), **R** ralenti (4 s), **S** points bonus instantanés.
- Un impact sans bouclier = game over. L'écran de fin affiche tes stats (temps, near-miss, meilleur combo, niveau).
- Persistance locale (`localStorage`) : record, meilleur combo, nombre de parties.

## Technique

- Un seul fichier `index.html` : canvas 2D + `requestAnimationFrame`, calques pré-rendus (nébuleuse, vignette, scanlines, sprites de glow), rendu additif (`lighter`) pour les particules/ondes de choc.
- Sons et musique : WebAudio (oscillateurs + bruit filtré), aucun fichier audio.
- Favicon SVG embarquée (data URI).
- Responsive, tactile, pause automatique quand l'onglet est caché.
- Déploiement : workflow GitHub Actions `.github/workflows/pages.yml` (branche `main`).

## Personnaliser

Toutes les constantes de gameplay sont lisibles en haut du `<script>` de `index.html` : vitesse/intervalle des météores, seuil de near-miss, cap du combo (`Math.min(8, …)`), bonus de série (`combo % 8`), durées des power-ups, palette de couleurs…
