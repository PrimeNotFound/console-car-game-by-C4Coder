# 🏎️ Console Car Racing Game (C++)

This is a classic terminal-based car racing game made using C++. It's a simple but fun game where you dodge incoming enemy cars by moving left or right.

## 🎮 Features

- Real-time car control using keyboard input
- ASCII-art-based car and enemy visuals
- Random enemy car generation
- Score tracking system
- Game over and restart functionality

---

## 🔧 Requirements

- Windows OS
- A C++ compiler (like `g++` or MSVC)
- Windows-compatible console (uses `windows.h`, `conio.h`, etc.)

---

## ▶️ Controls

- `A` → Move car to the left  
- `D` → Move car to the right  
- `ESC` → Quit the game

---
### 🧠 Collision Detection Logic

#### Original Version :

```cpp
int collision() {
    if (enemyY[0] + 4 >= 23) { // Vertical range near car
        if (enemyX[0] + 4 - carPos >= 0 && enemyX[0] + 4 - carPos < 9) {
            return 1; // Collision detected
        }
    }
    return 0; // No collision
}
```

#### ✅ Modified Version (Improved, Bounding Box Check)

This version checks both enemies and uses accurate bounding box logic :

```cpp
int collision() {
    for (int i = 0; i < 2; i++) {
        if (enemyFlag[i] == true) {
            // Check vertical overlap with car
            if (enemyY[i] + 4 >= 22 && enemyY[i] <= 25) {
                // Check horizontal overlap with car
                if (enemyX[i] + 4 >= carPos && enemyX[i] <= carPos + 3) {
                    return 1; // Collision detected
                }
            }
        }
    }
    return 0; // No collision
}

```


## 🔄 Versions Overview

There are **two versions** of this game:  
- 🎯 **Original Version** (simple and functional)  
- ⚡ **Modified Version** (improved visuals and mechanics)

### 🔍 Comparison Table

| Feature                     | Original Version                          | Modified Version                          |
|----------------------------|--------------------------------------------|--------------------------------------------|
| **Enemy Car Drawing**      | 2-line enemy (`" ** "`, `" ** "`)         | Full 4-line enemy (`"****"`, `" ** "`, `"****"`, `" ** "`) |
| **Collision Detection**    | Only checks `enemy[0]`, basic logic        | Checks both `enemy[0]` & `enemy[1]` with bounding box |
| **Border Characters**      | `±` character used                        | Classic `#` character used                 |
| **Visual Appearance**      | Lighter and simpler                       | More detailed and immersive                |
| **Difficulty**             | Easier (fewer enemies, less accurate hits)| More challenging (accurate collisions + 2 enemies) |
| **Code Logic**             | Simpler, beginner-friendly                | Cleaner structure, more advanced logic     |
| **Enemy Activation**       | Only activates `enemy[1]` later           | Same logic, but smoother transitions       |
| **Gameplay Feedback**      | Basic                                    | Enhanced with improved visuals and collision checks |

---

## 🚀 How to Run

### 1. Compile the Code

```bash
g++ car_game.cpp -o car_game
```

## 📸 Screenshots
#### We got a very poitive response from the owner :
![Screenshot 2025-04-16 010249](https://github.com/user-attachments/assets/0b5bb377-b5ab-491e-b73e-974e50170118)



---

## 🤝 Contributions

Feel free to fork, play around, or even improve the game logic! Add obstacles, change enemy patterns, or implement power-ups — up to you!

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 💡 Future Ideas

- Add soundtrack using `PlaySound`
- Support for more lanes / cars
- Difficulty levels
- Cross-platform support using `ncurses` or SDL

