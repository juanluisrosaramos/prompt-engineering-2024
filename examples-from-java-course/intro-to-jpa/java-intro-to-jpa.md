# Intro to JPA

## Lesson Overview :pencil2:

SQL and Java are powerful companions but they function in fundamentally different ways which can make integrating the two difficult. Spring Data JPA is an abstraction layer that makes integrating Java projects with SQL databases much easier. This lesson introduces the basics of Spring Data JPA.

<br>

## Learning Objectives :notebook:

By the end of this lesson, you will be able to:

- Articulate the purpose of Spring Data JPA
- Identify key Spring JPA Data annotations

<br>

## Key Definitions and Examples :key:

### Maven

Maven is a build tool (like Make is for C/C++, or Ant and Gradle are for Java). It compiles your source code into binary, runs the tests, etc.

<br>

### Spring Boot

Spring Boot is a library, which helps you create an application faster. It is a bunch of code written by others available for you to use it.

Your application can use Spring Boot as a library and you can build it via Maven, so you can run your application as well.

All in all, Spring Boot is a project initializer based on Spring. It prevents you from writing long code with features such as auto-configuration and lets you avoid excessive configuration. The Spring Framework is a solid option for developers, with the many enhancements listed above. However, when used with Spring Boot, it is highly advantageous.

The [Spring Initializr](https://start.spring.io) is ultimately a web application that can generate a Spring Boot project structure for you. It doesn't generate any application code, but it will give you a basic project structure and either a Maven or a Gradle build specification to build your code with.

<u><i>Example:</i></u>

Follow along while the teacher explains the different aspects of the following sample application [**demo-api**](https://github.com/ironhack-labs/lesson-code-java-api-demo).

- **Controller Layer:** The Controller layer is the conductor of operations for a request. It controls the transaction scope and manages the session-related information for the request. The controller first dispatches a command and then calls the appropriate view processing logic to render the response.

- **Data Layer:** This layer’s responsibility is limited to Create, Retrieve, Update and Delete (CRUD) operations on a data source, which is usually a relational or non-relational database. Repository classes are usually put in a repository package.

- **Service Layer:** Calculations, data transformations, data processes and cross-record validations (business rules) are usually done at this layer. They get called by the controller classes and might call repositories or other services. Service classes are usually put in a service package.

Ensure that you have created the table and inserted seed data for the demo application in your RDBMS using the following script.

```sql
CREATE TABLE student (
    id INT AUTO_INCREMENT NOT NULL,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
  PRIMARY KEY(id)
);

INSERT INTO student (first_name, last_name) VALUES
('Maya', 'Charlotte'),
('James', 'Fields'),
('Michael', 'Alcocer'),
('Tomas', 'Lacroix'),
('Sara', 'Bisat'),
('Helena', 'Sepulvida'),
('Michael', 'Goodman'),
('Jacob', 'Armas'),
('Luceilla', 'Sepulvida');
```

Run the application and test the different routes available using Postman.

<br>

### Spring JPA

Spring Boot JPA is a Java specification for managing relational data in Java applications. It allows us to access and persist data between Java object/ class and relational database. JPA follows Object-Relation Mapping (ORM). It is a set of interfaces.

<br>

### Repository

The actual strength of Spring Data JPA lies in the repository abstraction. It abstracts the data store-specific implementation details and allows us to write the business logic code on a higher abstraction level. We only need to learn how to use the Spring Data repository interfaces instead of worrying about the implementation of these interfaces. Spring Data provides an implementation for these repository interfaces out-of-the-box.

<br>

### JpaRepository

JpaRepository is a JPA (Java Persistence API) specific extension of Repository. It contains the full API of CrudRepository and PagingAndSortingRepository. So it contains API for basic CRUD operations and also API for pagination and sorting.

**Note:** It is indeed not necessary to put the @Repository annotation on interfaces that extend JpaRepository; Spring recognizes the repositories by the fact that they extend one of the predefined Repository interfaces.

<br>

### Entity

Entities in JPA are nothing but POJOs representing data that can be persisted in the database. An entity represents a table stored in a database. Every instance of an entity represents a row in the table.

<u><i>Example:</i></u>

Create a new Spring Boot application that includes a course model and its corresponding repository.

```java
@Entity
@Table(name = "course")
public class Course {

  @Id
  @Column(name="course_code")
  private String courseCode;

  @Column(name="course_name")
  private String courseName;

  // constructor, getters and setters omitted for brevity
}
```

```java
@Repository
public interface CourseRepository extends JpaRepository<Course, String> {

}
```

<br>

## Additional Resources :clipboard:

If you would like to study these concepts before the class or would benefit from some remedial studying, please utilize the resources below:

- [Introduction to Spring Framework by Spring.io](https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/overview.html)
- [Spring Boot Introduction by Amitph](https://www.amitph.com/spring-boot-introduction/)
- [Spring Data JPA by Baeldung](https://www.baeldung.com/the-persistence-layer-with-spring-data-jpa)
- [Accessing Data with JPA by Spring.io](https://spring.io/guides/gs/accessing-data-jpa/)
- [Spring Data JPA Repositories by Atta](https://attacomsian.com/blog/spring-data-jpa-repositories)
