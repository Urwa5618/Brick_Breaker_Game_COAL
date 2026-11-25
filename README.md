# 🧱 Brick Breaker (x86 Assembly)

A classic **Brick Breaker** game written entirely in **MASM x86 assembly** using the **Irvine32** library. It runs in the Windows console and was built as a project for the **EL-2003 Computer Organization & Assembly Language** lab.

---

## ✨ Features

- 🎮 **3 levels** with different brick layouts (full wall, striped, holes)
- ⚙️ **3 difficulty modes** – Easy, Medium, Hard
- 🎨 **Colour themes** – different brick and border colours for each level
- 👤 **Player name** entry (up to 12 characters)
- 🏆 **Top-5 leaderboard**, saved permanently in `leaderboard.dat`
- 🖥️ **Auto-centred game screen** – stays centred in the console, including full screen, and re-centres live when the window is resized
- ⚡ Ball **speeds up** as bricks are destroyed
- 🎯 Paddle **hit position** controls the ball's direction (left / middle / right third)

---

## 🕹️ Controls

| Key | Action |
|-----|--------|
| `←` / `→` or `A` / `D` | Move paddle |
| `ESC` | Quit current game |
| `ENTER` | Play (main menu) |
| `L` | Open leaderboard (main menu) |
| `R` | Reset leaderboard (inside leaderboard screen) |

On the end screen: `Y` = play again, `D` = change difficulty, `N` = main menu.

---

## 📊 Difficulty Modes

| Mode | Lives | Paddle Width | Starting Speed | Score Multiplier |
|------|:-----:|:------------:|:--------------:|:----------------:|
| Easy   | 5 | 11 (wide)   | 85 ms/frame (slow)   | ×1 |
| Medium | 3 | 9 (normal)  | 70 ms/frame (normal) | ×2 |
| Hard   | 2 | 7 (small)   | 55 ms/frame (fast)   | ×3 |

---

## 🏅 Scoring

- Each brick gives **(4 − row) × 10 × difficulty multiplier** points, so top-row bricks are worth the most.
- Clearing a level gives a **level bonus**.
- Each level starts faster than the last, and the ball speeds up with every brick destroyed (down to a minimum of 25 ms per frame).
- Clear all **3 levels** to win.

---

## 🛠️ Requirements

