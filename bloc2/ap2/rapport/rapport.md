# Rapport de suivi de projet

Chaque groupe aura à rendre compte de l'avancée du projet en fournissant régulièrement un **rapport de suivi de projet**.

## Contenu d'un rapport de suivi de projet

Les sections suivantes décrivent le contenu attendu dans le rapport. Quel que soit l'état d'avancée du projet, mettez un soin particulier dans la rédaction de ce rapport, détaillez au maximum, veillez à un aspect et un contenu professionnels. La notation prend autant en compte la qualité du rapport et son professionnalisme que la qualité technique de la production. Intégrez tout ce qui est décrit ci-dessous. Tout manquement sera pénalisé.

## Apport des membres

Les contributions de chacun des membres de l'équipe doivent être clairement indiquées.

## Journal de bord

Un journal de bord doit être inclus. Il détaille les activités de chaque membre de l'équipe lors de chaque séance, les tâches effectuées, le temps passé, les difficultés rencontrées, ou toute autre remarque jugée pertinente.

## Analyse des besoins

À partir du cahier des charges (très verbeux), vous produirez un document qui synthétisera le plus simplement possible l'ensemble des besoins exprimés.

## Fonctionnalités

La description technique détaillée des fonctionnalités correspondantes aux besoins exprimés, ainsi que leur statut : _en attente_ / _en cours_ / _terminée_.

## Outils de gestion de projet

La description des outils de gestion de projet que vous avez mis en place pour sa réalisation : outils numériques (Trello, Jira...), techniques de gestion mises en place au sein de l'équipe, etc. Des captures d'écran seront fournies lorsque cela sera pertinent (notamment un tableau Kanban correspondant au point précédent).

## Conception et développement

La description des produits techniques utilisés et des documents associés :

- développement
- bibliothèques Java particulières et bibliothèques externes
- conception de la base de données : analyse, dictionnaire de données, schéma relationnel, diagramme EA...
- une analyse des difficultés rencontrées, comment vous les avez surmontées ou non

## Documentation

Deux types de documentation sont demandées :

### La documentation utilisateur

Un document séparé à l'intention des usagers du logiciel. Format : PDF, Markdown ou HTML.

### La documentation du code

La documentation du code est intégrée au code source, au [format Javadoc](https://koor.fr/Java/Tutorial/java_javadoc_introduction.wp) pour les classes et les méthodes publiques. Elle documente ce que font chacune de ces classes et méthodes.

À partir de cette documentation _inline_, on générera également une documentation HTML grâce à l'outil Javadoc (voir le lien ci-dessus également). Cette documentation automatiquement générée sera hébergée avec le reste de votre rapport.

La documentation technique comprendra également une section indiquant comment tester le code fourni : que doit faire le testeur pour lancer l'application dans les conditions souhaitées ? Y a-t-il des outils, des choses particulières à installer ? Notamment, comment charger le jeu de test de données fourni ?

## Support

Le document pourra être présenté sous l'une des deux formes suivantes : PDF ou hébergé sur le web.

### Rapport PDF

Si vous choisissez la forme PDF, le fichier devra être présent dans votre dépôt Github, dans un répertoire situé à la racine et appelé *rapport*. Les annexes (voir section « Annexes ») seront également placées dans ce répertoire (dans le rapport PDF, vous référencerez ces documents dans les sections qui y correspondent - tout document non cité dans le rapport est considéré comme absent).

### Rapport hébergé sur le web (forme préférée)

On préférera héberger le rapport sur le web. Une valeur sûre est l'hébergement sur le dépôt du projet grâce à _Github Pages_ ou au _Github Wiki_ de votre projet. Utilisez alors Markdown pour structurer votre rapport, et insérer des liens markdown vers les images, les autres pages, les documents annexes... Le fichier README.md, à la racine de votre dépôt, contiendra un lien vers votre page principale de rapport.

## Annexes

Les annexes sont les fichiers externes qui n'ont, par commodité, pas été inclus directement dans le rapport (schémas numériques ou numérisés, MOCODO, sketches d'interfaces graphiques, photos, fichiers .sql d'exportation, documentation utilisateur, documentation Javadoc, etc.)

## Code

Le code effectif de l'application qui sera dans le dépôt devra être une version immédiatement fonctionnelle et testable de ce qui a été décrit comme implémenté dans le rapport. Vous ne pourrez inclure de code non-fonctionnel que s'il n'empêche pas le programme de se dérouler correctement (commentez-le si nécessaire) et en référençant ce code dans votre rapport, là où vous expliquerez pourquoi la fonctionnalité n'est pas terminée.

## Rapport de fin de projet

En fin de projet, le rapport de suivi deviendra tout naturellement votre rapport final.

Dans ce rapport final uniquement, sera ajoutée une section particulière : un bilan de cette première expérience de travail en équipe en mode projet, ce que vous en retirez, ce que vous changerez dans l'optique de vos futurs projets.
