# Règles du dépôt (dsa)

Sources : `labo-info-pass` (`AGENTS.md`), commits / templates de `labo-tech-info-2`, `labo-tech-info-3`, `tech-info-1`, `methodo-algo`, `outils-info-ia`.

## Quiz (strict)

1. **Pas de gras sur les réponses** — choix (liste + récap) en graisse normale, y compris `<strong>` / `<b>` imbriqués ; idem feedback / verdict du débrief. Stem (énoncé) : emphase UI autorisée.
2. **Ordre des réponses aléatoire** — `shuffleAllOptions()` (ou équivalent) au chargement et au reset ; scoring sur `question.correct` (ids stables `value`), pas la position ni la lettre affichée.
3. **Lettres A–D = ordre visuel uniquement** — dans les données, `label` **sans** préfixe « A. » / « B. ». À l'affichage, toujours montrer `A.` `B.` `C.` `D.` selon la position après shuffle (`String.fromCharCode(65 + index)`).
4. **Titres d'onglet / H1 quiz** — format `Séance N — Quiz`.

## Titres Pages (strict)

5. **Onglet exercices** — `Séance N — Exercices` (via `page_title` dans `.github/workflows/deploy.yml`).
6. **Onglet accueil** — `DSA — ISIB` (em dash).
7. **Marp `title` des slides** — `Séance N — <thème>` ; le `header` garde la marque du cours (`DSA — Séance N …`).

## Contenu quiz (quand on remplit pour de vrai)

8. **~10 QCM** par séance une fois le quiz réel rédigé.
9. **Pas d'indice « leading »** dans l'énoncé qui donne la réponse.
10. **Mauvaises réponses en rouge** (`--color-error`) : modèle tech-info-1 / methodo-algo (toutes questions visibles). Si on reprend le template une-question-à-la-fois (labo-info-pass / LTI2), ne pas diverger de ce template sans décision explicite.

## Slides (style)

11. **Pas de tirets cadratins « IA » dans la prose** des slides (séparateurs de propositions) — préférer virgules / parenthèses / points-virgules ; garder `—` dans titres / headers / plages numériques.

## Nommage des fichiers

12. **Fichiers** : `cours_seance_NN.md`, `exercices_seance_NN.md`, `quiz_seance_NN.html` (underscores, pas de tiret long dans le nom de fichier). Les tirets longs (`—`) sont réservés aux **titres de pages** et en-têtes Marp.

Tout nouveau `quiz_seance_*.html` / page générée doit respecter 1–7 et 12 ; 8–11 dès qu'on écrit du contenu pédagogique.
