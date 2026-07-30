# Cartographie IA & déploiement en PME

Retour d'expérience sur huit immersions menées dans une PME cosmétique française — distribution pharmacie B2B, e-commerce B2C — pour découvrir les processus réels et en dériver ce qui peut être déployé.

Ce document décrit l'approche, ce que le terrain a produit, et où en est le passage du diagnostic à la livraison. La liste des cas d'usage n'est pas l'intérêt principal ; ce qu'on apprend en la construisant l'est davantage.

---

## Le problème posé

Une entreprise décide d'« intégrer l'IA ». La formulation ne veut rien dire tant qu'on n'a pas mis les mains dans les journées de travail, et elle ouvre deux impasses classiques.

La première consiste à partir de l'outil et à chercher où le plaquer. On obtient des démonstrations qui fonctionnent en réunion et qui ne survivent pas au premier contact avec les données réelles.

La seconde consiste à écrire un cahier des charges depuis le siège, à le confier à un prestataire, et à découvrir dix-huit mois plus tard que le processus décrit dans le document n'est pas celui que les équipes appliquent. C'est l'échec le plus fréquent et le plus coûteux.

L'approche retenue évite les deux en allant s'asseoir dans les services. Pas pour valider une hypothèse : pour découvrir ce qui se passe réellement.

## Le périmètre

Huit immersions, une par service.

| Volet | Nature dominante des besoins |
|---|---|
| Commerce B2B | Agrégation d'information avant appel, transcription, création d'actions |
| Back-office | Pré-saisie de commandes, tickets, réponses standardisées |
| Supply chain | Contrôle de facturation transporteur, détection d'anomalies de prévision |
| Influence | Qualification de profils, veille, contractualisation |
| R&D / réglementaire | Recherche documentaire, contrôle de conformité, cartographie projet |
| Comptabilité / DAF | Audit de fichiers récurrents, réconciliation, construction budgétaire |
| Force terrain | Résumé pré-visite, compte rendu par dictée |
| Transverse | Montée en compétence sur l'usage individuel |

Une centaine de cas d'usage au total.

---

## L'approche

### Aller dans la pièce

Aucune grille imposée en entrée. Un questionnaire ne produit que les réponses qu'il contenait déjà ; une conversation produit ce à quoi personne n'avait pensé. Plusieurs des cas les plus rentables sont apparus en fin de session, sur une remarque incidente — un fichier de plusieurs milliers de lignes mentionné en passant, un contrôle hebdomadaire que personne n'avait jamais chiffré.

Contrepartie assumée : la transcription digresse, revient en arrière, se contredit. C'est le prix de la matière brute, et elle reste exploitable.

### Croiser deux sources

Chaque immersion produit une transcription intégrale et un compte rendu structuré. Le compte rendu donne la charpente ; la transcription donne le détail sur lequel la priorisation se joue réellement — le montant d'un écart, le volume d'un fichier, la fréquence d'une tâche, le nom de l'outil qui bloque. Ce détail ne figure jamais dans une synthèse.

### Chiffrer sur le moment

« Ça prend du temps » ne se priorise pas. « Une heure et demie par semaine » se priorise. Le chiffre doit être demandé pendant la session : après, il n'est plus disponible, et personne ne le reconstruit de mémoire.

### Rendre les dépendances explicites

Priorisation en cinq niveaux, de P0 (prérequis bloquants) à P4 (arbitrage à instruire). Chaque cas porte un effort estimé, un impact, ses dépendances, ses KPI et ses points ouverts.

Les points ouverts comptent autant que le reste : ils rendent visible ce qui n'est pas tranché, plutôt que de le masquer derrière une formulation assurée. Un plan qui ne montre aucune incertitude n'a pas été confronté au terrain.

### Généraliser d'un service au suivant

Le passage obligé une fois les huit volets écrits. Les mêmes briques reviennent sous des habillages différents : le résumé par compte du commerce est le même objet que le résumé par produit de la R&D ; l'agent mail apparaît partout ; le ticketing revient dans trois services. Sans cette relecture, on finance cinq fois la même chose et on obtient cinq implémentations divergentes à maintenir.

### Industrialiser le livrable

Un document par volet, généré par script (`docx` en Node.js). Charte identique sur les huit, régénérable après retour terrain sans repasser par une mise en forme manuelle. Le format compte : un document de travail se corrige et se rediffuse, une présentation se périme.

---

## Ce que le terrain a produit

### Le modèle n'est jamais le goulot d'étranglement

Sur les huit volets, le même prérequis P0 revient : la donnée. Base documentaire éclatée entre plusieurs outils, conventions de nommage absentes, documents fournisseurs répartis sur quatre plateformes selon les habitudes de chacun.

