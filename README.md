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
   
   ```cpp
   void Setup() {
       gameOver = false;
       dir = STOP;
       length = 3;
       snake[0] = Point(WIDTH / 2, HEIGHT / 2);
       GenerateFood();
   }
   ```

2. **Rendering (`DrawBoard` method)**:
   - Clears the console and draws the board.
   - Displays the snake, food, and score.
   
   ```cpp
   void DrawBoard() {
       system("cls");
       for (int i = 0; i < HEIGHT; ++i) {
           for (int j = 0; j < WIDTH; ++j) {
               if (i == 0 || i == HEIGHT - 1 || j == 0 || j == WIDTH - 1)
                   cout << "#";
               else if (Point(j, i) == snake[0])
                   cout << "@";
               else if (Point(j, i) == food)
                   cout << "F";
               else cout << " ";
           }
           cout << endl;
       }
       cout << "Score: " << score << endl;
   }
   ```

3. **User Input (`Input` method)**:
   - Detects key presses (`WASD` keys to move, `X` to quit).
   
   ```cpp
   void Input() {
       if (_kbhit()) {
           switch (_getch()) {
               case 'a': if (dir != RIGHT) dir = LEFT; break;
               case 'd': if (dir != LEFT) dir = RIGHT; break;
               case 'w': if (dir != DOWN) dir = UP; break;
               case 's': if (dir != UP) dir = DOWN; break;
               case 'x': gameOver = true; break;
           }
       }
   }
   ```

4. **Game Logic (`Logic` method)**:
   - Moves the snake and checks for collisions.
   - Increases length and score when food is eaten.
   
   ```cpp
   void Logic() {
       Point newHead = snake[0];
       switch (dir) {
           case LEFT: newHead.x--; break;
           case RIGHT: newHead.x++; break;
           case UP: newHead.y--; break;
           case DOWN: newHead.y++; break;
           default: return;
       }

       if (newHead.x < 1 || newHead.x >= WIDTH - 1 || newHead.y < 1 || newHead.y >= HEIGHT - 1)
           gameOver = true;

       for (int i = length; i > 0; i--) {
           snake[i] = snake[i - 1];
       }
       snake[0] = newHead;

       if (newHead == food) {
           score++;
           length++;
           GenerateFood();
       }
   }
   ```

5. **Food Generation (`GenerateFood` method)**:
   - Places food randomly, ensuring it is not on the snake.
   
   ```cpp
   void GenerateFood() {
       do {
           food.x = rand() % (WIDTH - 2) + 1;
           food.y = rand() % (HEIGHT - 2) + 1;
       } while (isOnSnake(food));
   }
   ```

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
```sh
 g++ -o snake_game snake_game.cpp
 ./snake_game
```
## Credits
-https://youtu.be/E_-lMZDi7Uw?si=fzUip6IYLdX8sGQy
-https://youtu.be/W1e5wO7XR2w?si=xD7aR7Ws5peGUr2x
-https://www.geeksforgeeks.org/

## Contributions
-Aryan Kanani 
   Code Developement and README file
-Shivam Thanki
   Code Developement and Rectification of errors
-Arjunsinh Vaghela
   Code Developement and OPtimization of code

