---
marp: true
theme: dsa
title: "Séance 2 — Récursivité et diviser pour régner"
paginate: true
header: "DSA — Séance 2 [Sylvain Huraux - HE2B - ISIB](mailto:shuraux@he2b.be)"
footer: "[← Retour à l'accueil](../../index.html)"
---

## Séance 2

Récursivité et diviser pour régner

Bloc : Fondations

[→ Quiz](quiz_seance_02.html)
[→ Exercices](exercices_seance_02.html)

---

## Objectifs de la séance

- Pile d'appels, condition d'arrêt, limites de récursion (`sys.setrecursionlimit`).
- Mémoïsation (`functools.lru_cache`).
- Diviser pour régner, théorème maître (énoncé et utilisation pratique).
- Recherche binaire : invariant de boucle, preuve de terminaison et correction.
- Introduction au backtracking.

---

## Démo live

Fibonacci (récursif naïf → mémoïsé), puis Binary Search avec preuve d'invariant.

---

## Point d'ancrage théorique

Preuve d'exactitude de la dichotomie via un invariant de boucle.

---

## Structure type (3 h)

- ~45 min : cours magistral (concepts et rigueur)
- ~15 min : démo live coding
- ~2 h : exercices pratiques avec correction collective de 1–2 problèmes clés

---

## Pour la suite

Les slides détaillés seront enrichis séance par séance.
Appliquer la méthode d'entretien sur chaque exercice.
