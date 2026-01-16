# Cahier des charges du projet « Application Gestion de frais »

Développement d'une application de gestion des frais de déplacement, de restauration et d'hébergement générés par les déplacements des visiteurs.

## Domaine d'étude

L'entreprise souhaite porter une attention nouvelle à sa force commerciale dans un double objectif : obtenir une vision plus régulière et efficace de l'activité menée sur le terrain auprès des praticiens, mais aussi redonner confiance aux équipes malmenées par les fusions récentes.

### Les visiteurs

La force commerciale d'un laboratoire pharmaceutique est assurée par un travail de conseil et d'information auprès des prescripteurs. Les visiteurs médicaux (ou délégués) démarchent les médecins, pharmaciens, infirmières et autres métiers de santé susceptibles de prescrire aux patients les produits du laboratoire. L'objectif d'une visite est d'actualiser et rafraîchir la connaissance des professionnels de santé sur les produits de l'entreprise. Les visiteurs ne font pas de vente, mais leurs interventions ont un impact certain sur la prescription de la pharmacopée du laboratoire.

Pour donner une organisation commune aux délégués médicaux, l'entreprise a adopté l'organisation de la flotte de visiteurs existant chez Galaxy, selon un système hiérarchique par région et, à un niveau supérieur, par secteur géographique (Sud, Nord, Paris-Centre, Antilles-Guyane, etc).

Il n'y a pas eu d'harmonisation de la relation entre les personnels de terrain (Visiteurs et Délégués régionaux) et les responsables de secteur. Les habitudes en cours avant la fusion ont été adaptées sans que soient données des directives au niveau local. On souhaite améliorer le contact entre ces acteurs mobiles autonomes et les différents services du siège parisien de l'entité Europe. Il s’agit d’uniformiser la gestion du suivi des visites.

### Les déplacements

Les déplacements et actions de terrain menées par les visiteurs engendrent des frais qui doivent être pris en charge par la comptabilité. On cherche à agir au plus juste de manière à limiter les excès sans pour autant diminuer les frais de représentation qui font partie de l'image de marque d'un laboratoire. Chez Galaxy, le principe d'engagement des frais est celui de la carte bancaire au nom de l'entreprise. Chez Swiss-Bourdin, une gestion forfaitaire des principaux frais permet de limiter les justificatifs. Pour tout le reste, le remboursement est fait après retour des pièces justificatives. Une gestion unique de ces frais et remboursement pour l'ensemble de la flotte visite est souhaitée.

### Objectif

Les équipes du service développement auront à produire puis à fournir les éléments applicatifs permettant la gestion des frais de déplacement.

## Description du domaine de gestion

### La gestion des frais de déplacement

Grand poste de dépense, la gestion des frais de déplacement des visiteurs demande un suivi très précis. L’enveloppe annuelle pour ce seul poste s’élève à près de 25 millions d’euros. Il n’est donc pas question de le laisser s’envoler, tout en ne limitant pas les visiteurs à des hôtels de second ordre ou des repas chiches (il en va aussi de l’image de marque du laboratoire et de la motivation des équipes).

Les prix d’hébergement ou de nourriture étant variés d’un lieu à l’autre, d’une région à l’autre, il a été procédé à une évaluation statistique permettant de dégager un montant forfaitaire dans la fourchette haute des dépenses pour chaque type de frais standard : repas midi, nuitée (hôtel), kilométrage (remboursement des frais kilométriques, chaque visiteur dispose d'un badge pour le télépéage pour éviter le remboursement de ces petits montants).

Le remboursement de l'ensemble des frais engagés par les visiteurs s’organise mensuellement et donne lieu à une fiche de frais identifiée par le numéro du visiteur et le mois de l’année.

### Organisation des remboursements

La gestion est la suivante :

- à chaque dépense type (hôtel, repas...) correspond un montant forfaitaire appliqué (on parle de frais « forfaitisé »). Le justificatif n’est pas demandé (les rapports de visite serviront de preuve) mais doivent être conservés pendant trois années par les visiteurs. Des contrôles réguliers sont faits par les délégués régionaux qui peuvent donner lieu à des demandes de remboursement de trop perçu par le visiteur ;
- pour toute dépense en dehors du forfait (repas en présence d'un spécialiste lors d'une animation, achat de fournitures, réservation de salle pour une conférence, etc.), le visiteur enregistrera la date, le montant et le libellé de la dépense. Il doit fournir au service comptable une facture acquittée.

### Processus à informatiser

Actuellement, au plus tard le 20 de chaque mois, le service comptable adresse aux visiteurs la fiche d'état de frais pour le mois en cours ([PDF fiche d'état de frais engagés](fiche_etat_frais.pdf)). L'application devra permettre de produire automatiquement l'équivalent de ces fiches de manière à les mettre à disposition des visiteurs pour la saisie en ligne.

