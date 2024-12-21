# Virtual League Simulation in C++

This project implements a **virtual soccer league** simulation with teams, players, and coaches. It includes classes for **Team**, **Player**, **Coach**, **League**, and more, allowing you to:

- **Initialize** a set of teams, each with its own formation and coach.  
- **Generate** a fixture (match schedule) automatically.  
- **Simulate** matches by calculating goals and outcomes based on performance metrics.  
- **Display** league standings, player details, and search functionalities via a simple console menu.

## About

This repository showcases:
- **Object-Oriented Design**: Classes `Coach`, `Player`, and `Team` inherit from a common abstract `Employee` class, illustrating polymorphism and clean architecture.
- **Data Handling**: Methods read from `.txt` files to generate names, surnames, and team data, then store them in static vectors.
- **Simulation Logic**: Match outcomes are determined by comparing teams’ overall and position-based performances (offense, defense, midfield).
- **Console Menu**: A straightforward text-based menu system in `utils.cpp`/`utils.h` guides you through searching, modifying, and simulating league actions.

---

## Table of Contents

1. [Features](#features)  
3. [Dependencies](#dependencies)  
4. [Build and Run](#build-and-run)  
5. [Usage](#usage)  
6. [Implementation Details](#implementation-details)  
7. [Contributing](#contributing)  

---

## Features

1. **Coach & Player Singletons**  
   - `Coach::getInstance()` and `Player::getInstance()` manage data reading and static vectors storing names/surnames.  
   - Ensures only one instance handles these global resources.

2. **Employee Hierarchy**  
   - `Employee` is an abstract base class with pure virtual methods (`readData`, `print`, etc.).  
   - `Coach` and `Player` inherit from it and implement domain-specific behavior.

3. **Team Class**  
   - Holds a `Coach`, a list of `Player`s, formation logic, and performance metrics (e.g., defensive, midfield, forward performance).  
   - Overloaded operators (`operator++`, `operator--`, `operator+=`, etc.) to update wins, draws, losses, goals for/against, and points.

4. **League Class**  
   - Maintains a vector of teams and a singly linked list (`SinglyLinkedList`) of matches.  
   - Generates a round-robin fixture, simulates matches, and tracks standings.

5. **Menu System**  
   - Defined in `utils.h/.cpp`, presents a text-based UI for operations:
     - Searching for players or teams.
     - Changing team formations.
     - Printing standings or match results.

---

## Dependencies

- **C++11 or higher** (for `auto`, range-based loops, etc.).  
- A standard library implementation supporting `<vector>`, `<string>`, `<iostream>`, `<fstream>`, `<iomanip>`, etc.

No third-party libraries are required. If you’re using a specific compiler (GCC, Clang, MSVC), ensure it supports modern C++ features.

---

## Build and Run

1. **Clone** or download this repository:
   ```bash
   git clone https://github.com/YourUsername/VirtualLeague.git
   cd VirtualLeague
   ```
2. **Compile** the sources (example with g++):
   ```bash
   g++ -std=c++11 -o league \
       coach.cpp \
       player.cpp \
       team.cpp \
       league.cpp \
       utils.cpp \
       main.cpp
   ```
   *(Adjust file names and paths as necessary.)*

3. **Run** the compiled executable:
   ```bash
   ./league
   ```
   On Windows:
   ```bat
   league.exe
   ```

---

## Usage

1. **Check Data Files**  
   - Ensure `.txt` files (e.g., `takimlar.txt`, `isim.txt`, `soyisim.txt`) are present for reading team, coach, and player names.
   - If any file is missing or unreadable, the program will print an error and exit.

2. **Menu Navigation**  
   - On startup, the program initializes data (players, coaches, teams), generates a fixture, and loads the main menu.
   - **Main Menu** offers options like *Player Menu*, *Team Menu*, *League Menu*.
   - Choose an option (1, 2, 3, etc.) and press Enter.  
   - Subsequent menus allow for searching, modifying, or simulating matches.

3. **League Simulation**  
   - Once the league is started (e.g., “Make Matches”), it simulates match outcomes based on random factors and performance metrics.
   - **Standings** can be printed, showing teams sorted by points (wins, draws, losses, goals for/against).

---

## Implementation Details

- **Singleton Pattern**  
  The `Coach` and `Player` classes are singletons—only one instance manipulates their static data vectors.
- **Overloaded Operators**  
  `Team` overloads increment (`++`), decrement (`--`), plus-equal (`+=`), and minus-equal (`-=`) operators to manage wins, losses, draws, and goals.
- **Singly Linked List**  
  Matches are stored as nodes (`SinglyNode`) with pointers to two `Team*` objects. A `match()` function simulates all stored matches.
- **Searching**  
  - `searchPlayerByName(...)` scans players in each team until a match is found.
  - `searchTeamByName(...)` and `searchTeamByAbbreviation(...)` help retrieve a team quickly.
- **Error Handling**  
  - `ifstream` checks if files exist.
  - Basic input validation in console menus prevents out-of-range selections.

---

## Contributing

Contributions are welcome! If you’d like to propose changes:

1. **Fork** the repository and clone locally.  
2. Create a **new branch** (`feature/new-idea`).  
3. **Commit** your changes and **push** to your fork.  
4. Open a **Pull Request** describing the modifications.

---

**Enjoy managing your virtual soccer league!** If you have questions or suggestions, feel free to open an issue or contact the repository maintainers.
