# Agrata Authentication Service

A Node.js TypeScript-based authentication service providing secure user authentication and authorization capabilities.

## 🚀 Features

- User registration and login
- JWT-based authentication
- Password hashing and validation
- Role-based access control
- Token refresh mechanism
- Email verification
- Password reset functionality
- Rate limiting and security middleware

## 📋 Prerequisites

Before running this application, make sure you have the following installed:

- Node.js (v18 or higher)
- npm or yarn
- MongoDB or PostgreSQL (depending on your database choice)

## 🛠️ Installation

1. Clone the repository:
```bash
git clone https://github.com/Tweniee/agrata_node.git
cd agrata_node/authService
```

2. Install dependencies:
```bash
npm install
```

3. Create environment configuration:
```bash
cp .env.example .env
```

4. Configure your environment variables in `.env` file (see Configuration section)

5. Build the project:
```bash
npm run build
```

## ⚙️ Configuration

Create a `.env` file in the root directory with the following variables:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database Configuration
DATABASE_URL=mongodb://localhost:27017/agrata_auth
# OR for PostgreSQL
# DATABASE_URL=postgresql://username:password@localhost:5432/agrata_auth

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRES_IN=24h
JWT_REFRESH_SECRET=your-refresh-token-secret
JWT_REFRESH_EXPIRES_IN=7d

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your-email@gmail.com
SMTP_PASS=your-app-password

# Security
BCRYPT_ROUNDS=12
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100

# CORS
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:3001
```

## 🚀 Running the Application

### Development Mode
```bash
npm run dev
```

### Development with Auto-reload
```bash
npm run dev:watch
```

### Production Mode
```bash
npm run build
npm start
```

## 📚 API Documentation

For detailed API documentation, see [API_DOCUMENTATION.md](./docs/API_DOCUMENTATION.md)

### Quick API Overview

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | Register a new user |
| `/api/auth/login` | POST | User login |
| `/api/auth/logout` | POST | User logout |
| `/api/auth/refresh` | POST | Refresh access token |
| `/api/auth/verify-email` | POST | Verify email address |
| `/api/auth/forgot-password` | POST | Request password reset |
| `/api/auth/reset-password` | POST | Reset password |
| `/api/auth/profile` | GET | Get user profile |
| `/api/auth/profile` | PUT | Update user profile |

## 🧪 Testing

```bash
# Run tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch
```

## 📁 Project Structure

```
src/
├── controllers/        # Route controllers
├── middleware/         # Custom middleware
├── models/            # Database models
├── routes/            # API routes
├── services/          # Business logic
├── utils/             # Utility functions
├── types/             # TypeScript type definitions
├── config/            # Configuration files
└── index.ts           # Application entry point
```

## 🔒 Security Features

- Password hashing using bcrypt
- JWT token-based authentication
- Rate limiting to prevent brute force attacks
- Input validation and sanitization
- CORS protection
- Helmet.js security headers
- SQL injection prevention
- XSS protection

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support and questions, please open an issue on GitHub or contact the development team.

## 🔄 Changelog

See [CHANGELOG.md](./docs/CHANGELOG.md) for a list of changes and version history. 