# Séance 1 — Complexité, tableaux et *hash*

<nav class="page-nav">
  <a href="../../index.html">← Retour à l'accueil</a>
  <a href="cours_seance_01.html">Slides</a>
  <a href="quiz_seance_01.html">Quiz</a>
  <a href="exercices_seance_01.html">Exercices</a>
</nav>

## Plan du jour

1. Pourquoi un programme peut être « trop lent »
2. Mesurer le coût : temps et mémoire
3. Premiers outils : notations, boucles, listes Python
4. Dictionnaires et ensembles (`dict`, `set`)
5. Une méthode pour attaquer un exercice
6. Démo, puis exercices

On introduit les termes **au fur et à mesure**.

## Objectifs (en français simple)

À la fin de la séance, vous pourrez :

- expliquer pourquoi on parle de **coût** d'un algorithme
- estimer si une boucle est plutôt linéaire ou quadratique
- savoir ce que coûtent `append`, `pop(0)`, `x in list`
- utiliser un `dict` / `set` pour éviter de tout recalculer
- suivre une **démarche en 7 étapes** sur un exercice

## Pourquoi mesurer le coût ?

Deux programmes qui « marchent » ne se valent pas toujours.

Exemple d'idée : pour chaque élément, reparcourir toute la liste.

- Sur 10 valeurs : aucun souci
- Sur 100 000 valeurs : ça peut devenir inutilisable

On veut un langage commun pour dire : « ça croît trop vite quand $n$ augmente ».

## Deux axes : temps et espace

Quand on analyse un algorithme, on regarde surtout :

- le **temps** : combien de travail (opérations) pour une entrée de taille $n$
- l'**espace** : combien de mémoire **en plus** de l'entrée

On compare des **ordres de grandeur**, pas des millisecondes sur une machine précise.

## Taille de l'entrée : $n$

$n$ = taille du problème (longueur d'une liste, nombre d'éléments, …).

Questions utiles :

- Si $n$ double, le travail double-t-il aussi ?
- Ou est-il multiplié par 4 ? Par davantage ?

C'est le cœur de l'analyse de complexité.

## Une intuition avant les formules

| Croissance | Idée | Exemple typique |
| --- | --- | --- |
| Constante | ne dépend presque pas de $n$ | lire `a[i]` |
| Linéaire | proportionnel à $n$ | une boucle sur la liste |
| Quadratique | proportionnel à $n^2$ | deux boucles imbriquées |
| Logarithmique | croît très lentement | diviser $n$ par 2 à chaque fois |

Ensuite seulement : les notations $O$, $\Omega$, $\Theta$.

## Modèle de coût (idée)

Pour compter, on fait des hypothèses simples :

- lire / écrire une case mémoire : coût **constant**
- comparer ou additionner deux entiers « machine » : coût **constant**
- ce qui compte vraiment : les **boucles** et les parcours

Attention en Python : certaines opérations ont l'air simples mais cachent un parcours.

## Notations $O$, $\Omega$, $\Theta$

Pour une fonction de coût $T(n)$ :

| Notation | Sens intuitif |
| --- | --- |
| $T(n) = O(g(n))$ | au plus de l'ordre de $g$ (plafond) |
| $T(n) = \Omega(g(n))$ | au moins de l'ordre de $g$ (plancher) |
| $T(n) = \Theta(g(n))$ | exactement de l'ordre de $g$ |

En pratique on dit souvent « $O(n)$ » même quand on pense $\Theta(n)$.  
Si le meilleur et le pire cas diffèrent, on le précise.

## Lire un $O(\cdot)$ correctement

$f(n) = O(g(n))$ signifie :

il existe $c > 0$ et $n_0$ tels que pour $n \ge n_0$, $|f(n)| \le c \cdot g(n)$.

Conséquences :

- $O(n)$ est « meilleur » que $O(n^2)$ quand $n$ est grand
- les constantes disparaissent : $3n + 100 = O(n)$
- le terme dominant gagne : $n^2 + n = O(n^2)$

## Analyser une boucle simple

```python
for x in a:          # n itérations
    s += x           # coût constant
```

Coût : $\Theta(n)$ (linéaire).

Règle : **nombre d'itérations × coût du corps** (si le corps est uniforme).

## Boucles imbriquées

```python
for i in range(n):
    for j in range(n):
        ...  # coût constant
```

Coût : $\Theta(n^2)$ (quadratique).

Variante triangulaire :

```python
for i in range(n):
    for j in range(i, n):
        ...
```

Toujours $\Theta(n^2)$ (somme $n + (n-1) + \cdots + 1$).

## Boucles qui « sautent » plus vite

```python
i = 1
while i < n:
    ...      # coût constant
    i *= 2
```

Nombre d'itérations : $\Theta(\log n)$.

Repères utiles :

- diviser / multiplier par 2 → souvent $\log n$
- `i` de $1$ à $n$ avec `i += 1` → linéaire
- deux indices qui se rapprochent depuis les extrémités → souvent linéaire

## Meilleur, moyen, pire cas

