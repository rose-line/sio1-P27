## Exercice : Simulation de gestion de stock d'un produit

### Contexte

Un magasin vend un produit unique. Chaque jour, il en reçoit une certaine quantité en stock et en vend une certaine quantité. Le gérant souhaite suivre l'évolution du stock sur plusieurs jours.

L'objectif est d'écrire un programme Java qui simule la gestion du stock du produit à travers les jours. Voici les spécifications du programme :

1. Le programme demande à l'utilisateur :

    - le stock initial

    - le seuil d'alerte (stock minimal recommandé)

    - le nombre de jours à simuler

2. Pour chaque jour :

    - le programme demande la quantité reçue et la quantité vendue

    - il met à jour le stock

    - il affiche le stock actuel

    - si le stock est inférieur ou égal au seuil d'alerte, il affiche un message d'alerte

    - si le stock devient négatif, il affiche un message d'erreur et arrête la simulation

    - pour forcer l'arrêt du programme prématurément, une solution est d'utiliser une variable booléenne `simulationEnCours` qui est mise à `false` en cas de stock négatif ; cette variable pourra être testée dans une condition pour savoir si on continue ou pas

3. À la fin de la simulation (dernier jour terminé si l'on y parvient), le programme affiche le stock final : `Simulation terminée. Stock final : X unités`

### Exemple de sortie (interactions avec l'utilisateur incluses)

Cet exemple illustre une simulation qui s'arrête prématurément (au troisième jour au lieu de cinq) à cause d'un stock négatif. Vous veillerez à ce que votre programme produise une sortie dont le format soit similaire.

```
Quel est le stock initial ? 50
Quel est le seuil d'alerte ? 10
Combien de jours doit durer la simulation ? 5

Jour 1
------
Quantité de produits reçue ? 20
Quantité de produits vendue ? 30
Le stock actuel est de : 40

Jour 2
------
Quantité de produits reçue ? 0
Quantité de produits vendue ? 35
Le stock actuel est de : 5
ATTENTION : le stock est sous le seuil d'alerte !

Jour 3
------
Quantité de produits reçue ? 10
Quantité de produits vendue ? 20
Le stock actuel est de : -5
ERREUR : le stock est négatif. Simulation arrêtée.
```

### Question 1

Quelles sont les données que vous allez stocker dans des variables ? Pour chaque variable, précisez :
  - son nom (choisissez un nom pertinent)
  - son type
  - son rôle
  - cette donnée est-elle récupérée auprès de l'utilisateur ou entièrement gérée par le programme ?

Répondez sur le fichier README.md fourni dans le dépôt GitHub Classroom (voir ci-dessous).

### Question 2

Quelles structures de contrôle (conditions et/ou boucles) allez-vous utiliser ? Pour chaque structure, précisez :
  - son type (conditionnelle / boucle)
  - son rôle
  - pourquoi ce type de structure est adapté à ce rôle ?

Répondez sur le fichier README.md.

### Question 3

Écrire l'algorithme complet de ce programme en pseudo-code (en français).

Répondez sur le fichier README.md.

### Question 4

Implémentez l'algorithme en Java. Veillez à bien reproduire le format de sortie (format d'affichage) demandé.

Le code est à écrire dans le fichier `src/App.java` fourni.

### Rendu sur GitHub Classroom

Le rendu est à faire sur GitHub, dans un dépôt GitHub Classroom. **Vous ne devez pas créer le dépôt vous-même sur votre compte**, mais utiliser la procédure décrite dans la section _Procédure de rendu sur GitHub Classroom_ de la page [Installation, configuration et utilisation de Git/GitHub](../install/git_github_install.md). Le système va créer automatiquement un dépôt privé pour vous dans lequel vous déposerez votre code.

Voici le lien d'invitation à utiliser dans la procédure : https://classroom.github.com/a/4j2ajBfM
