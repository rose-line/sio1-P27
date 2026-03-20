# Présentation de libGDX

## La bibliothèque libGDX

libGDX est un framework de développement de jeux open-source qui fournit un ensemble complet de bibliothèques et d'outils pour créer des jeux 2D et 3D. Il tourne sur le JDK, et supporte donc les langages de développement Java, Kotlin, Groovy... connus pour leur portabilité et leur facilité d'utilisation. Il est conçu pour être indépendant de la plateforme : vous pouvez déployer le même code sur plusieurs plateformes (Windows, macOS, Linux, Android, iOS, web).

libGDX est utilisé pour développer des jeux indie/commerciaux, et il dispose d'une communauté active qui contribue à son développement et à son support. Tous les trois mois est organisé un événement, appelé _Game Jam_, pendant lequel les développeurs du monde entier créent des jeux en utilisant le framework.

## Mise en place

Le projet de base fourni est déjà compilable et fonctionnel. Il a été généré avec le générateur de projet [gdx-liftoff](https://github.com/libgdx/gdx-liftoff).

libGDX utilise _Gradle_ (et non _Maven_) pour gérer les dépendances et les tâches de construction. Installez l'extension _Gradle_ sur votre IDE, pour pouvoir faciliter son utilisation.

Pour lancer le projet, rendez-vous sur le panneau _Gradle_ à gauche, localisez et lancez la tâche `lwjgl3:run`. Vous devriez voir une fenêtre s'ouvrir, avec un logo dessiné à l'écran. Vous pouvez aussi lancer la tâche en ligne de commande, en vous plaçant à la racine du projet et en exécutant `./gradlew lwjgl3:run` (ou `gradlew.bat lwjgl3:run` sous Windows).

Le projet est structuré en plusieurs modules, certains correspondant à une plateforme cible (desktop, web, etc.). Le code commun à toutes les plateformes se trouve dans le répertoire `core`. C'est dans ce module que nous allons travailler.

## Conception d'un jeu vidéo : La boucle de jeu

La **boucle de jeu** est un _pattern_ uniformément utilisé dans les jeux vidéo. C'est la structure centrale qui fait progresser le jeu. Elle répète continuellement une séquence d'étapes (de nombreuses fois par seconde), mettant à jour l'état du jeu et rendant la scène en donnant l'illusion du mouvement. Une boucle de jeu typique se compose des phases suivantes :

1. *Traitement des entrées* : collecter les entrées de l'utilisateur, telles que les pressions de touches, les clics de souris ou les événements tactiles.
2. *Mise à jour* : mettre à jour l'état du jeu en fonction des entrées de l'utilisateur et d'autres facteurs. Cette phase inclut le déplacement des objets du jeu, la vérification des collisions et la gestion des événements du jeu.
3. *Rendu* : dessiner l'état actuel du jeu à l'écran (graphismes, effets visuels, interface utilisateur...).
4. *Contrôle du timing* : maintenir un taux de rafraîchissement constant en mesurant le temps entre les frames. Cela garantit que le jeu se comporte de manière cohérente sur différents matériels.

Voici donc un exemple simplifié d'une boucle de jeu, utilisant des méthodes pour chaque étape :

```java
while (isGameRunning) {
  processInput();
  updateGameState();
  renderScene();
  controlFrameRate();
}
```

Avec un framework comme libGDX, vous n'avez pas besoin d'implémenter cette boucle de jeu vous-même : le framework s'en charge pour vous. Vous devez simplement implémenter les méthodes qui seront appelées à chaque étape de la boucle de jeu par libGDX, qui s'assurera que ces méthodes sont appelées au bon moment.

## La boucle de jeu dans libGDX

La boucle de jeu est gérée automatiquement et supportée par la classe `ApplicationAdapter`. La classe principale du jeu doit être créée à partir de cette classe, comme dans le code fourni. Ce n'est pas vous qui créez la méthode `main()` : celle-ci est également gérée par le framework, et va automatiquement appeler les méthodes que vous implémentez dans votre classe principale.

Voici comment fonctionne la boucle de jeu de libGDX : la logique de votre jeu est encapsulée notamment dans les méthodes `create()`, `render()` et `dispose()` pour définir le comportement de votre jeu. Examinez le code de base fourni pour voir comment ces méthodes sont utilisées (`Main.java` à localiser dans le répertoire `core`).

1. `create()` : Cette méthode est appelée une seule fois au début du jeu. C'est ici que vous initialisez les ressources, chargez les assets (images, sons, etc.) et configurez l'environnement de jeu. Vous pouvez la voir comme le « constructeur » de la classe principale.
2. `render()` : La méthode render() est où réside la boucle de jeu principale. libGDX appelle cette méthode de manière répétée (à chaque _frame_) pour mettre à jour l'état du jeu et rendre la scène. C'est ici que vous traiterez les entrées, mettrez à jour les objets du jeu et dessinerez les éléments à l'écran.
3. `dispose()` : Cette méthode est appelée lorsque le jeu est fermé ou que les ressources doivent être libérées. C'est ici que vous nettoyez et libérez les ressources utilisées par votre jeu (textures, sons, etc.) pour éviter les fuites de mémoire.

Voici un exemple simplifié avec une boucle de jeu de base :

```java
public class MyGame implements ApplicationListener {
  @Override
  public void create() {
    // Code d'initialisation, chargement des assets, configuration de l'environnement de jeu
    // Tout ce qu'il faut faire une seule fois au début du jeu
  }

  @Override
  public void render() {
    processInput();
    updateGameState();
    renderGame();
  }

  // Traitement des entrées (input utilisateur : clavier, souris...)
  private void processInput() {
    // ...
  }

  // Mise à jour de l'état du jeu (déplacer les objets du jeu, vérifier les collisions, vérifier les conditions de victoire/défaite...)
  private void updateGameState() {
    // ...
  }

  // Rendu (dessiner finalement l'état actuel du jeu, qui prend en compte les entrées et le changement d'état)
  private void renderGame() {
    // ...
  }

  @Override
  public void dispose() {
    // Nettoyage et libération des ressources
  }

  // D'autres méthodes de cycle de vie (resize de la fenêtre, pause, resume) peuvent aussi être automatiquement appelées par le framework, mais elles ne sont pas obligatoires
}
```

## Objets du jeu

Les objets du jeu sont les entités avec lesquelles le joueur interagit. Ces objets peuvent inclure des personnages, des ennemis, des items, des obstacles, etc. Chaque objet du jeu a des propriétés propres telles que sa position, sa taille, ses points de vie... (variables d'état) et un comportement spécifique (méthodes). **Les objets du jeu sont donc naturellement représentés par des instances de classes Java**.

Par exemple, dans un jeu de plateforme simple, vous pourriez avoir une classe `Player` qui représente le personnage principal et une classe `Enemy` pour les créatures hostiles. Plusieurs instances (objets) `Enemy` seraient créées pour affronter une instance de `Player`.

## Physique et collisions

Les moteurs physiques comme _Box2D_, intégrés à libGDX, aident à simuler les interactions physiques telles que la gravité, les collisions et les forces. La **détection de collision** est le processus d'identification lorsque deux objets se croisent. Cela vous permet de répondre à des événements tels que le passage du joueur sur un item, ou les interactions entre un objet et le sol...

Pour détecter une collision entre deux objets, il vous faut les « _box_ » de ces objets, c'est-à-dire des rectangles (ou d'autres formes plus précises) qui englobent les objets (classe `Rectangle`). Vous pouvez ensuite vérifier si ces boîtes se chevauchent pour déterminer s'il y a une collision avec la méthode `overlaps()` de la classe `Rectangle` :

```java
Rectangle playerBox = getPlayerBox();     // obtenir la "box" du joueur
Rectangle obstacleBox = getObstacleBox(); // obtenir la "box" de l'obstacle
if (playerBox.overlaps(obstacleBox)) {    // elles se chevauchent ?
  // Infliger des dommages au joueur...
}

private Rectangle getPlayerBox() {
  return new Rectangle(playerX, playerY, playerWidth, playerHeight);
}

private Rectangle getObstacleBox() {
  return new Rectangle(obstacleX, obstacleY, obstacleWidth, obstacleHeight);
}
```

> La classe `Sprite` de libGDX fournit une méthode `getBoundingRectangle()` qui retourne un rectangle englobant le sprite, ce qui nous épargne de devoir calculer manuellement ces rectangles. Nous n'utiliserons pas la classe `Sprite` dans ce TP, mais vous pouvez explorer cet aspect.

## _Framerate_ et « _delta time_ »

Pour maintenir un **taux de rafraîchissement constant** (quel que soit le matériel), on utilise la méthode `Gdx.graphics.getDeltaTime()`, qui renvoie le temps écoulé depuis la dernière _frame_. En prenant en compte ce temps écoulé, on put faire en sorte que les mouvements et les animations soient fluides et cohérents.

```java
float deltaTime = Gdx.graphics.getDeltaTime();
playerPosX += playerSpeed * deltaTime;  // Déplacer le joueur en fonction du temps écoulé
```

Sur les machines plus rapides, le `deltaTime` sera plus petit, et donc la valeur calculée `playerPosX` (déplacement du joueur) sera plus petite aussi. Sur les machines plus lentes, le `deltaTime` sera plus grand, ce qui compensera la baisse de performance et maintiendra une expérience de jeu identique (jusqu'au point bien sûr où la différence devient perceptible et le jeu « saccade »).

## SpriteBatch

`SpriteBatch` est une classe de libGDX utilisée pour **dessiner des textures** (images) à l'écran. Elle permet de regrouper plusieurs dessins en un seul appel de rendu, ce qui améliore les performances. Vous pouvez utiliser `SpriteBatch` pour dessiner des personnages, des objets et d'autres éléments graphiques dans votre jeu.

Il faut commencer par créer une instance de `SpriteBatch` dans votre classe principale, généralement dans la méthode `create()`. Puis, vous pouvez utiliser cette instance pour dessiner des sprites dans la méthode `render()`.

```java
// Initialisation du SpriteBatch
SpriteBatch spriteBatch = new SpriteBatch();
// Initialisation d'une texture et d'un sprite
Texture texture = new Texture("sprite.png");
Sprite sprite = new Sprite(texture); // Crée le sprite avec cette texture
sprite.setPosition(100, 100);

// Puis, dans la méthode render() :
spriteBatch.begin(); // Il faut dire qu'on commence à dessiner
sprite.draw(spriteBatch); // dessine le sprite en utilisant le SpriteBatch
// ... dessiner d'autres éléments du jeu ...
spriteBatch.end(); // Fini !
```

Dans cet exemple, nous chargeons une texture à partir d'un fichier image, créons un sprite à partir de cette texture et le positionnons à (100, 100) sur l'écran. Nous utilisons ensuite le SpriteBatch pour dessiner le sprite dans les blocs `begin()` et `end()`.

## Entrées clavier

Gérer les entrées clavier dans libGDX est simple. Vous pouvez utiliser la méthode `Gdx.input.isKeyPressed(int key)` pour vérifier si une touche spécifique est actuellement enfoncée. Par exemple :

```java
if (Gdx.input.isKeyPressed(Keys.LEFT)) {
  // La touche flèche gauche est enfoncée
}
```

libGDX fournit des constantes comme `Keys.LEFT` pour toutes les touches de clavier courantes.

## Entrées souris / touch

Pour gérer les entrées de la souris (ou le tactile sur les appareils mobiles), on utilise des méthodes comme `Gdx.input.getX()` et `Gdx.input.getY()` qui récupèrent la position actuelle du curseur de la souris. Vous pouvez également vérifier les clics en utilisant des méthodes comme `Gdx.input.isButtonPressed(int button)` :

```java
if (Gdx.input.isButtonPressed(Input.Buttons.LEFT)) {
  // Le bouton gauche de la souris est cliqué
  int mouseX = Gdx.input.getX();
  int mouseY = Gdx.input.getY();
  System.out.println("Clic aux coordonnées (" + mouseX + ", " + mouseY + ")");
}
```

> Sous libGDX, la position (0,0) correspond au coin inférieur gauche de la fenêtre, et les coordonnées augmentent vers la droite (en x) et vers le haut (en y).

> `Gdx.input.isTouched()` permet de vérifier si l'écran est touché (sur mobile) ou si un bouton de la souris est enfoncé (sur desktop), quel que soit le clic/tap.

## _Timer_

libGDX fournit une classe `Timer` pour exécuter des tâches après un certain délai ou à intervalles réguliers. On peut gérer ce délai avec un simple `float` en lui ajoutant le `deltaTime` à chaque frame :

```java
float timer;

private void updateGameState() {
  float delta = Gdx.graphics.getDeltaTime();

  // ...

  timer += delta;        // ajoute le delta au timer
  if (timer > 10f) {     // il s'est passé plus de 10 secondes ?
    timer = 0;           // reset
    System.out.println("10 secondes se sont écoulées ! Reset du timer...");
  }
}
```

Vous pouvez aussi utiliser `Timer.schedule()` pour planifier une tâche à exécuter après un délai spécifié, ou `Timer.scheduleTask()` pour planifier une tâche répétitive.

Voici un exemple d'utilisation de `Timer` pour exécuter une tâche après un délai de 5 secondes :

```java
Timer.schedule(new Timer.Task() {
  @Override
  public void run() {
    System.out.println("Cette tâche est exécutée 1 fois après un délai de 5 secondes");
  }
}, 5);      // délai en secondes
```

Et voici comment planifier une tâche répétitive qui s'exécute toutes les 3 secondes :

```java
Timer.schedule(new Timer.Task() {
  @Override
  public void run() {
    System.out.println("Cette tâche est exécutée toutes les 3 secondes");
  }
}, 0, 3);   // délai initial de 0 secondes, puis répétition toutes les 3 secondes
```

## Ajouter du texte à l'écran



## Interface utilisateur (UI)

L'interface utilisateur (UI) est essentielle pour créer des menus, des HUD (affichages tête haute) et d'autres éléments à l'écran avec lesquels les joueurs interagissent. libGDX fournit des outils comme _Scene2D_ pour construire des interfaces utilisateur. _Scene2D_ vous permet de créer facilement des boutons, des étiquettes, des champs de texte et autres.

```java
// Création d'un simple bouton avec Scene2D
TextButton startButton = new TextButton("Start", skin);
// Gestion de l'événement "clic du bouton"
startButton.addListener(new ClickListener() {
  @Override
  public void clicked(InputEvent event, float x, float y) {
    // Gérer le clic du bouton
    startNewGame();
  }
});
```