Ce n'est pas une contrainte propre à l'IA — retrouver une information coûte déjà du temps aux équipes. Mais l'IA rend le coût mesurable : une base mal rangée produit un assistant qui se trompe, et l'échec est imputé au modèle alors qu'il vient de l'indexation.

Conséquence pratique : le chantier de structuration a une valeur propre, indépendante de l'IA. C'est un argument nettement plus solide pour le financer.

### Un quart des irritants remontés ne relèvent pas de l'IA

Un bug de synchronisation entre deux systèmes après migration, qui bloque une réconciliation entière. Un contrôle effectué trois fois par trois personnes. Un workflow de validation qui gagnerait à ne se déclencher que sur écart. Une facture papier imprimée, tamponnée, puis ressaisie.

Ils remontent parce que la question posée est « qu'est-ce qui vous prend du temps », pas « où mettriez-vous de l'IA ». Ils sont conservés dans la cartographie, étiquetés comme tels : ce sont souvent les plus rentables, et les écarter pour préserver la cohérence du récit serait malhonnête envers le client.

### Brancher un assistant élargit le périmètre d'accès sans changer les permissions

Le constat le plus intéressant du programme. Un partage documentaire compte vingt-cinq personnes. C'était tenable tant qu'accéder à l'information supposait de savoir où chercher : la friction faisait office de contrôle d'accès implicite.

Un assistant branché sur ce même partage supprime la friction. Chacune des vingt-cinq personnes acquiert une capacité d'extraction qu'elle n'avait pas, sans qu'aucun droit n'ait été modifié. Le périmètre théorique est inchangé ; le périmètre réel ne l'est plus du tout.

Il faut donc redécouper les accès par profil métier **avant** de brancher quoi que ce soit. Aucune documentation d'outil ne réclame ce travail ; il n'apparaît que si on se pose la question à temps.

### Le quick win ne sert pas à gagner du temps

Il sert à acheter la confiance. Un contrôle documentaire qui occupait une demi-journée et prend désormais quelques minutes, testé la semaine suivante sur un dossier contenant une erreur connue, produit davantage d'effet qu'une feuille de route à dix-huit mois.

L'ordre compte : quelque chose qui tourne d'abord, chantier structurant ensuite. L'inverse épuise la patience avant la première démonstration, et il n'y a pas de seconde occasion.

### Le profil moteur pèse plus que l'outil

Dans plusieurs services, une personne utilisait déjà l'IA de son côté, sans qu'on le lui demande. Ce sont ces profils qui portent l'adoption — pas les licences distribuées uniformément ni les référents désignés par organigramme. Les repérer pendant l'immersion coûte zéro et change la trajectoire.

### La montée en compétence obéit à d'autres règles

La huitième session n'a pas produit de cas d'usage à industrialiser mais un guide d'usage individuel : douze usages quotidiens, avec des exemples directement réutilisables. Objet différent, format différent — et probablement le livrable au meilleur rendement à court terme, puisqu'il ne dépend d'aucun développement.

---

## Livrer pendant le terrain, pas après

Les deux phases ne se sont pas succédé : la mise en œuvre a démarré dès les premiers ateliers, pendant que les volets suivants étaient encore à explorer. Le premier service visité était le plus contraint ; il n'y avait aucune raison de le faire patienter jusqu'à ce que le huitième soit documenté.

### Systèmes livrés

