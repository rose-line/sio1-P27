## Exercices M2 - Structures conditionnelles

_Si l'écriture de "méthodes" n'a pas encore été abordée dans le cours :_

- _faites comme si tout se passait dans la méthode `main` comme d'habitude_
- _ignorez les exercices 2, 3, 7_
- _considérez les entrées comme des entrées clavier et les sorties comme des affichages sur le terminal_

### 1. Parité

Écrire une méthode `demanderEntierEtAfficherParite` qui demande un entier à l'utilisateur, et qui affiche si cet entier est pair ou pas.

Exemple d'exécution :

```
Entrez un nombre : 13
13 est impair.
```

Tip : pour savoir si un nombre est divisible par un autre nombre, on peut utiliser l'opérateur _modulo_ (`%`). Par exemple, `nb % 3` est évalué à `true` si le nombre contenu dans la variable `nb` est divisible par 3. Un nombre pair est divisible par 2, un nombre impair ne l'est pas.

---

### 2. Parité 2

Il est très fréquent d'écrire des « méthodes-tests » qui renvoient un booléen `true` ou `false` en fonction de ce qui leur est passé en paramètre.

Refactorez (changer le code sans changer le comportement) l'exercice précédent pour que le test de parité soit dans sa propre méthode-test appelée `estPair`. Dans la méthode `demanderEntierEtAfficherParite` précédemment écrite, on aura donc maintenant notamment le fragment de code suivant :

```java
if (estPair(nb)) {
  System.out.println(nb + " est pair.");
} ...
```

---

### 3. Refactoring

Réécrire le programme suivant pour éliminer la redondance. Rappel : un refactoring ne doit absolument pas changer les fonctionalités du programme (en ce qui concerne ce programme, ça veut dire que la sortie doit être _exactement_ la même).

```java
public static void main(String[] args) {
  Scanner console = new Scanner(System.in);
  System.out.print("Combien va dépenser Fred ? ");
  int montant = console.nextInt();
  System.out.println();
  int nbBillets1 = montant / 20;
  if (nbBillets1 * 20 < montant) {
    nbBillets1++;
  }

  System.out.print("Combien va dépenser Cathy ? ");
  montant = console.nextInt();
  System.out.println();
  int nbBillets2 = montant / 20;
  if (nbBillets2 * 20 < montant) {
    nbBillets2++;
  }

  console.close();
  System.out.println("Fred aura besoin de " + nbBillets1 + " billets de 20.");
  System.out.println("Cathy aura besoin de " + nbBillets2 + " billets de 20.");
}
```

---

### 4. Couleurs

Écrire une méthode qui demande une lettre à l'utilisateur et qui retourne la couleur correspondante. Les lettres valides sont R, V, B. Les couleurs correspondantes sont rouge, vert, bleu. L'utilisateur peut entrer la lettre en minuscule ou en majuscule. La méthode doit retourner « connais pas » si l'entrée utilisateur n'est pas valide. C'est la méthode appelante (`main`) qui se chargera d'effectuer l'affichage de la couleur choisie.

Trois exemples d'exécution :

```
Quelle couleur souhaitez-vous ? b
Vous avez choisi le bleu.

Quelle couleur souhaitez-vous ? R
Vous avez choisi le rouge.

Quelle couleur souhaitez-vous ? Rouge
Connais pas.
```

Aide : pour comparer des strings, on n'utilise pas l'opérateur d'égalité `==`. Il faut utiliser la méthode `equals` de la classe String :

```java
// ne fonctionne pas, même si s1 et s2 contiennent la même string
if (s1 == s2) { ... }

// Il faut utiliser equals comme ceci pour savoir si s1 est identique à s2
if (s1.equals(s2)) { ... }
```

---

### 5. Capitale

Écrire une méthode `estCapitalisé` qui teste si une string commence ou non par une lettre majuscule.

`capitale("Bonjour")` retournera `true` <br>
`capitale("paRiS")` retournera `false` <br>
`capitale("FALSE")` retournera `true` <br>

