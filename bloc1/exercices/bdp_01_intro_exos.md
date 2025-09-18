## Exercices M1 - Manipulation de variables, entrées et sorties

### Exercice 1

Disons qu’il est 12 h 34 min 56 s (utilisez des variables avec des valeurs « en dur »). Écrire un programme qui affiche le nombre de secondes écoulées depuis minuit. La sortie (l'affichage à l'écran) ressemblera à ceci :

```
Il est 12 h 34 min 56 s.
Il s'est écoulé xxxxx secondes depuis minuit.
```

`xxxxx` étant bien entendu calculé dans le programme et remplacé dans la sortie.

---

### Exercice 2

Même chose mais l'heure est demandée à l'utilisateur :

```
Entrez les heures : 21
Entrez les minutes : 43
Entrez les secondes : 17

Il est 21 h 43 min 17 s.
Il s'est écoulé xxxxx secondes depuis minuit.
```

---

### Exercice 3

Même chose que ex. 2 mais la sortie précise cette fois le nombre de secondes _avant_ minuit :

```
Entrez les heures : 14
Entrez les minutes : 01
Entrez les secondes : 10

Il est 14 h 01 min 10 s.
Il y a encore xxxxx secondes avant minuit.
```

---

### Exercice 4

Maintenant disons qu'il est 15 h 27 min 12 s. Calculez le _pourcentage_ de temps écoulé depuis tout à l'heure (12:34:56) par rapport aux 24 heures d'une journée. Considérez l'utilisation de nombres flottants pour afficher ce pourcentage avec décimales. N’hésitez pas à utiliser des variables intermédiaires (même si vous n'allez pas les afficher) pour vous faciliter la tâche et rendre le code plus lisible.

---

### Exercice 5

Le but est de programmer un tout petit jeu, une sorte de « Devinez le nombre ». Une fois terminé, vous devez avoir exactement la sortie suivante (excepté bien sûr le nombre à deviner et la proposition du joueur, qui vont changer à chaque exécution) :

```
Je pense à un nombre entre 1 et 100 inclus. Devinez lequel.
Entrez un nombre : 36
Vous proposez : 36
Le nombre auquel je pensais était : 47
Vous étiez à 11 de la bonne réponse.
```

Vous aurez besoin de générer un nombre aléatoire entre 1 et 100. Renseignez-vous sur le type objet `Random` de Java du package `java.util`. Vous verrez qu'il s'utilise un peu comme un objet `Scanner`.