# Contributing to Agrata Authentication Service

Thank you for your interest in contributing to the Agrata Authentication Service! This document provides guidelines and information for contributors.

## 🤝 Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct:

- Be respectful and inclusive
- Use welcoming and inclusive language
- Be collaborative and constructive
- Focus on what is best for the community
- Show empathy towards other community members

## 🚀 Getting Started

### Prerequisites

- Node.js 18 or higher
- npm or yarn
- Git
- MongoDB or PostgreSQL
- Basic knowledge of TypeScript and Express.js

### Development Setup

1. **Fork the repository**
   ```bash
   git clone https://github.com/your-username/agrata_node.git
   cd agrata_node/authService
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp env.example .env
   # Edit .env with your configuration
   ```

4. **Start development server**
   ```bash
   npm run dev:watch
   ```

## 📝 How to Contribute

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates.

**Bug Report Template:**
```markdown
**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem.

**Environment:**
- OS: [e.g. Windows, macOS, Linux]
- Node.js version: [e.g. 18.17.0]
- npm version: [e.g. 9.6.7]

**Additional context**
Add any other context about the problem here.
```

### Suggesting Features

Feature requests are welcome! Please provide:

- Clear description of the feature
- Use case and benefits
- Possible implementation approach
- Any relevant examples or mockups

**Feature Request Template:**
```markdown
**Is your feature request related to a problem?**
A clear and concise description of what the problem is.

**Describe the solution you'd like**
A clear and concise description of what you want to happen.

**Describe alternatives you've considered**
A clear and concise description of any alternative solutions.

**Additional context**
Add any other context or screenshots about the feature request.
```

### Pull Requests

1. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

2. **Make your changes**
   - Follow the coding standards
   - Add tests for new functionality
   - Update documentation if needed

3. **Test your changes**
   ```bash
   npm test
   npm run lint
   npm run build
   ```

4. **Commit your changes**
   ```bash
   git commit -m "Add amazing feature"
   ```

5. **Push to your fork**
   ```bash
   git push origin feature/amazing-feature
   ```

6. **Create a Pull Request**
   - Use a clear and descriptive title
   - Fill out the PR template
   - Link any related issues

## 📋 Development Guidelines

### Code Style

We use ESLint and Prettier for code formatting. Please ensure your code follows these standards:

```bash
# Check linting
npm run lint

# Fix linting issues
npm run lint:fix

# Format code
npm run format
```

### Coding Standards

#### TypeScript Guidelines
- Use TypeScript for all new code
- Define proper interfaces and types
- Avoid `any` type unless absolutely necessary
- Use meaningful variable and function names

#### File Structure
```
src/
├── controllers/     # Route handlers
├── middleware/      # Custom middleware
├── models/         # Database models
├── routes/         # API routes
├── services/       # Business logic
├── utils/          # Utility functions
├── types/          # TypeScript definitions
├── config/         # Configuration files
└── tests/          # Test files
```

#### Naming Conventions
- **Files**: kebab-case (e.g., `user-controller.ts`)
- **Classes**: PascalCase (e.g., `UserService`)
- **Functions/Variables**: camelCase (e.g., `getUserById`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_LOGIN_ATTEMPTS`)

### Testing

#### Test Structure
- Unit tests for individual functions
- Integration tests for API endpoints
- End-to-end tests for complete workflows

#### Writing Tests
```typescript
// Example test structure
describe('UserController', () => {
  describe('register', () => {
    it('should create a new user with valid data', async () => {
      // Test implementation
    });

    it('should return error for invalid email', async () => {
      // Test implementation
    });
  });
});
```

#### Test Commands
```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- user.test.ts
```

### Documentation

#### Code Documentation
- Use JSDoc comments for functions and classes
- Document complex algorithms and business logic
- Keep comments up-to-date with code changes

```typescript
/**
 * Authenticates a user with email and password
 * @param email - User's email address
 * @param password - User's password
 * @returns Promise resolving to authentication result
 * @throws {AuthenticationError} When credentials are invalid
 */
async function authenticateUser(email: string, password: string): Promise<AuthResult> {
  // Implementation
}
```

#### API Documentation
- Update API documentation for new endpoints
- Include request/response examples
- Document error responses

### Security Guidelines

#### Security Checklist
- [ ] Validate all user inputs
- [ ] Use parameterized queries
- [ ] Implement proper authentication
- [ ] Add rate limiting where appropriate
- [ ] Log security events
- [ ] Handle errors securely (no sensitive data in error messages)

#### Security Review Process
All security-related changes require:
- Security team review
- Penetration testing (for major changes)
- Documentation updates

## 🔄 Development Workflow

### Branch Strategy

- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: Feature development branches
- `hotfix/*`: Critical bug fixes
- `release/*`: Release preparation branches

### Commit Messages

Follow conventional commit format:

```
type(scope): description

[optional body]

[optional footer]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code refactoring
- `test`: Test changes
- `chore`: Build/tooling changes

**Examples:**
```
feat(auth): add password reset functionality
fix(validation): handle edge case in email validation
docs(api): update authentication endpoint documentation
```

### Release Process

1. Create release branch from `develop`
2. Update version numbers
3. Update CHANGELOG.md
4. Test thoroughly
5. Merge to `main` and tag release
6. Deploy to production
7. Merge back to `develop`

## 🧪 Testing Guidelines

### Test Categories

#### Unit Tests
- Test individual functions in isolation
- Mock external dependencies
- Fast execution
- High code coverage

#### Integration Tests
- Test API endpoints
- Test database interactions
- Test service integrations

#### End-to-End Tests
- Test complete user workflows
- Test critical business processes
- Run against staging environment

### Test Data Management

- Use factories for test data creation
- Clean up test data after each test
- Use separate test database
- Avoid hardcoded test data

### Performance Testing

- Load testing for critical endpoints
- Memory leak detection
- Database query optimization
- Response time monitoring

## 📊 Code Review Process

### Review Checklist

#### Functionality
- [ ] Code works as intended
- [ ] Edge cases are handled
- [ ] Error handling is appropriate
- [ ] Performance considerations

#### Code Quality
- [ ] Code is readable and maintainable
- [ ] Follows project conventions
- [ ] No code duplication
- [ ] Proper abstractions

#### Security
- [ ] Input validation
- [ ] Authentication/authorization
- [ ] No sensitive data exposure
- [ ] SQL injection prevention

#### Testing
- [ ] Adequate test coverage
- [ ] Tests are meaningful
- [ ] Tests pass consistently
- [ ] Performance tests if needed

### Review Guidelines

#### For Reviewers
- Be constructive and respectful
- Explain the reasoning behind suggestions
- Focus on code, not the person
- Approve when ready, request changes when needed

#### For Authors
- Respond to all feedback
- Ask questions if unclear
- Make requested changes promptly
- Thank reviewers for their time

## 🚀 Deployment

### Staging Deployment
- Automatic deployment from `develop` branch
- Run full test suite
- Manual testing by QA team

### Production Deployment
- Manual deployment from `main` branch
- Requires approval from team lead
- Rollback plan must be ready
- Monitor post-deployment

## 📞 Getting Help

### Communication Channels
- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General questions and discussions
- **Email**: security@agrata.com (for security issues)

### Documentation
- [API Documentation](./API_DOCUMENTATION.md)
- [Security Guidelines](./SECURITY.md)
- [Deployment Guide](./DEPLOYMENT.md)

## 🎉 Recognition

Contributors will be recognized in:
- CONTRIBUTORS.md file
- Release notes
- Project documentation

Thank you for contributing to the Agrata Authentication Service! 🙏 