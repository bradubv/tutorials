# Packaging a library

## Step 1: Create the Java Library

1. Project Structure:
```
my-library/
├── src/
│   └── main/
│       └── java/
│           └── org/
│               └── team7525/
│                   └── GreetLibrary.java
├── build.gradle
└── settings.gradle
```

2. Library Code (GreetLibrary.java):
```
package org.team7525;

public class GreetLibrary {
    public static String greet(String name) {
        return "Hello, " + name + "!";
    }
}
```

3. build.gradle:
```
plugins {
    id 'java'
    id 'maven-publish' // Enables publishing to a Maven repository
}

group = 'org.team7525'
version = '1.0.0'

publishing {
    publications {
        mavenJava(MavenPublication) {
            from components.java
        }
    }
    repositories {
        maven {
            name = "local"
            url = uri("file://${buildDir}/maven-repo") // Local repository for demonstration
        }
    }
}
```

4. settings.gradle:
```
    rootProject.name = 'greet-library'
```

## Step 2: Build and Publish the Library

1. Build the Library: Run the following command in the terminal:
```
./gradlew build
```

2. Publish the Library to a Local Maven Repository:
```
./gradlew publish
```
This will create a local Maven repository at build/maven-repo.

## Step 3: Create a Simple Project to Use the Library

1. Project Structure:
```
my-app/
├── src/
│   └── main/
│       └── java/
│           └── org/
│               └── team7525/
│                   └── MyApp.java
├── build.gradle
└── settings.gradle
```

2. Application Code (MyApp.java):
```
package org.team7525;

import org.team7525.GreetLibrary;

public class MyApp {
    public static void main(String[] args) {
        String message = GreetLibrary.greet("World");
        System.out.println(message);
    }
}
```

3. build.gradle:
```
plugins {
    id 'application'
}

repositories {
    maven {
        url = uri("../greet-library/build/maven-repo") // Local repository
    }
    mavenCentral() // For other dependencies if needed
}

dependencies {
    implementation 'org.team7525:greet-library:1.0.0'
}

application {
    mainClass = 'org.team7525.MyApp'
}
```

4. settings.gradle:
```
rootProject.name = 'my-app'
```

## Step 4: Run the Application

1. Run the application: Navigate to the my-app directory and run:
```
./gradlew run
```

This should print:
```
    Hello, World!
```

## Example:

1. Clone the library repository https://github.com/bradubv/greet-lib.git

2. Open a terminal (CTRL + `) and build the library
```
./gradlew build
```

3. Publish the library to the locally created repo
```
./gradlew publish
```

4. Clone the applicaton repository https://github.com/bradubv/greet-app.git . It is important to clone this project in the same directory where the library project was cloned.  This is because a relative path to the repository was used in the gradle file.

5. Open a terminal (CTRL + `) and build the app
```
./gradlew build
```

6. Run the application
```
./gradlew run
```

## Additional exercises:

1. Dependency Management: How does Gradle download the library from the local Maven repository.
1. Publishing to a Remote Repository: Instead of publishing to a local repository publish the library to a remote Maven repository like Maven Central or GitHub Packages.
1. Versioning: Updating the library version (e.g., 1.0.1) and how dependencies in other projects are affected.
1. Testing: Include unit tests in my-library using JUnit and demonstrate how testing works during the build.