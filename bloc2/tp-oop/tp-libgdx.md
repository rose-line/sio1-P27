# TP libGDX

## Présentation de libGDX

Voir [ici](tp-libgdx-presentation.md).

## TP sur GH Classroom

Le [lien d'invitation](https://classroom.github.com/a/BszUAi1G)

## Dépôt du prof

[Dépôt utilisé lors du cours](https://github.com/rose-line/b2-tp-libgdx-p27)

## À implémenter

À partir du projet de base fourni, implémenter les fonctionnalités suivantes (développement incrémental = on teste à chaque étape) :

* Remplacer l'image par un personnage et ajuster sa taille

* Le faire se déplacer avec les touches du clavier

* L'empêcher de sortir de l'écran

* Ajouter une deuxième entité (ennemi)

* Si le personnage touche l'ennemi (collision), afficher un message dans la console

* Remplacer le message par une explosion à l'écran

* Puis afficher « _Game Over_ » après 2 secondes (ce peut être une nouvelle image)

* Faire bouger l'ennemi de manière rectiligne (en ligne droite) vers une direction aléatoire au départ, puis le faire rebondir sur les bords de l'écran

* Afficher le score en fin de partie (score = nombre de secondes passées sans toucher un ennemi) (ici, ça doit être du texte)

* C'est trop facile : ajouter un ennemi supplémentaire qui apparaît après un certain temps (disons 10 secondes)

* Arrivé ici, il faut penser régulièrement à s'arrêter avant d'implémenter une nouvelle fonctionnalité et systématiquement regarder si un _refactoring_ ne serait pas judicieux

  * _Refactoring_ = réorganisation du code pour le rendre plus clair, plus lisible, plus maintenable, sans changer son comportement (sans ajouter de fonctionnalité)

  * exemple 1 : extraire une classe depuis une classe existante, comme la classe `Enemy` depuis la classe principale

    * car de nombreux comportements concernent les ennemis

    * et cela devient nécessaire lorsqu'on veut gérer correctement plusieurs ennemis

  * exemple 2 : extraire une méthode depuis une méthode existante

    * car la méthode devient trop longue et difficile à lire

    * ou bien parce que le code est répété à plusieurs endroits

  * exemple 3 : renommer une variable ou une méthode parce qu'on a mieux compris son rôle ou qu'on a trouvé un nom plus clair

  * exemple 4 : supprimer du code mort

    * code commenté qui n'est plus utilisé

    * ce code a de toute façon sûremnent été _commité_, donc au pire, on peut le retrouver dans l'historique du dépôt Git si on en a vraiment besoin

* Faire en sorte que les ennemis apparaissent à des endroits aléatoires

* Éviter les _instant kills_ malchanceux au _spawn_ d'un ennemi (« l'endroit aléatoire » ne doit pas être à côté du personnage)

* Gestion du meilleur score : à chaque fin de partie, afficher le score de la partie et le meilleur score sur la session

* Sauvegarde du meilleur score dans un fichier (conservé et repris entre les sessions)
