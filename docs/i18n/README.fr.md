# Doctor Bones

Doctor Bones est un modèle de dépôt indépendant des fournisseurs d’IA pour le développement assisté par IA.

Il aide à garder la mémoire du projet dans le dépôt, au lieu de la laisser enfermée dans le chat. Il donne à l’équipe humain/IA une discipline de travail partagée : ordres de travail, playbooks, exemples, vérifications, règles de passation et habitudes de préparation aux releases.

## Langues

- [English](../../README.md)
- [Español](README.es.md)
- Français : ce fichier
- [Deutsch](README.de.md)
- [Português do Brasil](README.pt-BR.md)

## Ce que c’est

Doctor Bones n’est pas un autre agent de programmation.

C’est une couche de discipline native du dépôt pour utiliser des assistants IA et des agents de programmation sans perdre l’intention, les contraintes, les vérifications ni l’historique du projet.

Le modèle de base est :

```text
intention humaine
→ l’IA de premier plan clarifie la tâche
→ le dépôt capture une guidance durable
→ l’IA exécutrice réalise un travail borné
→ les vérifications contrôlent ce qui peut l’être
→ la clôture se rattache à l’intention source
```

Pense à l’IA de premier plan comme à l’assistant de planification et d’architecture. Pense à l’IA exécutrice comme au travailleur qui a accès aux fichiers, à un environnement d’exécution, aux tests et aux outils de commit/PR.

Le dépôt est la couche de mémoire et de discipline entre les deux.

## Démarrage

1. Si tu as copié ce modèle, réécris bientôt ce README autour de ton vrai projet.
2. Lis [`examples/README.md`](../../examples/README.md) pour voir les exemples de workflows “day-in-the-life”.
3. Lis [`readme_pmp.md`](../../readme_pmp.md) au moins une fois et garde-le sous la main.
4. Lis [`AGENTS.md`](../../AGENTS.md) avant de demander à un assistant IA de modifier le dépôt.
5. Utilise un ordre de travail pour les tâches substantielles, multi-fichiers, sensibles à l’architecture ou sensibles au processus.
6. Lance les vérifications disponibles avant de considérer le travail comme terminé.

## Prompt de démarrage pour l’IA de premier plan

Remplace `<chemin vers ton dépôt>` par le vrai chemin de ton dépôt. Tu peux aussi demander à ton IA de premier plan de mettre à jour ce README pour ton nouveau projet.

Quand tu démarres un nouveau chat ou un nouvel onglet pour ce dépôt, colle ceci dans l’IA de premier plan :

```text
Tu es l’IA de premier plan pour <chemin vers ton dépôt>

L’état actuel du dépôt passe avant la mémoire du chat. Inspecte l’état actuel du dépôt avant de donner des conseils d’architecture, d’écrire des ordres de travail ou de suggérer des changements du dépôt.

Lis d’abord README.md, examples/README.md, readme_pmp.md, AGENTS.md et la guidance du dossier concerné. Puis identifie l’état actuel, la cible, les contraintes, la décision premier-plan/exécuteur et le plus petit prochain pas utile.
```

## Raccourci d’ordre de travail

Pour un travail substantiel, discute avec l’IA de premier plan jusqu’à ce que la tâche soit claire, puis dis :

```text
Create a workorder and also show it to me here.
```

Tu peux copier un lien vers le fichier d’ordre de travail et demander à ton IA exécutrice, dans un environnement pour ce dépôt, de l’exécuter.

Tu peux aussi copier/coller le corps de l’ordre de travail si tu as demandé à l’IA de premier plan de l’afficher d’abord. Garde ce bloc propre : pas de citations, notes d’assistant, explications, liens supplémentaires ni commentaires dans le corps de l’ordre de travail.

## Vérifications

Lance ceci depuis la racine du dépôt quand c’est disponible :

```text
python tools/pmp_check.py --area all
python -m pytest
```

Si une vérification échoue, colle la sortie exacte de la commande dans l’IA de premier plan et demande la plus petite correction sûre.

## À propos de Doctor Bones

Doctor Bones est une discipline de travail agnostique vis-à-vis des fournisseurs d’IA pour les projets assistés par IA.

La version courte :

```text
intention capturée
portée bornée
contraintes préservées
exécuteur instruit
vérifications requises
clôture rattachée à l’intention source
```

L’explication complète se trouve dans [`readme_pmp.md`](../../readme_pmp.md).
