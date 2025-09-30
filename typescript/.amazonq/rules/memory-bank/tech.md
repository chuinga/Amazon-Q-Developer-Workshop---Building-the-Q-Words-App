# Technology Stack

## Programming Languages
- **TypeScript 5.7.2** - Primary development language with strict type checking
- **JavaScript** - Runtime execution environment
- **HTML/CSS** - Frontend markup and styling via EJS templates

## Core Framework & Runtime
- **Node.js** - Server-side JavaScript runtime (v14+ required)
- **Express.js 4.18.3** - Web application framework for HTTP server
- **EJS 3.1.10** - Embedded JavaScript templating engine
- **express-ejs-layouts 2.5.1** - Layout support for EJS templates

## Development Tools
- **ts-node 10.9.2** - TypeScript execution environment for development
- **ts-node-dev 2.0.0** - Development server with auto-restart
- **ESLint 9.3.0** - Code linting and style enforcement
- **dotenv 16.4.7** - Environment variable management

## Testing Framework
- **Jest 29.7.0** - JavaScript testing framework
- **ts-jest 29.2.3** - TypeScript preprocessor for Jest
- **@jest/globals 29.7.0** - Jest global functions and types
- **babel-jest 29.7.0** - Babel integration for Jest

## Build System
- **TypeScript Compiler** - Transpiles TypeScript to JavaScript
- **Babel** - JavaScript transpilation and polyfills
  - @babel/core 7.24.9
  - @babel/preset-env 7.24.8
  - @babel/preset-typescript 7.24.7

## Cloud Integration
- **AWS SDK 2.1580.0** - Amazon Web Services integration capabilities

## Development Commands

### Build & Compilation
```bash
npm run build          # Compile TypeScript to JavaScript
```

### Development Server
```bash
npm start              # Start server in workshop mode
npm run start:standalone # Start server in standalone mode
```

### Testing
```bash
npm test               # Run Jest test suite
```

### Package Management
```bash
npm install            # Install all dependencies
```

## Configuration Files
- **`tsconfig.json`** - TypeScript compiler options and project settings
- **`jest.config.js`** - Jest testing framework configuration
- **`package.json`** - NPM dependencies and scripts
- **`.env`** - Environment-specific variables
- **`run-local.sh`** - Local development startup script