- Windows (32-bit console application)
- **Visual Studio** with the **MASM** (x86) toolchain
- **[Irvine32 library](https://github.com/surferkip/asmbook)** set up for Visual Studio (`Irvine32.inc` and `Irvine32.lib`)

---

## 🚀 How to Build & Run

### Option 1: Visual Studio
1. Set up an Irvine32 MASM project in Visual Studio (x86 / Win32 configuration).
2. Add `source.asm` to the project.
3. Build and run (`Ctrl + F5`).

### Option 2: Command line (MASM)
Run these in a Developer Command Prompt, from the folder containing `source.asm` and the Irvine32 files (adjust the Irvine path to your setup):

```bat
ml /c /coff /I C:\Irvine source.asm
link /subsystem:console /libpath:C:\Irvine source.obj irvine32.lib kernel32.lib user32.lib
source.exe
```

> 💡 `leaderboard.dat` is created automatically in the game's working folder the first time a score is saved.

---

## 📁 Project Structure

```
.
├── source.asm        # Complete game source code
├── leaderboard.dat   # Auto-generated high-score file (created at runtime)
└── README.md
```

---

## 🧠 How It Works (Technical Notes)

- The whole game is drawn on a **virtual 80×25 canvas**. A custom `GotoXYo` routine adds a centring offset (`offX`, `offY`) to every position, which keeps the game centred in any console size.
- Brick layouts are stored as **48-byte tables** (4 rows × 12 columns), one per level.
- Difficulty settings (lives, speed, paddle width, multiplier) are stored in **lookup tables** indexed by the chosen difficulty.
- The main loop runs: `Delay → CheckResize → HandleInput → MoveBall → DrawHUD`.
- Collision handling in `MoveBall` checks, in order: side walls → top wall → bricks → paddle → pit (life lost).
- The leaderboard is stored as one binary block (5 names + 5 scores) read and written with the Windows file API.

---

## 📸 Screenshots

*Add screenshots of your game here, for example:*

```
![Main Menu](screenshots/menu.png)
![Gameplay](screenshots/gameplay.png)
![Leaderboard](screenshots/leaderboard.png)
```

---

## 👨‍💻 Author

**Your Name**
Roll No: `XX-XXXX`
EL-2003 Computer Organization & Assembly Language Lab

---

## 📄 License

This project was created for educational purposes. Feel free to learn from it and modify it. Add a license of your choice (e.g. MIT) if you want others to reuse it.# 🧱 Brick Breaker (x86 Assembly)

A classic **Brick Breaker** game written entirely in **MASM x86 assembly** using the **Irvine32** library. It runs in the Windows console and was built as a project for the **EL-2003 Computer Organization & Assembly Language** lab.

---

## ✨ Features

- 🎮 **3 levels** with different brick layouts (full wall, striped, holes)
- ⚙️ **3 difficulty modes** – Easy, Medium, Hard
- 🎨 **Colour themes** – different brick and border colours for each level
- 👤 **Player name** entry (up to 12 characters)
- 🏆 **Top-5 leaderboard**, saved permanently in `leaderboard.dat`
- 🖥️ **Auto-centred game screen** – stays centred in the console, including full screen, and re-centres live when the window is resized
- ⚡ Ball **speeds up** as bricks are destroyed
- 🎯 Paddle **hit position** controls the ball's direction (left / middle / right third)

---

## 🕹️ Controls

| Key | Action |
|-----|--------|
| `←` / `→` or `A` / `D` | Move paddle |
| `ESC` | Quit current game |
| `ENTER` | Play (main menu) |
| `L` | Open leaderboard (main menu) |
| `R` | Reset leaderboard (inside leaderboard screen) |

On the end screen: `Y` = play again, `D` = change difficulty, `N` = main menu.

---

## 📊 Difficulty Modes

| Mode | Lives | Paddle Width | Starting Speed | Score Multiplier |
|------|:-----:|:------------:|:--------------:|:----------------:|
| Easy   | 5 | 11 (wide)   | 85 ms/frame (slow)   | ×1 |
| Medium | 3 | 9 (normal)  | 70 ms/frame (normal) | ×2 |
| Hard   | 2 | 7 (small)   | 55 ms/frame (fast)   | ×3 |

---

## 🏅 Scoring

- Each brick gives **(4 − row) × 10 × difficulty multiplier** points, so top-row bricks are worth the most.
- Clearing a level gives a **level bonus**.
- Each level starts faster than the last, and the ball speeds up with every brick destroyed (down to a minimum of 25 ms per frame).
- Clear all **3 levels** to win.

---

## 🛠️ Requirements

- Windows (32-bit console application)
- **Visual Studio** with the **MASM** (x86) toolchain
- **[Irvine32 library](https://github.com/surferkip/asmbook)** set up for Visual Studio (`Irvine32.inc` and `Irvine32.lib`)

---

## 🚀 How to Build & Run

### Option 1: Visual Studio
1. Set up an Irvine32 MASM project in Visual Studio (x86 / Win32 configuration).
2. Add `source.asm` to the project.
3. Build and run (`Ctrl + F5`).

### Option 2: Command line (MASM)
Run these in a Developer Command Prompt, from the folder containing `source.asm` and the Irvine32 files (adjust the Irvine path to your setup):

```bat
ml /c /coff /I C:\Irvine source.asm
link /subsystem:console /libpath:C:\Irvine source.obj irvine32.lib kernel32.lib user32.lib
source.exe
```

> 💡 `leaderboard.dat` is created automatically in the game's working folder the first time a score is saved.

---

## 📁 Project Structure

```
.
├── source.asm        # Complete game source code
├── leaderboard.dat   # Auto-generated high-score file (created at runtime)
└── README.md
```

---

## 🧠 How It Works (Technical Notes)

- The whole game is drawn on a **virtual 80×25 canvas**. A custom `GotoXYo` routine adds a centring offset (`offX`, `offY`) to every position, which keeps the game centred in any console size.
- Brick layouts are stored as **48-byte tables** (4 rows × 12 columns), one per level.
- Difficulty settings (lives, speed, paddle width, multiplier) are stored in **lookup tables** indexed by the chosen difficulty.
- The main loop runs: `Delay → CheckResize → HandleInput → MoveBall → DrawHUD`.
- Collision handling in `MoveBall` checks, in order: side walls → top wall → bricks → paddle → pit (life lost).
- The leaderboard is stored as one binary block (5 names + 5 scores) read and written with the Windows file API.

---

## 📸 Screenshots

*Add screenshots of your game here, for example:*

```
![Main Menu](screenshots/menu.png)
![Gameplay](screenshots/gameplay.png)
![Leaderboard](screenshots/leaderboard.png)
```

---

## 👨‍💻 Authors

|**Urwa Rafique**  | **Awais Muhammad Khan**|
|Roll No: `25K-3066`| Roll No: `25K-0845`|
EL-2003 Computer Organization & Assembly Language Lab

---

## 📄 License

This project was created for educational purposes. Feel free to learn from it and modify it. Add a license of your choice (e.g. MIT) if you want others to reuse it.
