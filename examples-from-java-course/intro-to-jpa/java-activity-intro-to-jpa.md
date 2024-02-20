# CFU: Intro to JPA

## Introduction :pencil2:

This activity will help you practice and assess the knowledge and skills you just learned. During a bootcamp, it's important to spend a lot of time practicing what you've learned. The exercises given to you are just the start. You will get the opportunity to practice more in labs and later, in projects.

We encourage you that once you finish the exercises on the Student Portal platform, try to find more challenges to work on online

**Note:** You are provided with solution to each exercise. The purpose of providing solutions to exercises is to allow you to compare your own work to see if you have a similar or correct approach.

It is not meant to be used as a way to cheat or copy the answers.

It is important to understand the reasoning behind the solution in order to improve your own understanding and problem-solving abilities.

<br>

## Spring Boot

### Instructions

Research and answer the following:

1. Why are interfaces important in complex applications?
2. What is meant by "separation of concerns"?
3. What is the purpose of a Service Layer?
4. Why is business logic not included in the Data or Controller Layer?

<br>

<details style="font-size: 14px; cursor: pointer; outline: none;">
<summary> Click for Solution </summary>

1. Why are interfaces important in complex applications?  
   Interfaces are important in complex applications because they allow for flexibility and modularity. They provide a clear, defined set of methods that can be implemented by different classes, allowing for easier integration and testing of new features or modules.

2. What is meant by "separation of concerns"?  
   "Separation of concerns" refers to the practice of separating different aspects or functions of an application into distinct units or layers, such as the Data Layer, Service Layer and Controller Layer. This helps to organize the code and make it easier to maintain and modify.

3. What is the purpose of a Service Layer?  
   The Service Layer is a layer in an application that contains the business logic, or the logic that performs the core functionality of the application. It is responsible for handling and processing data, making decisions based on that data and communicating with other layers or external systems.

4. Why is business logic not included in the Data or Controller Layer?  
   Business logic should not be included in the Data or Controller Layer because these layers have specific responsibilities and purposes. The Data Layer is responsible for managing data storage and retrieval, while the Controller Layer is responsible for handling incoming requests and directing them to the appropriate resources. Including business logic in these layers would violate the principle of separation of concerns and could lead to confusion and code that is more difficult to maintain.

</details>

<br>

## Spring Boot & JPA

### Instructions

Research and answer the following:

1. What is Spring Boot?
2. What is JPA?
3. What is a repository in Spring Data JPA?
4. What is an entity in JPA?
5. How do you configure a Spring Boot application to connect to a database?

<br>

<details style="font-size: 14px; cursor: pointer; outline: none;">
<summary> Click for Solution </summary>

1. What is Spring Boot?  
   Spring Boot is a framework for building stand-alone, production-grade Spring-based applications with minimal configuration. It provides a set of pre-configured options and dependencies that make it easier to develop Spring applications.

2. What is JPA?  
   JPA stands for Java Persistence API. It is a Java specification for managing, storing and accessing data in relational databases. JPA provides a set of interfaces and annotations for mapping Java objects to database tables and for performing database operations.

3. What is a repository in Spring Data JPA?  
   A repository in Spring Data JPA is a Spring-provided interface that defines methods for performing CRUD operations on a database. It acts as a database access layer, providing a way to perform database operations without having to write raw SQL statements.

4. What is an entity in JPA?  
   An entity in JPA is a Java object that represents a row in a database table. It is annotated with the `@Entity` annotation and mapped to a database table using the `@Table` annotation.

5. How do you configure a Spring Boot application to connect to a database?  
   To configure a Spring Boot application to connect to a database, you need to specify the database connection properties in the `application.properties` or `application.yml` file. This includes the database driver, URL, username and password. You also need to include the appropriate database driver dependency in your project.

</details>
