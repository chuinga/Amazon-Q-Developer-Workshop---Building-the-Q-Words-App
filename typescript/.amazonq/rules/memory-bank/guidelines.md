# Development Guidelines

## Code Quality Standards

### TypeScript Configuration
- Use strict TypeScript compilation with explicit type annotations
- Enable all strict mode flags in `tsconfig.json`
- Prefer explicit return types for public methods
- Use `unknown` type for error handling instead of `any`

### Import/Export Patterns
- Use ES6 import syntax: `import express from 'express'`
- Mix CommonJS exports with ES6 imports: `export = ClassName`
- Group imports: external libraries first, then internal modules
- Use path-based imports for internal modules: `../services/WordSelectionService`

### Class Structure Standards
- Use PascalCase for class names: `WordList`, `GameController`
- Implement public/private visibility modifiers consistently
- Place constructor after property declarations
- Group methods by functionality (public first, then private)

### Error Handling Conventions
```typescript
try {
    // operation
} catch (error: unknown) {
    throw new Error(`Context message: ${(error as Error).message}`);
}
```

## Architectural Patterns

### Singleton Pattern Implementation
```typescript
private static instance: ClassName;
public static getInstance(): ClassName {
    if (!ClassName.instance) {
        ClassName.instance = new ClassName();
    }
    return ClassName.instance;
}
```

### Controller Pattern
- Use Express Router for route organization
- Initialize routes in constructor via `initializeRoutes()`
- Pass configuration (workshopMode, basePath) through constructor
- Use private helper methods for request processing

### Service Layer Pattern
- Services encapsulate business logic
- Controllers delegate to services for complex operations
- Services manage dependencies (repositories, external APIs)
- Keep services stateless when possible

### Repository Pattern
- Repositories handle data access and persistence
- Provide CRUD operations with descriptive method names
- Return copies of data to prevent external modification: `return [...this.wordlist]`
- Handle file I/O operations with proper error handling

## Naming Conventions

### Variables and Methods
- Use camelCase: `currentWord`, `getRandomWord()`
- Boolean variables use descriptive names: `workshopMode`, `containsWord()`
- Constants use UPPER_CASE: `const WORD = new Word()`

### File Organization
- Controllers end with `Controller.ts`
- Services end with `Service.ts`
- Models use singular nouns: `Word.ts`, `GameStatus.ts`
- Use descriptive directory names: `controllers/`, `services/`, `models/`

## Environment Configuration

### Environment Variables
- Use `dotenv` for environment configuration
- Check environment variables with strict equality: `process.env.WORKSHOP_MODE === 'true'`
- Provide fallback values: `parseInt(process.env.PORT || '8090', 10)`
- Log configuration values for debugging

### Path Management
```typescript
const basePath = workshopMode ? '/proxy/8090' : '';
// Utility function for path construction
getFullPath: (path: string): string => {
    return `${base}${path.startsWith('/') ? path : `/${path}`}`;
}
```

## Testing Standards

### Test Structure
- Use Jest with `@jest/globals` imports
- Organize tests with `describe` blocks for each class
- Use descriptive test names explaining the expected behavior
- Include placeholder tests for future implementation

### Test File Naming
- Test files end with `.test.ts`
- Match the source file name: `wordlist.test.ts` for `WordList.ts`

## Express.js Patterns

### Middleware Configuration
```typescript
this.app.use(express.static(path.join(__dirname, 'static')));
this.app.use(express.json());
this.app.use(express.urlencoded());
```

### Template Rendering
- Use EJS for server-side rendering
- Pass context variables consistently: `{ user, workshopMode, basePath }`
- Set global template variables via `app.locals`

### Route Handling
- Use typed Request/Response from Express
- Validate required parameters with early returns
- Handle both GET and POST routes in controllers
- Use query parameters for GET, body parameters for POST

## Code Organization Principles

### Separation of Concerns
- Controllers handle HTTP concerns only
- Services contain business logic
- Models define data structures and validation
- Repositories manage data persistence

### Dependency Injection
- Pass dependencies through constructors
- Use composition over inheritance
- Keep classes focused on single responsibilities

### Configuration Management
- Centralize configuration in dedicated modules
- Use environment variables for deployment-specific settings
- Provide sensible defaults for all configuration options