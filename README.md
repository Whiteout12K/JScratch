# JScratch

### A JavaScript-Driven Interpretation of Scratch

JScratch is a **.js-driven game engine inspired by the Scratch programming language**, designed from the ground up for the modern web.

While Scratch focuses on visual block programming, JScratch takes the same approachable programming concepts and translates them into **JavaScript function calls**. This allows projects to retain the simplicity and structure of Scratch while gaining the flexibility, performance, and deployability of a web-based JavaScript environment.

Wtih all Scratch driven visuals encoded into a .js format, one can take a step into easing into the web development sphere. Beside the basic Scratch blocks, several additional blocks centered on manipulating css styles and retrieving internet items are built-in. Even more code blocks will be added in the future, but user-made codes are also supported.

For setup, simply download this entire repo file, place it into your favorite code editor (strongly suggest VS Code), install the Go Live extention, and deploy and run on your local desktop.

> **JScratch is Scratch-inspired programming taken to another level — built for the web first.**

---

## Table of Contents

* [Introduction](#introduction)
* [Core Philosophy](#core-philosophy)
* [Getting Started](#getting-started)
* [How JScratch Works](#how-jscratch-works)
* [Canvas Blocks](#canvas-blocks)
* [Sprite Blocks](#sprite-blocks)
* [Motion Blocks](#motion-blocks)
* [Operator Blocks](#operator-blocks)
* [Variable Blocks](#variable-blocks)
* [Sensing Blocks](#sensing-blocks)
* [Control Blocks](#control-blocks)
* [Event Blocks](#event-blocks)
* [Function Blocks](#function-blocks)
* [Sound Blocks](#sound-blocks)
* [Example Project](#example-project)
* [Designing JScratch Projects](#designing-jscratch-projects)
* [Important Notes](#important-notes)

---

# Introduction

JScratch is a **web-first programming and game engine** based on the ideas behind Scratch.

Instead of dragging blocks together in a visual editor, JScratch represents those blocks as JavaScript functions.

For example, a Scratch-style concept such as:

> Move a character 10 steps

can be represented by:

```js
moveTo("Player1", 10, 0);
```

Likewise, creating a sprite can be as simple as:

```js
createSprite("Player1");
```

This approach makes JScratch useful for people who enjoy Scratch's straightforward programming model but want to work directly with JavaScript, files, assets, websites, and deployable web games.

---

# Core Philosophy

JScratch is designed around several principles.

### Scratch-inspired

JScratch follows many familiar Scratch concepts:

* Sprites
* Costumes
* Variables
* Operators
* Sensing
* Control flow
* Events
* Broadcasts
* Functions
* Sounds

The goal is to make the programming model easy to understand while still allowing more advanced projects.

### JavaScript-driven

JScratch projects are written using JavaScript.

Instead of a custom visual block file, a project can directly contain code such as:

```js
createSprite("Player1");

spriteCostume(
    "Player1",
    "images/player.png",
    1
);

moveTo("Player1", 0, 0);
```

This makes JScratch naturally compatible with the web ecosystem.

### Web-first

JScratch is designed specifically around browser-based projects.

Projects can use:

* HTML
* CSS
* JavaScript
* Images
* Audio
* Web hosting
* Web APIs
* Server-side services
* Databases
* Other JavaScript libraries

The goal is not simply to recreate Scratch in JavaScript, but to create a programming environment that **fits naturally into the web**.

### Deployable

A JScratch project can ultimately be hosted like a normal website or web game.

This makes the engine suitable for:

* Small games
* Interactive experiences
* Prototypes
* Educational projects
* Browser games
* Larger web applications

---

# Getting Started

A JScratch project generally consists of JavaScript code running alongside the JScratch engine.

A basic project might look like:

```js
canvasColor("#686565");

createSprite("Player1");

spriteCostume(
    "Player1",
    "images/player.png",
    1
);

moveTo("Player1", 0, 0);
```

The engine interprets the JScratch functions and updates the game canvas.

Assets such as images and sounds can be stored in project folders.

Example:

```text
project/
├── index.html
├── js/
│   ├── engine.js
│   └── game.js
├── images/
│   ├── player.png
│   └── enemy.png
└── sound/
    └── play.mp3
```

---

# How JScratch Works

JScratch divides functionality into several categories inspired by Scratch's block system.

| Category  | Purpose                                  |
| --------- | ---------------------------------------- |
| Canvas    | Controls the game canvas                 |
| Sprite    | Creates and manages sprites              |
| Motion    | Moves and rotates sprites                |
| Operators | Performs calculations and logic          |
| Variables | Stores project and sprite data           |
| Sensing   | Reads input and game information         |
| Control   | Handles loops and conditional logic      |
| Events    | Handles broadcasts and event-driven code |
| Functions | Creates reusable code                    |
| Sound     | Controls game audio                      |

Most blocks are designed to behave like normal JavaScript functions.

For example:

```js
setVar("score", 100);
```

can later be read with:

```js
getVar("score");
```

This makes blocks composable.

For example:

```js
moveTo(
    "Player1",
    add(getVar("x"), 10),
    getVar("y")
);
```

---

# Canvas Blocks

Canvas blocks control the overall game canvas.

## `canvasColor()`

Sets the canvas background color when no canvas image is being used.

```js
canvasColor("#686565");
```

**Parameter:**

| Parameter   | Description       |
| ----------- | ----------------- |
| `color_hex` | Hexadecimal color |

---

## `canvasCostume()`

Sets the canvas background image.

```js
canvasCostume(
    "images/sample_canvas.png",
    2
);
```

**Parameters:**

| Parameter      | Description       |
| -------------- | ----------------- |
| `costume_path` | Path to the image |
| `scale`        | Image scale       |

The costume path can be blank when no image is desired.

---

## `canvasSize()`

Sets the canvas scale.

```js
canvasSize(2);
```

This changes the size without changing the currently selected costume.

---

## `canvasChangeSize()`

Changes the current canvas scale.

```js
canvasChangeSize(0.1);
```

Positive values increase the scale.

Negative values decrease it.

---

## `canvasEffect()`

Applies an effect to the canvas.

```js
canvasEffect("brightness", 0);
```

Supported effects:

### Brightness

```js
canvasEffect("brightness", 50);
```

Controls brightness from `0–100`.

`0` represents no effect, while `100` produces maximum brightness.

### Ghost

```js
canvasEffect("ghost", 50);
```

Controls opacity from `0–100`.

### Color

```js
canvasEffect("color", 50);
```

Changes the hue of the canvas.

`0` and `100` represent the default color, while values between them cycle through the color spectrum.

---

## `costumeOfCanvas()`

Returns the current canvas costume path.

```js
costumeOfCanvas();
```

---

## `sizeOfCanvas()`

Returns the current canvas size.

```js
sizeOfCanvas();
```

---

# Sprite Blocks

Sprite blocks create and manage objects inside the game.

## `createSprite()`

Creates a sprite.

```js
createSprite("Player1");
```

**Parameter:**

```text
sprite_name
```

Example:

```js
createSprite("Enemy1");
createSprite("Player1");
```

---

## `spriteCostume()`

Sets a sprite's costume.

```js
spriteCostume(
    "Player1",
    "images/sample_sprite.png",
    1
);
```

**Parameters:**

| Parameter      | Description      |
| -------------- | ---------------- |
| `sprite_name`  | Sprite to modify |
| `costume_path` | Image path       |
| `scale`        | Image scale      |

The scale determines the image width.

> `1` represents approximately **160 canvas pixels**.

---

## `spriteSetSize()`

Sets the sprite's scale without changing its costume.

```js
spriteSetSize("Player1", 1);
```

---

## `spriteChangeSize()`

Changes the sprite's scale.

```js
spriteChangeSize("Player1", 0.1);
```

Positive values grow the sprite.

Negative values shrink it.

---

## `spriteEffect()`

Applies an effect to a sprite.

```js
spriteEffect(
    "Player1",
    "brightness",
    0
);
```

Supported effects:

* `brightness`
* `ghost`
* `color`

The effects use the same `0–100` range described in the Canvas Effects section.

---

## `spriteShow()`

Shows a sprite.

```js
spriteShow("Player1");
```

---

## `spriteHide()`

Hides a sprite.

```js
spriteHide("Player1");
```

---

## `spriteLayer()`

Moves a sprite to a specific rendering layer.

```js
spriteLayer("Player1", 1);
```

Higher/lower layer numbers can be used to control the rendering order.

---

## `goFront()`

Moves a sprite to the front layer.

```js
goFront("Player1");
```

---

## `goBack()`

Moves a sprite to the back layer.

```js
goBack("Player1");
```

---

## `costumeOfSprite()`

Returns the current costume path of a sprite.

```js
costumeOfSprite("Player1");
```

---

## `sizeOfSprite()`

Returns the current sprite size.

```js
sizeOfSprite("Player1");
```

---

## `deleteSprite()`

Completely removes a sprite.

```js
deleteSprite("Player1");
```

---

# Motion Blocks

Motion blocks control sprite positioning, direction, and movement.

## `spriteX()`

Returns the X coordinate of a sprite.

```js
spriteX("Player1");
```

---

## `spriteY()`

Returns the Y coordinate.

```js
spriteY("Player1");
```

---

## `spriteDirection()`

Returns the sprite's direction in degrees.

```js
spriteDirection("Player1");
```

---

## `moveToEdge()`

Moves a sprite a specified distance from the edges of the canvas.

```js
moveToEdge(
    "Player1",
    "left",
    30,
    "top",
    30
);
```

**Parameters:**

```text
sprite_name
horizontal_side
distance_x
vertical_side
distance_y
```

Example:

```js
moveToEdge("Player1", "right", 20, "bottom", 20);
```

---

## `moveTo()`

Immediately moves a sprite to a coordinate.

```js
moveTo(
    "Player1",
    0,
    0
);
```

---

## `moveToSprite()`

Immediately moves one sprite to another.

```js
moveToSprite(
    "Player1",
    "Enemy1"
);
```

---

## `facing()`

Changes the direction a sprite faces.

```js
facing("Player1", "left");
```

Supported directions:

```text
left
right
up
down
```

---

## `direction()`

Sets the sprite's rotation.

```js
direction("Player1", 30);
```

Directions use degrees from `0–360`.

---

## `turn()`

Rotates a sprite by a specified amount.

```js
turn("Player1", 15);
```

---

## `glideTo()`

Gradually moves a sprite to a coordinate.

```js
glideTo(
    "Player1",
    100,
    100,
    5
);
```

**Parameters:**

```text
sprite_name
x
y
time_in_seconds
```

---

## `glideToSprite()`

Gradually moves one sprite toward another.

```js
glideToSprite(
    "Player1",
    "Enemy1",
    5
);
```

The final parameter represents the movement time in seconds.

---

# Operator Blocks

Operators provide calculations, comparisons, strings, and Boolean logic.

## Mathematical Operators

### `add()`

```js
add(1, 2);
```

Returns:

```text
3
```

### `sub()`

```js
sub(5, 4);
```

Returns:

```text
1
```

### `mult()`

```js
mult(2, 2);
```

Returns:

```text
4
```

### `div()`

```js
div(10, 2);
```

Returns:

```text
5
```

### `mod()`

Returns the remainder.

```js
mod(5, 2);
```

Returns:

```text
1
```

### `round()`

Rounds a number.

```js
round(0.6);
```

Returns:

```text
1
```

### `randomNum()`

Generates a random number between two values.

```js
randomNum(1, 10);
```

---

# Boolean Operators

Boolean operators return `true` or `false`.

## `gThan()`

Checks if the first value is greater than the second.

```js
gThan(3, 5);
```

---

## `lThan()`

Checks if the first value is less than the second.

```js
lThan(3, 5);
```

---

## `gEqThan()`

Checks for greater than or equal.

```js
gEqThan(3, 5);
```

---

## `lEqThan()`

Checks for less than or equal.

```js
lEqThan(3, 5);
```

---

## `equal()`

Checks strict equality.

```js
equal(3, 5);
```

Conceptually equivalent to:

```js
3 === 5
```

---

## `and()`

Returns true when both conditions are true.

```js
and(true, true);
```

---

## `or()`

Returns true when either condition is true.

```js
or(true, true);
```

---

## `not()`

Reverses a Boolean value.

```js
not(true);
```

Returns:

```text
false
```

---

# String Operators

## `join()`

Combines two values into one string.

```js
join(
    "images/",
    "sample_sprite.png"
);
```

This can also be used dynamically:

```js
createSprite(
    join("Enemy", "1")
);
```

---

## `letter()`

Returns a character at a specific position.

```js
letter(2, "images");
```

For example, the second character of `"images"` is:

```text
m
```

---

## `length()`

Returns the length of a string.

```js
length("images");
```

Returns:

```text
6
```

---

## `contain()`

Checks whether one string exists inside another.

```js
contain("im", "images");
```

Returns `true`.

---

# Variable Blocks

Variables store information that can be changed during gameplay.

## `makeVar()`

Creates a global variable.

```js
makeVar("var1");
```

---

## `setVar()`

Sets a variable's value.

```js
setVar("var1", 1);
```

---

## `changeVarBy()`

Changes a variable by a specified amount.

```js
changeVarBy("var1", 3);
```

To subtract:

```js
changeVarBy("var1", -3);
```

---

## `getVar()`

Gets the value of a variable.

```js
getVar("var1");
```

---

# Sprite Variables

Sprite variables are private variables associated with individual sprites.

## `makeSpriteVar()`

Creates a sprite variable.

```js
makeSpriteVar(
    "Player1",
    "health"
);
```

---

## `setSpriteVar()`

Sets a sprite variable.

```js
setSpriteVar(
    "Player1",
    "health",
    100
);
```

---

## `changeSpriteVarBy()`

Changes a sprite variable.

```js
changeSpriteVarBy(
    "Player1",
    "health",
    3
);
```

---

## `getSpriteVar()`

Returns a sprite variable.

```js
getSpriteVar(
    "Player1",
    "health"
);
```

---

# Sensing Blocks

Sensing blocks allow a project to interact with the player and game world.

## `touchingMouse()`

Checks whether a sprite is touching the mouse.

```js
touchingMouse("Player1");
```

Returns a Boolean.

---

## `touchingSprite()`

Checks whether two sprites are touching.

```js
touchingSprite(
    "Player1",
    "Enemy1"
);
```

---

## `touchingColor()`

Checks whether a sprite is touching a particular color.

```js
touchingColor(
    "Player1",
    "#000000"
);
```

---

## `distanceMouse()`

Returns the distance between a sprite and the mouse.

```js
distanceMouse("Player1");
```

---

## `distanceSprite()`

Returns the distance between two sprites.

```js
distanceSprite(
    "Player1",
    "Enemy1"
);
```

---

## `keyPressed()`

Checks whether a key or mouse button is currently pressed.

```js
keyPressed("space");
```

Supported key types include:

### Letters

```text
"a"
"b"
"c"
...
```

### Numbers

```text
"1"
"2"
"3"
...
```

### Arrow Keys

```text
"arrowleft"
"arrowright"
"arrowup"
"arrowdown"
```

### Mouse

```text
"leftclick"
"rightclick"
```

### Other

```text
"shift"
```

---

## `mouseX()`

Returns the current mouse X coordinate.

```js
mouseX();
```

---

## `mouseY()`

Returns the current mouse Y coordinate.

```js
mouseY();
```

---

# Date and Time Sensing

JScratch can also retrieve the current date and time.

```js
currentYear();
currentMonth();
currentDay();

currentHour();
currentMin();
```

### Examples

```js
currentYear();
```

Returns the current year.

```js
currentMonth();
```

Returns the current month as a number.

For example:

```text
January = 1
February = 2
March = 3
```

`currentHour()` uses military/24-hour time.

---

# Control Blocks

Control blocks manage loops, delays, and conditional execution.

## `wait()`

Pauses execution for a specified number of seconds.

```js
wait(1);
```

Decimal values are supported:

```js
wait(0.5);
```

---

## `repeat()`

Repeats code a specified number of times.

```js
repeat(
    100,

    // code
);
```

Repeats can be nested.

Example:

```js
ENGINE.scripts.push(
    repeat(
        100,

        // code

        repeat(
            10,

            // nested code
        )
    )
);
```

Nested repeats do not require another `ENGINE.scripts.push()`.

---

## `ifBlock()`

Runs code when a condition is true.

An optional `else` section can run when the condition is false.

```js
ifBlock(
    equal(
        getVar("Var1"),
        1
    ),

    // code if true

    "else",

    // code if false
);
```

---

## `repeatUntil()`

Repeats code until a condition becomes true.

```js
repeatUntil(
    equal(
        getVar("Var1"),
        2
    ),

    // code
);
```

---

## `whileBlock()`

Runs code while a condition remains true.

```js
whileBlock(
    equal(
        getVar("Var1"),
        1
    ),

    // code
);
```

It can also be used with a constant true condition for continuous execution:

```js
whileBlock(
    true,

    // code
);
```

---

## `forever()`

Runs code continuously until stopped.

```js
forever(

    // code

);
```

This is useful for game loops and constantly running behavior.

Example:

```js
forever(
    ifBlock(
        keyPressed("arrowright"),

        moveTo(
            "Player1",
            add(spriteX("Player1"), 5),
            spriteY("Player1")
        )
    )
);
```

---

## `endScript()`

Stops the current repeating or looping script.

```js
endScript();
```

This can be used to exit:

* `repeat()`
* `repeatUntil()`
* `whileBlock()`
* `forever()`

---

# Event Blocks

Events allow different parts of a project to communicate.

## `broadcast()`

Starts a broadcast event while allowing the current code to continue.

```js
broadcast("Start Menu");
```

Broadcast names should be unique to the event they represent.

---

## `broadcastAndWait()`

Broadcasts an event and waits for the receiving code to finish.

```js
broadcastAndWait("Start Menu");
```

This is useful when another sequence must complete before the current script continues.

---

## `whenBroadcast()`

Receives a broadcast.

```js
whenBroadcast(
    "Start Menu",

    // code
);
```

The broadcast name must match.

For example:

```js
broadcast("Start Game");

whenBroadcast(
    "Start Game",

    createSprite("Player1")
);
```

Broadcasts allow multiple sequences of code to operate independently and communicate with each other.

---

# Function Blocks

JScratch supports JavaScript functions for reusable code.

A function can be declared normally:

```js
function testFunc(){

    // code

}
```

It can then be called with:

```js
testFunc();
```

Functions are useful for grouping repeated behavior.

For example:

```js
function spawnPlayer(){

    createSprite("Player1");

    spriteCostume(
        "Player1",
        "images/player.png",
        1
    );

    moveTo(
        "Player1",
        0,
        0
    );
}

spawnPlayer();
```

### Current Function Limitation

Parameters in normal JavaScript functions are not treated as JScratch variable blocks.

JScratch variables are inherently global, while sprite variables can be used to maintain private sprite-specific values.

---

# Sound Blocks

> **Important:** Browser audio policies generally require the user to interact with the page before audio can begin. A JScratch project should therefore receive a screen interaction before attempting to start sound on project startup.

---

## `makeSound()`

Creates and stores a sound under a name.

```js
makeSound(
    "Sound",
    "sound/play.mp3"
);
```

**Parameters:**

```text
sound_name
sound_path
```

---

## `playSound()`

Plays a stored sound.

```js
playSound("Sound");
```

---

## `stopAllSound()`

Stops all active sounds.

```js
stopAllSound();
```

---

## `stopSound()`

Stops a specific sound.

```js
stopSound("Sound");
```

---

## `setPitch()`

Sets the pitch of a sound.

```js
setPitch(
    "Sound",
    5
);
```

Supported range:

```text
-100 to 100
```

---

## `changePitch()`

Changes a sound's pitch.

```js
changePitch(
    "Sound",
    1
);
```

Negative values lower the pitch.

---

## `setPan()`

Sets the left/right stereo position.

```js
setPan(
    "Sound",
    0
);
```

Supported range:

```text
-100 to 100
```

Generally:

```text
-100 = left
0    = center
100  = right
```

---

## `setVolume()`

Sets a sound's volume.

```js
setVolume(
    "Sound",
    100
);
```

Where:

```text
100 = normal volume
0   = silent
```

---

## `changeVolume()`

Changes a sound's volume.

```js
changeVolume(
    "Sound",
    1
);
```

Negative values decrease volume.

---

## `volumeOfSound()`

Returns the current volume of a sound.

```js
volumeOfSound("Sound");
```

---

# Example Project

The following example demonstrates how several JScratch systems can work together.

```js
canvasColor("#686565");

createSprite("Player1");

spriteCostume(
    "Player1",
    "images/player.png",
    1
);

moveTo(
    "Player1",
    0,
    0
);

makeVar("score");
setVar("score", 0);

makeSpriteVar(
    "Player1",
    "health"
);

setSpriteVar(
    "Player1",
    "health",
    100
);

forever(

    ifBlock(
        keyPressed("arrowright"),

        moveTo(
            "Player1",
            add(
                spriteX("Player1"),
                3
            ),
            spriteY("Player1")
        )
    ),

    ifBlock(
        keyPressed("arrowleft"),

        moveTo(
            "Player1",
            sub(
                spriteX("Player1"),
                3
            ),
            spriteY("Player1")
        )
    )

);
```

This small example already combines:

* Canvas configuration
* Sprite creation
* Costumes
* Positioning
* Global variables
* Sprite variables
* Input sensing
* Operators
* Conditional logic
* A continuous game loop

---

# Designing JScratch Projects

JScratch works particularly well when code is organized around **game objects and behaviors**.

A project might separate its code into files such as:

```text
js/
├── game.js
├── player.js
├── enemies.js
├── menu.js
├── combat.js
└── audio.js
```

For example:

### Player

```js
function setupPlayer(){

    createSprite("Player1");

    spriteCostume(
        "Player1",
        "images/player.png",
        1
    );

    moveTo(
        "Player1",
        0,
        0
    );
}
```

### Enemy

```js
function setupEnemy(){

    createSprite("Enemy1");

    spriteCostume(
        "Enemy1",
        "images/enemy.png",
        1
    );

    moveTo(
        "Enemy1",
        100,
        0
    );
}
```

### Game Setup

```js
setupPlayer();
setupEnemy();
```

This lets JScratch projects grow beyond small demonstrations while maintaining the simple block-like API.

---

# Why JavaScript?

Scratch provides an excellent programming model for learning and experimentation.

JScratch takes that model and removes the requirement for a dedicated visual editor.

Instead, JavaScript becomes the medium through which the blocks are expressed.

For example:

```js
ifBlock(
    touchingSprite(
        "Player1",
        "Enemy1"
    ),

    changeVarBy(
        "score",
        10
    )
);
```

The code still reads like a sequence of programming blocks, but it can be placed directly inside a web project.

This provides access to the larger JavaScript ecosystem while maintaining a Scratch-inspired programming style.

---

# JScratch vs. Traditional Scratch

| Feature                | Scratch          | JScratch             |
| ---------------------- | ---------------- | -------------------- |
| Programming model      | Visual blocks    | JavaScript functions |
| Primary environment    | Scratch editor   | Web                  |
| Code editing           | Block interface  | `.js` files          |
| Sprites                | Yes              | Yes                  |
| Variables              | Yes              | Yes                  |
| Operators              | Yes              | Yes                  |
| Events                 | Yes              | Yes                  |
| Broadcasts             | Yes              | Yes                  |
| Sound                  | Yes              | Yes                  |
| Web integration        | Limited          | Native               |
| JavaScript integration | Limited          | Core feature         |
| Deployment             | Scratch platform | Web hosting          |
| External libraries     | Limited          | JavaScript ecosystem |
| HTML/CSS integration   | Limited          | Native               |

JScratch is therefore not intended to replace Scratch.

Instead, it explores what a **Scratch-like programming model can look like when designed around JavaScript and the web from the beginning.**

---

# Important Notes

### Coordinate System

Sprite positioning uses the JScratch game coordinate system rather than standard HTML page coordinates.

Use:

```js
spriteX("Player1");
spriteY("Player1");
```

to retrieve a sprite's current position.

---

### Scaling

Sprite and canvas scaling is separate from the selected costume.

For example:

```js
spriteCostume(
    "Player1",
    "images/player.png",
    1
);
```

sets the costume and its initial scale.

The scale can then be changed independently:

```js
spriteSetSize(
    "Player1",
    2
);
```

Or adjusted incrementally:

```js
spriteChangeSize(
    "Player1",
    0.1
);
```

---

### Effects

Effects use numerical values rather than CSS-style declarations.

For example:

```js
spriteEffect(
    "Player1",
    "ghost",
    50
);
```

Supported effects currently include:

```text
brightness
ghost
color
```

---

### Loops

Loops are designed to work with the JScratch execution system.

Continuous behavior can be written using:

```js
forever(

    // code

);
```

Repeated behavior can use:

```js
repeat(
    10,

    // code

);
```

Nested loops are supported.

---

### Broadcasts

Broadcasts are useful for separating major systems.

For example:

```js
broadcast("Start Game");
```

can trigger:

```js
whenBroadcast(
    "Start Game",

    // start game code
);
```

This allows menus, gameplay systems, effects, and other sequences to communicate without needing to place everything into one script.

---

# Project Vision

JScratch is ultimately an experiment in combining two ideas:

**The accessibility of Scratch**

with

**the flexibility of JavaScript and the web.**

The goal is to make game programming feel approachable without restricting the project to a closed programming environment.

A JScratch project can start with something as simple as:

```js
createSprite("Player");
```

and eventually grow into a complete browser game containing:

* Multiple scenes
* Menus
* Characters
* Animation
* Sound
* Game logic
* Persistent data
* Web APIs
* Databases
* Custom HTML interfaces
* JavaScript libraries
* Online deployment

JScratch is **Scratch-inspired at its core, JavaScript-driven in implementation, and web-first by design.**

---

# Quick Reference

## Canvas

```js
canvasColor();
canvasCostume();
canvasSize();
canvasChangeSize();
canvasEffect();
costumeOfCanvas();
sizeOfCanvas();
```

## Sprites

```js
createSprite();
spriteCostume();
spriteSetSize();
spriteChangeSize();
spriteEffect();
spriteShow();
spriteHide();
spriteLayer();
goFront();
goBack();
costumeOfSprite();
sizeOfSprite();
deleteSprite();
```

## Motion

```js
spriteX();
spriteY();
spriteDirection();
moveToEdge();
moveTo();
moveToSprite();
facing();
direction();
turn();
glideTo();
glideToSprite();
```

## Operators

```js
add();
sub();
mult();
div();
mod();
round();
randomNum();

gThan();
lThan();
gEqThan();
lEqThan();
equal();

and();
or();
not();

join();
letter();
length();
contain();
```

## Variables

```js
makeVar();
setVar();
changeVarBy();
getVar();

makeSpriteVar();
setSpriteVar();
changeSpriteVarBy();
getSpriteVar();
```

## Sensing

```js
touchingMouse();
touchingSprite();
touchingColor();
distanceMouse();
distanceSprite();
keyPressed();

mouseX();
mouseY();

currentYear();
currentMonth();
currentDay();
currentHour();
currentMin();
```

## Control

```js
wait();
repeat();
ifBlock();
repeatUntil();
whileBlock();
forever();
endScript();
```

## Events

```js
broadcast();
broadcastAndWait();
whenBroadcast();
```

## Functions

```js
function myFunction(){

}
```

## Sound

```js
makeSound();
playSound();
stopAllSound();
stopSound();

setPitch();
changePitch();

setPan();

setVolume();
changeVolume();
volumeOfSound();
```

---

# License

Add the project's license information here.

---

**JScratch — Scratch-inspired programming, rebuilt for JavaScript and the web.**
