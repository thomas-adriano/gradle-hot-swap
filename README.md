# gradle-hot-swap
### Hot Swap functionality to Gradle projects in Eclipse and IntelliJ

This script uses [spring-loaded](https://github.com/spring-projects/spring-loaded) to provide hot swap functionality to Gradle application projects.

### How it Works
* Adding spring-loaded parameters to JVM initialization (via [applicationDefaultJvmArgs](https://docs.gradle.org/current/userguide/application_plugin.html#N16043))
* (re)generating Eclipse .classpath and IntelliJ .iml files to change the output dir to gradle's output dir (necessary to spring-loaded watching process)

### Constraints
* The target project MUST have the Gradle application plugin applied (`apply plugin: 'application'`);

### Getting started
* Add this line to your build.gradle file: `apply from: "hot-swap.gradle"`
* Make sure yout IDE are compiling the sources after change or on save;
* Execute the `run` task from Gradle application plugin

### Caveats
* In eclipse, after the first time you execute the `gradle run` (application plugin task) you have to refresh the target project, otherwise hot swap will just not work.
