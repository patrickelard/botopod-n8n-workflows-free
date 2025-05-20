# 🧠 n8n Workflow — L01 - Collect Ideas (AI Agent)

Ce workflow n8n reçoit une liste d’articles (via webhook), analyse leur pertinence pour LinkedIn, génère un résumé court, puis stocke les idées retenues dans un Google Sheet.

## 🔍 Objectif

Faciliter la création de contenu tech en automatisant la veille et la sélection d’articles intéressants à repartager sur LinkedIn, avec un résumé de qualité généré par une IA.

---

## ⚙️ Fonctionnalités

- ✅ Filtrage automatique des articles selon leur **pertinence pour LinkedIn**
- ✅ Résumé concis (250 mots max) adapté à un **partage professionnel**
- ✅ Stockage dans **Google Sheets** pour relecture et publication différée
- ✅ Utilise l’API **OpenAI** pour les traitements IA
- ✅ Appelable depuis un autre workflow (`L00 - Fetch Articles`) via **webhook**

---

## 📦 Entrées attendues

Ce workflow s’exécute via un **webhook HTTP POST** et attend un tableau JSON d’articles au format suivant :

```json
[
  {
    "title": "Titre de l’article",
    "link": "https://exemple.com/article",
    "date": "2025-05-20T12:00:00Z",
    "source": "Medium"
  },
  ...
]

## 🔧 Configuration requise
Avant d’activer le workflow, configure les éléments suivants :

1. 🔑 OpenAI
Ajoute ta clé API OpenAI dans le noeud OpenAI Chat Model (par exemple: meta-llama/llama-3.1-8b-instruct).

2. 📄 Google Sheets
Connecte ton compte Google via OAuth2.

Spécifie :

Le nom du fichier Google Sheet (ex. LinkedIn Ideas)

Le nom de l’onglet cible (ex. Feuille 1)

## 🧠 Logique IA utilisée
Chaque article est envoyé à un LLM avec cette consigne :

"Cet article est-il pertinent pour être partagé sur LinkedIn par un profil tech senior (Java / DevOps / Agile / Freelance) ?
Si oui, génère un résumé de 250 mots maximum, au ton clair et humain.
Sinon, retourne une chaîne vide."

Si le résumé généré est vide ou trop court, l’article est ignoré.

📤 Résultat
Les articles jugés pertinents sont ajoutés au Google Sheet avec :

✅ Un résumé exploitable immédiatement

📅 La date d’analyse

🔗 Le lien original

🏷️ La source

### 🚀 Comment tester
Lance manuellement le workflow

Envoie une requête POST au webhook avec une liste d’articles en JSON

Vérifie le contenu ajouté dans Google Sheets

📡 Intégration avec L00 - Fetch Articles
Ce workflow est conçu pour être déclenché automatiquement depuis le workflow L00 - Fetch Articles, qui collecte les flux RSS tech.

### 🧱 Personnalisation possible
Modifier la consigne GPT pour ajuster le ton ou les critères de pertinence

Ajouter une notation de pertinence (score 1 à 5)

Enrichir le résumé avec des hashtags ou CTA

Publier automatiquement sur LinkedIn via Zapier ou un autre workflow

## 📁 Fichier d’export n8n
Tu peux importer le fichier suivant dans n8n pour tester ou cloner ce workflow :

L01 - Collect Ideas.json

## 📬 Questions / Suggestions
Tu veux adapter ce workflow à un autre usage (veille métier, Notion, newsletters) ?
→ Ouvre une issue ou contacte-moi sur LinkedIn : https://www.linkedin.com/in/patrickelard/