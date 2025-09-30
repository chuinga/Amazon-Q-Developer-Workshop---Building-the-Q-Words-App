# Technology Stack

## Programming Languages & Versions
- **Java**: 1.8 (Spring Boot 2.7.2)
- **Python**: 3.x (Flask 2.0.1)
- **C#**: .NET Core/5+
- **Node.js**: Latest LTS
- **TypeScript**: Latest stable

## Build Systems & Dependencies

### Java (Maven)
- Spring Boot Starter Web
- Spring Boot Starter Thymeleaf
- AWS Java SDK S3
- Apache Commons Lang3
- Lombok
- JUnit 4.13.2

### Python (pip)
- Flask 2.0.1
- Werkzeug 2.0.1
- python-dotenv 0.19.0
- Flask-WTF 0.15.1
- pytest 6.2.5

### Node.js/TypeScript (npm)
- Express.js
- EJS templating
- Jest testing framework
- Babel for transpilation

### C# (NuGet)
- ASP.NET Core MVC
- Entity Framework (if applicable)

## Development Commands

### Java
```bash
mvn clean install    # Build project
mvn spring-boot:run  # Run application
mvn test            # Run tests
```

### Python
```bash
pip install -r requirements.txt  # Install dependencies
python app.py                   # Run application
pytest                         # Run tests
```

### Node.js/TypeScript
```bash
npm install    # Install dependencies
npm start      # Run application
npm test       # Run tests
```

## AWS Integration
- AWS Java SDK for S3 integration
- Cloud deployment ready
- Environment-based configuration