Le même algorithme peut coûter différemment selon l'entrée.

- **pire cas** : la situation la plus défavorable
- **moyen** : sous un modèle « typique » d'entrées
- **meilleur** : rarement le plus utile pour choisir un algo

Exemple : chercher une valeur dans une liste non triée

- meilleur : $O(1)$ (elle est en tête)
- pire : $O(n)$

## Espace auxiliaire

On compte la mémoire **en plus** de l'entrée.

| Approche | Espace typique |
| --- | --- |
| Quelques variables | $O(1)$ |
| Une structure de taille $n$ | $O(n)$ |
| Beaucoup d'appels empilés (récursion) | $O(n)$ |
| Copie complète de l'entrée | $O(n)$ (à justifier) |

« Modifier sur place » n'implique pas toujours un espace $O(1)$ si la pile d'appels grossit.

## Tableaux dynamiques (`list`)

En Python, `list` = tableau dynamique contigu.

- indexation `a[i]` : $O(1)$
- `append` en fin : $O(1)$ **amorti**
- `insert(0, x)` / `pop(0)` : $O(n)$ (décalage)
- `x in a` : $O(n)$ (parcours)

La disposition en mémoire explique presque tous les pièges.

## Complexité amortie : `append`

Parfois un `append` déclenche un **redimensionnement** (copie vers un tableau plus grand).

Si on double la capacité à chaque fois :

- la plupart des `append` sont $O(1)$
- les rares copies coûtent $O(n)$, mais de moins en moins souvent
- sur $n$ `append` : coût total $\Theta(n)$ ⇒ **$O(1)$ amorti** par opération

## Point d'ancrage : preuve (agrégat)

Capacités successives : $1, 2, 4, \ldots, 2^{k}$ avec $2^{k} \ge n$.

Coût des copies : $1 + 2 + 4 + \cdots + 2^{k} < 2^{k+1} = O(n)$.

Coût des écritures « normales » : $O(n)$.

Total pour $n$ `append` : $O(n)$ ⇒ amorti $O(1)$.

(La méthode des potentiels donne la même conclusion, plus fine.)

## Dictionnaire et ensemble : l'idée

Besoin fréquent : « ai-je déjà vu cette valeur ? » ou « quelle info est liée à cette clé ? »

Structures Python :

- `dict` : **clé → valeur**
- `set` : ensemble de clés (présence / absence)

Derrière : une *hash table* (table de hachage).

## *Hash table* : principe

Associer **clé → valeur** avec accès **moyen** $O(1)$.

1. Fonction de *hash* : clé $\mapsto$ indice de seau (*bucket*)
2. Tableau de seaux
3. Gestion des **collisions** (plusieurs clés au même endroit)

On retient : accès très rapide en moyenne, mémoire en $O(n)$.

## Collisions et coûts

Deux clés peuvent avoir le même *hash*.

- **Moyen** (bonne fonction, charge raisonnable) : $O(1)$
- **Pire cas** (tout dans le même seau) : $O(n)$

Formulation utile : « $O(1)$ moyen, $O(n)$ pire cas » pour `dict` / `set`.

## Quand sortir un `dict` / `set` ?

Situations fréquentes dès aujourd'hui :

- détecter un doublon → `set`
- compter des occurrences → `dict` (ou `Counter`)
- retrouver l'indice d'une valeur déjà vue → `dict`
- tester rapidement une présence → `set` plutôt que `x in list`

Trade-off : on paie de la **mémoire** pour gagner du **temps**.

## Pièges Python (1/2)

| Opération | Coût | Remarque |
| --- | --- | --- |
| `a.append(x)` | $O(1)$ amorti | OK en boucle |
| `a.pop()` | $O(1)$ | fin de liste |
| `a.pop(0)` | $O(n)$ | préférer `collections.deque` |
| `a.insert(0, x)` | $O(n)$ | idem |
| `x in a` (list) | $O(n)$ | `x in set` est moyen $O(1)$ |

## Pièges Python (2/2)

Concaténation de chaînes :

```python
s = ""
for t in parts:
    s += t          # O(n²) au total
```

Préférer `"".join(parts)` : $O(n)$.

Autres :

- `list.copy()` / slicing `a[:]` : $O(n)$
- tri `sorted(a)` : $O(n \log n)$ et nouvelle liste

## Une méthode pour résoudre un exercice

Avant de coder, on suit **toujours** les mêmes 7 étapes.

Objectif : ne pas se jeter sur le clavier, et pouvoir expliquer sa démarche.

Les noms anglais de patterns (*sliding window*, *DP*, …) viendront plus tard dans le cours.  
Aujourd'hui : la **démarche**.

## 1. Clarification

Reformuler le problème **avec vos mots**.

Questions utiles :

- Que reçoit-on en entrée ? Que doit-on renvoyer ?
- Quelles tailles sont possibles pour $n$ ?
- Doublons autorisés ? Ordre important ?
- Que faire s'il n'y a pas de solution ?

Sans clarification, on résout souvent le **mauvais** problème.

