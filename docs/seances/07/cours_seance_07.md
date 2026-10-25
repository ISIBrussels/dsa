---
marp: true
theme: dsa
title: "Séance 7 — Arbres binaires de recherche (BST) et équilibrage"
paginate: true
header: "DSA — Séance 7 [Sylvain Huraux - HE2B - ISIB](mailto:shuraux@he2b.be)"
footer: "[← Retour à l'accueil](../../index.html)"
---

## Séance 7

Arbres binaires de recherche (BST) et équilibrage

Bloc : Arbres et tas

[→ Quiz](quiz_seance_07.html)
[→ Exercices](exercices_seance_07.html)

---

## Objectifs de la séance

- Propriété de recherche binaire, opérations : recherche, insertion, suppression.
- Lien parcours infixe ↔ ordre trié.
- Dégénérescence en liste liée et nécessité de l'équilibrage.
- Arbres auto-équilibrés (AVL, Rouge-Noir : principe des rotations, garanties).
- Alternatives pratiques en Python : module `bisect`, `sortedcontainers`.

---

## Structure type (3 h)

- ~45 min : cours magistral (concepts et rigueur)
- ~15 min : démo live coding
- ~2 h : exercices pratiques avec correction collective de 1–2 problèmes clés

---

## Pour la suite

Les slides détaillés seront enrichis séance par séance.
Appliquer la méthode d'entretien sur chaque exercice.
