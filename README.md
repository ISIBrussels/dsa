# Algorithmique & Structure de Données

Dépôt du cours **Algorithmique & Structure de Données** (DSA, Master 1 Info) à l'ISIB - HE2B.

- **Durée totale** : 42 h
- **Organisation** : 14 séances de 3 h
- **Format** : cours magistral, démo live coding, exercices pratiques (Python)
- **Évaluation** : oral façon *coding interview* (question technique de code)

## Accès rapide aux contenus

- Landing page GitHub Pages : [https://isibrussels.github.io/dsa/](https://isibrussels.github.io/dsa/)  
  *(dépôt : [`ISIBrussels/dsa`](https://github.com/ISIBrussels/dsa))*
- Slides de cours, quiz et exercices : liens ci-dessous

## Plan des séances

| Séance | Durée | Thème |
| :---: | :---: | --- |
| 1 | 3 h | Complexité, méthode *coding interview*, tableaux et *hash* |
| 2 | 3 h | Récursivité et *divide and conquer* |
| 3 | 3 h | *Two pointers*, *sliding window*, *prefix sums* |
| 4 | 3 h | *Linked lists*, *stacks*, *queues* |
| 5 | 3 h | *Sorting* et recherche avancée |
| 6 | 3 h | *Binary trees* et parcours |
| 7 | 3 h | *BST* et équilibrage |
| 8 | 3 h | *Heaps*, *priority queues*, Tries |
| 9 | 3 h | Représentations et parcours de graphes |
| 10 | 3 h | *Topological sort* et Union-Find |
| 11 | 3 h | *Shortest paths* |
| 12 | 3 h | *Dynamic programming* (1/2) |
| 13 | 3 h | *Dynamic programming* (2/2), *greedy*, backtracking |
| 14 | 3 h | Synthèse et *Problem Solving* libre |

## Séances

- **Séance 1 — Complexité, méthode *coding interview*, tableaux et *hash*** : [Cours](docs/seances/01/cours_seance_01.md) · [Quiz](docs/seances/01/quiz_seance_01.html) · [Exercices](docs/seances/01/exercices_seance_01.md)
- **Séance 2 — Récursivité et *divide and conquer*** : [Cours](docs/seances/02/cours_seance_02.md) · [Quiz](docs/seances/02/quiz_seance_02.html) · [Exercices](docs/seances/02/exercices_seance_02.md)
- **Séance 3 — *Two pointers*, *sliding window*, *prefix sums*** : [Cours](docs/seances/03/cours_seance_03.md) · [Quiz](docs/seances/03/quiz_seance_03.html) · [Exercices](docs/seances/03/exercices_seance_03.md)
- **Séance 4 — *Linked lists*, *stacks*, *queues*** : [Cours](docs/seances/04/cours_seance_04.md) · [Quiz](docs/seances/04/quiz_seance_04.html) · [Exercices](docs/seances/04/exercices_seance_04.md)
- **Séance 5 — *Sorting* et recherche avancée** : [Cours](docs/seances/05/cours_seance_05.md) · [Quiz](docs/seances/05/quiz_seance_05.html) · [Exercices](docs/seances/05/exercices_seance_05.md)
- **Séance 6 — *Binary trees* et parcours** : [Cours](docs/seances/06/cours_seance_06.md) · [Quiz](docs/seances/06/quiz_seance_06.html) · [Exercices](docs/seances/06/exercices_seance_06.md)
- **Séance 7 — *BST* et équilibrage** : [Cours](docs/seances/07/cours_seance_07.md) · [Quiz](docs/seances/07/quiz_seance_07.html) · [Exercices](docs/seances/07/exercices_seance_07.md)
- **Séance 8 — *Heaps*, *priority queues*, Tries** : [Cours](docs/seances/08/cours_seance_08.md) · [Quiz](docs/seances/08/quiz_seance_08.html) · [Exercices](docs/seances/08/exercices_seance_08.md)
- **Séance 9 — Représentations et parcours de graphes** : [Cours](docs/seances/09/cours_seance_09.md) · [Quiz](docs/seances/09/quiz_seance_09.html) · [Exercices](docs/seances/09/exercices_seance_09.md)
- **Séance 10 — *Topological sort* et Union-Find** : [Cours](docs/seances/10/cours_seance_10.md) · [Quiz](docs/seances/10/quiz_seance_10.html) · [Exercices](docs/seances/10/exercices_seance_10.md)
- **Séance 11 — *Shortest paths*** : [Cours](docs/seances/11/cours_seance_11.md) · [Quiz](docs/seances/11/quiz_seance_11.html) · [Exercices](docs/seances/11/exercices_seance_11.md)
- **Séance 12 — *Dynamic programming* (1/2)** : [Cours](docs/seances/12/cours_seance_12.md) · [Quiz](docs/seances/12/quiz_seance_12.html) · [Exercices](docs/seances/12/exercices_seance_12.md)
- **Séance 13 — *Dynamic programming* (2/2), *greedy*, backtracking** : [Cours](docs/seances/13/cours_seance_13.md) · [Quiz](docs/seances/13/quiz_seance_13.html) · [Exercices](docs/seances/13/exercices_seance_13.md)
- **Séance 14 — Synthèse et *Problem Solving* libre** : [Cours](docs/seances/14/cours_seance_14.md) · [Quiz](docs/seances/14/quiz_seance_14.html) · [Exercices](docs/seances/14/exercices_seance_14.md)

## Structure du dépôt

Alignée sur les dépôts `methodo-algo`, `tech-info-1` et `labo-tech-info-*` :

- `docs/index.md` — page d'accueil du site GitHub Pages
- `docs/seances/NN/` — contenu de chaque séance (`cours_seance_NN.md` Marp, quiz HTML, exercices)
- `docs/themes/` — thème Marp
- `.github/workflows/deploy.yml` — build Marp + déploiement Pages
- `AGENTS.md` — règles du dépôt (quiz, titres, tirets)
- `private-notes/` — notes personnelles (ignorées par git)
