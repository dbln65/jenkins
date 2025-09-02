# Demo Java App with Jenkins Pipeline

This repository contains a simple Java application built with **Maven** and integrated with **Jenkins** for continuous integration (CI).  
It demonstrates how to structure a Java project, run unit tests, and automate builds with Jenkins.

---

## 📂 Project Structure

-----------------

```bash
.
├── Jenkinsfile
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── example
    │               └── App.java
    └── test
        └── java
            └── com
                └── example
                    └── AppTest.java
```

---

## ⚙️ How It Works

1. **Build Tool: Maven**  
   - Compiles the Java source code  
   - Runs unit tests (using JUnit 5)  
   - Packages the app into a `.jar` file located in `target/`

2. **Continuous Integration: Jenkins**  
   - The `Jenkinsfile` defines a declarative pipeline.  
   - Pipeline stages:  
     - **Checkout** → Pulls the repository from GitHub  
     - **Build & Test** → Runs `mvn clean install` inside a Docker container  
     - **Test Reports** → Jenkins collects and displays results from `target/surefire-reports/`  
     - **Artifacts** (optional) → The built `.jar` can be archived in Jenkins for download  

---

## ▶️ Running Locally

Build and run the app:

```bash
mvn clean install
java -cp target/demo-app-1.0-SNAPSHOT.jar com.example.App
```
Run unit tests:
```bash
mvn test
```

## 🛠 Requirements

- Java 11 or higher

- Maven 3.x

- (Optional) Jenkins with Docker installed for pipeline automation

## 🚀 CI/CD with Jenkins

- Jenkins automatically builds the project when changes are pushed to the main branch

- Test results are visible inside Jenkins under Test Result

- Build artifacts (the .jar file) can be archived and downloaded from Jenkins
