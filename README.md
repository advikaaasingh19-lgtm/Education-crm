# EducationCrmProject

A CRM (Customer Relationship Management) system for educational institutions, built with **Spring Boot 3.3** and **Java 17**. It helps manage students, employees, courses, inquiries, and follow-ups, with integrated online payments.

## Features

- Server-side rendered UI with **Thymeleaf**
- Student/employee/course/inquiry management (see `controllers/` and `entities/`)
- Follow-up tracking for leads and inquiries
- Data persistence using **Spring Data JPA** with **MySQL**
- Input validation via **Spring Validation**
- Online payment integration via **Razorpay**

## Tech Stack

| Layer          | Technology                  |
|----------------|------------------------------|
| Language       | Java 17                     |
| Framework      | Spring Boot 3.3.12          |
| Templating     | Thymeleaf                   |
| Database       | MySQL                       |
| ORM            | Spring Data JPA / Hibernate |
| Payments       | Razorpay Java SDK           |
| Build Tool     | Maven                       |

## Prerequisites

- Java 17 or higher
- Maven (or use the included `mvnw` / `mvnw.cmd` wrapper — no separate install needed)
- MySQL server running locally or accessible remotely
- A Razorpay account with API keys (for payment features)

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/advikaaasingh19-lgtm/Education-crm.git
cd Education-crm
```

### 2. Configure the database and secrets

Create a `src/main/resources/application.properties` (or `application-local.properties`) file with your own values — **do not commit real credentials**:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/education_crm
spring.datasource.username=your_db_username
spring.datasource.password=your_db_password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

razorpay.key.id=your_razorpay_key_id
razorpay.key.secret=your_razorpay_key_secret
```

Make sure the referenced MySQL database (e.g. `education_crm`) exists before running the app:

```sql
CREATE DATABASE education_crm;
```

### 3. Build and run

Using the Maven wrapper:

```bash
./mvnw spring-boot:run        # macOS/Linux
mvnw.cmd spring-boot:run       # Windows
```

Or build a jar and run it:

```bash
./mvnw clean package
java -jar target/EducationCrmProject-1.0.jar
```

The app will start on `http://localhost:8080` by default.

## Project Structure

```
src/main/java/in/vk/main/
├── controllers/    # MVC controllers (Admin, Course, Employee, FollowUps, Inquiry, User)
├── api/            # REST-style API endpoints (FollowUps, Inquiry, Orders)
├── entities/       # JPA entities (Course, Employee, User, Orders, Inquiry, FollowUps)
├── repositories/   # Spring Data JPA repositories
├── dto/            # Data transfer objects
└── EducationCrmProjectApplication.java

src/main/resources/
└── templates/      # Thymeleaf HTML views (admin, employee, login, register, courses, etc.)
```

## Reference Documentation

- [Apache Maven documentation](https://maven.apache.org/guides/index.html)
- [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/3.3.1/maven-plugin/reference/html/)
- [Thymeleaf](https://docs.spring.io/spring-boot/docs/3.3.1/reference/htmlsingle/index.html#web.servlet.spring-mvc.template-engines)
- [Spring Web](https://docs.spring.io/spring-boot/docs/3.3.1/reference/htmlsingle/index.html#web)
- [Razorpay Java SDK](https://github.com/razorpay/razorpay-java)

## License

No license specified yet. Add a `LICENSE` file if you'd like to open-source this project.
