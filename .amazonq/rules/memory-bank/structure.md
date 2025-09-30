# Project Structure

## Directory Organization
```
workshop-all/
├── java/           # Spring Boot implementation
├── python/         # Flask implementation  
├── csharp/         # ASP.NET Core implementation
├── nodejs/         # Express.js implementation
├── typescript/     # TypeScript/Express implementation
├── prompts/        # Amazon Q Developer prompts
├── scripts/        # Installation and setup scripts
└── frontend/       # Shared frontend resources
```

## Core Components (Per Language)
Each language implementation follows consistent MVC architecture:

### Controllers
- **GameController**: Handles game logic and API endpoints
- **HomeController**: Manages home page and navigation

### Models
- **Word**: Represents game words with properties
- **GameStatus**: Tracks current game state

### Repositories
- **WordList**: Data access layer for word management

### Services
- **WordSelectionService**: Business logic for word selection

### Views/Templates
- **game**: Game interface template
- **home**: Landing page template

## Architectural Patterns
- **MVC Architecture**: Clear separation of concerns
- **Repository Pattern**: Data access abstraction
- **Service Layer**: Business logic encapsulation
- **RESTful APIs**: Consistent endpoint design
- **Template Rendering**: Server-side view generation

## Shared Resources
- Static assets (CSS, JavaScript, images)
- Word lists and game data
- Configuration files
- Test suites