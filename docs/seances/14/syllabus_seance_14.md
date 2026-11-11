# Séance 14 — Synthèse : signaux de pattern, intervalles, *bit manipulation*

<nav class="page-nav">
  <a href="../../index.html">← Retour à l'accueil</a>
  <a href="cours_seance_14.html">Slides</a>
  <a href="quiz_seance_14.html">Quiz</a>
  <a href="exercices_seance_14.html">Exercices</a>
</nav>

## Objectifs de la séance

- Grille « signaux de l'énoncé → famille d'algorithmes » (outil de lecture autonome).
- Tableau récapitulatif des complexités fondamentales (temps / espace).
- Intervalles : tri, fusion, *greedy* / *sweep line*.
- *Bit manipulation* : XOR, masks, opérations classiques en *coding interview*.
- Signaux conflictuels : comment arbitrer entre plusieurs patterns.
- Pièges classiques et gestion du stress en *coding interview*.

## Signaux → famille (1/2)

- *Sous-tableau contigu* / somme de plage → *sliding window*, *prefix sums*
- *Shortest path* / coût minimum → *BFS*, Dijkstra
- $K$ éléments extrêmes → *heap*, *Quickselect*
- Nombre de combinaisons / optimisation séquentielle → *DP*
- Toutes les configurations possibles → *backtracking*

## Signaux → famille (2/2)

- Intervalles qui se chevauchent / agenda → tri + *greedy* / *sweep line*
- Parité, bits manquants, flags compacts → *bit manipulation* (souvent XOR)
- Ordre / ordonnancement avec dépendances → *topological sort*
- Connexité / fusion de composants → *Union-Find*
- Autocomplétion / dictionnaire de préfixes → *Trie*

## Complexités à retenir

| Structure / algo | Temps typique | Espace |
| --- | --- | --- |
| *Hash table* (moyen) | $O(1)$ | $O(n)$ |
| *Heap* insert / pop | $O(\log n)$ | $O(n)$ |
| *Binary search* | $O(\log n)$ | $O(1)$ |
| Tri par comparaison | $\Omega(n \log n)$ | varie |
| *BFS* / *DFS* | $O(V + E)$ | $O(V)$ |
| Dijkstra (*binary heap*) | $O((V + E) \log V)$ | $O(V)$ |
| *DP* 1D / 2D | $O(n)$ / $O(n \cdot m)$ | souvent compressible |

## Intervalles

- Représentation : paires `[start, end]`, conventions demi-ouvertes vs fermées.
- Premier réflexe : **trier** (par `start`, parfois par `end`).
- Fusion (*merge*) : balayage linéaire après tri, $O(n \log n)$.
- *Greedy* sur intervalles : choix du prochain qui se termine le plus tôt (ordonnancement).
- *Sweep line* : événements « début / fin », compteur d'actifs (ex. salles occupées).

## *Bit manipulation*

- Opérateurs : `&`, `|`, `^`, `~`, `<<`, `>>` (attention au signe en Python).
- XOR : $x \oplus x = 0$, $x \oplus 0 = x$ (trouver l'élément unique, échanger sans temp).
- Masks : isoler / fixer / basculer un bit (`x & (1 << k)`, `x |= (1 << k)`).
- Astuces fréquentes : `x & (x - 1)` (ôte le bit 1 de poids faible), `x & -x` (bit isolé).
- Compter les bits (*popcount*), parité, sous-ensembles via *bitmask* (lien avec *DP*).

## Quand les signaux conflictuent

1. Reformuler la contrainte dominante (contigu ? ordre ? optimal global ?).
2. Estimer le naïf et le plafond acceptable ($n \le 10^5$ ⇒ viser $O(n \log n)$ ou mieux).
3. Lister 2 patterns candidats, dérouler un exemple sur chacun.
4. Choisir celui qui respecte **toutes** les contraintes (pas seulement le mot-clé de l'énoncé).
5. Garder une variante en poche pour les questions de suivi.

## Démo live

1. **Insert Interval** : tri implicite + fusion locale (intervalles).
2. **Single Number** : réduction par XOR (*bit manipulation*).
3. Lecture à voix haute d'un énoncé Hard : identifier les signaux avant de coder.

## Pièges *coding interview*

- Coder avant d'avoir un invariant / une complexité cible.
- Oublier les cas limites (vide, singleton, déjà trié, doublons, overflow).
- Confondre *contiguous* (*subarray*) et *subsequence*.
- Muter la structure pendant un parcours (liste, graphe).
- Stress : verbaliser, découper, proposer un naïf correct puis optimiser.

## Structure type (3 h)

- ~45 min : cours magistral (grille, intervalles, *bits*, arbitrage)
- ~15 min : démo live coding
- ~2 h : exercices Medium/Hard avec correction collective de 1–2 problèmes clés

## Pour la suite

Réviser la grille de signaux avant l'oral.
Appliquer la méthode d'entretien sur chaque exercice.

<nav class="page-nav">
  <a href="../../index.html">← Retour à l'accueil</a>
  <a href="cours_seance_14.html">Slides</a>
  <a href="quiz_seance_14.html">Quiz</a>
  <a href="exercices_seance_14.html">Exercices</a>
</nav>

<footer class="site-footer"><a href="mailto:shuraux@he2b.be">Sylvain Huraux - HE2B - ISIB</a></footer>
