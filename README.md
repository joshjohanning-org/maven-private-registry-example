# GitHub Maven Package Example

### Overview

An example GitHub Package Registry package using Java and Maven

### Installation

Ensure you have added `mattamorphic` to your ~/.m2/settings.xml for the package registry 

(See this guide)[https://help.github.com/en/articles/configuring-apache-maven-for-use-with-github-package-registry#installing-a-package]

Add the dependency to your pom.xml file:

```
<dependency>
    <groupId>com.mattamorphic</groupId>
    <artifactId>github-maven-package-example</artifactId>
    <version>VERSION</version>
</dependency>
```

Then run from the root dir of the project:

```
mvn install
```