## What is Kinetic Conundrum? ##

[Kinetic Conundrum]( https://rastala-games.itch.io/kinetic-conundrum) is physics-driven puzzle / platformer game, 
where the goal is to wrangle target balls through a puzzle to the pockets using combination of player-induced collisions and effects of gravity.

My goal was to build something interesting and maybe fun while learning a game development. While I’m quite familiar with software development 
in general, coding a game was something new to me. Therefore I wanted to build something that I could ship quickly, in order of months, 
while honing my skills, as a stepping-stone towards something more ambitious – my motto here was “If it can be done, it can be done better".

I wanted to keep the scope small, to make it easier to release quickly to get feedback, and iterate the original idea didn’t have legs, in 
minimum viable product style. The limited scope meant few things:

 * Simple game mechanics and user interface.
 * Simple graphics that I could create in DYI mode without need for professional caliber art and animations, meaning basic shapes like spheres or tiles.
 * Leverage an existing game engine instead of creating my own.
   
My first idea was to create a kind of minigolf-billiards hybrid with the goal of pocketing target balls, but with more dynamic gameplay with 
balls moving around and colliding in real time. However, after creating few levels I realized that the gameplay was too chaotic and unpredictable. 
Therefore, I pivoted to the current design that turned out to be more playable.

### Anatomy of a level ###

Let’s look of one of the levels - spoiler alert for level 7!

![Kinetic Conundrum Level 7 video clip](https://github.com/rastala/rastala.github.io/blob/main/docs/assets/images/kinetic_conundrum_rec_medium.gif)

The goal is to drive the blue target ball at the lower platform into the pocket nearby. What makes it a puzzle instead of straightforward 
platformer is that there’s no direct route for the player-controlled cyan ball to get to the blue ball. Instead, the player has to figure 
out a more complicated sequence of collisions and kinetic trajectories that lead to blue ball getting pocketed.

The trick is to use one of the red balls as an in-between to knock the blue ball in, and use the see-saws to launch the red balls, 
in a kind of Rube Goldberg chain reaction, as shown on the video.To make the puzzle not trivially easy, I had to block off shortcut 
solutions, such as skipping the see-saw mechanism and directly using the player ball or player ball plus a red ball to knock the blue 
ball in. The way I did this on this level was by making the player ball slightly larger than the red or blue balls, and by creating passages 
wide enough for red and blue balls, but too narrow for the player ball. There are other ways to eliminate shortcuts or force a more difficult 
solution you might see on other levels.

In addition to the main puzzle element, the difficulty can be adjusted by adding side-challenges. Note that one of the red balls is in 
a bit awkward position and has to be wrangled up to a higher platform before it can be placed on the see-saw and launched. For an easier 
puzzle, I could have placed that red ball near the see-saw to start with. For a more difficult puzzle, I could have created a complicated 
route, maybe with a chasm that’d need to be crossed.

When designing the game mechanics and levels, the user experience considerations included:

 * Each level should have a puzzle element, and solution requires thinking ahead about the kinetics of the objects involved.
 * Each level should have one or few valid solutions.
 * Simple controls with minimal ramp-up to get started.
 * Realistic-feeling physics. Trajectories, collisions and bounces should look and feel right. However, maintaining constants of motion or continuous symmetries precisely, like in a scientific physics simulation, is not a priority.

As physics engine, I used [Godot Rapier Physics]( https://github.com/appsinacup/godot-rapier-physics) instead of Godot’s default, as it seemed 
to give the kinetics a better and smoother feel with fewer collision-related glitches. 

Some issues that turned out difficult to avoid include:
 * Levels may have unexpected shortcut solutions outside the “official” solution path. For example, the collision physics can give a lucky bounce that results in a ball getting pocketed.
 * I tried to sort the levels from easiest to hardest, and to avoid having similar levels back-to-back. However, it was difficult to objectively determine whether level is easy or hard, especially since I know the trick to solving the level.

### Development process and shipping ###

I used [Godot](https://godotengine.org/) as the game engine. The benefits were:
 *	Free open-source product with rich community support. 
 *	Built-in GUI for editing levels.
 *	Support for 2D graphics rendering.
 * 	Support for input and event handling.
 *  Support for physics handling.

I used [Krita](https://krita.org/) for creating graphics. It had way more functionality than I actually needed, but after some playing around, I was able to 
figure out how to create basic pixel art shapes. 

Figuring out how to build the object model and interactions in the context of Godot engine was an interesting mix of old and new, and 
probably worth a future deep dive. 

The development loop was roughly: Create basic game logic and few initial levels > Test playability and correctness > Fine-tine game logic 
and elements > Test > Create more levels > Test > Fine-tune >  Test >  Repeat until enough levels. 

At some points I had to step back and update or re-create game elements (“scenes” in Godot parlance) to improve physics handling or to 
make levels work better. This occasionally resulted in a big re-building of existing levels.

The game is available at [itch.io](https://itch.io/). I decided to release a short, free browser version, and a pay-to-download version with 
more levels. Why the paid-for version? It’s really a marketing experiment, to test the price-point and business viability of the game going forward. 
I don’t expect to make a huge profit, the value is really getting a less biased signal that I’d get by giving the game away for free. 

### Future plans ###

I haven’t decided yet whether to build a v2. It depends on the user reception and feedback, and whether I want to keep going on this 
project or start something new. Some possible future improvements I’ve though of include:

 * New gameplay elements. I have some creative ideas here. Also it seems new elements are needed to create new puzzles that don’t repeat earlier ideas.
 * In the same spirit, more elaborate physics interactions.
 * Fancier graphics. Animations, shaders etc. are something I’d like to learn.
 * urrently, the coin collecting is a bit of disconnected game mechanic, and could be worked into a more interesting part of scoring or game progression.

To give Kinetic Conundrum a try, visit [the itch.io project page]( https://rastala-games.itch.io/kinetic-conundrum).
