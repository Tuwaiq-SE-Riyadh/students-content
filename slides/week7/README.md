
# Spring Boot Development Environment

## Learning Objectives

*After this lesson, students will be able to:*

- Use the IntelliJ IDE.
- Explain how Tomcat is used.
- Build and manage projects using Maven.
- Integrate APIs into your project using Postman.

### LESSON GUIDE

| TIMING  | TYPE  | TOPIC  |
|:-:|---|---|
| 5 min  | Introduction  | Learning Objectives |
| 10 min | Exercise | Installing the IDE |
| 5 min | Exercise | Installing the Server |
| 10 min | Exercise | Installing Postman |
| 20 min | Exercise | Installing the Build Tool |
| 5 min  | Conclusion  | Review/Recap |

## Introduction (5 min)

When building complicated web applications with lots of dependencies and features, how your development environment is set up can almost always make or break your application. How will you run your application? How will you manage dependencies? How can you get support for the framework you're using?

We're going to answer all of these questions for you in this lesson. Yes, we're going to be downloading and installing lots of things together, so bear with us. But think of this lesson as less of an "install-fest" and more about learning *what* these tools do for you and *how* they work together.

Here's what we'll be setting up:

- An IDE (IntelliJ).
- A server to run your application (Tomcat).
- An API environment (Postman).
- A tool to build and manage dependencies (Maven).

----

## Installing the IDE: IntelliJ (10 min)

> **Instructor Note**: Skip this part if students have already installed IntelliJ.

The first thing we need to install is the IDE we'll use to build our projects: IntelliJ. The IDE is going to make your life as a Spring developer much, much easier.

> **Knowledge Check**: Why are IDEs helpful?

**Stop, do not pass go!** 

You should already have JDK 8 configured on your system. To double check, run `java -version` in the terminal. If it's not configured, [click here](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) to do so now.

One of the great debates in the Java community is around IDEs: IntelliJ or Eclipse. People have strong (STRONG!) opinions about which is better, and honestly, it's easy to make arguments for either side. 

For this course, we'll use IntelliJ Community Edition (CE). Keep in mind that IntelliJ CE limits features for users (for example, you're unable to install a web server). Spring Boot has a web server installed as a service that will be used to manage applications.

- Download IntelliJ [here](https://www.jetbrains.com/idea/download/#section=mac).
- Choose "Community Edition."

Follow the steps to download, install, and open IntelliJ.

----

## Tomcat (5 min)

[Apache Tomcat](http://tomcat.apache.org/), created by the Apache Software Foundation, is an open-source HTTP server and a container for Java Servlet/Java Server Pages (JSP). JSP allows us to create dynamic webpages in Java, and Tomcat provides a server for us to run them.

A web server is a container that's used to run applications that satisfy client requests. The communication between client and server takes place using the **Hypertext Transfer Protocol** (HTTP).

-----

## Installing Postman (10 min)

Postman is a tool used for interacting with HTTP APIs. Postman will act as our client to send requests to the server and get a response back to test the APIs. It is a very useful tool. You can learn more about it [here](https://www.getpostman.com/). 

Download the Postman app [here](https://www.getpostman.com/products), making sure to get the app and not the Chrome extension. (Postman Chrome is deprecated and is missing essential Postman features.) 

Postman has many features that you'll learn more about as we progress.

---

## Understanding Maven (20 min)

According to [Apache](https://maven.apache.org/), Maven is a software project management and comprehension tool. Based on the concept of a **project object model** (POM), Maven can manage a project's build, reporting, and documentation from a central piece of information.

Maven is a build tool that's used in building and managing any Java-based project. Maven’s primary goal is to allow a developer to comprehend the complete state of a development effort in the shortest period of time. 

In order to attain this goal, there are several areas of concern that Maven attempts to deal with:

- Making the build process easier.
- Providing a uniform build system.
- Providing high-quality project information.
- Providing guidelines for best practices development.
- Allowing transparent migration to new features.

You can read more about it [here](https://maven.apache.org/what-is-maven.html). Most modern IDEs give the option of creating Maven projects by default. You'll get to practice that in the following sections.

### Where It All Starts: `pom.xml`

The project object model (POM) is the fundamental unit of work in Maven. The `pom.xml` file contains information about the project and configuration details used by Maven to build the project. When executing a task or goal, Maven looks for the POM in the current directory. It reads the POM, gets the needed configuration information, and then executes the goal. You can read more about POM [here](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html).

You'll mostly be making changes in `pom.xml` to add in the _dependencies_ for Spring Boot, etc. A dependency is a JAR file that is added to the classpath for a successful build of your project.

### Creating a Maven Project

Lets create a Maven project in IntelliJ before going into further details.

Open IntelliJ and create a new project. Select "Maven Project." After selecting your workspace location, you'll see multiple archetypes. An **archetype** is a project template that creates files that are relevant to your project. We'll select the webapp archetype `maven-archetype-webapp`. Give the Artifact ID as `maven-demo` and Group ID as `ex`. Update the release version to `1.0`.

As soon as the application loads, Maven will start downloading all of the dependencies. There's something known as [**central repository**](https://repo.maven.apache.org/maven2/) in Maven, where all of the dependencies are stored. You can even search for the dependencies [here](https://search.maven.org/). 

Copy and paste the most appropriate one in the `pom.xml` file. There is also a **local Maven repository** where all of the JARs are cached. For Mac users, this local repository is found in the `~/.m2/repository/` directory.

You'll also see a pop up in IntelliJ to enable Auto Import. Enable that option.

In our case, copy and paste the code below in `pom.xml`:

```mvn
<dependency>
	<groupId>javax.servlet</groupId>
  	<artifactId>javax.servlet-api</artifactId>
	<version>4.0.1</version>
</dependency>
```

In the console, along with other application details at the end, you should see a `Build Success` message, which means all of the dependencies are downloaded and successfully resolved.  

> Sometimes there are compilation errors in the code due to a dependency. One thing you can always try is reimporting all of them. Right click on the `maven-demo` project and you'll see a `Maven` option toward the bottom of the list. Click on `Reimport` to resolve all of the dependencies again. 

You can use Maven to build, deploy, and test your application. We'll be working on Spring Boot, which comes with its own ecosystem, so for now we'll use Maven purely as a dependency management tool. We'll learn more about Maven and what it can do as we progress through these lessons.

### How Does Maven Install Dependencies?

When a dependency is added to `pom.xml`, Maven first looks into the local repository to see if it is available. If not, then it goes to the central repository to look for the files. Once found, it downloads and saves them in a local repo and they are then used to build and run the app. 

This is essentially the whole idea of using a build tool such as Maven. As a developer, you just give your requirements in a POM file, and after that it becomes Maven's responsibility to resolve everything for you.

## How Does It All Come Together?

We'll use IntelliJ to write and compile our code and manage our application. Maven will manage all of the dependencies we need in our application. Tomcat is our web server, which will run our application. Postman will be our client tool for sending HTTP requests to the server and getting back a response. 

-----

## Conclusion (5 min)

With that, welcome to the world of building Java applications! You're all set up to create and build Spring Boot projects in IntelliJ.

## Additional Resources

- [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)