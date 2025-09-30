# Getting Started with QWords Game

## Overview
QWords is a Wordle-like word guessing game built with **TypeScript** and **Express.js**. Players have 5 attempts to guess a 6-letter word with visual feedback after each guess.

## Framework & Technology Stack

### Core Technologies
- **TypeScript 5.7.2** - Primary development language with strict typing
- **Express.js 4.18.3** - Web application framework
- **EJS 3.1.10** - Server-side templating engine
- **Node.js** - Runtime environment (v14+ required)

### Development Tools
- **Jest 29.7.0** - Testing framework
- **ts-node 10.9.2** - TypeScript execution for development
- **ESLint 9.3.0** - Code linting
- **Bootstrap 5.3** - Frontend CSS framework

## Prerequisites

Before starting, ensure you have:
- **Node.js** (v14 or higher)
- **npm** (Node Package Manager)
- A code editor (VS Code recommended)

## Quick Setup

### 1. Install Dependencies
```bash
cd typescript
npm install
```

### 2. Environment Configuration
The application uses environment variables defined in `.env`:
```
PORT=8090
WORKSHOP_MODE=true
```

### 3. Start Development Server
```bash
# Workshop mode (default)
npm start

# Standalone mode
npm run start:standalone
```

### 4. Access the Application
Open your browser and navigate to:
- Workshop mode: `http://localhost:8090/proxy/8090`
- Standalone mode: `http://localhost:8090`

## Application Structure

### MVC Architecture
```
typescript/
├── controllers/          # HTTP request handlers
│   ├── GameController.ts    # Game logic and routes
│   └── HomeController.ts    # Home page routes
├── models/              # Data structures
│   ├── Word.ts             # Word entity with game logic
│   └── GameStatus.ts       # Game state enumeration
├── services/            # Business logic
│   └── WordSelectionService.ts  # Word selection logic
├── repositories/        # Data access layer
│   └── WordList.ts         # Word database operations
├── views/              # EJS templates
│   ├── game.ejs           # Main game interface
│   └── home.ejs           # Landing page
├── resources/          # Static data
│   └── default-words.txt  # Word database
└── static/             # Web assets
    └── images/
```

### Core Application Files
- **`index.ts`** - Application entry point and server initialization
- **`app.ts`** - Express configuration and middleware setup
- **`config.ts`** - Environment configuration utilities

## Key Classes & Components

### 1. Word Class (`models/Word.ts`)
Handles individual word operations and game feedback:
```typescript
class Word {
    getInfo(guess: string): string    // Returns feedback (+, ?, X)
    isCorrect(guess: string): boolean // Checks if guess matches
    contains(c: string): boolean      // Checks if letter exists
}
```

### 2. WordList Class (`repositories/WordList.ts`)
Manages the word database with singleton pattern:
```typescript
class WordList {
    static getInstance(): WordList    // Singleton access
    getRandomWord(): string          // Selects random word
    containsWord(word: string): boolean // Validates word exists
    loadWordsFromFile(path: string): void // Loads custom word lists
}
```

### 3. GameController (`controllers/GameController.ts`)
Orchestrates game flow and HTTP handling:
- **GET `/game`** - Initialize new game session
- **POST `/game`** - Process player guesses and update state

### 4. WordSelectionService (`services/WordSelectionService.ts`)
Encapsulates word selection business logic:
```typescript
class WordSelectionService {
    getWord(): string  // Returns selected word for game
}
```

## Game Mechanics

### Feedback System
After each guess, players receive letter-by-letter feedback:
- **`+`** - Correct letter in correct position (green)
- **`?`** - Correct letter in wrong position (yellow)
- **`X`** - Letter not in the word (red)

### Game States
Tracked via `GameStatus` enum:
- **`INPROGRESS`** - Game is active
- **`SUCCESS`** - Player guessed correctly
- **`FAILED`** - Player used all 5 attempts

## Development Commands

### Building & Running
```bash
npm run build          # Compile TypeScript to JavaScript
npm start              # Start in workshop mode
npm run start:standalone # Start in standalone mode
```

### Testing
```bash
npm test               # Run Jest test suite
```

### Configuration Modes
- **Workshop Mode** (`WORKSHOP_MODE=true`) - Uses `/proxy/8090` base path
- **Standalone Mode** (`WORKSHOP_MODE=false`) - Uses root path

## Project Features

### Session Management
- Tracks user game state across HTTP requests
- Maintains attempt counters and game progress

### Responsive UI
- Bootstrap-based interface
- Mobile-friendly design
- Interactive visual feedback

### Configurable Word Lists
- Default 6-letter word database in `resources/default-words.txt`
- Support for custom word lists via file loading

### Environment Flexibility
- Workshop mode for training environments
- Standalone mode for independent deployment
- Configurable ports and base paths

## Next Steps

1. **Explore the Code** - Start with `index.ts` and follow the MVC flow
2. **Run Tests** - Execute `npm test` to understand the testing approach
3. **Customize Words** - Modify `default-words.txt` to add your own word lists
4. **Extend Features** - Add new game modes or difficulty levels

The application demonstrates modern TypeScript development patterns with clean architecture, making it an excellent learning resource for web development! 🎯