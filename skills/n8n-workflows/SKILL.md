---
name: n8n-workflows
description: Créer, modifier ou déboguer des workflows n8n, notamment le bot Telegram → Notion. À utiliser dès qu'il est question de n8n, de workflow, de nœud ou du bot Telegram (« crée un workflow », « modifie le bot Telegram », « ajoute un nœud », « pourquoi mon workflow plante »).
---

# Workflows n8n

## Avant de construire
1. Résumer en 3 lignes ce que fera le workflow (déclencheur → traitement → résultat), puis **attendre ma validation** avant de créer ou de modifier quoi que ce soit.
2. Vérifier les credentials disponibles (`list_credentials`). Si un credential manque, le signaler et utiliser un credential à connecter plutôt que d'en inventer un.

## Conventions
- **Noms des nœuds :** en français, en commençant par un verbe (« Lire le message », « Créer la capture », « Prévenir l'erreur »).
- **Captures :** toute capture va dans la base Notion « Capture ». Respecter exactement les propriétés et les valeurs décrites dans [notion-capture.md](notion-capture.md).
- **Erreurs :** chaque branche qui peut échouer (appel API, transcription, écriture Notion, IA) renvoie un message Telegram qui explique simplement ce qui a échoué et quoi faire.

## Après avoir construit
1. Valider le workflow, puis le tester avec un message d'exemple (texte, et vocal si le workflow le gère).
2. **Ne jamais publier ou activer le workflow sans mon accord explicite.**
3. M'expliquer chaque nœud simplement : une ligne par nœud, ce qu'il reçoit et ce qu'il fait.
