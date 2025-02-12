# Snake Game in C++

## Overview
This game is designed to be executed on Windows OS.
This project is a simple console-based Snake game written in C++. The player controls the snake using the keyboard, trying to eat food while avoiding collisions with the walls and itself. The game keeps track of the score and allows restarting after a game over.

## Data Structures Used
- **Class `Point`**: Represents coordinates (x, y) on the game board.
- **Enum `Direction`**: Defines movement directions (STOP, LEFT, RIGHT, UP, DOWN).
- **Array `snake[MAX_LENGTH]`**: Stores the snake's body positions.
- **Class `SnakeGame`**: Manages the game logic, including movement, collisions, food generation, and score tracking.

## Header Files Used
- `<iostream>`: Handles input and output operations.
- `<conio.h>`: Provides `_kbhit()` and `_getch()` functions for detecting key presses (Windows-specific).
- `<windows.h>`: Enables `Sleep()` for delay functionality.
- `<ctime>`: Used for random food generation.
- `<algorithm>`: Utilized for updating the high score using `max()`.

## Game Logic
1. **Setup (`Setup` method)**:
   - Initializes the snake's position and length.
   - Generates the first food item.
   
  ![Screenshot 2025-02-13 035542](https://github.com/user-attachments/assets/7bf4a9de-d7cc-420b-b754-36504bf83739)


2. **Rendering (`DrawBoard` method)**:
   - Clears the console and draws the board.
   - Displays the snake, food, and score.
   
   ![Screenshot 2025-02-13 035659](https://github.com/user-attachments/assets/d283fd0c-cf6f-4237-a1cb-f2d86f1c61a8)


3. **User Input (`Input` method)**:
   - Detects key presses (`WASD` keys to move, `X` to quit).
   
   ![Screenshot 2025-02-13 035710](https://github.com/user-attachments/assets/5e1c0f04-fbd2-4956-a745-4c53a33f2e69)


4. **Game Logic (`Logic` method)**:
   - Moves the snake and checks for collisions.
   - Increases length and score when food is eaten.
   
   ![Screenshot 2025-02-13 035723](https://github.com/user-attachments/assets/a05054d5-3e5d-4aa6-a65e-998e73fbce7f)


5. **Food Generation (`GenerateFood` method)**:
   - Places food randomly, ensuring it is not on the snake.
   
   ![Screenshot 2025-02-13 035735](https://github.com/user-attachments/assets/7fdf929d-1f07-474d-80f7-62add4afeba1)


6. **Game Loop (`Run` method)**:
   - Repeats drawing, handling input, and updating logic.
   - Prompts the user to restart or quit after game over.

## How to Play
- Use `W`, `A`, `S`, `D` to move the snake.
- Eat food (`F`) to grow longer and score points.
- Avoid hitting walls (`#`) and yourself.
- Press `X` to quit during gameplay.
- After game over, press `R` to restart or `Q` to quit.

## Compilation & Execution
![Screenshot 2025-02-13 035745](https://github.com/user-attachments/assets/74ad9f63-723a-496e-8d7a-4fa7a459cb0b)


