# API Documentation

## Overview

The Agrata Authentication Service provides RESTful API endpoints for user authentication and authorization. All endpoints return JSON responses and use standard HTTP status codes.

## Base URL

```
http://localhost:3000/api/auth
```

## Authentication

Most endpoints require authentication via JWT tokens. Include the token in the Authorization header:

```
Authorization: Bearer <your-jwt-token>
```

## Response Format

All API responses follow this standard format:

```json
{
  "success": true,
  "message": "Operation successful",
  "data": {
    // Response data here
  },
  "error": null
}
```

Error responses:

```json
{
  "success": false,
  "message": "Error description",
  "data": null,
  "error": {
    "code": "ERROR_CODE",
    "details": "Detailed error information"
  }
}
```

## Status Codes

| Code | Description |
|------|-------------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 422 | Validation Error |
| 429 | Too Many Requests |
| 500 | Internal Server Error |

## Endpoints

### 1. User Registration

Register a new user account.

**Endpoint:** `POST /api/auth/register`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "securePassword123",
  "firstName": "John",
  "lastName": "Doe",
  "phoneNumber": "+1234567890"
}
```

**Validation Rules:**
- `email`: Valid email format, unique
- `password`: Minimum 8 characters, must contain uppercase, lowercase, number, and special character
- `firstName`: Required, 2-50 characters
- `lastName`: Required, 2-50 characters
- `phoneNumber`: Optional, valid phone format

**Response (201):**
```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "user": {
      "id": "user_id",
      "email": "user@example.com",
      "firstName": "John",
      "lastName": "Doe",
      "phoneNumber": "+1234567890",
      "isEmailVerified": false,
      "role": "user",
      "createdAt": "2024-01-01T00:00:00.000Z"
    },
    "tokens": {
      "accessToken": "jwt_access_token",
      "refreshToken": "jwt_refresh_token",
      "expiresIn": 86400
    }
  }
}
```

**Error Responses:**
- `400`: Invalid input data
- `409`: Email already exists

---

### 2. User Login

Authenticate user and receive access tokens.

**Endpoint:** `POST /api/auth/login`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "user": {
      "id": "user_id",
      "email": "user@example.com",
      "firstName": "John",
      "lastName": "Doe",
      "role": "user",
      "lastLoginAt": "2024-01-01T00:00:00.000Z"
    },
    "tokens": {
      "accessToken": "jwt_access_token",
      "refreshToken": "jwt_refresh_token",
      "expiresIn": 86400
    }
  }
}
```

**Error Responses:**
- `400`: Missing email or password
- `401`: Invalid credentials
- `403`: Account locked or disabled

---

### 3. User Logout

Invalidate user session and tokens.

**Endpoint:** `POST /api/auth/logout`

**Headers:** `Authorization: Bearer <access_token>`

**Request Body:**
```json
{
  "refreshToken": "jwt_refresh_token"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Logout successful",
  "data": null
}
```

---

### 4. Refresh Token

Get new access token using refresh token.

**Endpoint:** `POST /api/auth/refresh`

**Request Body:**
```json
{
  "refreshToken": "jwt_refresh_token"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Token refreshed successfully",
  "data": {
    "accessToken": "new_jwt_access_token",
    "expiresIn": 86400
  }
}
```

**Error Responses:**
- `401`: Invalid or expired refresh token

---

### 5. Email Verification

Verify user email address.

**Endpoint:** `POST /api/auth/verify-email`

**Request Body:**
```json
{
  "token": "email_verification_token"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Email verified successfully",
  "data": {
    "user": {
      "id": "user_id",
      "email": "user@example.com",
      "isEmailVerified": true
    }
  }
}
```

---

### 6. Resend Email Verification

Request new email verification token.

**Endpoint:** `POST /api/auth/resend-verification`

**Headers:** `Authorization: Bearer <access_token>`

**Response (200):**
```json
{
  "success": true,
  "message": "Verification email sent successfully",
  "data": null
}
```

---

### 7. Forgot Password

Request password reset token.

**Endpoint:** `POST /api/auth/forgot-password`

**Request Body:**
```json
{
  "email": "user@example.com"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Password reset email sent",
  "data": null
}
```

