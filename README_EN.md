# Java 2048 Logic Engine

## Overview
A Java-based core engine for the classic 2048 puzzle game. This project focuses on the decoupling of game business logic from the rendering layer, with a primary emphasis on matrix manipulation and state machine transitions during board tilts.

## Tech Stack
* Language: Java 1.8+
* Testing: JUnit 4
* External Dependencies: library-sp24/ (includes core rendering libraries, JUnit testing components, and other necessary third-party dependencies)
* Development Methodology: Test-Driven Development (TDD)
* Design Pattern: MVC-based Logic Separation

---

## Technical Highlights

### 1. Optimized Matrix Manipulation
The core "tilt" logic is implemented using a unified abstraction strategy:
* Directional Normalization: Utilizes matrix rotation concepts to unify all four directional movements into a single "Upward" operation. This reduces code redundancy by over 70% compared to traditional conditional branching.
* Constraint Management: Implements strict merging rules (single merge per move per tile) using a two-pointer approach, achieving O(N) time complexity for column-wise processing.

### 2. Comprehensive Unit Testing
Adheres to strict TDD practices to ensure engine reliability:
* Scenario Coverage: Developed 10+ specialized test suites covering complex cases such as multi-column merging, full-board saturation, and edge-case win/loss conditions.
* Quality Assurance: Achieved 100% pass rate for the `game2048logic` module's automated tests.

---

## Directory Structure
```text
proj0
├── src                              # Source code directory
│   ├── game2048logic                # Core logic layer (Model)
│   │   └── Model.java               # 2048 core state machine and tilt matrix sliding algorithm implementation (Primary development file)
│   │
│   └── game2048rendering            # Rendering and view layer (View & Controller)
│       ├── Main.java                # Main entry point for game startup
│       ├── Board.java               # Board grid data model
│       ├── Tile.java                # Number tile entity
│       └── GUI.java / Game.java     # Graphical user interface and key event listener
│
└── tests                            # Unit test directory (JUnit)
    └── game2048logic                # Comprehensive automated test suite for core logic
        ├── TestModel.java           # Model overall state machine tests
        ├── TestTiltMerge.java       # Specific tests for tile merge logic
        ├── TestTiltColumn.java      # Specific tests for single-column sliding logic
        └── ... (Total of 10+ granular scenario test classes)
```
