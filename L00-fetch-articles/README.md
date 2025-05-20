# Workflow L00 – Fetch Articles (RSS)

> Agrège automatiquement des flux RSS technologiques, filtre les articles pertinents et les transmet à un workflow de traitement en aval (`L01 - Collect Ideas`).

## 🎯 Objectif

Centraliser et automatiser la veille technologique en récupérant régulièrement les derniers articles de sources sélectionnées (blogs, magazines tech, plateformes dev, etc.).

## 🛠 Fonctionnement

1. **Planification** : un nœud *cron* déclenche le workflow à intervalles réguliers (ex: toutes les 3h).
2. **Lecture RSS** : plusieurs flux RSS sont interrogés en parallèle via des nœuds `RSS Feed Read`.
3. **Nettoyage & dédoublonnage** :
   - Regroupement des articles
   - Élimination des doublons via titre + URL
4. **Filtrage optionnel** : par mot-clé ou domaine
5. **Envoi des articles** :
   - Via un Webhook ou `Execute Workflow` vers `L01 - Collect Ideas`
   - Format JSON standardisé

## 🔧 Configuration

### Variables d’environnement (optionnelles)

- `FEED_URLS` : liste des flux RSS à suivre (ou à configurer directement dans les nœuds)
- `NEXT_WORKFLOW_WEBHOOK_URL` : URL du workflow de traitement en aval

### Nœuds à adapter

- `RSS Feed Read` : personnalise les URLs de flux
- `Webhook` ou `Execute Workflow` : adapte l’URL ou le nom du sous-workflow cible

## 📤 Format de sortie (JSON)

```json
{
  "title": "Pourquoi les monades ne sont pas si compliquées",
  "link": "https://monblogtech.dev/articles/monades-facile",
  "pubDate": "2025-05-18T08:12:00.000Z",
  "source": "monblogtech.dev"
}

Ce format est ensuite utilisé par le workflow L01 - Collect Ideas.

## 🧪 Test rapide

Tu peux tester ce workflow manuellement en le déclenchant depuis l’interface n8n et en inspectant les articles en sortie.
Pense à désactiver temporairement les appels à L01 si tu veux tester ce workflow seul.

## 📌 Astuces

    Pour ajouter facilement de nouveaux flux, duplique un nœud RSS Feed Read existant.

    Tu peux combiner ce workflow avec un nœud n8n Schedule Trigger ou un service externe (Zapier, GitHub Action) pour une exécution plus fine.

    🧩 Ce workflow fait partie de la collection Botopod n8n Workflows.