- [Pipeline d'analyse des appels commerciaux](./pipeline-appels) — analyse des appels et génération de livrables de coaching.

Ce fonctionnement suppose de travailler avec les équipes qui construisent — développement Salesforce, PHP, Python — plutôt que de leur transmettre un cahier des charges en fin de mission. Le rôle consiste alors à tenir les deux bouts en même temps : continuer à découvrir les processus des services non encore visités, et alimenter en spécifications exploitables ceux qui sont déjà en cours d'implémentation. Les retours des premières mises en production nourrissent en retour les ateliers suivants — on arrive dans le service d'après en sachant ce qui a résisté ailleurs.

État à fin juillet 2026.

| Chantier | Volet d'origine | État |
|---|---|---|
| Pré-saisie des commandes depuis emails et pièces jointes | Back-office | En production |
| Extension de la pré-saisie à l'ensemble de l'équipe | Back-office | En production |
| Lecture automatique des PDF de stock | Back-office / terrain | En production |
| Résumé automatique des fiches de compte | Commerce / terrain | En test |
| Assistant interne de recommandation produit | Transverse | En test |
| Analyse de l'historique conversationnel à des fins de coaching | Commerce | En cours, six livrables |
| Tableau de bord managérial hebdomadaire | Commerce | En attente du précédent |
| Digitalisation des flux comptables (bon à payer, coordonnées bancaires) | Comptabilité / back-office | Cadrage |

### Ce que le déploiement a appris

**Le premier système livré est celui qui avait été désigné comme bloqueur numéro un de son volet.** La pré-saisie des commandes était le point le plus douloureux du back-office ; c'est ce qui est parti en premier et ce qui a été étendu à l'équipe. Le classement issu du terrain a tenu au contact de la réalité.

**L'ordre de livraison reproduit l'ordre du terrain.** Les immersions avaient été séquencées par priorité — le service le plus contraint en premier — et la mise en production a suivi la même séquence, arbitrée sur le temps effectivement gagné. Le back-office concentre les premiers systèmes pour la raison qui en avait fait le premier volet visité. La priorisation n'est donc pas un livrable produit à la fin de la cartographie : elle était déjà à l'œuvre dans la façon dont la cartographie a été menée.

**Un diagnostic couvre, une livraison creuse.** Huit volets cartographiés, trois systèmes en production, tous dans le même service. Avancer de front sur huit périmètres aurait produit huit prototypes et aucun système utilisé quotidiennement.

**Les prérequis P0 n'ont bloqué personne, parce que rien de ce qui a été livré n'en dépendait.** Les critères de sélection — donnée déjà disponible, résultat vérifiable contre une référence connue, aucun développement préalable — ont fait leur travail, l'arbitrage final se jouant sur le temps effectivement rendu aux équipes. La structuration documentaire reste nécessaire pour la suite ; elle n'était pas nécessaire pour démarrer.

**Une chaîne de dépendance s'est matérialisée exactement comme annoncé.** Le tableau de bord managérial attend l'analyse conversationnelle qui doit l'alimenter. C'est précisément l'intérêt de rendre les dépendances explicites : l'attente devient une décision assumée plutôt qu'une surprise en fin de trimestre.

**Un chantier non cartographié est apparu.** Une cartographie date à partir du jour où elle est rendue. Elle sert de base de comparaison, pas de périmètre figé — et la vraie question n'est pas de savoir si de nouveaux sujets émergent, mais si le cadre de priorisation permet de les intégrer sans tout renégocier.

**Le seul incident notable est un problème de couverture de données, pas de modèle.** Sur la production des fiches de coaching, la restitution ne faisait ressortir que deux commerciaux : le modèle tournait correctement, l'échantillon n'était pas représentatif de l'équipe. Détecté et corrigé sur ce livrable, le correctif est en cours de propagation aux autres. Même nature de problème qu'en phase de terrain, trois mois plus tard, sur un objet entièrement différent — et repéré cette fois parce qu'on savait où regarder.

---

## Ce qui a été ajusté en cours de route

Le protocole n'était pas figé au premier atelier. Plusieurs correctifs ont été appliqués pendant le cycle plutôt que notés pour une prochaine fois — c'est le bénéfice direct d'une phase de terrain étalée sur huit sessions au lieu d'un audit unique.

**La question des accès est entrée dans le protocole dès son apparition.** Elle a émergé sur un volet dont la base documentaire était particulièrement sensible, puis a été posée systématiquement dans les immersions suivantes et rétro-appliquée aux volets déjà traités. Elle conditionne l'architecture ; la découvrir en cours de cycle plutôt qu'après aura évité d'avoir à revenir sur des choix déjà faits.

**Le chiffrage est devenu une question posée en séance.** « Combien de temps par semaine » plutôt que « est-ce que ça vous prend du temps ». Une tâche non chiffrée pendant l'atelier ne se chiffre plus après : personne ne reconstitue la durée de mémoire, et elle sort de fait de la priorisation.

**Les cas sans IA ont été étiquetés comme tels dès la restitution**, avec leur propre séquencement. Mélangés aux autres, ils héritaient d'un calendrier qui ne leur convenait pas — alors qu'ils comptent parmi les plus rentables.

**Chaque volet a été relu par le service concerné** avant que la priorisation soit figée. Le document sort du regard de celui qui a animé l'atelier ; c'est l'équipe qui vivra avec, et son arbitrage n'est pas le même.

---

## Stack

- **Claude** — analyse des transcriptions, structuration, rédaction
- **Claude Code** — génération documentaire (`docx` / Node.js), charte constante, régénération après retour terrain

---

*Les éléments nominatifs, financiers et techniques propres à l'entreprise ont été retirés de ce retour d'expérience.*
