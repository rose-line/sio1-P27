# Utilisation de Git et GitHub

## Installation de Git

Git est un logiciel de gestion de versions décentralisé. Cela va vous permettre de sauvegarder vos travaux en local puis de les synchroniser avec un dépôt distant en ligne (GitHub dans notre cas).

Pour installer Git :

- Téléchargement : https://git-scm.com

- Installation : laissez toutes les options par défaut

- Redémarrage de la machine après installation

## Compte GitHub

GitHub est une plateforme de développement collaboratif utilisant Git. Cela va vous permettre dans un premier temps de sauvegarder vos travaux en ligne et de les partager avec votre professeur. Chaque étudiant doit créer un compte GitHub.

- Création de compte : https://github.com

- Évitez d'utiliser un pseudo qui ne fasse pas professionnel : votre dépôt GitHub pourra être consulté par des recruteurs potentiels (suggestion : *prénom.nom* ou *pnom*).

- Évitez d'utilisez votre email `ltpdampierre.fr` : ce dernier ne fonctionnera plus après la fin de votre scolarité.

- Une fois le compte créé, vous devez, dans votre profil, renseigner votre nom complet (bouton « *Edit profile* »), et ce quel que soit le pseudo que vous avez choisi.

## Configuration locale de Git

- Ouvrez un terminal en ligne de commande (sous VS Code ou depuis votre système)

- Cette première commande permet de configurer votre pseudo (remplacez « Jean Dupont » par votre pseudo sur GitHub)

  - `git config --global user.name "Jean Dupont"`

- Cette seconde commande permet de configurer votre email (remplacez « jean.dupont@gmail.com » par votre adresse email utilisée sur GitHub)

  - `git config --global user.email jean.dupont@gmail.com`

## Utilisation basique

On décrit ici l'utilisation basique de Git et GitHub via Visual Studio Code.

### Création d'un dépôt Git et publication automatique sur GitHub

C'est la première étape : faire gérer votre projet par Git et le relier à votre compte GitHub.

- Sous VS Code, localisez le panneau de *gestion de version* (à gauche, icône avec trois cercles reliés).

- Cliquez sur le bouton « *Publish to GitHub* ».

- VS Code vous demande d'indiquer le nom du dépôt (par défaut, le nom du dossier courant) et si le dépôt doit être public ou privé :

  - *public* : votre dépôt sera visible par tout le monde

  - *private* : votre dépôt sera visible uniquement par vous et les personnes que vous aurez invitées

- Si c'est la première fois, GitHub va vous demander éventuellement de vous connecter, et d'autoriser VS Code à accéder à votre compte GitHub.

- Une fois le dépôt créé et publié, VS Code vous propose d'ouvrir le dépôt sur GitHub (vous pourrez y vérifier que le dépôt a été créé sur votre compte et que le contenu de votre dossier de projet a été envoyé en ligne).

### Suivi des modifications avec Git

Une fois que votre projet est sous gestion de version avec Git, celui-ci va automatiquement surveiller les modifications apportées aux fichiers. À présent, vous allez régulièrement (à chaque fin d'exercice, ou même à chaque petite avancée significative) sauvegarder vos modifications localement (*commit*) puis les envoyer sur GitHub (*synchronisation*).

- **Suivi des modifications** : à chaque modification de fichier, le panneau de gestion de version indique qu'il y a des modifications non suivies (un chiffre rouge indique le nombre de fichiers modifiés) ; vous pouvez tester en modifiant légèrement un fichier du projet (ajoutez une ligne vide par exemple) ; le fichier modifié apparaît dans la liste des modifications du panneau.

- **Ajout à l'index** : cliquez sur l'icône `+` à côté de chaque fichier modifié pour indiquer que vous souhaitez que cette modification soit prise en compte dans la prochaine sauvegarde (on dit qu'on « ajoute le fichier à l'index »).

- **Message de *Commit*** : quand l'index est prêt, vous allez procéder à ce qu'on appelle un *commit* ; un *commit* enregistre les modifications de l'index dans l'historique de votre projet. Vous devez d'abord saisir un message de *commit* dans le champ prévu à cet effet (tout en haut du panneau). Ce message doit être court mais explicite sur les modifications apportées (exemple : « *exercice 3 fini* » ou « *correction du bug d'affichage* »).

- ***Commit*** : cliquez sur l'icône `Commit ✓` pour valider le *commit* : à ce moment, **les modifications du commit sont sauvegardées localement, mais pas sur GitHub**.

- **Synchronisation avec GitHub** : pour envoyer les modifications sur GitHub, cliquez sur le bouton « *Synchronize Changes* ». À ce moment, **les modifications du commit sont visibles sur GitHub**.

- Note : il arrivera que vous oubliiez de renseigner le message de *commit* avant de cliquer sur l'icône `Commit ✓` ; dans ce cas, VS Code ouvrira un fichier, et vous devrez ajouter votre message de *commit* à la fin de ce fichier. Sauvegardez et fermez le fichier. Votre *commit* sera alors effectué.
