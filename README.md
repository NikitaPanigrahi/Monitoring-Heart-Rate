# Monitoring-Heart-Rate
Heart Monitor API - Spring Boot
Project Overview :
This is a Spring Boot-based REST API for managing users, patients, and heart rate data. 

Setup & Installation :
1. Clone the Repository
2. Configure Database (Optional)
By default, the project uses H2 in-memory database. If using MySQL, update src/main/resources/application.properties:
spring.datasource.url=jdbc:mysql://localhost:3306/heart_monitor_db
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update
3. Run the Application
Using Maven:
mvn spring-boot:run

API Documentation
1. User API
Register a User
POST /api/users/register
{
  "email": "test@example.com",
  "password": "test123"
}
Response:
{
  "id": 1,
  "email": "test@example.com",
  "message": "User registered successfully"
}
User Login
POST /api/users/login
{
  "email": "test@example.com",
  "password": "test123"
}
Response:
{
  "message": "Login successful"
}
2. Patient API
Add a Patient
POST /api/patients
{
  "name": "John Doe",
  "age": 45,
  "gender": "M"
}
Response:
{
  "id": 1,
  "message": "Patient added successfully"
}
Get Patient Details
GET /api/patients/1
Response:
{
  "id": 1,
  "name": "John Doe",
  "age": 45,
  "gender": "M"
}
3. Heart Rate API
Record Heart Rate Data
POST /api/heartrate
{
  "patientId": 1,
  "heartRate": 75,
  "timestamp": "2025-02-18T10:30:00"
}
Response:
{
  "id": 1,
  "message": "Heart rate recorded successfully"
}
Retrieve Heart Rate Data for a Patient
GET /api/heartrate/1 Response:
[
  {
    "patientId": 1,
    "heartRate": 75,
    "timestamp": "2025-02-18T10:30:00"
  }
]

The API allows:
User Registration & Login (without authentication protocols, just email-password matching).
Managing Patients (adding and retrieving patient details).
Heart Rate Monitoring (recording and retrieving heart rate data).

Tech Stack :
Java 17/21 (or your selected version)
Spring Boot 3.3.8 (or your chosen version)
Spring Data JPA (for database operations)
H2 Database (in-memory database for testing)
JUnit & Mockito (for unit testing)
Lombok (for reducing boilerplate code)
Spring Boot DevTools (for live reloading)

Assumptions & Decisions :
No authentication mechanism (JWT or OAuth2 is not implemented; only email-password matching is used).
H2 in-memory database is used for testing, but MySQL can be configured.
Timestamps for heart rate use1 format (yyyy-MM-dd'T'HH:mm:ss).

Future Enhancements :
Implement JWT-based authentication for security.
Add Swagger API documentation.
Integrate with external health monitoring devices.
