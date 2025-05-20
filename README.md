# Botopod n8n Workflows

> Une collection de workflows n8n conçus par [Botopod](https://www.botopod.com) pour automatiser la veille technologique, la génération d'idées, la publication de contenu et bien plus.

## 🧠 Objectif

Ce dépôt regroupe les automatisations n8n développées par Botopod. Chaque workflow est documenté et pensé pour être **modulaire**, **réutilisable** et **orienté production**.

## 📦 Workflows disponibles

| ID    | Nom                            | Description                                                                 |
|-------|--------------------------------|-----------------------------------------------------------------------------|
| L00   | Fetch Articles (RSS)           | Agrège automatiquement des flux RSS tech et envoie les articles à un sous-workflow |
| L01   | Collect Ideas (AI agent)       | Analyse les articles, génère des idées de posts LinkedIn avec l’aide d’un agent IA |

> 📁 Chaque workflow est documenté dans son propre dossier (ex: `./L00-fetch-articles`)

## 🚀 Installation

1. Cloner ce dépôt :
   ```bash
   git clone https://github.com/botopod/botopod-n8n-workflows-free.git
   cd botopod-n8n-workflows-free
1. Importer les fichiers .json des workflows dans n8n :

    Via l'interface "Import workflow" (dans l'onglet Workflows)

    Ou en ligne de commande si tu utilises une instance auto-hébergée

1. Adapter les variables d’environnement si nécessaire :

    API Keys, URLs, secrets...

    Voir les fichiers README.md dans chaque dossier de workflow

## 🔧 Prérequis

    Instance n8n (self-hosted ou Cloud)

    Connaissances de base sur les webhooks, APIs REST, flux RSS

    (optionnel) Accès à une IA (OpenAI API, etc.)

## 🧩 License

MIT — Utilisation libre, contributions bienvenues ✨

## 🤝 Contribuer

Tu veux proposer une amélioration, corriger un bug ou ajouter un nouveau workflow ?
➡️ Crée une issue ou envoie une pull request !

    Fait avec ❤️ par Botopod — Automatise mieux, crée plus.