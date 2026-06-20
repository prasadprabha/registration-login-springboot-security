# Registration & Login - Spring Boot Security

A user registration and login module built with Spring Boot 3, Spring Security, Spring MVC, Thymeleaf, and MySQL.

---

## Tech Stack & Versions

- Java 17
- Spring Boot 3.0.0
- Spring Security 6 (included via Spring Boot 3)
- Spring Data JPA (Hibernate)
- Thymeleaf
- MySQL (production) / H2 In-Memory DB (development)
- Lombok
- Maven

---

## Features

- User registration with form validation
- Secure login and logout
- Password encoding using BCrypt
- Role-based access control (USER role)
- Protected routes — only authenticated users can access the users list page
- Thymeleaf-based UI (register, login, home, users pages)
- Separate Spring Security configurations for dev and prod profiles
- H2 console enabled in dev profile for easy database inspection

---

## Project Structure

```
src/main/java/com/example/registrationlogindemo/
├── config/         # Spring Security config (dev & prod)
├── controller/     # AuthController (register, login, users)
├── dto/            # UserDto for registration form
├── entity/         # User and Role entities
├── repository/     # UserRepository and RoleRepository
├── security/       # CustomUserDetailsService
└── service/        # UserService interface and implementation
```

---

## Prerequisites

- Java 17+
- Maven 3.8+
- MySQL 8+ (for production profile only)

---

## Running the Application

### Development (H2 in-memory database)

The default profile is `dev`. No database setup required.

```bash
./mvnw spring-boot:run
```

- App runs at: `http://localhost:8080`
- H2 Console: `http://localhost:8080/h2-console`
  - JDBC URL: `jdbc:h2:mem:testdb`
  - Username: `sa`
  - Password: *(leave blank)*

### Production (MySQL)

1. Create a MySQL database:
   ```sql
   CREATE DATABASE login_system;
   ```

2. Update credentials in `application-prod.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/login_system
   spring.datasource.username=<your_username>
   spring.datasource.password=<your_password>
   ```

3. Run with the `prod` profile:
   ```bash
   ./mvnw spring-boot:run -Dspring-boot.run.profiles=prod
   ```

---

## Available Pages

| URL | Description | Access |
|---|---|---|
| `/` | Home page | Public |
| `/register` | User registration form | Public |
| `/login` | Login page | Public |
| `/users` | List of registered users | Authenticated only |

---

## Build (JAR)

```bash
./mvnw clean package
java -jar target/registration-login-demo-0.0.2-SNAPSHOT.jar
```
