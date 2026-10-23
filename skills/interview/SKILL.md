---
name: interview
description: Interroger l'utilisateur sans relâche, en français, sur un plan, une décision ou une idée pour la mettre à l'épreuve. À utiliser quand l'utilisateur veut challenger sa réflexion ou dit « interview », « interroge-moi », « cuisine-moi », « challenge-moi ».
---

Interroge l'utilisateur sans relâche, en français, jusqu'à atteindre une compréhension partagée. Représente le sujet comme un *arbre de décisions* : chaque décision se ramifie en d'autres décisions qui en dépendent.

Parcours l'arbre par *tours*. La *frontière*, ce sont toutes les décisions dont les prérequis sont déjà tranchés : les questions que tu peux poser maintenant sans deviner des réponses que tu n'as pas encore entendues. Pose toute la frontière en un seul tour : numérote chaque question et donne ta réponse recommandée. Puis attends les réponses de l'utilisateur avant le tour suivant.

Formate un tour ainsi :

```
❓ **Q1** - **<titre de la question>** : <corps de la question, éventuellement sur plusieurs paragraphes, avec des choix possibles>

➡️ <ta réponse recommandée>

---

❓ **Q2** - **<titre de la question>** : <corps de la question>

➡️ <ta réponse recommandée>
```

Formule chaque question de façon à ce qu'un « oui » accepte ta réponse recommandée.

Chaque réponse remodèle l'arbre : les décisions tranchées repoussent la frontière et débloquent les questions qui en dépendaient. Recalcule la frontière et pose le tour suivant. Une question dont la réponse dépend d'une autre question encore ouverte dans ce tour appartient à un tour ultérieur, pas à celui-ci.

Trouver les faits est ton travail, jamais celui de l'utilisateur. Quand une question de la frontière nécessite un fait de l'environnement (fichiers, outils, documentation, web…), envoie un sous-agent le chercher ; ne demande jamais à l'utilisateur ce que tu peux vérifier toi-même. Ne bloque pas dessus : une recherche en cours est un prérequis non tranché, donc seules les questions qui en dépendent attendent son retour ; pose le reste de la frontière tout de suite. Les décisions appartiennent à l'utilisateur : soumets-les-lui une par une et attends.

La session est terminée quand la frontière est vide : chaque branche de l'arbre visitée, rien de supposé en silence. Termine par un récapitulatif des décisions prises. N'agis pas avant que l'utilisateur confirme que vous êtes arrivés à une compréhension partagée.
