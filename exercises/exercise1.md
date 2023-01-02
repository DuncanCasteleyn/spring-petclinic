# Exercise 1: Upgrading to Spring Boot 3
1. Upgrade the application to require Java 17
2. Upgrade the Spring Boot version to 3.0.x
3. Use IntelliJ IDEA's migration tool to migrate the project to Jakarta EE <br />
You can fine the tool by going to `Refactor -> Migrate Packages and Classes -> Java EE to Jakarta EE`
4. To the ehcache dependency in the pom.xml, add the following: `<classifier>jakarta</classifier>` so that maven knows it needs the jakarta version of the dependency, if you don't do this you will notice no version will be found from the spring boot parent pom, but when you add the classier it will find the correct version.
5. Because jaxb bind is no longer included in java 17 we need to add it as a dependecy, add the following to the pom.xml:
```xml
<dependency>
    <groupId>jakarta.xml.bind</groupId>
    <artifactId>jakarta.xml.bind-api</artifactId>
</dependency>
```
6. Run `mvn clean verify` to recompile using java 17
7. Run the application and verify that it works as expected
