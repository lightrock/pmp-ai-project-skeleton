Pour l'introduction publique, consulte le [site GitHub Pages de Doctor Bones](https://lightrock.github.io/drbones/).

# Doctor Bones

Doctor Bones est un modèle de dépôt indépendant des fournisseurs pour le développement assisté par IA.

Il t'aide à garder la mémoire du projet dans le dépôt plutôt que piégée dans le chat. Il donne à ton équipe humain/IA une discipline opérationnelle partagée : ordres de travail, playbooks, exemples, vérifications, règles de passation et habitudes de préparation aux releases.

L'idée est que, chaque fois que tu démarres un nouveau projet, tu démarres avec un Doctor Bones.

Tu n'as pas forcément besoin de récupérer ta copie de ce modèle sur ton PC local ou dans ton environnement d'agent pour l'utiliser. Doctor Bones porte son architecture cognitive dans le dépôt lui-même. Si tu suis les instructions de démarrage ci-dessous, ton IA de premier plan devrait avoir assez d'intelligence projet pour raisonner à partir des consignes du dépôt, des exemples, des playbooks, des vérifications et des règles de passation.

Par défaut, rien n'a besoin de "tourner" quelque part au sens traditionnel, et tu n'as pas forcément besoin d'invoquer un exécuteur comme Codex. Oriente d'abord ton IA de premier plan vers l'instance de dépôt appropriée basée sur Doctor Bones. Utilise un exécuteur seulement quand la tâche exige des modifications de fichiers, un environnement d'exécution, des vérifications, des commits ou des pull requests.

## En savoir plus sur l'idée

Avant que l'IA code, apprends au dépôt à parler. Avant que l'IA affirme que c'est terminé, définis ce que terminé veut dire. Avant que l'IA recommande, sépare les preuves de la conclusion. Avant que l'IA applique un patch, définis l'autorité, la vérification et les règles de frontière.

Pouvons-nous définir des standards natifs du dépôt que Cursor, Codex, Claude Code, Copilot... et les bots GitHub devraient respecter ?

Pouvons-nous rendre cela facile à adapter à tes besoins précis ?

## Travail en cours / TODO / À TERMINER

Voir [TODO.md](../../TODO.md) pour la liste de travail approximative de ce qui doit encore devenir des fichiers de dépôt, des schémas, des rubriques, des exemples, des vérifications et des cibles d'intégration.

## Langues

- [English](../../README.md)
- [Español](README.es.md)
- Français : ce fichier
- [Deutsch](README.de.md)
- [Português do Brasil](README.pt-BR.md)
- [हिन्दी](README.hi.md)

## Ce que c'est

C'est une couche de discipline native du dépôt pour utiliser des assistants IA et des agents de programmation sans perdre l'intention, les contraintes, les vérifications ni l'historique du projet.

Le modèle de base est :

```text
intention humaine
→ l'IA de premier plan clarifie la tâche
→ le dépôt capture des consignes durables
→ l'IA exécutrice réalise un travail borné
→ les vérifications contrôlent ce qui peut l'être
→ la finalisation se rattache à l'intention source
```

Pense à l'IA de premier plan comme à l'assistant de planification et d'architecture. Pense à l'IA exécutrice comme au travailleur qui a accès aux fichiers, à un environnement d'exécution, aux tests et aux outils de commit/PR.

Le dépôt est la couche de mémoire et de discipline entre les deux.

## Démarrage

1. Si tu as copié ce modèle, réécris bientôt ce README autour de ton vrai projet.
2. Lis [`examples/README.md`](../../examples/README.md) pour voir les exemples de workflow day-in-the-life.
3. Lis [`readme_pmp.md`](../../readme_pmp.md) au moins une fois et garde-le à portée de main.
4. Lis [`AGENTS.md`](../../AGENTS.md) avant de demander à un assistant IA de modifier le dépôt.
5. Utilise un ordre de travail pour les travaux substantiels, multi-fichiers, sensibles à l'architecture ou sensibles au processus.
6. Lance les vérifications disponibles avant de considérer le travail comme terminé.

## Limite de processus

Ne crée pas les ordres de travail de ton projet dans le dépôt source public Doctor Bones, sauf si tu contribues intentionnellement à Doctor Bones lui-même.

Pour ton propre projet, crée ou utilise d'abord ton propre dépôt à partir de ce modèle. Ensuite, oriente ton IA de premier plan vers l'URL de ce dépôt de projet et crée les ordres de travail là-bas.

Utilise `lightrock/drbones` comme modèle source, implémentation de référence et projet amont. Utilise ton dépôt copié basé sur Doctor Bones comme l'endroit où vivent la mémoire de ton projet, les ordres de travail, les leçons apprises et les changements propres au projet.

## Prompt de démarrage pour l'IA de premier plan

Ce prompt est destiné à un dépôt créé à partir du modèle Doctor Bones. Après avoir copié ce modèle, remplace `<your project repository URL>` par l'URL de ton propre dépôt de projet.

Quand tu démarres un nouveau chat ou un nouvel onglet pour ton dépôt de projet, colle ceci dans l'IA de premier plan :

```text
You are the foreground AI for <your project repository URL>.

Current repo state beats chat memory. Inspect the current project repository before giving
architecture advice, writing workorders, or suggesting repo changes.

Read README.md, examples/README.md, readme_pmp.md, AGENTS.md, and the relevant folder
guidance from the project repository first. Then identify current state, target, constraints,
foreground/executor decision, and the smallest useful next move.
```

## Raccourci d'ordre de travail

Pour un travail substantiel dans ton dépôt de projet copié, discute avec l'IA de premier plan jusqu'à ce que la tâche soit claire, puis dis :

```text
Create a workorder and also show it to me here.
```

Tu peux copier un lien vers le fichier d'ordre de travail et demander à ton IA exécutrice, travaillant dans un environnement pour ton dépôt de projet, de l'exécuter.

Tu peux aussi copier/coller le corps de l'ordre de travail si tu as demandé à l'IA de premier plan de l'afficher d'abord. Garde ce bloc de copier/coller propre : pas de citations, notes d'assistant, explications, liens supplémentaires ni commentaires dans le corps de l'ordre de travail.

## Vérifications

Lance ces commandes depuis la racine du dépôt quand elles sont disponibles :

```text
python tools/pmp_check.py --area all
python -m pytest
```

Si une vérification échoue, colle la sortie exacte de la commande dans l'IA de premier plan et demande la plus petite correction sûre.
