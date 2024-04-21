# Snake-Game-Engine
## Game/Engine Demo
https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/f6d194cd-0c78-42cf-bce2-314d7240bc6d


**Project Documentation**: https://dkd2101.github.io/html/index.html


**Project Explanation**:
<img width="639" alt="Screenshot 2024-04-21 at 6 16 45 PM" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/a088a76a-8f3c-47c7-afbe-2e6fc2ecc3e3">

<img width="618" alt="Screenshot 2024-04-21 at 6 17 07 PM" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/12f0921c-e00b-4d22-8ae1-f65b18cb4dd0">

<img width="646" alt="Screenshot 2024-04-21 at 6 18 01 PM" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/b6d6790a-f000-4b3b-b613-0954534bd5e8">

This engine utilizes C++ to render and handle memory management nad core engine functionality and Python to utilize this engine and create a base version of the Google Snake Game. Seen above are three scenes implemented with our engine that are cycle through during the course of the snake game
<img width="399" alt="Screenshot 2024-04-21 at 7 13 57 PM" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/17d39112-cbc8-4ad3-9a52-08e81ad3509e">

<img width="451" alt="Screenshot 2024-04-21 at 7 14 38 PM" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/089aefb5-2044-42b3-8c1a-016d58a85ce8">

I've also implemented a GUI application in WXWidgets that allows us to create and save new snake level configurations. This would be great in making more puzzle based snake levels with collecting apples and not running into walls. My engine supports loading in game objects from a text file therefore we could simply pass in this text file to my engine to load the file into a scene. The game logic could then be changed in Python to have different win conditions and not be score based and be more level completion centric.

**Data Hierarchy**
![_application_8cpp__incl](https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/4fc528f9-563b-4d6b-89e9-203dd1a63e48)

Everything in my engine is accessed through the Application. We have a map of GameObjects stored within each scene and Update, Render, and Input callback functions that must be run in each loop in order to display the game. The application handles all interactions between gameobjects and scene management.

**Scene Handling**
In order to handle multiple scenes, the Application has a list of Scenes that can be indexed to inside of the application. Functions that create scenes return integers representing their position in the list for access later inside of the python script.

Upon a scene opening, we then change the curScene variable which represents the current scene we have "open" similarly to how Unity manages one Scene and its gameobjects at a time. Each Scene then has it's own mapping of id's to gameobjects that they are responsible for updating and rendering accordingly

**Componentization**
Components are very individualized and each have their own Update, Render, and Input functions so that they can be solely responsible for updating themselves. They store references for the gameobject they are on in order to be able to manipulate it.

The current components we have are: 
TextureComponent
Collision2DComponent
TransformComponent

**Game Objects**
Everything in our game is considered a GameEntity. When adding through the application we always add a Transform and Collision2D component to the gameobject. A gameobject is also capable of having children for which it is responsible for calling update, render, and input calls to.

