# Example project for reproducing grails-core issue #12953

## About this repository

This repository is for reproducing [grails-core issue #12953](https://github.com/grails/grails-core/issues/12953).

All of the files here are the defaults generated by `grails create-app` except for just two changes:
* The addition of a simple Grails script (`scripts/hello-world.groovy`) for demonstrating the problem.
* A config block in `build.gradle` for the `runScript` task to avoid an unrelated error caused by Spring Boot Devtools`.

There are branches for reproducing the issue in different versions of Grails.

This repository includes the Grails and Gradle wrappers, so you do not need to have either installed. (You will, however, need an appropriate JDK installed.)

## How to reproduce the bug

To reproduce the bug, simply `cd` into a clone of this repository and run:
```
./grailsw run-script scripts/hello-world.groovy
```

Instead of the script executing and printing a message as expected, the command simply sits idle after the application context starts.

If you run the script directly via the Gradle task instead, you can see the underlying stack trace that prevents the script from executing:
```
./gradlew runScript -Pargs='scripts/hello-world.groovy'
```
