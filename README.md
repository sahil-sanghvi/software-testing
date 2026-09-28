[![Java](https://img.shields.io/badge/Java-JUnit%205-25A162?logo=junit5&logoColor=white)](https://junit.org/junit5/)
[![Testing](https://img.shields.io/badge/testing-property--based%20(jqwik)-informational)](https://jqwik.net/)

# Pacman Test Suite

A set of test files written against **[JPacman](https://github.com/SERG-Delft/jpacman-framework)**, the open-source Pac-Man implementation created and maintained by Arie van Deursen at TU Delft's Software Engineering Research Group (see `UPSTREAM-LICENSE.txt` and the attribution below). This is a testing exercise, not a Pac-Man implementation — none of the game engine is mine or included here; clone it from the link above to run these tests against real code.

## What's here

Seven test classes covering different parts of the engine, using a mix of standard JUnit 5 tests and property-based tests:

| File | Covers | Technique |
|---|---|---|
| `board/BoardTest.java` | Board construction and square lookup | Parameterized JUnit |
| `board/UnitSquarePropertyTest.java` | Square adjacency invariants | Property-based (jqwik) |
| `game/GameFactoryTest.java` | Game factory wiring | JUnit + Mockito |
| `game/SinglePlayerGameTest.java` | Single-player game lifecycle | JUnit |
| `level/PlayerPropertyTest.java` | Player state invariants | Property-based (jqwik) |
| `property/DirectionPropertyTest.java` | `Direction` enum invariants | Property-based (jqwik) |
| `property/PointCalculatorPropertyTest.java` | Score calculation invariants | Property-based (jqwik) |

The property-based tests generate many randomized inputs per run rather than a fixed set of hand-picked cases — useful for catching edge cases in enum/state invariants that example-based tests tend to miss.

## Running these tests

These tests compile against JPacman's `board`, `game`, `level`, and `npc.ghost`
packages, JUnit 5, jqwik (property-based testing), AssertJ, and Mockito — none of
which are vendored here, since this repo is the tests, not the engine.

To run them yourself:

1. Clone the engine this test suite targets:
   ```bash
   git clone https://github.com/SERG-Delft/jpacman-framework.git
   ```
2. Copy this repo's `src/test/java/nl/tudelft/jpacman/` into the cloned engine at the
   same path, overwriting/merging with its existing `src/test/java/nl/tudelft/jpacman/`.
3. Run the engine's Gradle test task from inside that checkout:
   ```bash
   ./gradlew test
   ```

The engine repo already includes JUnit 5, jqwik, AssertJ, and Mockito as test
dependencies in its own `build.gradle`, so no extra setup is needed beyond that.

## Attribution

JPacman is created and maintained by Arie van Deursen and contributors, licensed under Apache 2.0 (`UPSTREAM-LICENSE.txt`). This folder contains only test code written against it — no engine source is included or claimed as original work.

## 🎓 Project Context

Built as part of **SENG 275: Software Development Methods II** at the University of
Victoria.

## ⚠️ Academic Integrity Notice

This repository is maintained for portfolio and educational purposes only. If you are
currently enrolled in SENG 275 at the University of Victoria or a similar software
testing course, please note that using this code in your own assignments may
constitute a violation of Academic Integrity policies.
