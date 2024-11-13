# Java Gradle Project

These are instructions for starting a plain Java project in the standard distribution of Visual Studio Code.  wpilib comes with it's own (generally older) version of Visual Studio Code.  The instructions on this page can also run in the Visual Studio Code that comes with wpilib, but not by starting a new wpilib project.  

Starting a Java Gradle project in Visual Studio Code (VS Code) is straightforward with the help of the Java and Gradle extensions. Here’s a step-by-step guide to get started:

## Step 1: Install Necessary Extensions
Ensure the following extensions are installed in VS Code:
1. Extension Pack for Java (includes Debugger for Java, Java Test Runner, etc.)
2. Gradle for Java (provides Gradle support)

To install:
* Go to the Extensions view (Ctrl+Shift+X) and search for "Java Extension Pack" and "Gradle for Java."
* Install them both.

## Step 2: Create a New Gradle Project
You can create a Gradle project directly using the terminal or via the VS Code interface:

Option 1: Using the VS Code Command Palette
1. Open the Command Palette (Ctrl+Shift+P).
2. Type and select Java: Create Java Project.
3. Choose Gradle as the build tool.
4. Follow the prompts to configure the project (e.g., project name, package, etc.).
5. VS Code will create the project structure and open it for you.

Option 2: Using the Terminal
1. Open the terminal in VS Code (Ctrl+ `).
2. Run the following command:
```
gradle init
```

Follow the interactive prompts:
3. Select type of project to generate: application or library (for a basic Java project, choose application).
  * Select implementation language: Java.
  * Select build script DSL: Groovy or Kotlin (default is Groovy).
  * Select test framework: JUnit (default for testing).
  * Project name: Enter your desired project name.

Gradle will generate the project structure.

## Step 3: Project Structure
After initialization, you’ll see a structure similar to this:
```
my-gradle-project/
├── build.gradle         # Gradle build script
├── settings.gradle      # Project settings
├── gradle/              # Gradle wrapper files
├── gradlew              # Unix Gradle wrapper
├── gradlew.bat          # Windows Gradle wrapper
└── src/
    ├── main/
    │   └── java/
    │       └── com/
    │           └── example/
    │               └── App.java   # Main application class
    └── test/
        └── java/
            └── com/
                └── example/
                    └── AppTest.java  # Unit tests
```

## Step 4: Run and Debug Your Project
1. Run the Project:
  * Open App.java (or your main class).
  * Click the Run button above the main method or use the Command Palette (Ctrl+Shift+P) and select Run Java.

2. Debug the Project:
  * Set breakpoints by clicking in the left gutter of the editor.
  * Press F5 or use the Command Palette to start debugging.
  * Ensure your launch.json file is set up correctly (VS Code often auto-generates it for Java).

## Step 5: Edit the build.gradle File
Modify build.gradle to add dependencies, plugins, or custom tasks as needed. Example:

```
plugins {
    id 'java'
    id 'application'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'com.google.guava:guava:31.1-jre'
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.2'
}

application {
    mainClass = 'com.example.App'
}
```
Run ./gradlew build in the terminal to compile the project and resolve dependencies.

## Step 6: Explore Gradle Tasks
Use the Gradle extension to explore available tasks:
  1. Open the Gradle Tasks view from the Explorer panel.
  2. Run tasks like build, run, or test directly from the interface.

## Step 7: Version Control (Optional)
If using Git, initialize a repository:
```
git init
```

Commit your project:
```
git add .
git commit -m "Initial commit"
```