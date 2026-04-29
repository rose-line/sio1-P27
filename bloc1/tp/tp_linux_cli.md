# TP Linux CLI - Renforcement de la manipulation en ligne de commande

## Installation Linux ou VM

Vous pouvez réutiliser une VM Linux dont vous disposez déjà (pour info, le TP a été réalisé sous une distribution compatible RHEL). Sans indications contraires, toutes les opérations doivent être effectuées avec un compte utilisateur sans privilèges particuliers (certaines questions nécessiteront néanmoins l'exécution de commandes en tant qu'administrateur : vous utiliserez alors `sudo`). Lorsque des répertoires ou fichiers précisés n'existent pas sur votre système, vous pouvez les remplacer par d'autres répertoires/fichiers similaires (attention de ne pas déplacer/supprimer des fichiers hors de votre répertoire utilisateur).

### Références

- Documents issus de vos propres recherches sur Internet
- La documentation des commandes incluse avec le système (cf partie 4)
- Si vous le souhaitez, le [document compagnon du MOOC « Maîtriser le shell Bash »](www.opimedia.be/DS/languages/Bash/MOOC-Maitriser-le-shell-Bash--Document-compagnon--v2-6-2019.pdf), en français et relativement bien fait

### Les commandes à considérer

`pwd, cd, ls, file, less, head, tail, mkdir, cp, mv, rm, rmdir, touch, echo, set, unset, export, env, alias, history, nl, find, grep, sed`

### Les fonctionnalités du shell à considérer

- « Globbing » de fichier
- Variables Shell
- Variables d'environnement (commandes `export` et `env`)
- Alias de commandes (commande `alias`)
- Historique de commandes
- Redirection d'entrées/sorties (STDOUT, STDERR, STDIN, utilisations des caractères `<` et `>` dans les commandes)
- « Piping » (caractère `|` dans les commandes, bien comprendre différence avec `>`)
- Sous-commandes (`$(commande a executer)` à l'intérieur d'une autre commande)
- Expressions régulières
- Bien comprendre `find` (recherche fichiers) et `grep` (recherche dans fichiers)
- Commande `sed` pour éditer un fichier en ligne de commande (automatiquement), par exemple pour remplacer une chaîne de caractère par une autre
- Commandes d'archivage et de compression : `tar`, `gzip`, `gunzip` `bz2`, `xz`

### 1. Gestion de fichiers

1/ Ouvrir un terminal

2/ Afficher le nom du répertoire courant

3/ En utilisant un chemin absolu, aller directement sur le répertoire `/etc`

4/ À partir de là, et en utilisant un chemin relatif, aller directement sur le répertoire `/etc/skel`

5/ En utilisant un chemin relatif, remonter sur `etc`

6/ Afficher les fichiers du répertoire courant

7/ Même chose en « affichage détaillé », en montrant notamment les permissions, tailles de fichiers, etc. et également les fichiers cachés

8/ Afficher tous les fichiers du répertoire courant qui commencent par `s`

9/ Lancer la commande qui permet de déterminer le type de contenu dans le fichier `/etc/group` (sans afficher le contenu du fichier)

10/ Afficher uniquement les cinq dernières lignes du fichier `/etc/group`

11/ Exécuter la commande qui revient directement à votre répertoire personnel, sans avoir à préciser le nom exact de celui-ci

12/ Créer un répertoire nommé `temp` dans votre répertoire personnel

13/ Copier le fichier `/etc/passwd` dans le répertoire `temp`

14/ Copier le répertoire `/etc/ppp` (et ses éventuels sous-répertoires) dans le répertoire courant (ne pas s'occuper des éventuelles erreurs "permission denied" pour certains fichiers du répertoire)

15/ Renommer le répertoire précédemment copié dans le répertoire courant en `peers`

16/ Mettre à jour le _timestamp_ du fichier `temp/passwd` à la date et heure courantes

17/ Créer un nouveau fichier vide nommé `test` dans le répertoire `temp`

18/ Supprimer le fichier `temp/passwd`

19/ Supprimer le répertoire `peers`

20/ Expliciter : « répertoire courant », « répertoire racine », « répertoire personnel »

### 2. Quelques fonctionnalités du Shell

1/ Afficher toutes les variables shell avec leur contenu. À quoi servent les variables shell ?

2/ Afficher le contenu de la variable `HOME`. À quoi sert cette variable ?

3/ Afficher le contenu de la variable `TEST` (noter que cette variable n'a en fait aucun contenu actuellement)

4/ Faire en sorte que le shell courant affiche plutôt un message d'erreur quand une variable indéfinie est utilisée

5/ Modifier la variable `PATH` pour ajouter le répertoire `/opt`. À quoi sert cette variable ?

6/ Créer une variable d'environnement appelée `EVENT` et lui donner la valeur "maintenant" en utilisant une seule commande

7/ Afficher toutes les variables d'environnement. À quoi servent les variables d'environnement ? Quelle est la différence avec les variables shell ?

8/ Créer un alias dans le shell courant pour la commande `ls` de telle sorte que ça lance la commande `ls -a`

9/ Afficher tous les alias du shell courant

10/ Supprimer du shell courant l'alias défini en question 8/

11/ Afficher une liste des commandes précédemment exécutées

12/ Re-exécuter la dernière commande `ls` de l'historique (interdit de remonter avec la flêche du haut !)

13/ Modifier la variable qui spécifie le nombre maximum de commandes stockées dans l'historique du shell courant (la mettre à 2000)

14/ Exécuter la commande `ps -ef` et utiliser un _pipe_ (`|`) pour passer la sortie à la commande `less`. À quoi sert `ps` ? À quoi sert `less` ? À quoi sert un *pipe* ?

15/ Afficher tous les fichiers dans la structure du répertoire `etc` (sous-répertoires inclus) dont le groupe propriétaire est le groupe `lp` (utiliser la commande `find`)

16/ Afficher tous les lignes dans le fichier `etc/passwd` qui contiennent au moins trois nombres d'affilé

17/ Utiliser la commande `sed` pour afficher le fichier `/etc/passwd` avec toutes les occurrences de `root` remplacées par `XXXX`. Attention, ne surtout pas modifier le fichier `/etc/passwd` lui-même.

18/ Indiquer en quelques mots les usages des commandes `grep`, `find` et `sed`

### 3. Compression

Ces manipulations sont à exécuter dans votre répertoire personnel.

1/ En utilisant la commande `tar` avec l'option « verbose », créer un fichier tar appelé `etcppp.tar` qui contient le contenu du répertoire `/etc/ppp` (ne pas tenir compte des messages d'erreurs potentiels)

2/ Afficher le contenu de l'archive `etcppp.tar` (sans l'extraire)

