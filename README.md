# Snake-Game-Engine
## Game/Engine Demo
https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/f6d194cd-0c78-42cf-bce2-314d7240bc6d


**Project Documentation**: https://dkd2101.github.io/html/index.html


## Project Explanation
<img width="639" alt="Screenshot 2024-04-21 at 6 16 45 PM" justify-content="center" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/a088a76a-8f3c-47c7-afbe-2e6fc2ecc3e3">

<img width="618" alt="Screenshot 2024-04-21 at 6 17 07 PM" justify-content="center" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/12f0921c-e00b-4d22-8ae1-f65b18cb4dd0">

<img width="646" alt="Screenshot 2024-04-21 at 6 18 01 PM" justify-content="center" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/b6d6790a-f000-4b3b-b613-0954534bd5e8">

This engine utilizes C++ to render and handle memory management nad core engine functionality and Python to utilize this engine and create a base version of the Google Snake Game. Seen above are three scenes implemented with our engine that are cycle through during the course of the snake game <br />
<img width="399" alt="Screenshot 2024-04-21 at 7 13 57 PM" justify-content="center" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/17d39112-cbc8-4ad3-9a52-08e81ad3509e">

<img width="451" alt="Screenshot 2024-04-21 at 7 14 38 PM" justify-content="center" src="https://github.com/dkd2101/Snake-Game-Engine/assets/35245790/089aefb5-2044-42b3-8c1a-016d58a85ce8">

I've also implemented a GUI application in WXWidgets that allows us to create and save new snake level configurations. This would be great in making more puzzle based snake levels with collecting apples and not running into walls. My engine supports loading in game objects from a text file therefore we could simply pass in this text file to my engine to load the file into a scene. The game logic could then be changed in Python to have different win conditions and not be score based and be more level completion centric.

## Data Hierarchy
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

## Post Mortem
Looking at the development of this Game Engine I think that one thing I can really focus on more is the GUI interface and developing that to be more interactive directly with the engine itself. Due to the time constraint and the ordering of which I learned things, I did not have as much time as I liked to get familiar with wx widgets to the point where I was comfortable/capable of making a complex GUI that interfaced with my engine module. I also initially took the design of this project in a compltely wrong direction before scrapping it. Initialy I misunderstood the assignment and started editing the cpp to be very focused on creating GameObjects for SPECIFICALLY the snake game I was trying to develop. However, after reading through piazza posts and discussing with other classmates, I found that this was not the design approach that was expected as doing it this way supported no other forms of games. I also at the time I started had not finished the pybind assignment which after finishing that assignment greatly changed my understanding of how I should be designing my engine. Moving forward in the refactor, I focused greatly on making the cpp engine module as OPEN as possible focusing on exposing functions that would help me if I were to use a command line version of something like Unity. <br/>
If I had more months on this project, I definitely would focus more on Resource Management and GUI interaction within my engine. Right now I support loading new levels through a text file the GUI produces, however I was not able to accomplish a detailed drag and drop tile system or live changes throgh the widget interactions. I definitely would focus more development time into the widget, especially since I have an established working cpp engine in the backend. From what I've used of WxWidget I think I would still use this over other things such as Unity as it being a C++ library gives the possibility of directly making it work with the engine module that I have. I'd probably dedicate around a month to learn wxwidget and develop a drag and drop level system. After that I would spend a 2-3 months on learning the best way to manage and implement sound resources so that I could add sound implementation through Application calls to my engine.

