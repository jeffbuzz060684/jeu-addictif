# jeu-addictif


Un jeu d'arcade web **addictif** en un seul fichier HTML : esquive les météores qui tombent, enchaîne les *near-miss* pour faire grimper ton multiplicateur de combo, et bats ton record. Zéro dépendance, zéro asset externe — tout (graphismes néon, particules, screen shake, musiques et effets sonores) est généré en direct par le navigateur.

## Jouer

Ouvre simplement `index.html` dans n'importe quel navigateur moderne (double-clic suffit), sur ordinateur ou mobile. Aucune installation, aucun serveur requis.

Pour le mettre en ligne gratuitement : active **GitHub Pages** sur ce dépôt (Settings → Pages → branche `main`, dossier `/root`), puis ouvre l'URL fournie.

## Comment jouer

| Action | Contrôles |
|---|---|
| Se déplacer | `←` `→` ou `A` `D`, souris, ou toucher (glisser) |
| Démarrer / rejouer | `Espace`, `Entrée`, clic ou tap |
| Pause / reprendre | `P` ou bouton ⏸ en haut à droite |
| Son on/off | `M` ou bouton ♪ en haut à droite |
| Recommencer à tout moment | `R` |

## Règles

- Les météores tombent de plus en plus vite et de plus en plus nombreux : **un nouveau niveau toutes les 12 secondes**.
- Un météore qui te frôle sans te toucher = **near-miss** : points bonus et **combo +1**. Tous les 4 combos, ton **multiplicateur augmente** (jusqu'à ×8).
- Le score augmente avec le temps de survie, multiplié par ton combo.
- Power-ups qui tombent :
  - **B (bleu)** : bouclier — absorbe un impact.
  - **R (violet)** : ralenti — le temps ralentit pendant 4 s.
- Un seul impact (sans bouclier) = game over. Le record est sauvegardé localement (`localStorage`).

## Technique

- Un seul fichier `index.html` : HTML + CSS + JS inline, canvas 2D, `requestAnimationFrame`.
- Sons et musique : WebAudio (oscillateurs + bruit blanc), générés sans fichier audio.
- Record persistant via `localStorage`.
- Responsive : le canvas s'adapte à la fenêtre, tactile supporté.

## Personnaliser

Toutes les constantes de gameplay sont regroupées et lisibles dans le `<script>` de `index.html` : vitesse des météores (`150 + level * 26`), intervalle d'apparition (`430 - level * 30`), seuil de near-miss, cap du combo (`Math.min(8, ...)`), durées des power-ups, palette de couleurs, etc.
