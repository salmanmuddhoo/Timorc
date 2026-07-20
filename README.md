# Timorc — Analyse des temps

Dashboard web pour analyser l'export Timorc **« Temps passé par personne »** (CSV).

**Aucune donnée n'est stockée ni transmise** : le fichier CSV est lu et analysé
entièrement dans le navigateur (JavaScript côté client, zéro backend, zéro
`localStorage`). Rechargez la page et tout disparaît.

## Utilisation

1. Ouvrez `index.html` dans un navigateur (double-clic suffit — aucun serveur requis),
   ou hébergez le fichier sur n'importe quel hébergement statique (GitHub Pages, etc.).
2. Glissez-déposez l'export CSV Timorc (« Temps passé par personne »).
3. Filtrez par période, intervenant, projet et catégorie.

## Format attendu

Export CSV Timorc avec séparateur `;`, encodage Windows‑1252 ou UTF‑8 (détection
automatique), et les colonnes : `Projet`, `Intervenant`, `Tâche`, `Jour`,
`Temps passé` (les lignes de sous-total sans `Jour` sont ignorées).

## Règles de classification

| Catégorie | Règle |
|---|---|
| **Non-productif** | projet commençant par `MAURITIUS9` (pilotage, recrutement, formation non liée à la prod…) |
| **Congé** | projet commençant par `ZZZ_NPR` (« PAS DE PRESTATION ») |
| **Productif** | tout le reste |

## Ce que montre le dashboard

- **KPI** : total saisi, productif, non-productif et congés (avec parts en %).
- **Répartition par intervenant** : barres empilées productif / non-productif / congé.
- **Tâches non-productives** : total équipe par tâche MAURITIUS9, et détail par
  intervenant — pour voir quelle tâche non-productive consomme le plus de temps.
- **Temps par projet** (hors congés) et **congés par intervenant**.
- **Évolution journalière** par catégorie.
- **Tableau de détail** (intervenant × projet × tâche) avec recherche, tri et
  export CSV.

Unité : jours (`1,00` = une journée). Thèmes clair et sombre.
