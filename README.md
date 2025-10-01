# NestJS Starter Kit

A comprehensive NestJS backend starter kit with PostgreSQL, Prisma ORM, JWT authentication, role-based access control, and modern development practices.

## 🚀 Features

- **🔐 Authentication & Authorization**
  - JWT-based authentication with refresh tokens
  - Role-based access control (RBAC)
  - Permission-based authorization
  - Cookie-based token management

- **📊 Database & ORM**
  - PostgreSQL database
  - Prisma ORM with type-safe database access
  - Database migrations
  - Seed data support

- **🏗️ Architecture**
  - Modular NestJS architecture
  - Clean separation of concerns
  - DTO validation with class-validator
  - Global exception handling
  - Request/Response interceptors

- **📝 API Documentation**
  - Swagger/OpenAPI integration
  - Auto-generated API documentation
  - Environment-based Swagger configuration

- **🔧 Development Tools**
  - ESLint & Prettier for code formatting
  - Jest for testing
  - Winston for logging
  - Docker support for development and production

## 📋 Prerequisites

- Node.js (v18 or higher)
- PostgreSQL
- Docker (optional)

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd nest-starter-kit
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env` file in the root directory:
   ```env
   # Database
   DATABASE_URL="postgresql://username:password@localhost:5432/nest_starter_kit"

   # JWT
   JWT_SECRET="your-jwt-secret-key"
   JWT_REFRESH_SECRET="your-refresh-secret-key"

   # Application
   NODE_ENV="development"
   PORT=3002

   # CORS (optional)
   DEVELOPMENT_URL="http://localhost:3000"
   STAGING_URL="https://staging.example.com"
   PRODUCTION_URL="https://example.com"
   ```

4. **Database Setup**
   ```bash
   # Generate Prisma client
   npx prisma generate

   # Run database migrations
   npx prisma migrate dev

   # Seed the database
   npm run seed
   ```

## 🚀 Running the Application

### Development Mode
```bash
npm run start:dev
```

### Production Mode
```bash
npm run build
npm run start:prod
```

### Docker Development
```bash
# Start with Docker Compose
docker-compose -f docker/development/docker-compose.yaml up
```

## 📚 API Documentation

Once the application is running, you can access:

- **Swagger UI**: `http://localhost:3002/swagger`
- **API JSON**: `http://localhost:3002/swagger.json`

## 🏗️ Project Structure

```
src/
├── common/                 # Shared utilities and decorators
│   ├── decorators/         # Custom decorators (@Public, @Permission)
│   ├── guards/            # Authentication and authorization guards
│   ├── interceptors/      # Request/Response interceptors
│   ├── middlewares/       # HTTP logging middleware
│   ├── strategies/        # Passport strategies
│   └── utils/             # Helper functions
├── configurations/         # Application configurations
├── modules/               # Feature modules
│   ├── auth/              # Authentication module
│   ├── user/              # User management
│   ├── role/              # Role management
│   ├── permission/        # Permission management
│   ├── department/        # Department management
│   ├── collection-count/  # Collection statistics
│   └── prisma/            # Database service
└── main.ts                # Application entry point
```

## 🔐 Authentication & Authorization

### Authentication Flow
1. **Login**: `POST /auth/login`
   - Returns access token and refresh token
   - Tokens are stored in HTTP-only cookies

2. **Refresh Token**: `POST /user/refresh-token`
   - Generates new access token using refresh token

3. **Logout**: `POST /auth/logout`
   - Clears authentication cookies

### Authorization System
- **Roles**: Define user roles (e.g., Admin, User, Manager)
- **Permissions**: Granular permissions (e.g., `users:create`, `roles:edit`)
- **Guards**: Automatic permission checking on protected routes

## 📊 Database Schema

The application uses the following main entities:

- **User**: User accounts with role and department associations
- **Role**: User roles with permission mappings
- **Permission**: Granular permissions for access control
- **Department**: Organizational departments
- **RolePermission**: Many-to-many relationship between roles and permissions

```
## 📝 Logging

The application uses Winston for structured logging:

- **HTTP Logs**: Request/response logging
- **Error Logs**: Application errors
- **Combined Logs**: All application logs
- **Daily Rotation**: Automatic log file rotation

Logs are stored in the `logs/` directory.

## 🐳 Docker Support

### Development
```bash
docker-compose -f docker/development/docker-compose.yaml up
```

### Production
```bash
docker-compose -f docker/production/docker-compose.yaml up
```

## 🔧 Available Scripts

- `npm run start` - Start the application
- `npm run start:dev` - Start in development mode with hot reload
- `npm run start:debug` - Start in debug mode
- `npm run build` - Build the application
- `npm run test` - Run unit tests
- `npm run test:e2e` - Run e2e tests
- `npm run lint` - Run ESLint
- `npm run format` - Format code with Prettier
- `npm run seed` - Seed the database

## 🌍 Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_URL` | PostgreSQL connection string | Required |
| `JWT_SECRET` | JWT signing secret | Required |
| `JWT_REFRESH_SECRET` | Refresh token secret | Required |
| `NODE_ENV` | Environment mode | `development` |
| `PORT` | Application port | `3002` |

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Htet Thu** - *Initial work*

---

**Happy Coding! 🚀**
