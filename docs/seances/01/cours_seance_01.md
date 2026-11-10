---
marp: true
theme: isib
title: "Séance 1 — Complexité, méthode *coding interview*, tableaux et *hash*"
paginate: true
header: "DSA — Séance 1 [Sylvain Huraux - HE2B - ISIB](mailto:shuraux@he2b.be)"
footer: "[← Retour à l'accueil](../../index.html)"
---

## Séance 1

Complexité, méthode *coding interview*, tableaux et *hash*

Bloc : Fondations

[→ Quiz](quiz_seance_01.html)
[→ Exercices](exercices_seance_01.html)

---

## Objectifs de la séance

- Pourquoi la complexité : modèle de coût RAM, notations $O$, $\Omega$, $\Theta$
- Analyser boucles simples et imbriquées
- Complexité amortie (`list.append`, doublement de capacité)
- *Hash table* : principe, collisions, moyen vs pire cas
- Coûts cachés en Python (`pop(0)`, `x in list`, `s += ...`)
- Appliquer la **méthode d'entretien** (7 étapes) dès le premier exercice

---

## Pourquoi ce cours ?

Objectif pédagogique : raisonner comme en *coding interview* (et en conception réelle).

- Choisir une structure / un pattern **avant** de coder
- Justifier temps et espace
- Communiquer clairement sous contrainte de temps

Examen oral : 25 min, façon *coding interview* (question technique de code).

---

## Fil rouge : la méthode d'entretien

Appliquée **systématiquement** à chaque exercice du cours :

1. Clarification
2. Exemples
3. Approche naïve
4. Optimisation
5. Implémentation
6. Validation
7. Bilan

Ce n'est pas du « théâtre » : c'est la grille d'évaluation de l'oral.

---

## 1. Clarification

Reformuler le problème **avec vos mots**.

Questions utiles :

- Types des entrées ? Bornes sur $n$ ?
- Doublons autorisés ? Ordre stable attendu ?
- Que faire si aucune solution ? Plusieurs solutions ?
- Contraintes mémoire ? Entrée mutable ?

Si vous codez sans clarifier, vous résolvez souvent le **mauvais** problème.

---

## 2. Exemples

Dérouler 1–2 cas à la main **avant** toute idée d'algo.

- Un cas « normal »
- Un cas limite (vide, singleton, déjà trié, tous égaux…)

Écrire l'entrée et la sortie attendue sur le tableau.

Les exemples deviennent vos premiers tests.

---

## 3. Approche naïve

Proposer un *brute force* correct, même lent.

Toujours annoncer :

- idée (souvent $O(n^2)$ / $O(n!)$…)
- complexité **temps**
- complexité **espace**

Un naïf correct + honnête vaut mieux qu'un « optimal » faux.

---

## 4. Optimisation

Chercher le **pattern** ou la structure qui coupe le coût.

Questions guides :

- Que recalcule-t-on trop souvent ?
- Que peut-on précalculer / mémoriser (*hash*, *prefix*, …) ?
- Faut-il de l'ordre (*sort*, *heap*) ou de l'accès $O(1)$ (*hash*) ?

Nommer la famille : *two pointers*, *sliding window*, *hash table*, *DP*…

---

## 5. Implémentation

Code Python idiomatique, lisible, sans magie.

- Noms clairs (`seen`, `left`, `best`)
- Éviter les *one-liners* opaques en entretien
- Gérer explicitement les cas limites

On optimise la clarté **autant** que la constante.

---

## 6. Validation

*Dry run* sur les exemples, puis cas limites :

- `[]`, `[x]`, deux éléments
- Déjà optimal / déjà pire cas
- Doublons, négatifs, zéros

Verbaliser : « ici `i` vaut …, `seen` contient … »

---

## 7. Bilan

Clôturer à voix haute :

