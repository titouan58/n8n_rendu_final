---
name: doubt-code
description: "Douter de son propre code : le remettre en question, se poser des questions critiques et vérifier sur internet (docs officielles, bonnes pratiques à jour) pour aboutir au code le plus optimal. À utiliser quand l'utilisateur dit « doute de ton code », « doubt code », « vérifie que c'est optimal », ou après avoir écrit un morceau de code non trivial."
---

# Douter de son code

Pars du principe que le code que tu viens d'écrire (ou celui qu'on te montre) **n'est pas encore le meilleur possible**. Ton travail : le prouver ou le réfuter avec des faits, pas avec ton intuition.

## 1. Délimiter

Identifie précisément le code à examiner (fichiers, fonctions, diff). Relis-le en entier avant de juger. Note le langage, les versions des bibliothèques (`package.json`, `requirements.txt`, lockfiles…) et le contexte d'exécution.

## 2. Se poser les questions qui fâchent

Pour chaque morceau significatif, écris les doutes sous forme de questions concrètes :

- **Exactitude** : quelles entrées le cassent ? Cas limites (vide, null, très grand, concurrent, Unicode, fuseaux horaires) ? Gestion des erreurs ?
- **API et versions** : est-ce que j'utilise cette API comme la doc actuelle le recommande ? Est-elle dépréciée ? Existe-t-il une fonction native qui fait déjà ça ?
- **Performance** : quelle complexité ? Requêtes N+1, boucles imbriquées, allocations inutiles, appels réseau répétés ?
- **Sécurité** : injection, secrets en dur, validation des entrées, permissions ?
- **Simplicité** : peut-on faire la même chose avec moins de code ? Une abstraction est-elle inutile ? Le code ressemble-t-il au reste du projet ?
- **Alternatives** : quelle autre approche un expert choisirait-il, et pourquoi ?

Ne garde que les doutes qui pourraient réellement changer le code.

## 3. Vérifier sur internet

Pour chaque doute qui dépend d'un fait externe, cherche la réponse avec WebSearch puis WebFetch :

- Privilégie les **sources primaires** : documentation officielle, changelog, RFC, code source de la bibliothèque, issues GitHub des mainteneurs.
- Vérifie que la source correspond à **la version utilisée** dans le projet.
- Méfie-toi des articles de blog et réponses Stack Overflow anciens ; recoupe-les avec la doc.
- Note l'URL de chaque source qui fonde une conclusion.

Les doutes qui se vérifient localement (comportement, performance) se testent plutôt en exécutant le code, les tests ou un petit script de mesure.

## 4. Trancher

Pour chaque doute, conclus : **confirmé** (le code doit changer), **infirmé** (le code est bon, avec la preuve), ou **incertain** (à soumettre à l'utilisateur). Ne change rien sur la base d'une préférence non étayée.

## 5. Rapporter puis corriger

Présente un tableau court :

| Doute | Verdict | Preuve / source | Changement proposé |
|---|---|---|---|

Puis applique les changements confirmés (sauf si l'utilisateur a demandé seulement un audit), relance les tests et indique honnêtement ce qui passe ou échoue. Les points incertains sont posés à l'utilisateur sous forme de questions numérotées avec ta recommandation.
