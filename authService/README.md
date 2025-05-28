# Agrata Node.js TypeScript Application

A Node.js application built with TypeScript, featuring proper type definitions and modern development tools.

## Features

- ✅ TypeScript with strict type checking
- ✅ Node.js types (@types/node)
- ✅ Development and production builds
- ✅ Hot reload during development
- ✅ Source maps for debugging
- ✅ Clean build process

## Prerequisites

- Node.js (>= 18.0.0)
- npm (>= 8.0.0)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Tweniee/agrata_node.git
cd agrata_node
```

2. Install dependencies:
```bash
npm install
```

## Available Scripts

### Development
```bash
# Run in development mode with hot reload
npm run dev

# Run in development mode with file watching
npm run dev:watch
```

### Production
```bash
# Build the application
npm run build

# Start the built application
npm start
```

### Utilities
```bash
# Clean the dist folder
npm run clean

# Build after cleaning
npm run prebuild
```

## Project Structure

```
agrata_node/
├── src/                 # TypeScript source files
│   └── index.ts        # Main application entry point
├── dist/               # Compiled JavaScript files (generated)
├── package.json        # Project dependencies and scripts
├── tsconfig.json       # TypeScript configuration
├── .gitignore         # Git ignore rules
└── README.md          # This file
```

## TypeScript Configuration

The project uses a modern TypeScript configuration with:

- **Target**: ES2020
- **Module**: CommonJS
- **Strict mode**: Enabled
- **Source maps**: Enabled
- **Declaration files**: Generated
- **Unused variable detection**: Enabled

## Node.js Types Usage

The application demonstrates various Node.js type usages:

- File system operations with proper typing
- Process events and signals
- Environment variables with type safety
- Memory usage monitoring
- Platform and architecture detection

## Environment Variables

- `PORT`: Server port (default: 3000)
- `NODE_ENV`: Environment mode (development/production/test)

## Development Workflow

1. **Start development server**:
   ```bash
   npm run dev
   ```

2. **Make changes** to TypeScript files in the `src/` directory

3. **Build for production**:
   ```bash
   npm run build
   ```

4. **Run production build**:
   ```bash
   npm start
   ```

## TypeScript Benefits

- **Type Safety**: Catch errors at compile time
- **IntelliSense**: Better IDE support and autocomplete
- **Refactoring**: Safe code refactoring with confidence
- **Documentation**: Types serve as inline documentation
- **Modern JavaScript**: Use latest JavaScript features

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Ensure TypeScript compilation passes
5. Submit a pull request

## License

ISC License