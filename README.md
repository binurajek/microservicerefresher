# Employee Microservice

A Spring Boot microservice for managing employee data with full CRUD operations.

## Prerequisites

- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+

## MySQL Setup

### Install MySQL

**macOS**: Download and install from [MySQL Official Website](https://dev.mysql.com/downloads/mysql/) or use Homebrew:
```bash
brew install mysql
brew services start mysql
```

**Linux**:
```bash
sudo apt-get update
sudo apt-get install mysql-server
sudo systemctl start mysql
```

**Windows**: Download installer from [MySQL Official Website](https://dev.mysql.com/downloads/installer/)

### Configure MySQL
```bash
# Login to MySQL with your credentials
mysql -u root -p

# Create database
CREATE DATABASE microservicedb;

# Exit MySQL
exit;
```

## Project Setup

1. Clone the repository
2. Update `src/main/resources/application.properties` with your MySQL credentials:
```properties
spring.datasource.username=root
spring.datasource.password=your_password
```

3. Build the project:
```bash
mvn clean install
```

4. Run the application:
```bash
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

## API Endpoints

### 1. Create Employee
```
POST http://localhost:8080/api/employees
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "department": "IT",
  "salary": 75000.00
}
```

### 2. Get Employee by ID
```
GET http://localhost:8080/api/employees/1
```

### 3. Get All Employees
```
GET http://localhost:8080/api/employees
```

### 4. Update Employee
```
PUT http://localhost:8080/api/employees/1
Content-Type: application/json

{
  "name": "John Doe Updated",
  "email": "john.updated@example.com",
  "department": "HR",
  "salary": 85000.00
}
```

### 5. Delete Employee
```
DELETE http://localhost:8080/api/employees/1
```

## Project Structure

```
src/main/java/org/binz/microservicerefresher/
├── controller/          # REST controllers
├── model/              # JPA entities
├── repository/         # JPA repositories
├── service/            # Service interfaces
└── service/impl/       # Service implementations
```

## Technologies Used

- Spring Boot 4.0.3
- Spring Data JPA
- MySQL
- Lombok
- Maven

## Testing with Postman

Import the requests above into Postman or use curl:

```bash
# Create employee
curl -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{"name":"Jane Smith","email":"jane@example.com","department":"Finance","salary":80000}'

# Get all employees
curl http://localhost:8080/api/employees
```
