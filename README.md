
# 🛡️ Spring Boot JWT Authentication Project

A complete implementation of **JWT-based Authentication** using **Spring Boot**, **Spring Security**, **JPA**, and **PostgreSQL**.
This project supports **user registration**, **login**, **token generation**, **token validation**, and **secured REST APIs** with a stateless authentication mechanism.

---

## 🚀 Features

* 🔐 **JWT Authentication** (Access Tokens)
* 👤 **User Registration & Login**
* 🗄️ **Spring Security with DaoAuthenticationProvider**
* 🧭 **Custom JWT Authentication Filter**
* 🏛️ **Role-Based Access (USER, ADMIN)**
* 🗃️ **PostgreSQL Database Integration**
* ⚙️ **Spring Data JPA ORM**
* 📦 **Clean Layered Architecture**
* 🚫 **CSRF Disabled** for stateless APIs

---

## 🧱 Project Architecture

```
src/main/java
 └── com.prashanth.security
     ├── auth
     ├── config
     ├── demo
     ├── user
     └── SecurityApplication.java
```

### **Main Components**

#### 🔹 `JwtService`

Handles token generation, extraction, and validation.

#### 🔹 `JwtAuthenticationFilter`

Intercepts incoming requests and validates JWT tokens.

#### 🔹 `ApplicationConfiguration`

Defines authentication provider, password encoder, and `UserDetailsService`.

#### 🔹 `SecurityConfiguration`

Defines security rules, protected endpoints, and filter chain.

#### 🔹 `AuthenticationService`

Handles register & login logic.

#### 🔹 `User` Entity

Implements `UserDetails`, represents application users.

---

## 🛠️ Technologies Used

* **Java 17+**
* **Spring Boot**
* **Spring Security**
* **Spring Data JPA**
* **PostgreSQL**
* **JWT (io.jsonwebtoken JJWT)**
* **Lombok**

---

## 🗂️ API Endpoints

### 👉 Public Endpoints

| Method | URL                         | Description               |
| ------ | --------------------------- | ------------------------- |
| POST   | `/api/v1/auth/register`     | Register a new user       |
| POST   | `/api/v1/auth/authenticate` | Login & receive JWT token |

### 👉 Secured Endpoints

| Method | URL                       | Description        |
| ------ | ------------------------- | ------------------ |
| GET    | `/api/v1/demo-controller` | Requires valid JWT |

---

## 🔑 How Authentication Works

1. User registers or logs in
2. Server generates a **JWT token**
3. Client sends token in request header:

   ```
   Authorization: Bearer <jwt-token>
   ```
4. `JwtAuthenticationFilter` validates token
5. If valid → User is authenticated & request is processed
6. If invalid → 403 Unauthorized

---

## 🗄️ Database Configuration (`application.yml`)

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/jwt_security
    username: postgres
    password: your_password
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
```

---

## ▶️ Running the Project

1. Clone the repo
2. Configure PostgreSQL database
3. Update DB credentials in `application.yml`
4. Run the project:

```
mvn spring-boot:run
```

---

## 📬 Sample JSON Requests

### Register

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@gmail.com",
  "password": "12345"
}
```

### Authenticate

```json
{
  "email": "john@gmail.com",
  "password": "12345"
}
```

