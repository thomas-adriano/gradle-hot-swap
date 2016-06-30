# gradle-hot-swap
### Hot Swap functionality to Gradle projects in Eclipse and IntelliJ

This script uses [spring-loaded](https://github.com/spring-projects/spring-loaded) to provide hot swap functionality to Gradle application projects. It does not create any new tasks, instead it uses the application's plugin `run` task.

### Getting started
* Make sure the build.gradle file from the target project has the application plugin applied (`apply plugin: 'application'`);
* Make sure yout IDE are compiling the sources after change or on save;
* Add this line to your build.gradle file: `apply from: "hot-swap.gradle"`
* Execute the `run` task from Gradle application plugin

### How it Works
* Adding spring-loaded parameters to JVM initialization (via [applicationDefaultJvmArgs](https://docs.gradle.org/current/userguide/application_plugin.html#N16043))
* (re)generating Eclipse .classpath and IntelliJ .iml files to change the output dir to gradle's output dir (necessary to spring-loaded watching process)

### Constraints
* The target project must have the Gradle application plugin applied (`apply plugin: 'application'`);
* The IDE must compile the sources after save or change;

### Caveats
* In eclipse, after the first time you execute the `gradle run` (application plugin task) you have to refresh the target project, otherwise hot swap will just not work.
