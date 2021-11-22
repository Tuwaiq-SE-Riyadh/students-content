
# Spring Data

### LEARNING OBJECTIVES

*After this lesson, you will be able to:*
- Explain how the Repository Pattern is used in Spring Data.
- Integrate a Spring Boot application with a Postgres database.
- Create endpoints for your application using Spring Data.
- Use annotations to get the right data from a relational database into your Spring application.

## Opening (10 mins)

[Spring Data’s](https://spring.io/projects/spring-data) mission is to provide a familiar and consistent Spring-based programming model for data access while still retaining the special traits of the underlying data store.

It makes it easy to use data access technologies, relational and non-relational databases, map-reduce frameworks, and cloud-based data services.

Some of its features are:
- Powerful repository and custom object-mapping abstractions
- Dynamic query derivation from repository method names
- Implementation domain base classes providing basic properties
- Possibility to integrate custom repository code
- Easy Spring integration via JavaConfig and custom XML namespaces
- Advanced integration with Spring MVC controllers

### Spring Data and JPA 

Modern web development almost always involves some kind of Object Relational Mapping (ORM) or Object Data Mapping (ODM) tool. Popular libraries such as Ruby's [ActiveRecord](http://guides.rubyonrails.org/active_record_basics.html), Node's [Mongoose](http://mongoosejs.com/), and Elixir's [Ecto](https://hexdocs.pm/ecto/Ecto.html) simplify many of the low-level database interactions that we are responsible for as software engineers. These tools provide development speed, safety, security, and ease of use that enable us to spend more time focusing on functionality and less time on complicated details.

Spring Boot provides its own unique ORM implementation that borrows from similar tools, but also augments them in many ways. Spring Data Entities and Repositories are an implementation of the [Repository Pattern](http://deviq.com/repository-pattern/) that will greatly simplify the process of connecting to and interacting with our databases in a Spring Boot environment.

-----



# Code Along: Spring Boot Database Integration



----


#### Additional Reading

You can read more about auto generating the id [here](https://www.objectdb.com/java/jpa/entity/generated#The_Auto_Strategy_).
