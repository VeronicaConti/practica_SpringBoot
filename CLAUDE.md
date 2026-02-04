# CLAUDE.md - AI Assistant Guide

This document provides context and guidelines for AI assistants working with this repository.

## Project Overview

**Name:** Practica_SpringBoot
**Author:** Veronica Conti
**Description:** A practice project for learning Spring Boot, HTTP concepts, and n8n workflow automation integration.
**Language:** Spanish (documentation) / English (code)

## Current Project Status

This is a **newly initialized repository** in the early setup phase. The project structure has not yet been implemented.

### Existing Files
- `README.md` - Project description (Spanish)
- `.gitignore` - Standard Java/Maven ignore rules
- `CLAUDE.md` - This file

### Planned Stack
- **Framework:** Spring Boot
- **Build System:** Maven (based on .gitignore patterns)
- **Language:** Java
- **Integration:** n8n workflow automation

## Expected Project Structure

When fully implemented, this project should follow standard Spring Boot conventions:

```
practica_SpringBoot/
├── pom.xml                           # Maven build configuration
├── README.md                         # Project documentation
├── CLAUDE.md                         # AI assistant guidelines
├── .gitignore                        # Git ignore rules
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/practica/
│   │   │       ├── PracticaApplication.java    # Main entry point
│   │   │       ├── controller/                  # REST controllers
│   │   │       ├── service/                     # Business logic
│   │   │       ├── repository/                  # Data access layer
│   │   │       ├── model/                       # Entity/DTO classes
│   │   │       └── config/                      # Configuration classes
│   │   └── resources/
│   │       ├── application.properties           # App configuration
│   │       ├── application.yml                  # Alternative config format
│   │       ├── static/                          # Static web resources
│   │       └── templates/                       # View templates
│   └── test/
│       ├── java/                                # Test classes
│       └── resources/                           # Test resources
└── target/                                      # Build output (git-ignored)
```

## Development Guidelines

### Code Conventions

1. **Package Structure:** Use domain-driven package organization
   - `controller/` - REST API endpoints
   - `service/` - Business logic with `@Service`
   - `repository/` - Data access with `@Repository`
   - `model/` - Entities, DTOs, and domain objects
   - `config/` - Configuration classes with `@Configuration`

2. **Naming Conventions:**
   - Classes: PascalCase (e.g., `UserController`, `UserService`)
   - Methods: camelCase (e.g., `getUserById`, `createUser`)
   - Constants: UPPER_SNAKE_CASE
   - Packages: lowercase (e.g., `com.example.practica`)

3. **Annotations:**
   - Use `@RestController` for REST endpoints
   - Use `@Service` for business logic classes
   - Use `@Repository` for data access classes
   - Use `@Autowired` or constructor injection for DI

### Build & Run Commands

Once Maven is configured:

```bash
# Build the project
mvn clean install

# Run the application
mvn spring-boot:run

# Run tests
mvn test

# Package as JAR
mvn package

# Skip tests during build
mvn clean install -DskipTests
```

### Testing Conventions

1. Test classes should be in `src/test/java/` mirroring the main structure
2. Use `@SpringBootTest` for integration tests
3. Use `@WebMvcTest` for controller unit tests
4. Use `@DataJpaTest` for repository tests
5. Name test classes with `*Test.java` suffix

## Configuration Guidelines

### application.properties / application.yml

Common configurations to include:
```properties
# Server configuration
server.port=8080

# Database (if needed)
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver

# JPA settings
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Logging
logging.level.root=INFO
logging.level.com.example.practica=DEBUG
```

### Profile-Based Configuration

- `application-dev.properties` - Development settings
- `application-prod.properties` - Production settings
- `application-test.properties` - Test environment settings

## n8n Integration Notes

This project is intended to integrate with n8n workflow automation. Consider:

1. **Webhooks:** Create webhook endpoints for n8n triggers
2. **REST APIs:** Design clean REST APIs for n8n HTTP nodes
3. **Authentication:** Implement API key or token-based auth for n8n access
4. **Documentation:** Use OpenAPI/Swagger for API documentation

## Git Workflow

### Branch Naming
- `main` - Production-ready code
- `develop` - Development integration branch
- `feature/*` - New features
- `bugfix/*` - Bug fixes
- `claude/*` - AI assistant work branches

### Commit Messages
Use clear, descriptive commit messages:
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `refactor:` - Code refactoring
- `test:` - Test additions/modifications
- `chore:` - Build/config changes

## AI Assistant Instructions

When working on this project:

1. **Before Making Changes:**
   - Read relevant files before modifying
   - Understand the existing structure and conventions
   - Check for existing tests that might be affected

2. **Code Quality:**
   - Follow Spring Boot best practices
   - Add appropriate error handling
   - Include validation for user inputs
   - Avoid introducing security vulnerabilities (SQL injection, XSS, etc.)

3. **Testing:**
   - Write tests for new functionality
   - Run existing tests after changes: `mvn test`
   - Ensure tests pass before committing

4. **Documentation:**
   - Update README.md when adding significant features
   - Add Javadoc comments for public APIs
   - Keep this CLAUDE.md file updated as the project evolves

5. **Dependencies:**
   - Add dependencies to `pom.xml` with specific versions
   - Prefer well-maintained, widely-used libraries
   - Document any new dependencies added

## Quick Reference

| Task | Command |
|------|---------|
| Build | `mvn clean install` |
| Run | `mvn spring-boot:run` |
| Test | `mvn test` |
| Package | `mvn package` |
| Clean | `mvn clean` |

## Troubleshooting

### Common Issues

1. **Port already in use:** Change `server.port` in application.properties
2. **Dependency conflicts:** Check `mvn dependency:tree` for conflicts
3. **Test failures:** Run specific test with `mvn test -Dtest=ClassName`

---

*Last updated: 2026-02-04*
