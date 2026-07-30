# Paul-Jean Poirson

[LinkedIn](https://www.linkedin.com/in/paul-jean-poirson/)

---

## Sur le terrain

### [Cartographie IA & déploiement en PME](./cartographie-ia)

**S'installer dans les équipes pour découvrir le processus réel — celui qu'aucun cahier des charges ne décrit — et en dériver ce qui peut effectivement être déployé.**

Huit services d'une PME cosmétique française (distribution pharmacie B2B, e-commerce B2C), pris un par un, en salle avec les gens qui font le travail : commerce, back-office, supply chain, influence, R&D / réglementaire, comptabilité, force terrain, plus une session de montée en compétence transverse.

Le point de départ n'est pas l'outil mais la journée de travail — ce qui prend du temps, ce qui se perd entre deux systèmes, ce qu'on ne fait plus faute de temps. Une centaine de cas d'usage recensés, priorisés de P0 (prérequis bloquants) à P4, avec les dépendances rendues explicites et les briques mutualisables identifiées entre services.

Les deux phases ne se sont pas succédé : l'implémentation a démarré dès les premiers ateliers, avec les équipes de développement, pendant que les volets suivants restaient à explorer. À fin juillet 2026 : trois systèmes en production, deux en test, quatre chantiers engagés. Le premier livré est celui qui avait été désigné comme le blocage principal de son service.

Trois constats structurants sont sortis du terrain, qu'aucune spécification écrite en amont n'aurait produits : le goulot d'étranglement est la donnée et jamais le modèle ; un quart des irritants remontés ne relèvent pas de l'IA mais d'un bug ou d'un contrôle redondant ; et brancher un assistant sur un partage documentaire existant élargit le périmètre d'accès réel sans qu'aucune permission n'ait changé.

Exemple détaillé d'un système livré : [pipeline d'analyse des appels commerciaux](./cartographie-ia/pipeline-appels).

#### Stack IA

- **Claude** — analyse des transcriptions, structuration des cas d'usage, rédaction des livrables
- **Claude Code** — pipeline de génération documentaire (`docx` via Node.js), charte constante sur les huit volets, régénérable après retour terrain

#### Approche

- Immersion service par service, atelier ouvert plutôt que questionnaire
- Vérité terrain : croisement transcription intégrale × compte rendu structuré
- Chiffrage à la source — une tâche se priorise sur une durée, pas sur un adjectif
- Priorisation P0–P4 : effort, impact, dépendances, KPI, points d'arbitrage ouverts
- Lecture transverse pour éviter de financer cinq fois la même brique
- Quick win identifié dans chaque volet, lançable sans dépendance technique
- Implémentation menée en parallèle du terrain, avec les équipes de développement (Salesforce, PHP, Python)

→ **[Documentation projet](./cartographie-ia)**

---

## Projet personnel

### ❡ [Corruption-Z](./corruption-z) — [corruption-z.com ↗](https://corruption-z.com)

**Un jeu vidéo et un univers fictionnel développé avec l'IA, sous direction humaine stricte.**

Survival-horror gothique-cosmique mené de bout en bout en solo, où l'IA est utilisée comme partenaire de production sur l'ensemble de la chaîne créative — cadrage du lore, écriture narrative, génération d'articles SEO, automatisation éditoriale — tout en gardant la direction artistique et la voix unifiées.

#### Stack IA

- **Claude** — lore, rédaction, design system
- **ChatGPT, Gemini, Cursor, Claude Code** — programmation du jeu
- **Claude Code** — pipeline éditorial automatisé → **120 articles créés et planifiés à ce jour**
- **Midjourney** — direction visuelle
- **Suno** — direction musicale

#### Stack technique

- **Le jeu**
    - Node.js, framework Sails.js
    - MongoDB
    - Git workflow
- **Le site public**
    - Astro · Cloudflare Pages · Workers + Cron Triggers
    - Content Collections
    - Git workflow

→ **[Documentation projet](./corruption-z)**

---

*Dernière mise à jour : 30 juillet 2026*
