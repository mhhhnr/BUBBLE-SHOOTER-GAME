# BUBBLE SHOOTER

## Project Overview
The Word Shooter game is a 2D letter–matching and shooting game developed using **C++**, **OpenGL**, and **GLUT**. The game displays falling alphabet tiles on a grid and allows the player to shoot letters from a shooter to form valid English words. We utilized a dictionary containing **370,099 English words** to validate the player's word formations. The project includes core gameplay features such as letter generation, shooter mechanics, scoring, timer handling, and Game Over conditions.

---

## Project Workflow
We started with an empty GLUT framework and gradually integrated essential game components. Our first steps included initializing the OpenGL window, loading textures for alphabets, and setting up the grid structure for letter placement. We then worked on dictionary loading, random alphabet generation, and the shooting mechanism. After completing the core gameplay flow, we refined interaction handling such as mouse input, keyboard control, and animation through timers.

---

## Game Initialization
The game window is initialized with size **930 × 660** pixels. Arrays such as `letters[9][15]` and `wordsin[9][15]` are used to store the visible alphabets and their numerical indices.  
The game loads **370,099 English words** from *words_alpha.txt*, which are used later to match and validate words formed by the player.

---

## Font & Textures
Textures for the 26 alphabets are loaded using OpenGL texture functions.  
Two texture-loading functions were used:

1. **RegisterTextures_Write()** – Loads BMP images and writes pixel data into a `.bin` file.  
2. **RegisterTextures()** – Reads the binary file and loads textures efficiently.

Each alphabet is stored as a **60×60 pixel tile** and rendered through `DrawAlphabet()`.

---

## Letter Grid Setup
The upper part of the board displays letters arranged in a **9×15 grid**.  
Initially:

- First **two rows** are filled with random alphabets using `GetAlphabet()`.  
- Remaining rows are initialized with placeholder values representing empty cells.

The grid is also responsible for detecting matches after shooting and for triggering a Game Over if critical positions become filled.

---

## Shooter Mechanism
The shooter is positioned at the bottom center of the screen (`fixedx = 435`, `fixedy = 10`).  
When the player clicks the mouse:

- The game calculates slope and shooting direction based on click coordinates.
- A selected alphabet travels upward until it collides with the grid.

Left mouse click is used for firing, and continuous aiming is managed using `MouseMoved()`.

---

## Dictionary-Based Word Matching
At startup, the game loads a dictionary containing **370,099 English words**.  
This dictionary is used for validating the player's formed word sequences.  
It ensures meaningful word creation and adds linguistic depth to gameplay.

---

## Timer and Game Over Logic
A countdown timer begins at **120 seconds** and updates using code at the end:

If forbidden grid cells such as `wordsin[8][7]` become filled, the game triggers a **GAME OVER** screen along with the final score display.

## Scoring System

The player earns score based on:

- Correct alphabet placement  
- Successful word formations  
- Clearing letter clusters  

The final score appears on the Game Over screen using:
"Your Score: " + Num2Str(score)
## Input Handling

### Mouse Controls
- **Left Click:** Shoot alphabet  
- **Mouse Movement:** Aim the shooter  

### Keyboard Controls
- **ESC:** Exit game  

---

## Game Development Approach

Our development approach emphasized **incremental progress** and **modular design**.  
We first established the **OpenGL rendering pipeline**, then progressively added:

- Dictionary loading (370k words)
- Texture registration and caching
- 2D letter grid setup
- Shooter mechanics & trajectory calculations
- Game Over detection system
- Timing and scoring systems

Each feature was built **step by step**, tested immediately, and refined.  
We improved maintainability and readability using comments, consistent formatting, and modular functions such as:

- `RegisterTextures()`
- `DrawAlphabet()`
- `MouseClicked()`
- `Timer()`
- `DisplayFunction()`

---

## Implementation Progress According to Requirements

### Basic Features
- Alphabet textures rendered on screen  
- Randomized letter grid  
- Shooter system implemented  
- Full OpenGL display loop  

### Dictionary
- Loaded **370,099 English words** from `words_alpha.txt`  
- Used for validating word formations  

### Letter Generation
- Random alphabet selection using `GetAlphabet()`  
- Letters stored in `letters[][]` and `wordsin[][]`  

### Shooting Mechanics
- Slope-based projectile logic  
- Aimed using mouse position  
- Letters placed into the falling grid  

### Word Matching
- Grid supports letter placement for matching logic  
- Dictionary used to validate combinations  

### Timer System
- Fully functional **120-second countdown**  
- Updates via `Timer()` callback  

### Game Over System
Triggered when forbidden cells (e.g., `wordsin[8][7]`) are filled.  
Displays textured **GAME OVER** message along with:

```cpp
"Your Score : " + Num2Str(score)


```cpp
timeleft = timeleft - 10;


