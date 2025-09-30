# Project Structure

## Directory Organization

### Core Application
- **`app.ts`** - Express application configuration and middleware setup
- **`index.ts`** - Application entry point and server initialization
- **`config.ts`** - Environment configuration and application settings

### MVC Architecture
- **`controllers/`** - Request handling and response logic
  - `GameController.ts` - Game logic, word validation, and game state management
  - `HomeController.ts` - Home page rendering and initial game setup
- **`models/`** - Data structures and type definitions
  - `Word.ts` - Word entity with validation and comparison methods
  - `GameStatus.ts` - Game state enumeration and status tracking
- **`views/`** - EJS templates for UI rendering
  - `game.ejs` - Main game interface with interactive elements
  - `home.ejs` - Landing page and game introduction

### Business Logic
- **`services/`** - Core business logic and algorithms
  - `WordSelectionService.ts` - Word selection and game initialization logic
- **`repositories/`** - Data access and word management
  - `WordList.ts` - Word database operations and word list management

### Resources & Assets
- **`resources/`** - Static data files
  - `default-words.txt` - Default word list for gameplay
- **`static/`** - Static web assets
  - `images/` - Game graphics and visual elements

### Testing & Configuration
- **`tests/`** - Test suites and specifications
  - `wordlist.test.ts` - Word list functionality tests
- **Configuration Files**
  - `package.json` - Dependencies and build scripts
  - `tsconfig.json` - TypeScript compiler configuration
  - `jest.config.js` - Testing framework setup
  - `.env` - Environment variables

## Architectural Patterns

### MVC Pattern Implementation
- **Models**: Define data structures and business entities
- **Views**: EJS templates for server-side rendering
- **Controllers**: Handle HTTP requests and coordinate between models and views

### Service Layer Architecture
- Controllers delegate business logic to service classes
- Services encapsulate game rules and word selection algorithms
- Repositories abstract data access patterns

### Component Relationships
- Controllers → Services → Repositories → Models
- Views receive data from Controllers via template rendering
- Configuration centralized in dedicated config module