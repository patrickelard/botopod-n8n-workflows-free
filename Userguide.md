🧠 n8n Botopod Tech Agent (RSS → IA → Ideas)
Automatise ta veille technologique et génère des idées de posts LinkedIn avec l’IA.
Un système modulaire, low-code, open source — alimenté par n8n.

🔧 Fonctionnement
Ce système repose sur deux workflows n8n interconnectés :

L00 - Fetch Articles (RSS)
Agrège quotidiennement des articles via une sélection de flux RSS.

Enrichit chaque article avec son titre, son lien, sa date et sa source.

Transmet les articles au workflow suivant via un webhook interne.

L01 - Collect Ideas (AI agent)
Filtre les articles selon leur pertinence pour LinkedIn (grâce au LLM).

Résume chaque article en 250 mots maximum (style clair, humain, engageant).

Stocke les idées retenues dans un Google Sheet pour publication ou relecture.

🧱 Prérequis
✅ Un compte n8n.cloud ou une instance auto-hébergée

✅ Un compte OpenAI (clé API)

✅ Un compte Google avec accès à Google Sheets

✅ (Optionnel) Une base de flux RSS à surveiller

🚀 Étapes d'installation
1. Importer les deux workflows
Depuis n8n, clique sur “Import Workflow” puis colle les JSON :

L00 - Fetch Articles (RSS).json

L01 - Collect Ideas (AI agent).json

Active les deux workflows.

2. Configurer le workflow L01 - Collect Ideas (AI agent)
🔑 Remplace la clé API OpenAI dans le noeud “OpenAI Chat Model”

📄 Connecte ton compte Google Sheets via OAuth2 ou API Key

📍 Spécifie le nom de ton fichier Google Sheet et l’onglet cible (ex. LinkedIn Ideas)

3. Configurer le workflow L00 - Fetch Articles (RSS)
📰 Dans le noeud "RSS Feed", entre tes flux préférés (ex : dev.to, Hacker News, InfoQ, Medium…)

🔗 Dans le noeud “HTTP Request”, colle l’URL du webhook déclenché par L01

4. Tester ton système
Lance manuellement le workflow L00 ou programme-le pour s’exécuter quotidiennement.

Vérifie que les idées apparaissent dans ton Google Sheet, résumées et prêtes à l’emploi !

✍️ Personnalisation
Tu peux facilement :

Ajouter ou supprimer des flux RSS

Changer les critères de filtrage de l’IA (tech, freelance, DevOps…)

Ajouter une classification par thème ou score de pertinence

🧪 Exemple de flux RSS utiles
Source	Flux RSS URL
InfoQ	https://www.infoq.com/feed/
dev.to	https://dev.to/feed/tag/java
Medium (Java)	https://medium.com/feed/tag/java
Hacker News	https://hnrss.org/frontpage
Stack Overflow	https://stackoverflow.blog/feed/

🤖 Exemple d'idée générée
Titre : “Unlocking Java’s Power with Virtual Threads”
Résumé : L’article explore les bénéfices des Virtual Threads introduits dans Java 21 pour améliorer la scalabilité des applications serveurs, sans changer le code métier. Utile pour les développeurs back-end souhaitant mieux comprendre les performances de la JVM moderne.
Lien : https://medium.com/java-thread

