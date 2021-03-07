# gradle-test

Explain that the jvm version of gradle variants conflicts with Kotlin jvm targets

## build
```
./gradlew build
```
In the built class file, the bytecode is showed as Java 8 because the target version has been set. (https://en.wikipedia.org/wiki/Java_class_file)

## outgoing variants

The gradle sets the variants of jvm version the same as the JDK version. In my local, it is JDK 11.
```
java -version
openjdk version "11.0.9.1" 2020-11-04
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.9.1+1)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.9.1+1, mixed mode)
```

Gradle variants output:
```
./gradlew outgoingVariants

> Task :outgoingVariants
--------------------------------------------------
Variant apiElements
--------------------------------------------------
Description = API elements for main.

Capabilities
    - :gradle-test:unspecified (default capability)
Attributes
    - org.gradle.category                 = library
    - org.gradle.dependency.bundling      = external
    - org.gradle.jvm.version              = 11
    - org.gradle.libraryelements          = jar
    - org.gradle.usage                    = java-api
    - org.jetbrains.kotlin.localToProject = public
    - org.jetbrains.kotlin.platform.type  = jvm
...
```

And that causes Gradle dependency resolve problem -- I have to use JDK 11 to add this dependency in my main project.
