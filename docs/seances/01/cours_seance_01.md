---
marp: true
theme: dsa
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

- Pourquoi la complexité : modèle de coût RAM, notations $O$, $\Omega$, $\Theta$.
- Analyse de boucles simples et imbriquées.
- Complexité amortie (cas du redimensionnement de `list.append`).
- *Hash table* : principe, collisions, coût moyen vs pire cas.
- Coûts cachés en Python (`pop(0)`, `x in list`, concaténations `s += ...`).

---

## Fil rouge : la méthode d'entretien

Appliquée systématiquement à chaque exercice du cours :

1. **Clarification** : reformuler, poser des questions (contraintes, types, cas limites).
2. **Exemples** : dérouler un ou deux cas concrets à la main.
3. **Approche naïve** : brute force + complexité spatiale/temporelle associée.
4. **Optimisation** : choix du bon pattern ou de la bonne structure de données.
5. **Implémentation** : code Python idiomatique et propre.
6. **Validation** : dérouler des tests à sec (notamment cas aux limites).
7. **Bilan** : complexité finale temps/espace (notations grand O).

---

## Démo live

Two Sum (du brute force $O(n^2)$ à la *hash table* $O(n)$).

---

## Point d'ancrage théorique

Preuve du coût amorti $O(1)$ du doublement de capacité d'un tableau dynamique (méthode de l'agrégat / des potentiels).

---

## Structure type (3 h)

- ~45 min : cours magistral (concepts et rigueur)
- ~15 min : démo live coding
- ~2 h : exercices pratiques avec correction collective de 1–2 problèmes clés

---

## Pour la suite

Les slides détaillés seront enrichis séance par séance.
Appliquer la méthode d'entretien sur chaque exercice.