- complexité temps finale
- complexité espace finale
- trade-off éventuel (plus d'espace pour moins de temps)
- variante possible si le jury change une contrainte

C'est la dernière impression de l'oral : soignez-la.

---

## Complexité : de quoi parle-t-on ?

Mesurer **comment le coût croît** avec la taille $n$ de l'entrée.

On ignore les constantes machine et on compare des **ordres de grandeur**.

Deux axes :

- **temps** (nombre d'opérations élémentaires)
- **espace** (mémoire auxiliaire, hors l'entrée)

---

## Modèle de coût RAM

Hypothèses de travail (assez réalistes pour l'analyse) :

- accès mémoire $O(1)$
- opérations arithmétiques / comparaisons $O(1)$ sur mots machine
- on compte surtout les boucles et les appels

En Python, certaines opérations « ressemblent » à $O(1)$ mais ne le sont pas (voir plus loin).

---

## Notations $O$, $\Omega$, $\Theta$

Pour une fonction de coût $T(n)$ :

| Notation | Sens intuitif |
| --- | --- |
| $T(n) = O(g(n))$ | au plus de l'ordre de $g$ (plafond) |
| $T(n) = \Omega(g(n))$ | au moins de l'ordre de $g$ (plancher) |
| $T(n) = \Theta(g(n))$ | exactement de l'ordre de $g$ |

En entretien on dit souvent « $O(n)$ » pour $\Theta(n)$ : précisez *best / average / worst* si ça change.

---

## Lire un $O(\cdot)$ correctement

$f(n) = O(g(n))$ signifie :

il existe $c > 0$ et $n_0$ tels que pour $n \ge n_0$, $|f(n)| \le c \cdot g(n)$.

Conséquences :

- $O(n) \subset O(n \log n) \subset O(n^2)$ (au sens large)
- les constantes disparaissent : $3n + 100 = O(n)$
- le terme dominant gagne : $n^2 + n = O(n^2)$

---

## Analyser une boucle simple

```python
for x in a:          # n itérations
    s += x           # O(1)
```

Coût : $\Theta(n)$.

Règle : **nombre d'itérations × coût du corps** (si le corps est uniforme).

---

## Boucles imbriquées

```python
for i in range(n):
    for j in range(n):
        ...  # O(1)
```

Coût : $\Theta(n^2)$.

Variante triangulaire :

```python
for i in range(n):
    for j in range(i, n):
        ...
```

Toujours $\Theta(n^2)$ (somme $n + (n-1) + \cdots + 1$).

---

## Boucles « qui dépendent de $i$ »

```python
i = 1
while i < n:
    ...      # O(1)
    i *= 2
```

Nombre d'itérations : $\Theta(\log n)$.

Repères utiles :

- diviser / multiplier par 2 → souvent $\log n$
- $i$ de $1$ à $n$ avec `i += 1` → linéaire
- deux indices qui se croisent (*two pointers*) → souvent linéaire

---

## Meilleur, moyen, pire cas

Toujours préciser **sur quoi** porte le $O$ :

- pire cas (*worst case*) : ce que l'adversaire force
- moyen (*average*) : sous un modèle d'entrées
- meilleur (*best*) : rarement le plus utile en entretien

Exemple : recherche dans une liste non triée

- meilleur : $O(1)$ (élément en tête)
- pire : $O(n)$

---

## Espace auxiliaire

On compte la mémoire **en plus** de l'entrée.

| Approche | Espace typique |
| --- | --- |
| Indices / quelques variables | $O(1)$ |
| Tableau / *hash* de taille $n$ | $O(n)$ |
| Récursion profondeur $n$ | $O(n)$ (*call stack*) |
| Copie de l'entrée | $O(n)$ (à justifier) |

« In-place » ≠ toujours $O(1)$ d'espace (la pile compte).

---

## Tableaux dynamiques (`list`)

En Python, `list` = tableau dynamique contigu.

- indexation `a[i]` : $O(1)$
- `append` en fin : $O(1)$ **amorti**
- `insert(0, x)` / `pop(0)` : $O(n)$ (décalage)
- `x in a` : $O(n)$ (parcours)

La géométrie mémoire explique presque tous les pièges.

---

## Complexité amortie : `append`

Parfois un `append` déclenche un **redimensionnement** (copie vers un tableau plus grand).

Si on double la capacité à chaque fois :

- la plupart des `append` sont $O(1)$
- les rares copies coûtent $O(n)$, mais de moins en moins souvent
- sur $n$ `append` : coût total $\Theta(n)$ ⇒ **$O(1)$ amorti** par opération

---

## Point d'ancrage : preuve (agrégat)

Capacités successives : $1, 2, 4, \ldots, 2^{k}$ avec $2^{k} \ge n$.

Coût des copies : $1 + 2 + 4 + \cdots + 2^{k} < 2^{k+1} = O(n)$.

Coût des écritures « normales » : $O(n)$.

Total pour $n$ `append` : $O(n)$ ⇒ amorti $O(1)$.

(La méthode des potentiels donne la même conclusion, plus fine.)

---

## *Hash table* : idée

Associer **clé → valeur** avec accès moyen $O(1)$.

1. Fonction de *hash* : clé $\mapsto$ indice de seau (*bucket*)
2. Tableau de seaux
3. Gestion des **collisions** (chaînage ou adressage ouvert)

En Python : `dict`, `set` (table de hachage).

---

## Collisions et coûts

Deux clés peuvent avoir le même *hash*.

- **Moyen** (bonne fonction, charge raisonnable) : $O(1)$
- **Pire cas** (toutes les clés dans le même seau) : $O(n)$

En entretien : dites « $O(1)$ moyen, $O(n)$ pire cas » pour `dict` / `set`.

Ne comptez pas sur le pire cas pathologique sauf question de suivi.

---

## Quand sortir un `dict` / `set` ?

Signaux fréquents :

- « existe-t-il un complément / un vu précédemment ? » → `set` / `dict`
- compter des fréquences → `dict` / `Counter`
- *anagram*, motifs sur multiset → fréquences
- indices à retrouver plus tard → `dict` clé → index

Trade-off classique : **espace $O(n)$** pour gagner un facteur $n$ en temps.

---

## Pièges Python (1/2)

| Opération | Coût | Remarque |
| --- | --- | --- |
| `a.append(x)` | $O(1)$ amorti | OK en boucle |
| `a.pop()` | $O(1)$ | fin de liste |
| `a.pop(0)` | $O(n)$ | préférer `collections.deque` |
| `a.insert(0, x)` | $O(n)$ | idem |
| `x in a` (list) | $O(n)$ | `x in set` est moyen $O(1)$ |

---

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

---

## Démo live : *Two Sum*

**Énoncé :** tableau d'entiers `nums`, cible `target`.  
Retourner les **indices** $i, j$ tels que `nums[i] + nums[j] == target`.

Méthode d'entretien (on la joue à voix haute) :

1. Clarifier : une seule solution ? indices distincts ? bornes ?
2. Exemple : `nums = [2, 7, 11, 15]`, `target = 9` → `[0, 1]`
3. Naïf : double boucle $O(n^2)$, espace $O(1)$

---

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

---

## *Two Sum* : *hash table*

Invariant : pour l'indice `i`, on a déjà stocké les valeurs vues.

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

---

## *Two Sum* : validation et bilan

Tests rapides :

- paire en tête / en queue / avec négatifs
- `target` unreachable (contrat : une solution existe, ou gérer l'absence)

Bilan à dire :

- naïf $O(n^2)$ / $O(1)$
- optimal moyen $O(n)$ / $O(n)$ grâce au `dict`
- signal : « complément déjà vu » ⇒ *hash*

---

## Exercices de la séance

1. **Contains Duplicate**
2. **Valid Anagram**
3. **Two Sum**
4. **Best Time to Buy/Sell Stock**
5. **Product of Array Except Self**

Pour chacun : les 7 étapes **avant** de coder.

Ressources : fiche mémo Python DSA + grille d'évaluation de l'oral.

---

## Signaux à reconnaître aujourd'hui

| Signal dans l'énoncé | Piste |
| --- | --- |
| Doublon / présence | `set` |
| Fréquences / *anagram* | `dict` / `Counter` |
| Complément vers une cible | `dict` valeur → index |
| Max / min en un passage | variable courante $O(1)$ |
| Produits / préfixe-suffixe | deux passes, espace $O(1)$ extra possible |

---

## Conclusion

- La méthode d'entretien structure **toute** réponse (cours et oral)
- $O$ / $\Omega$ / $\Theta$ : vocabulaire précis, pas de décoration
- `append` amorti $O(1)$ ; méfiez-vous de `pop(0)` et `s +=`
- `dict` / `set` : le premier levier d'optimisation sur tableaux

Prochaine séance : récursivité et *divide and conquer*.