---

### 8. Reset Password

Reset password using reset token.

**Endpoint:** `POST /api/auth/reset-password`

**Request Body:**
```json
{
  "token": "password_reset_token",
  "newPassword": "newSecurePassword123"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Password reset successfully",
  "data": null
}
```

---

### 9. Get User Profile

Get current user profile information.

**Endpoint:** `GET /api/auth/profile`

**Headers:** `Authorization: Bearer <access_token>`

**Response (200):**
```json
{
  "success": true,
  "message": "Profile retrieved successfully",
  "data": {
    "user": {
      "id": "user_id",
      "email": "user@example.com",
      "firstName": "John",
      "lastName": "Doe",
      "phoneNumber": "+1234567890",
      "isEmailVerified": true,
      "role": "user",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  }
}
```

---

### 10. Update User Profile

Update current user profile information.

**Endpoint:** `PUT /api/auth/profile`

**Headers:** `Authorization: Bearer <access_token>`

**Request Body:**
```json
{
  "firstName": "John",
  "lastName": "Doe",
  "phoneNumber": "+1234567890"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Profile updated successfully",
  "data": {
    "user": {
      "id": "user_id",
      "email": "user@example.com",
      "firstName": "John",
      "lastName": "Doe",
      "phoneNumber": "+1234567890",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  }
}
```

---

### 11. Change Password

Change user password (requires current password).

**Endpoint:** `PUT /api/auth/change-password`

**Headers:** `Authorization: Bearer <access_token>`

**Request Body:**
```json
{
  "currentPassword": "currentPassword123",
  "newPassword": "newSecurePassword123"
}
```

**Response (200):**
```json
{
  "success": true,
  "message": "Password changed successfully",
  "data": null
}
```

---

## Rate Limiting

API endpoints are rate-limited to prevent abuse:

- **Registration/Login**: 5 requests per 15 minutes per IP
- **Password Reset**: 3 requests per hour per IP
- **Email Verification**: 3 requests per hour per user
- **General API**: 100 requests per 15 minutes per IP

Rate limit headers are included in responses:

```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 99
X-RateLimit-Reset: 1640995200
```

## Error Codes

| Code | Description |
|------|-------------|
| `VALIDATION_ERROR` | Input validation failed |
| `INVALID_CREDENTIALS` | Wrong email or password |
| `TOKEN_EXPIRED` | JWT token has expired |
| `TOKEN_INVALID` | JWT token is malformed or invalid |
| `EMAIL_NOT_VERIFIED` | Email verification required |
| `ACCOUNT_LOCKED` | Account is temporarily locked |
| `RATE_LIMIT_EXCEEDED` | Too many requests |
| `USER_NOT_FOUND` | User does not exist |
| `EMAIL_ALREADY_EXISTS` | Email is already registered |
| `INTERNAL_ERROR` | Server error occurred |

## SDK Examples

### JavaScript/Node.js

```javascript
const axios = require('axios');

const authAPI = axios.create({
  baseURL: 'http://localhost:3000/api/auth',
  headers: {
    'Content-Type': 'application/json'
  }
});

// Login
const login = async (email, password) => {
  try {
    const response = await authAPI.post('/login', { email, password });
    const { accessToken } = response.data.data.tokens;
    
    // Set token for future requests
    authAPI.defaults.headers.common['Authorization'] = `Bearer ${accessToken}`;
    
    return response.data;
  } catch (error) {
    console.error('Login failed:', error.response.data);
    throw error;
  }
};

// Get profile
const getProfile = async () => {
  try {
    const response = await authAPI.get('/profile');
    return response.data;
  } catch (error) {
    console.error('Failed to get profile:', error.response.data);
    throw error;
  }
};
```

### cURL Examples

```bash
# Register
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "securePassword123",
    "firstName": "John",
    "lastName": "Doe"
  }'

# Login
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "securePassword123"
  }'

# Get profile (with token)
curl -X GET http://localhost:3000/api/auth/profile \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

## Postman Collection

A Postman collection with all endpoints is available at: [Agrata Auth API.postman_collection.json](./Agrata_Auth_API.postman_collection.json) 