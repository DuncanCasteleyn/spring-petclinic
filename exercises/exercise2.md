# Exercise 2: Adding native compilation
1. Add plugin to pom.xml:
```xml
      <plugin>
        <groupId>org.graalvm.buildtools</groupId>
        <artifactId>native-maven-plugin</artifactId>
      </plugin>
```
2. Run mvn spring-boot:process-aot
3. Navigate to `target/spring-aot/main/sources/org/springframework/samples/petclinic` and look how your classes have been pre-compiled with AOT stuff
4. Open some class files with IntelliJ's decompiler and look at the generated code.
5. Add profile native to your pom.xml and active the profle, then run `mvn spring-boot:build-image` 
5. Try and run the docker image `docker run -p 8080:8080 spring-petclinic:3.0.1`
6. Oops, it doesn't work. EhCache does not support AOT and native compilation. Let's replace it by another cache manager.
7. Remove EhCache from the pom.xml and add Caffeine to the pom.xml.
```xml
    <dependency>
      <groupId>com.github.ben-manes.caffeine</groupId>
      <artifactId>caffeine</artifactId>
    </dependency>
```
8. Build the native image again and run `docker run -p 8080:8080 spring-petclinic:3.0.1`
9. Let's navigate to our page, and it... 
