# **📚 Quiz App Backend**

This repository contains the backend for a **Quiz App**, developed using **Spring Boot**. The app provides functionalities to manage quizzes, retrieve questions by category, and calculate quiz results through a RESTful API.

---

## **🚀 Features**

### Quiz Management
- **Create quizzes** by specifying a category, number of questions, and title.
- **Retrieve questions** for a quiz in a structured format.
- **Submit quiz responses** and calculate the result.

### Question Management
- **Add new questions** with attributes like category, difficulty level, and correct answers.
- **Retrieve all questions** or filter by category.

---

## 🛠️ Technologies Used
- **Java 17 or higher** with Spring Boot
- **Spring Web** for REST API development
- **Spring Data JPA** for ORM
- **PostgreSQL** for data storage
- **Maven** for dependency management

---

## **🧩 Quiz and Question Structure**

### 📋 Quiz Format

A quiz is a collection of questions, each with multiple options but without revealing the correct answer.

```json
[
  {
    "id": 8,
    "questionTitle": "Which keyword is used to define a variable that won’t be reassigned?",
    "option1": "static",
    "option2": "final",
    "option3": "constant",
    "option4": "immutable"
  },
  {
    "id": 19,
    "questionTitle": "What is a linked list?",
    "option1": "A type of array",
    "option2": "A linear data structure",
    "option3": "A collection of objects",
    "option4": "A group of classes"
  }
]
```

### 📂 Question Format
A question includes its details, multiple-choice options, the correct answer, difficulty level, and category.

Each question follows a structured format:  
```json
{
  "id": 1,
  "questionTitle": "What is a class in Java?",
  "option1": "A function",
  "option2": "An object",
  "option3": "A data structure",
  "option4": "A loop",
  "rightAnswer": "An object",
  "difficultyLevel": "Easy",
  "category": "java"
}
```

---

## **🌐 API Endpoints**

###  Quiz Controller
| Method | Endpoint               | Description                                       |
|--------|------------------------|---------------------------------------------------|
| `POST`   | `/quiz/create`            | Create a quiz with category, number of questions, and title. |
| `GET`    | `/quiz/get/{id}`          | Get questions for a specific quiz by its ID.      |
| `POST`   | `/quiz/submit/{id}`       | Submit quiz responses and calculate the result.   |


### Question Controller

| Method | Endpoint                 | Description                                      |
|--------|--------------------------|--------------------------------------------------|
| `GET`    | `/question/allQuestions`    | Retrieve all available questions.                |
| `GET`    | `/question/category/{category}` | Retrieve questions by category.               |
| `POST`   | `/question/add`            | Add a new question to the database (JSON format). |
---
## 🛠️**Setup Instructions**
### Prerequisites
- Java 17 or higher
- Maven
- PostgreSQL

### Steps to Run
1. Clone the repository:
```bash
git clone <repository-url>
cd quiz_app
```
2. Configure your database in `'src/main/resources/application.properties'` with your PostgreSQL credentials:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/quiz_db
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
```
3. Build and run the application:
```bash
mvn clean install
mvn spring-boot:run
```
4. The API will be available at http://localhost:8080.

----

## **🗂️Folder Structure**
```csharp
C:\Users\anees\Desktop\Projects\Java Spring Boot\quiz_app
├── src\main\java\com\aneesh\quiz_app\
│   ├── controller\   # API Controllers (QuizController, QuestionController)
│   ├── dao\          # Data Access Layer
│   ├── model\        # Entity Classes (Quiz, Question, Response)
│   ├── service\      # Business Logic
├── src\main\resources\
│   ├── application.properties # Configuration
│   └── static\       # Optional static assets
```
---

## **🚀Example Usage**
### Create a Quiz:
```bash
POST /quiz/create?category=java&numQ=5&title=JavaBasics
```

### Get Quiz Questions:
```bash
GET /quiz/get/1
```

### Submit Quiz Responses:
Submit user responses as JSON:
```json

POST /quiz/submit/1
[
  { "questionId": 8, "selectedOption": "final" },
  { "questionId": 19, "selectedOption": "A linear data structure" }
]
```
---

## **📄License**
This project is licensed under the MIT License. See the LICENSE file for more details.

---

## **💡Acknowledgments**
Thanks to the open-source community for tools and libraries that made this project possible.🙌