#### Saisie et consultation

Après authentification grâce aux identifiants à leur disposition, les visiteurs saisissent les quantités de frais forfaitisés et les frais hors-forfait engagés pour le mois écoulé.

Ils ont accès en modification à la fiche tout au long du mois et peuvent y ajouter de nouvelles données ou supprimer des éléments saisis.

Les fiches de frais saisies peuvent être consultées par un visiteur jusqu’à 12 mois en arrière (au mois d’août 2025, on peut consulter des frais engagés de août 2024 à juillet 2025).

#### Clôture

La clôture d'une fiche est réalisée selon l’une des modalités suivantes :

- à la première saisie pour le mois N par le visiteur, sa fiche du mois N-1 est clôturée (si elle ne l’est pas déjà) ; par exemple, si un visiteur saisit des frais pour le mois de septembre dès le 1er septembre (premier jour de disponibilité pour cette fiche), sa fiche d’août est clôturée automatiquement ; un visiteur doit donc s'assurer que la saisie des frais du mois N-1 est toujours terminée avant de commencer sa saisie du mois N ;
- au début de la campagne de validation des fiches par le service comptable (voir section suivante), l'application clôture automatiquement toutes les fiches non clôturées du mois qui va être traité (le mois précédent) ; par exemple, la campagne de validation des fiches du mois d'août débute le 10 septembre et toutes les fiches non clôturées d'août sont clôturées automatiquement.

Ainsi, une fiche du mois N-1 est toujours clôturée entre le 1er et le 10 (inclus) du mois N.

#### Campagne de validation

Entre le 10 et le 20 du mois suivant la saisie par les visiteurs, le service comptabilité opère une validation des fiches.

Les comptables contrôlent que les frais forfaitisés sont conformes : nombre de jours enregistrés ne dépassant pas le nombre de jours effectivement travaillés (congés), distance kilométrique cohérente, éventuellement consultation des fiches de comptes-rendus pour s’assurer des déplacements effectifs. En cas d’incohérence ou d’erreur constatée, un contact est pris par téléphone avec le visiteur pour régler le litige. Les valeurs sont corrigées en conséquence directement sur l'état de frais par le comptable.

Pour les frais hors-forfait, le service comptable s’appuie sur les factures acquittées adressées par les visiteurs au plus tard le 10 du mois suivant la saisie. Les agents valident ou non (frais non justifiés ou non professionnels par exemple) les éléments de la demande. Un frais non validé reste sur l'état de frais mais est indiqué comme « rejeté », avec un motif de refus spécifié par le comptable. Le visiteur pourra voir, en consultant son historique des 12 derniers mois, les frais forfaitisés effectivement remboursés et les frais hors-forfait rejetés (avec le motif du rejet).

Les éléments reçus après le 10 seront reportés sur le mois ultérieur et seront basculés automatiquement sur la fiche du mois suivant leur saisie (éventuellement créée par l’application si elle ne l’est pas encore) par les comptables.

Après la clôture, les visiteurs peuvent consulter l’évolution de la fiche mais ne peuvent plus la modifier.

Les agents comptables reportent sur chaque facture reçue le numéro de matricule du visiteur, la date (année/mois) de prise en charge et les classent par ordre chronologique dans une pochette nominative pour chaque visiteur.

