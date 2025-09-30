i# Development Guidelines

## Code Quality Standards

### Naming Conventions
- **Java**: PascalCase for classes (`WordList`, `GameController`), camelCase for methods/variables (`getRandomWord`, `currentWord`)
- **Python**: PascalCase for classes (`WordList`, `GameController`), snake_case for methods/variables (`get_random_word`, `current_word`)
- **JavaScript**: camelCase for functions/variables (`addHoverEffect`, `shakeElement`)
- Package names use lowercase with dots (Java: `com.sample.qwords.repository`)

### Documentation Standards
- **Java**: Javadoc comments for public methods with `@param` and `@return` tags
- **Python**: Docstrings with parameter descriptions and return types
- **Inline comments**: Explain complex logic, especially in game mechanics
- TODO comments for incomplete features: `// TODO: Add javadocs comments`

### Error Handling Patterns
- **Java**: Try-catch blocks with proper exception propagation, logging errors before throwing
- **Python**: Custom exception classes inheriting from base `GameError` class
- **Validation**: Input validation with meaningful error messages
- **Logging**: Use appropriate logging levels (`log.info`, `System.out.println`)

## Structural Conventions

### MVC Architecture
- **Controllers**: Handle HTTP requests, delegate to services, manage view models
- **Models**: Simple data classes with business logic methods (`Word.getInfo()`)
- **Services**: Business logic layer (`WordSelectionService`)
- **Repositories**: Data access with singleton pattern implementation

### Singleton Pattern Implementation
```java
// Java singleton with lazy initialization
private static WordList instance;
public static WordList getInstance() { ... }

// Python singleton with class variable
_instance = None
@classmethod
def get_instance(cls): ...
```

### Session Management
- **Java**: `@SessionAttributes` annotation for Spring MVC
- **Python**: Flask session handling in controllers
- Track game state: attempts, current word, user information

## Common Implementation Patterns

### File I/O Operations
- **Resource Loading**: Try multiple file paths with fallback to defaults
- **Error Handling**: Graceful degradation when files not found
- **Encoding**: Explicit UTF-8 encoding for text files
- **Resource Cleanup**: Use try-with-resources (Java) or context managers (Python)

### Game Logic Patterns
```java
// Word comparison logic
if (guess.equalsIgnoreCase(selectedWord)) {
    // Success handling
}

// Attempt tracking
attempts = addAttempt(attempts);
if (attempts >= maxAttempts) {
    // Game over logic
}
```

### Frontend Interaction
- **Form Validation**: Client-side validation with visual feedback
- **Animation**: CSS transitions for user interactions (`transform: scale(1.1)`)
- **Event Handling**: DOM ready listeners, form submission prevention
- **Input Sanitization**: Regex patterns for allowed characters

### Dependency Injection
- **Java**: Constructor injection in Spring controllers
- **Python**: Service instantiation in controllers
- **Configuration**: External configuration files (application.properties, config.py)

## Testing Standards

### Test Structure
- **Naming**: Test methods describe behavior (`testGetCredentialsWithValidKeys`)
- **Coverage**: Test edge cases (null inputs, empty strings, boundary conditions)
- **Assertions**: Descriptive assertion messages
- **Setup**: Proper test data initialization and cleanup

### Common Test Patterns
```java
@Test
public void testMethodName() {
    // Arrange
    String input = "testValue";
    
    // Act
    Result result = methodUnderTest(input);
    
    // Assert
    assertNotNull("Result should not be null", result);
    assertEquals("Expected value", expected, result.getValue());
}
```

## Security Considerations
- **Input Validation**: Sanitize user inputs in both frontend and backend
- **Credential Handling**: Use placeholder values in examples (`<access_key>`)
- **Error Messages**: Avoid exposing sensitive information in error responses
- **Resource Access**: Validate file paths and resource access