3/ Créer un répertoire `extraction-tar`

4/ Extraire le contenu de l'archive `etcppp.tar` dans le répertoire `extraction-tar`

5/ Compresser l'archive `etcppp.tar` en utilisant la commande `gzip`, sans écraser le fichier `etcppp.tar` ; le fichier résultant devra se nommer `etcppp.tar.gz`

6/ Compresser l'archive `etcppp.tar` en utilisant la commande `bzip2`, sans écraser ; le fichier résultant devra se nommer `etcppp.tar.bz2`

7/ Comparer les tailles des deux fichiers compressés (`.gzip` et `.bz2`) ; lequel des deux algorithmes semble avoir un meilleur taux de compression ?

8/ Supprimer le fichier `etcppp.tar`

9/ Décompresser le fichier `etcppp.tar.gz`

10/ _En vous référant aux manipulations de cette partie_, expliquez les termes « archivage » et « compression ».

### 4. Obtenir de l'aide

- `man` et ses options (pour les commandes générales et les fichiers de configuration), `help` (pour les commandes shell seulement, comme `cd`), `whatis`, `info`
- Sur n'importe quelle commande, souvent une option `--help` (parfois `-h`) pour une aide plus brève

### 5. Identifier et résoudre les problèmes liés à une commande

Étapes générales de résolution d'un problème (valable au-delà des problèmes de commandes systèmes) :

- **Réunir des informations** : lire les messages d'erreurs, essayer une autre commande basique sur le même fichier (problème d'existence/d'accès ?)
- **Déterminer la cause probable** : utiliser `--help` ou `man/info`, internet (notamment, faire une recherche sur le message d'erreur spécifique), un ami/collègue, voire l'admin système (en fournissant les détails)...
- **S'assurer que toutes les actions sont documentées** : en a-t-on compris suffisamment et a-t-on tout ce qu'il faut pour aller à la fin de la procédure ? Pourra-ton « défaire » chaque étape si ça ne fonctionne pas ?
- **Effectuer les actions** : s'assurer que chaque action produit le résultat intermédiaire attendu avant de poursuivre ; toute la procédure tombe par terre sinon, et il pourra être difficile de « défaire » si on ne sait pas ce qui a été « fait »
- **Vérifier que le problème est résolu** : si ce n'est pas le cas, faut-il « défaire » ce qui a été essayé auparavant ? Souvent oui, car ces actions pourraient interférer avec une nouvelle solution potentielle et/ou créer des problèmes futurs
- **Vérifier, dans la mesure du possible, qu'il n'y a pas d'autres problèmes** : parfois un _fix_ d'un problème cause d'autres problèmes d'une ampleur encore plus importante (problème d'accès d'un utilisateur ? => on édite en root un fichier de configuration pour accorder les droits => on ferme par la même les droits d'autres utilisateurs, ou bien on introduit un problème de sécurité...)
- **Prendre note de la solution** : trouvez un système qui vous permet de documenter les solutions qui ont fonctionné pour un problème donné. Se dire « c'est bon, je m'en souviendrai » _ne fonctionne quasiment jamais_ pour un problème au-delà du trivial. Utilisez plutôt un outil numérique qui permettra des recherches aisées, des copier/coller de lignes de commandes, un système de tags, etc.

1/ Essayer d'exécuter la commande `ls /var/logs`

2/ La commande précédente échoue. Lire le message d'erreur et expliquer pourquoi

3/ Quelle commande pourrait-on exécuter pour déterminer le nom correct du répertoire de logs dans le répertoire `var` ?

4/ Corriger la commande initiale

5/ Essayer `head -N 7 /etc/passwd`

6/ Marche pas. Quelle commande peut-on exécuter pour connaître la bonne option ?

7/ Corriger la commande

8/ Essayer `cp /etc/passwd /var`

9/ Boum. Que se passe-t-il ?

10/ Comment ferait-on pour effectivement travailler sur une copie du fichier en tant que simple utilisateur ?
