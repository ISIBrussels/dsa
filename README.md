# Algorithmique et Structures de Données (DSA)

Dépôt du cours **Algorithmique et Structures de Données** (DSA, Master 1 Info) à l'ISIB - HE2B.

- **Durée totale** : 42 h
- **Organisation** : 14 séances de 3 h
- **Format** : cours magistral, démo live coding, exercices pratiques (Python)
- **Examen** : oral type entretien technique (25 min)

## Accès rapide aux contenus

- Landing page GitHub Pages : [https://isibrussels.github.io/dsa/](https://isibrussels.github.io/dsa/)  
  *(dépôt : [`ISIBrussels/dsa`](https://github.com/ISIBrussels/dsa))*
- Slides de cours, quiz et exercices : liens ci-dessous

## Plan des séances

| Séance | Durée | Thème |
| :---: | :---: | --- |
| 1 | 3 h | Complexité, méthode d'entretien, tableaux et hash |
| 2 | 3 h | Récursivité et diviser pour régner |
| 3 | 3 h | Two pointers, sliding window, prefix sums |
| 4 | 3 h | Listes chaînées, piles, files |
| 5 | 3 h | Tris et recherche avancée |
| 6 | 3 h | Arbres binaires et parcours |
| 7 | 3 h | Arbres binaires de recherche (BST) et équilibrage |
| 8 | 3 h | Tas, files de priorité, Tries |
| 9 | 3 h | Représentations et parcours de graphes |
| 10 | 3 h | Tri topologique et Union-Find |
| 11 | 3 h | Plus courts chemins |
| 12 | 3 h | Programmation dynamique (1/2) |
| 13 | 3 h | Programmation dynamique (2/2), glouton, backtracking |
| 14 | 3 h | Synthèse et Problem Solving libre |

## Séances

- **Séance 1 — Complexité, méthode d'entretien, tableaux et hash** : [Cours](docs/seances/01/cours_seance_01.md) · [Quiz](docs/seances/01/quiz_seance_01.html) · [Exercices](docs/seances/01/exercices_seance_01.md)
- **Séance 2 — Récursivité et diviser pour régner** : [Cours](docs/seances/02/cours_seance_02.md) · [Quiz](docs/seances/02/quiz_seance_02.html) · [Exercices](docs/seances/02/exercices_seance_02.md)
- **Séance 3 — Two pointers, sliding window, prefix sums** : [Cours](docs/seances/03/cours_seance_03.md) · [Quiz](docs/seances/03/quiz_seance_03.html) · [Exercices](docs/seances/03/exercices_seance_03.md)
- **Séance 4 — Listes chaînées, piles, files** : [Cours](docs/seances/04/cours_seance_04.md) · [Quiz](docs/seances/04/quiz_seance_04.html) · [Exercices](docs/seances/04/exercices_seance_04.md)
- **Séance 5 — Tris et recherche avancée** : [Cours](docs/seances/05/cours_seance_05.md) · [Quiz](docs/seances/05/quiz_seance_05.html) · [Exercices](docs/seances/05/exercices_seance_05.md)
- **Séance 6 — Arbres binaires et parcours** : [Cours](docs/seances/06/cours_seance_06.md) · [Quiz](docs/seances/06/quiz_seance_06.html) · [Exercices](docs/seances/06/exercices_seance_06.md)
- **Séance 7 — Arbres binaires de recherche (BST) et équilibrage** : [Cours](docs/seances/07/cours_seance_07.md) · [Quiz](docs/seances/07/quiz_seance_07.html) · [Exercices](docs/seances/07/exercices_seance_07.md)
- **Séance 8 — Tas, files de priorité, Tries** : [Cours](docs/seances/08/cours_seance_08.md) · [Quiz](docs/seances/08/quiz_seance_08.html) · [Exercices](docs/seances/08/exercices_seance_08.md)
- **Séance 9 — Représentations et parcours de graphes** : [Cours](docs/seances/09/cours_seance_09.md) · [Quiz](docs/seances/09/quiz_seance_09.html) · [Exercices](docs/seances/09/exercices_seance_09.md)
- **Séance 10 — Tri topologique et Union-Find** : [Cours](docs/seances/10/cours_seance_10.md) · [Quiz](docs/seances/10/quiz_seance_10.html) · [Exercices](docs/seances/10/exercices_seance_10.md)
- **Séance 11 — Plus courts chemins** : [Cours](docs/seances/11/cours_seance_11.md) · [Quiz](docs/seances/11/quiz_seance_11.html) · [Exercices](docs/seances/11/exercices_seance_11.md)
- **Séance 12 — Programmation dynamique (1/2)** : [Cours](docs/seances/12/cours_seance_12.md) · [Quiz](docs/seances/12/quiz_seance_12.html) · [Exercices](docs/seances/12/exercices_seance_12.md)
- **Séance 13 — Programmation dynamique (2/2), glouton, backtracking** : [Cours](docs/seances/13/cours_seance_13.md) · [Quiz](docs/seances/13/quiz_seance_13.html) · [Exercices](docs/seances/13/exercices_seance_13.md)
- **Séance 14 — Synthèse et Problem Solving libre** : [Cours](docs/seances/14/cours_seance_14.md) · [Quiz](docs/seances/14/quiz_seance_14.html) · [Exercices](docs/seances/14/exercices_seance_14.md)

## Structure du dépôt

Alignée sur les dépôts `methodo-algo`, `tech-info-1` et `labo-tech-info-*` :

- `docs/index.md` — page d'accueil du site GitHub Pages
- `docs/seances/NN/` — contenu de chaque séance (`cours_seance_NN.md` Marp, quiz HTML, exercices)
- `docs/themes/` — thème Marp
- `.github/workflows/deploy.yml` — build Marp + déploiement Pages
- `AGENTS.md` — règles du dépôt (quiz, titres, tirets)
- `private-notes/` — notes personnelles (ignorées par git)