La mise en paiement est faite au 20 du mois suivant la saisie par les visiteurs.

L'**état** de la fiche de frais fera l'objet d'un suivi précis qui sera affiché lors de la consultation, selon le cycle suivant :

![état_fiche](état_fiche_de_frais.png)

Actuellement, lorsque la fiche de frais arrive dans l'état « Remboursée », une fiche papier de remboursement de frais est éditée par le service comptabilité et remise au visiteur ([PDF fiche de remboursement de frais engagés](fiche_remboursement_frais.pdf)).

## Cahier des charges

### Définition du besoin

#### Définition

Le suivi des frais est actuellement géré de plusieurs façons selon le laboratoire d'origine des visiteurs. On souhaite uniformiser cette gestion. L'application doit permettre d'enregistrer tout frais engagé, aussi bien pour l'activité directe (déplacement, restauration et hébergement) que pour les activités annexes (événementiel, conférences, autres), et de présenter un suivi daté des opérations menées par le service comptable (mises à jour de l'état de la fiche).

#### Forme

L'application destinée aux visiteurs, délégués et responsables de secteur sera accessible depuis un ordinateur, tout comme la partie utilisée par les services comptables.

### Contraintes

#### Environnement technique

- Langage et écosystème Java
- Interface graphique de type bureau en JavaFX
- Gestionnaire de base de données MySQL
- JDBC pour l'interface entre le code Java et le SGBDR
- Toute autre bibliothèque (internes au JDK ou externes) que vous jugerez nécessaire

#### Modules

L'application présente deux modules :

- enregistrement et suivi par les visiteurs
- enregistrement des opérations par les comptables

#### Documentation

La documentation devra présenter l'arborescence des écrans pour chaque module, le descriptif des éléments, classes et bibliothèques utilisées, la liste des frameworks ou bibliothèques externes utilisés, la liste des divers outils de gestion de projet utilisés.

#### Responsabilités

Le commanditaire fournira à la demande toute information sur le contexte nécessaire à la production de l'application. Les demandes se feront sous la forme d'un ticket sur le dépôt Github (onglet _Issues_).

Le prestataire est à l'initiative de toute proposition technique complémentaire.

Le prestataire fournira un système opérationnel, une documentation technique permettant un transfert de compétence et un mode opératoire propre à chaque module.

## Spécifications fonctionnelles de l’application de gestion des frais

Ce document concerne les spécifications fonctionnelles de l'application « Gestion des frais ».

Cette application est destinée aux visiteurs médicaux et personnels du service comptable, les premiers pour renseigner et consulter leurs états de frais, les seconds pour réaliser le suivi des états de frais des visiteurs médicaux jusqu'à leur règlement.

#### Cas d'utilisation

Les besoins sont exprimés ici à l'aide des cas d'utilisation : le diagramme des cas d'utilisation pour la vue synthétique de « qui fait quoi », puis une fiche par cas d'utilisation pour décrire les échanges entre le système et l'utilisateur.

### Diagramme des cas d'utilisation

![diagramme_ucs](diagramme_ucs.png)

### Les fiches des cas d'utilisation (_Use Case_, ou _UC_)

#### Cas d'utilisation 1

- Nom cas d’utilisation : Se connecter
- Acteur déclencheur : Visiteur médical ou Comptable
- Pré conditions : Néant
- Post conditions : L’utilisateur est reconnu visiteur médical ou comptable

- Scénario nominal :

1. Le système affiche un formulaire de connexion
2. L'utilisateur saisit son login et son mot de passe et valide
3. Le système contrôle les informations de connexion, informe que le profil _Visiteur_ ou _Comptable_ est activé, et maintient affichée l'identité du visiteur médical / comptable connecté.

- Exceptions :

  - 3a. : le nom et/ou le mot de passe n’est pas valide
    - 3-a.1 Le système en informe l’utilisateur ; retour à l'étape 1

- Contraintes : Néant

- Questions ouvertes : Néant

#### Cas d'utilisation 2

- Nom cas d’utilisation : Renseigner fiche de frais
- Acteur déclencheur : Visiteur médical
- Pré conditions : Visiteur médical authentifié
- Post conditions : Néant

- Scénario nominal :

1. L’utilisateur demande à saisir un ou plusieurs frais pour le mois courant.
2. Le système retourne les frais actuellement saisis - éléments forfaitisés et hors-forfait - pour le mois courant.
3. L’utilisateur ajoute ou modifie éventuellement une ou des valeurs des frais au forfait et demande la validation.
4. Le système enregistre cette ou ces modifications et retourne ces valeurs à jour.
5. L’utilisateur ajoute éventuellement un nouveau frais hors-forfait en renseignant les différents champs (date d'engagement, libellé, montant) et valide.
6. Le système enregistre la ligne de frais hors-forfait.

- Exceptions :

  - 2.a C’est la première saisie pour le mois courant. Si ce n’est pas encore fait, le système clôt la fiche du mois précédent et crée une nouvelle fiche de frais avec des valeurs initialisées à 0. Retour à 3.
  - 4.a. Une valeur modifiée n’est pas numérique : le système indique « Valeur numérique attendue ». Retour à 3.
  - 6.a Un des champs n'est pas renseigné : le système indique : « Le champ date (ou libellé ou montant) doit être renseigné ».
  - 6.b La date d'engagement des frais hors-forfait est invalide : le système indique « La date d'engagement doit être valide ». Retour à 5.
  - 7.1 L’utilisateur sélectionne un frais hors-forfait pour suppression.
    - 7.2 Le système enregistre cette suppression après une demande de confirmation.

- Contraintes : Néant

#### Cas d'utilisation 3

- Nom cas d’utilisation : Consulter mes fiches de frais
- Acteur déclencheur : Visiteur médical
- Pré conditions : Visiteur médical authentifié
- Post conditions : néant

- Scénario nominal :

1. L'utilisateur demande à consulter ses frais.
2. Le système invite à sélectionner un mois donné.
3. L'utilisateur sélectionne un mois donné, puis valide.
4. Le système affiche l'état de la fiche de frais avec la date associée, les éléments forfaitisés – quantité pour chaque type de frais forfaitisé - et non forfaitisés – montant, libellé et date d'engagement - existant pour la fiche de frais du mois demandé.

- Exceptions : néant si les recommandations ci-dessous sont appliquées

- Contraintes : néant

- Questions ouvertes :

La sélection d'un mois pourra être facilitée par l'IHM. Il est possible de proposer les mois pour lesquels le visiteur médical connecté dispose d'une fiche de frais. On pourra se restreindre à remonter jusqu'au début de l'année civile précédente. Cela évitera en amont la gestion d'erreurs lors de la sélection du mois (étape 3).

#### Cas d'utilisation 4

- Nom cas d’utilisation : Valider fiche de frais
- Acteur déclencheur : Comptable
- Pré conditions :
  - Utilisateur Comptable authentifié
  - Toutes les fiches du mois qui vient de s’achever sont clôturées par un script
  - Le comptable dispose de tous les éléments pour évaluer la conformité des frais forfaitisés
- Post conditions : Néant

- Scénario nominal :

1. L’utilisateur demande à valider les fiches de frais
2. Le système propose de choisir le visiteur et le mois concernés
3. L’utilisateur sélectionne les informations et valide
4. Le système affiche le détail de la fiche de frais (frais forfaitisés et hors-forfait)
5. L’utilisateur actualise les informations des frais forfaitisés.
6. Le système indique que la modification a été prise en compte et affiche les informations actualisées.
7. L’utilisateur valide ou refuse des lignes de frais hors-forfaits, ou encore les reporte au mois suivant.
8. Le système permet de voir visuellement les lignes acceptées, refusées, et reportées. Pour chaque ligne refusée, le système permet de renseigner un champ pour indiquer la raison du refus.
9. L'utilisateur peut choisir de valider la fiche, ou d'y revenir plus tard si le travail n'est pas terminé.
10. Le système passe éventuellement la fiche à l’état « Validée » et met à jour la date de modification de la fiche.

- Exceptions :

  - 4-a : Aucune fiche de frais n’existe, le système affiche « Pas de fiche de frais pour ce visiteur ce mois ». Retour au 2
  - 7.a : L'utilisateur demande le report des frais hors-forfait pour lesquels une facture acquittée n’a pas été reçue dans les temps. Ce HF est automatiquement inclus dans l'ensemble des HF de l'état de frais du mois suivant. Si la fiche du mois suivant n’existe pas, le système génère une nouvelle fiche pour le visiteur en cours de traitement et pour le mois suivant. Cette nouvelle fiche a des valeurs à 0 pour les frais forfaitisés et est dans l’état « Saisie en cours ». Retour au 9

- Contraintes : néant

- Questions ouvertes : néant

#### Cas d'utilisation 5

- Nom cas d’utilisation : Suivre le paiement fiche de frais
- Acteur déclencheur : Comptable
- Pré conditions : Utilisateur Comptable authentifié
- Post conditions : Néant

- Scénario nominal :

1. L’utilisateur demande à suivre le paiement des fiches de frais.
2. Le système propose de choisir une fiche de frais parmi celles à valider et mises en paiement
3. L’utilisateur sélectionne les informations et valide
4. Le système affiche le détail de la fiche de frais (frais forfaitisés et hors-forfait)
5. L’utilisateur « Met en paiement » la fiche de frais
6. Le système modifie l’état de la fiche à « Mise en paiement » et met à jour la date de modification.

- Exceptions :

  - 4-a : Aucune fiche de frais n’existe, le système affiche « Pas de fiche de frais pour ce visiteur ce mois ». Retour au 2
  - 5.a : L’utilisateur indique que la fiche a été effectivement payée
  - 6.a : Le système modifie l’état de la fiche à « Remboursée » et enregistre la date de modification

- Contraintes : néant

- Questions ouvertes : néant

## Enregistrement des données

On fournira un diagramme entité-association et le schéma relationnel correspondant (on pourra utiliser [Looping](https://www.looping-mcd.fr/) ou [MoCoDo](http://www.mocodo.net/)). Un jeu de données de test devra être produit et pourra même être éventuellement généré par un outil (ex. : [GenerateData](http://www.generatedata.com))

## Évolutions possibles

- Hacher le mot de passe dans la base de données si ce n'est pas déjà fait
- Au niveau de l'UC « Consulter fiche frais », rendre la fiche de frais facilement imprimable, par exemple proposer la génération d'un fichier PDF.
- Au niveau des UCs « Saisir fiche frais » et "Consulter fiche frais", prévoir l'affichage des éléments intermédiaires de calcul permettant d'apprécier le montant correspondant à chaque ligne de frais forfaitisé, ainsi que les totaux des éléments forfaitisés et hors-forfait, de sorte à être plus proche du document relatif à la fiche de demande de remboursement.

## Contraintes du projet

- Travail collaboratif, mais les apports de chacun doivent être clairement distingués et documentés au fur et à mesure de l'avancement
- Utilisation d'outils numériques facilitant la gestion de projet et le travail collaboratif :
  - obligatoire (rendu sous cette forme) : dépôt Github (fourni) sur lequel seront rendus disponibles vos productions : code, rapports...
  - Googles Docs (rapport...) / Sheets / Drive
  - plateforme de discussion (Slack, Discord...)
  - plateformes de gestion de projet agile (méthode Kanban => Trello, Notion...)
  - tout autre outil, en ligne ou non, que vous jugerez productif ; sauf si cela est nécessaire (ex. : votre IDE comme VS Code), **évitez d'utiliser des applications qui ne permettent pas l'édition collaborative** (exemple de mauvaise pratique : travailler chacun sur un bout du rapport et se passer les fichiers en espérant qu'une version qui contient tout dans le bon ordre et sans doublon émerge facilement)
  - NB : tous les outils utilisés seront référencés dans vos rapports
