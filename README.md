# Snake_game_binary_brains

# Snake Game

This is a simple Snake game implemented in C++ using the `ncurses` library for terminal-based graphics.

## Features
- Classic snake movement (Up, Down, Left, Right)
- Food generation and snake growth
- Collision detection with walls and itself
- Scoring system
- Game restart functionality
- Non-blocking keyboard input using `ncurses`
- Smooth game speed control

## Requirements
To run this game, you need to have `ncurses` installed on your system. You can install it using:

**Ubuntu/Debian:**
```sh
sudo apt-get install libncurses5-dev libncursesw5-dev
```

**MacOS (using Homebrew):**
```sh
brew install ncurses
```

## How to Compile and Run
To compile the game, use the following command:
```sh
g++ snake_game.cpp -o snake_game -lncurses
```

Run the game:
```sh
./snake_game
```

## Code Explanation
The game consists of a `SnakeGame` class that handles game logic, input processing, rendering, and collision detection.

### Header Files Used:
- `#include <iostream>`: Used for standard input and output operations.
- `#include <ncurses.h>`: Provides terminal-based graphical interface and input handling.
- `#include <cstdlib>`: Includes functions like `rand()` for random number generation.
- `#include <ctime>`: Used for seeding the random number generator with `time(0)`.
- `#include <unistd.h>`: Provides `usleep()` for controlling the game speed.

### Data Structures Used:
- **Point Class**: Represents a coordinate (x, y) in the game.

- **SnakeGame Class**:
  - Manages game logic including the snake, food, movement, and rendering.
  - Uses an array of `Point` objects to represent the snake's body.

### Game Logic:
- **Initialization (`initializeGame()`)**:
  - Starts the game with a default snake length of 3 at the center.
  - Generates food at a random position ensuring it does not overlap with the snake.

- **Food Generation (`generateFood()`)**:
  - Uses `rand()` to position the food at a valid location inside the game boundaries.

- **Processing Input (`processInput()`)**:
  - Reads keyboard input to change the snake's direction.
  - Uses `ncurses` functions to handle non-blocking input.

- **Updating the Game (`update()`)**:
  - Moves the snake in the current direction.
  - Checks for collisions with walls or itself (ends the game if true).
  - If the snake eats food, it grows, and new food is generated.
  - Prevents the snake from exceeding the maximum allowed length.

- **Rendering the Game (`render()`)**:
  - Clears the screen and redraws the game state (snake, food, boundaries, score).
  - Displays the current score at the bottom of the screen.
  - Ensures smooth frame rendering to maintain a playable experience.

### Main Loop:
- Runs continuously, processing input, updating the game state, and rendering the screen.
- Ends when the snake collides with a wall or itself.
- After game over, prompts the user to restart or exit.

## Controls
| Key         | Action       |
|------------|-------------|
| `W` / `↑`  | Move Up     |
| `S` / `↓`  | Move Down   |
| `A` / `←`  | Move Left   |
| `D` / `→`  | Move Right  |
| `Q`        | Quit the game |

## Game Over and Restart
When the game ends, the user is prompted with the final score and can press `R` to restart or any other key to exit.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

