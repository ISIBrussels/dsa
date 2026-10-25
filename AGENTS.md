# Règles du dépôt (dsa)

Sources : `labo-info-pass` (`AGENTS.md`), commits / templates de `labo-tech-info-2`, `labo-tech-info-3`, `tech-info-1`, `methodo-algo`, `outils-info-ia`.

## Quiz (strict)

1. **Pas de gras sur les réponses** — choix (liste + récap) en graisse normale, y compris `<strong>` / `<b>` imbriqués ; idem feedback / verdict du débrief. Stem (énoncé) : emphase UI autorisée.
2. **Ordre des réponses aléatoire** — `shuffleAllOptions()` (ou équivalent) au chargement et au reset ; scoring sur `question.correct` (ids stables `value`), pas la position ni la lettre affichée.
3. **Lettres A–D = ordre visuel uniquement** — dans les données, `label` **sans** préfixe « A. » / « B. ». À l'affichage, toujours montrer `A.` `B.` `C.` `D.` selon la position après shuffle (`String.fromCharCode(65 + index)`).
4. **Titres d'onglet / H1 quiz** — format `Séance N — Quiz`.

## Titres Pages (strict)

5. **Onglet exercices** — `Séance N — Exercices` (via `page_title` dans `.github/workflows/deploy.yml`).
6. **Onglet accueil** — `DSA — ISIB` (em dash). Long course title stays in body H1 only. Marp `header` keeps short `DSA — Séance N …`.
7. **Marp `title` des slides** — `Séance N — <thème>` ; le `header` garde la marque du cours (`DSA — Séance N …`).

## Contenu quiz (quand on remplit pour de vrai)

8. **~10 QCM** par séance une fois le quiz réel rédigé.
9. **Pas d'indice « leading »** dans l'énoncé qui donne la réponse.
10. **Mauvaises réponses en rouge** (`--color-error`) : modèle tech-info-1 / methodo-algo (toutes questions visibles). Si on reprend le template une-question-à-la-fois (labo-info-pass / LTI2), ne pas diverger de ce template sans décision explicite.

## Slides (style)

11. **Pas de tirets cadratins « IA » dans la prose** des slides (séparateurs de propositions) — préférer virgules / parenthèses / points-virgules ; garder `—` dans titres / headers / plages numériques.

## Terminologie (strict)

12. **Franglais CS / industrie** — garder en **anglais** les termes techniques informatiques et d'industrie dans la prose française (titres, thèmes, objectifs, exemples) : *heap*, *queue*, *stack*, *linked list*, *sliding window*, *coding interview*, *Two Sum*, *BFS* / *DFS*, *dynamic programming*, *greedy*, *topological sort*, *shortest paths*, *hash table*, etc. Italique à la manière des siblings (`tech-info-1`) quand le terme est enchâssé dans une phrase française. **Garder le français** pour le cadrage pédagogique : séance, objectifs, consignes, structure d'évaluation, formulations de cours. Ne pas retraduire un terme anglais déjà installé.

## Nommage des fichiers

13. **Fichiers** : `cours_seance_NN.md`, `exercices_seance_NN.md`, `quiz_seance_NN.html` (underscores, pas de tiret long dans le nom de fichier). Les tirets longs (`—`) sont réservés aux **titres de pages** et en-têtes Marp.

Tout nouveau `quiz_seance_*.html` / page générée doit respecter 1–7, 12 et 13 ; 8–11 dès qu'on écrit du contenu pédagogique.
