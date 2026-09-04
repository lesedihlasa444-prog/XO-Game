Student Name: Lesedi Hlasa

Student Number: ST10512679

Module Name: Mobile App Scripting

Module code: MAST5112


# XO Game (Tic-Tac-Toe)

A two-player Tic-Tac-Toe mobile app built with **React Native (Expo) and TypeScript**, developed progressively through Stages 0â€“7 of the MAST2026 practical exercise.

## Overview

The app lets two players enter their names, then play Tic-Tac-Toe on a 3Ã—3 grid. Turns alternate between Player 1 (X) and Player 2 (O), the game detects a win as soon as three matching marks line up, announces the winner, and blocks further moves once the game is won.

## Features

- **Player name entry screen** â€” two text inputs and a "Start Game" button
- **Screen navigation** â€” stack-based navigation between the Home (player setup) screen and the Game screen, with player names passed as route parameters
- **Playable 3Ã—3 board** â€” tap any empty cell to place your mark
- **Turn management** â€” turns alternate automatically, with an on-screen indicator of whose turn it is
- **Win detection** â€” checks all nine board values for three matching marks in any row, column, or diagonal
- **Winner announcement** â€” displayed conditionally using the `&&` operator
- **Game-over guard** â€” once a winner is declared, further presses are ignored (`if (winner !== 0) return;`)

## Tech Stack

- React Native (Expo)
- TypeScript
- React Navigation (`@react-navigation/native`, `@react-navigation/native-stack`)
- React `useState` hook for all game state

## Project Structure

```
XOGAME/
â”œâ”€â”€ App.tsx # Entire app: App, PlayerScreen, GameScreen, styles
â”œâ”€â”€ index.ts # Entry point (registers App â€” unmodified)
â”œâ”€â”€ app.json # Expo configuration
â”œâ”€â”€ package.json # Dependencies and scripts
â”œâ”€â”€ tsconfig.json # TypeScript configuration
â””â”€â”€ assets/ # App icons and splash images
```

All game code lives in `App.tsx`, which contains three parts:

1. **`App()`** â€” wraps the app in a `NavigationContainer` with a stack navigator (Home â†’ Game)
2. **`PlayerScreen`** â€” collects both player names and navigates to the Game screen
3. **`GameScreen`** â€” holds the nine board states (`block1`â€“`block9`, each `0` = empty / `1` = Player 1 / `2` = Player 2), the turn state, `handlePress`, the win-check logic, and the board UI

## Development Journey (Stages 0â€“7)

What was added 

0-2 - Project setup, player name screen, navigation between screens 
3 - Board layout: nine `useState` blocks, `switch` statements to map each block's value to X / O / blank 
4 -`handlePress`: tapping a cell updates the correct block and alternates turns 
5 - Win detection and winner announcement using `&&` conditional rendering 
6 - **Refactor (display side):** the nine `switch` statements collapsed into one reusable `contentFor` function; added the game-over guard in `handlePress`. No change in behaviour 
7 - **Refactor (update side):** the nine near-identical `if (index === N)` blocks in `handlePress` collapsed into a single reusable pattern; key explanatory comments added. No change in behaviour 

Stages 6 and 7 demonstrate **refactoring**  restructuring working code without changing what it does: duplicate first, prove it works, then simplify.

## How to Run

1. Clone the repository and open the folder in VS Code
2. Install dependencies:
bash
npm install
npx expo install @react-navigation/native @react-navigation/native-stack react-native-screens react-native-safe-area-context
```
3. Start the development server:
```bash
npx expo start
```
4. Scan the QR code with the Expo Go app (Android/iOS) or press `w` to run in a web browser

## Key Concepts Demonstrated

- React hooks (useState) for component state
- Conditional rendering with ternaries and logical AND 
- Controlled inputs (TextInput with value + onChangeText)
- Stack navigation and passing parameters between screens via route.params
- `switch` statements and their refactoring into reusable functions
- Styling with StyleSheet.create and flexbox layout (flexDirection: row for board rows)

