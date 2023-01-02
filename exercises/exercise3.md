# Fixing our resources
In exercise 2 we got our application to work kind of natively... Let's fix that.

1. Create a new class called PetClinicRuntimeHints that implements RuntimeHintsRegistrar, we are going to register 2 resources there the h2 db files and the messages resource bundle.
```java
public class PetClinicRuntimeHints implements RuntimeHintsRegistrar {
    @Override
    public void registerHints(RuntimeHints hints, ClassLoader classLoader) {
        hints.resources().registerPattern("db/h2/*");
        hints.resources().registerPattern("messages/*");
    }
}
```
2. To the PetClinicApplication class add `@ImportRuntimeHints(PetClinicRuntimeHints.class)` on the class level
3. Let's build another native image and see if it works
4. It works! you learned to enable native compilation and how to add resources to the native image.
