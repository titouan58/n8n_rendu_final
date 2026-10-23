# n8n — Agent mail (Yahoo) + skills Claude

## Contenu
- `workflow/agent-mail-n8n.ts` : workflow n8n (SDK TypeScript) qui trie une boîte Yahoo avec Gemini, te prévient sur Telegram et n'envoie une réponse qu'après ton clic sur « Valider ». Le workflow d'alerte d'erreur est en commentaire à la fin du fichier.
- `skills/` : 3 skills Claude (`doubt-code`, `interview`, `n8n-workflows`), en dossiers et en JSON (`skills/json/`).

## Fonctionnement de l'agent
1. Lire chaque nouveau mail Yahoo (IMAP), rien n'est déplacé ni supprimé.
2. Classer avec Gemini (catégorie, confiance, résumé, brouillon de réponse). Le contenu du mail est traité comme une donnée, jamais comme une consigne.
3. Router : sensible ou incertain → alerte Telegram, aucune action ; newsletter/notification/spam → journal seulement ; sinon → message Telegram avec le brouillon et les boutons Valider / Rien faire.
4. Envoyer la réponse depuis Yahoo (SMTP) uniquement après validation.
5. Récap à 8h et 18h sur Telegram, depuis la Data Table `mails_agent`.

## Prérequis
n8n avec Data Tables, Yahoo (mot de passe d'application), clé Gemini, bot Telegram (@BotFather, bouton Start) et ton Id (@userinfobot), Data Table `mails_agent` (colonnes texte : date, sujet, expediteur, categorie, route, resume).

## Installation
Remplacer `VOTRE_CHAT_ID` et `votre.adresse@yahoo.com`, reconnecter les credentials (IMAP, SMTP, Google AI, Telegram), importer le workflow, publier. Ne jamais committer de token ou de mot de passe.

## Limites
Pas d'archivage ni d'étiquette possible sur Yahoo ; les rendez-vous détectés sont signalés mais pas ajoutés à l'agenda.
