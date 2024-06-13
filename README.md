# GitHub Maven Package Example

### Overview

An example GitHub Package Registry package using Java and Maven

[This](https://github.com/joshjohanning-org/maven-private-registry-example/blob/main/.github/workflows/maven-build.yml) authenticates to a private registry feed

```yml
    # OPTION 1 - use setup java
    #   - works well if only 1 private registry
    - name: Set up JDK 17
      uses: actions/setup-java@v3
      with:
        java-version: '17'
        distribution: 'temurin'
        cache: maven
        server-id: Java
        server-username: jjohanning0798
        server-password: ${{ secrets.AZDO_TOKEN }}

    - run: mvn help:effective-settings # -s settings.xml

    # OPTION 2: specify a settings.xml and use ${env.VARIABLES} in the file
    #   - works better if multiple private registries
    # - run: mvn -B package --file pom.xml -s settings.xml
    #   env:
    #     AZDO_TOKEN: ${{ secrets.AZDO_TOKEN }}

    - name: Build with Maven
      run: mvn -B package --file pom.xml -s settings.xml
      env:
        AZDO_TOKEN: ${{ secrets.AZDO_TOKEN }}
```

### Installation

Ensure you have added `mattamorphic` to your ~/.m2/settings.xml for the package registry 

(See this guide)[https://help.github.com/en/articles/configuring-apache-maven-for-use-with-github-package-registry#installing-a-package]

Add the dependency to your pom.xml file:

```
<dependency>
    <groupId>com.mattamorphic</groupId>
    <artifactId>github-maven-package-sample</artifactId>
    <version>VERSION</version>
</dependency>
```

Then run from the root dir of the project:

```
mvn install
```