## 2. Exemples

Dérouler 1–2 cas à la main **avant** toute idée d'algo.

- Un cas « normal »
- Un cas limite (liste vide, un seul élément, déjà trié, tous égaux…)

Écrire clairement l'entrée et la sortie attendue.

Ces exemples deviennent vos premiers tests.

## 3. Approche naïve

Proposer une solution **correcte**, même lente.

Toujours dire :

- l'idée (souvent : tout comparer à tout)
- le coût en **temps**
- le coût en **espace**

Un naïf correct et honnête vaut mieux qu'un « malin » faux.

## 4. Optimisation

Chercher comment éviter le travail inutile.

Questions guides :

- Que recalcule-t-on trop souvent ?
- Que peut-on retenir au fur et à mesure (`dict`, `set`, variables) ?
- Faut-il un passage, deux passages, un tri ?

On nommera les familles d'algorithmes progressivement dans les prochaines séances.

## 5. Implémentation

Code Python lisible, sans magie.

- Noms clairs (`seen`, `best`, `left`)
- Cas limites traités explicitement
- Une idée = un bloc de code compréhensible

La clarté compte autant que la vitesse.

## 6. Validation

Rejouer les exemples à la main sur le code (*dry run*).

Puis tester des limites :

- `[]`, `[x]`, deux éléments
- doublons, négatifs, zéros

Dire à voix haute ce que valent les variables à chaque étape.

## 7. Bilan

Terminer en résumant :

- complexité temps finale
- complexité espace finale
- éventuel compromis (plus de mémoire pour moins de temps)

Cette conclusion montre que vous maîtrisez ce que vous avez écrit.

## Lien avec l'examen oral

Plus tard dans le cursus, et à l'examen, cette démarche sert de fil conducteur.

L'oral (25 min) ressemble à une **question technique de code** du type *coding interview* :

- clarifier
- proposer un naïf
- améliorer
- coder
- justifier le coût

D'où le nom « méthode d'entretien » dans le reste du cours.

## Démo live : *Two Sum*

**Énoncé :** tableau d'entiers `nums`, cible `target`.  
Retourner les **indices** $i, j$ tels que `nums[i] + nums[j] == target`.

On applique la méthode à voix haute :

1. Clarifier : une seule solution ? indices distincts ?
2. Exemple : `nums = [2, 7, 11, 15]`, `target = 9` → `[0, 1]`
3. Naïf : double boucle $O(n^2)$, espace $O(1)$

## *Two Sum* : naïf

```python
def two_sum(nums, target):
    n = len(nums)
    for i in range(n):
        for j in range(i + 1, n):
            if nums[i] + nums[j] == target:
                return [i, j]
```

Correct, mais trop lent si $n \sim 10^5$.

## *Two Sum* : avec un `dict`

Idée : pour chaque valeur vue, retenir son indice.  
Quand on lit `x`, on demande si `target - x` a déjà été vu.

```python
def two_sum(nums, target):
    seen = {}  # valeur → indice
    for i, x in enumerate(nums):
        need = target - x
        if need in seen:
            return [seen[need], i]
        seen[x] = i
```

Temps moyen $O(n)$, espace $O(n)$.

## *Two Sum* : validation et bilan

Tests rapides :

- paire en tête / en queue / avec négatifs
- absences de solution (selon le contrat de l'énoncé)

Bilan :

- naïf $O(n^2)$ / $O(1)$
- version `dict` : $O(n)$ moyen / $O(n)$
- signal : « complément déjà vu » ⇒ dictionnaire

## Exercices de la séance

1. **Contains Duplicate**
2. **Valid Anagram**
3. **Two Sum**
4. **Best Time to Buy/Sell Stock**
5. **Product of Array Except Self**

Pour chacun : les 7 étapes **avant** de coder.

Ressources : fiche mémo Python DSA + grille d'évaluation de l'oral.

## Repères pour aujourd'hui

| Situation dans l'énoncé | Piste |
| --- | --- |
| Détecter un doublon | `set` |
| Compter des lettres / fréquences | `dict` |
| Retrouver un complément vers une cible | `dict` valeur → index |
| Max / min en un seul passage | une variable |
| Produits sans l'élément courant | deux passes (préfixe / suffixe) |

## Conclusion

- D'abord comprendre le **coût** (temps / espace, $O$)
- Puis les outils Python (`list`, `dict`, `set`) et leurs pièges
- Ensuite la **méthode en 7 étapes** pour structurer une solution
- Le cadrage *coding interview* / oral vient **après** ces bases

Prochaine séance : récursivité et *divide and conquer*.

<nav class="page-nav">
  <a href="../../index.html">← Retour à l'accueil</a>
  <a href="cours_seance_01.html">Slides</a>
  <a href="quiz_seance_01.html">Quiz</a>
  <a href="exercices_seance_01.html">Exercices</a>
</nav>

<footer class="site-footer"><a href="mailto:shuraux@he2b.be">Sylvain Huraux - HE2B - ISIB</a></footer>