La classe [`Character`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/Character.html) de la _Java Class Library_ contient plusieurs méthodes-tests (de la forme `isXXX`) qui retournent toutes un booléen (T/F). L'une d'entre elle pourra vous aider dans cet exercice.

---

### 6. Nombre de lettres

CET EXERCICE NE PEUT ÊTRE RÉALISÉ SANS AVOIR VU LES BOUCLES (Module 3)

Écrire une méthode `nbLettres` qui retourne le nombre de lettres (majuscules et minuscules) que contient une string donnée.

`nbLettres("Salut a toi, l'Espagnol !")` retournera `18`

(de même, explorez la classe [`Character`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/Character.html) à la recherche d'une méthode-test qui pourrait vous aider)

---

### 7. Structure if/else if

La méthode suivante ne compile pas. Indiquez pourquoi et corrigez l'erreur de compilation.

La compilation réussit maintenant, mais la méthode ne fonctionne pas comme on le voudrait. Indiquez dans quels cas elle retourne la bonne réponse. Puis corrigez pour obtenir le comportement souhaité.

(exemple : l'appel `nbImpairs(3, 2, 13)` est censé retourner 2, mais retourne 1)

```java
// Cette méhode retourne le nombre d'entiers impairs parmi ses trois paramètres
public static void nbImpairs(int nb1, int nb2, int nb3) {
  int nbImp = 0;
  if (nb1 % 2 != 0) {
    nbImp++;
  } else if (nb2 % 2 != 0) {
    nbImp++;
  } else if (nb3 % 2 != 0) {
    nbImp++;
  }
  return nbImp;
}
```

Pourriez-vous écrire cette méthode sans aucune instruction `if` ?

---

### 8. Jours du mois

Écrire une méthode `nbJoursDuMois` qui prend en entrée un numéro de mois (entre 1 et 12) et qui retourne le nombre de jours de ce mois (ignorez les années bissextiles).

`nbJoursDuMois(11)` retournera `30` <br>
`nbJoursDuMois(2)` retournera `28`

---

### 9. Année bissextile

Écrire une méthode `estBissextile` qui indique si une année est bissextile ou pas. Une année est bissextile si elle est divisible par 4, sauf tous les 100 ans (pas bissextile), sauf tous les 400 ans (bissextile).

`estBissextile(2019)` retournera `false` <br>
`estBissextile(2020)` retournera `true` <br>
`estBissextile(2100)` retournera `false` <br>
`estBissextile(2000)` retournera `true` <br>

---

### 10. Jours du mois v2

Écrire une nouvelle version de `nbJoursDuMois` qui prend deux paramètres (le numéro de mois et l'année) et qui prend en compte les années bissextiles. `nbJoursDuMois(2, 2020)` retournera donc `29`.

---

### 11. Jours du mois v3

Il se trouve que la fonctionnalité demandée existe déjà dans la JCL. Écrire une version 3 qui a la même entête que la V2 mais qui construit un objet de la classe [`YearMonth`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/time/YearMonth.html) de la JCL, puis appelle sur cet objet la méthode qui correspond à notre besoin.

Vous noterez que l'on ne construit pas un objet de type `YearMonth` en utilisant l'opérateur `new` (comme on le fait pour un `Scanner`, par exemple), mais en appelant la méthode `of`. La méthode `of` fait le `new` en interne et retourne l'objet construit. C'est ce qu'on appelle une « méthode-fabrique ».

---

### 12. Accumulation : sommePairsEtMax

CET EXERCICE NE PEUT ÊTRE RÉALISÉ SANS AVOIR VU LES BOUCLES (Module 3)

Écrire une méthode `sommePairsEtMax` qui prend en paramètre un objet `Scanner` pour la console. La méthode doit d'abord demander à l'utilisateur le nombre d'entiers qu'elle devra traiter, puis demander chacun de ces entiers. Quand l'utilisateur a fini d'entrer les nombres, la méthode doit afficher la somme de tous les nombres pairs qui ont été entrés, ainsi que le plus grand de tous les nombres.

Deux exemples de sortie :

```
Combien d'entiers ? 4
Entrez un entier : 2
Entrez un entier : 27
Entrez un entier : 18
Entrez un entier : 4
Somme des nombres pairs = 24, plus grand nombre = 27
__

Combien d'entiers ? 2
Entrez un entier : 1
Entrez un entier : 3
Somme des nombres pairs = 0, plus grand nombre = 3
```

---

### 13. Inverse

Écrire une méthode `deuxSens` qui vérifie si une string passée en paramètre peut se lire dans les deux sens. La méthode sera insensible à la casse (rappel : casse = distinction majuscules/minuscules).

```java
System.out.println(deuxSens("quelconque"));  // affichera 'false' car "quelconque" pas pareil que "euqnocleuq"
System.out.println(deuxSens("kayak"));       // 'true'
System.out.println(deuxSens("Un radar NU")); // 'true' (insensible à la casse)
System.out.println(deuxSens("Éric notre valet alla te laver ton ciré")); // 'false' (à cause des espaces et de la ponctuation)
// Ce dernier exemple fonctionne aussi avec "Luc" à la place de "Eric"
```

---

### 14. Inverse : suite

Même exercice mais cette fois la méthode sera insensible aux espaces et à la ponctuation. Le dernier exemple affichera donc `true`.

---

### 15. Nombre de mots

Écrire une méthode `nbMots` qui retourne le nombre de mots d'une string passée en paramètre. Les mots sont séparés par des espaces (autant d'espaces qu'on veut) ou de la ponctuation (en gros tout ce qui n'est pas une lettre ou un chiffre est considéré comme un séparateur de mots).

```java
nbMots("Bonjour tout le monde") retourne 4
nbMots("je-suis-un-robot") retourne 4
nbMots("   Plein    d'espaces...      et de la ponctuation !!!   ") retourne 7
```

---

### 16. Anniversaire

Écrire une méthode qui demande à l'utilisateur une date d'anniversaire et qui affiche le nombre de jours qui restent jusqu'à cette date (à partir du jour de l'exécution du programme).

Exemple d'exécution (si nous sommes le 19 novembre) :

```
Mois de naissance : 2
Jour de naissance : 5
Il reste 78 dodos jusqu'à votre anniversaire.
```

---

### 17. Chiffrement

Écrire une méthode `chiffrer` qui prend deux paramètres en entrée : un message et un décalage (entier). La méthode retournera le message sous forme chiffrée. Le chiffrement doit se faire en décalant dans l'alphabet chaque lettre du message initial du décalage spécifié. Si le décalage dépasse la lettre 'Z', on reprend cycliquement à 'A'. Par exemple, si le décalage est 3, voici les lettres chiffrées correspondantes :

```
'A' => 'D'
'B' => 'E'
'C' => 'F'
...
'W' => 'Z'
'X' => 'A'
'Y' => 'B'
'Z' => 'C'
```

On passera tout le message d'entrée en majuscule avant d'appliquer le chiffrement. Tout ce qui n'est pas une lettre ou un chiffre restera tel quel. On supposera que les entrées n'ont pas de lettres accentuées. Voici quelques exemples :

```
ABCD E => DEFG H
Salut a toi, punk anarchiste ! => HPAJI P IDX, EJCZ PCPGRWXHIT !
```

---

### 18. Déchiffrement

Écrire la méthode `déchiffrer` qui prend en paramètres un message chiffré selon la méthode précédente et le décalage correspondant et qui retourne le message déchiffré.

```
HPAJI P IDX, EJCZ PCPGRWXHIT ! => SALUT A TOI, PUNK ANARCHISTE !
```

---

### 19. Deviner le nombre, version 2

Reprenez le programme « Devinez le nombre » du TP précédent. Changez la sortie pour indiquer si votre nombre était trop grand ou trop petit. Le programme indiquera par exemple : `Perdu ! Vous avez dépassé de 34` ou bien `Perdu ! Il vous manquait 12`. Si on a gagné, le programme doit afficher : `Quel bol, vous avez trouvé !`
