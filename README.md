# Spring Ecommerce Server

## LiveReload

Step 1, Enable the following options in IntelliJ IDEA:

- Go to `Settings` -> `Build, Execution, Deployment` -> `Compiler` and check the box for `Build project automatically`.
- Go to `Settings` -> `Advanced Settings` and check the box for `Allow auto-make to start even if developed application is currently running`.

Step 2, Install the [LiveReload](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) extension in your browser and make sure it is enabled.

For more details, refer to [Developer Tools](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.devtools).

## Code Formatter

[Spring Java Format](https://github.com/spring-io/spring-javaformat) provides Spring-style formatting for Java code.

Step 1: Add the following plugin to `build.gradle.kts`. Then, click on the "Load Script Configurations" and "Load Gradle Changes" icons to apply the changes. For example:

```kotlin
plugins {
    // ...
    id("io.spring.javaformat") version "0.0.39"
}
// ...
```

Step 2: Download the latest version of [spring-javaformat-intellij-idea-plugin](https://repo1.maven.org/maven2/io/spring/javaformat/spring-javaformat-intellij-idea-plugin/0.0.39/) and install it in IntelliJ IDEA by selecting "Install from Disk".

Step 3: On the right side, click on the Gradle tab and then select the icon "Reload all Gradle projects". A yellow icon will appear in the status bar.

Step 4: Click on the "Reformat Code" icon to format your code.

## Develop with Docker

Step 1, Ensure that Docker is installed on both your computer and the remote server.

Step 2, Run the following command to build an image:

```bash
$ cd <your-project>
$ ./gradlew bootBuildImage --imageName=yourorg/yourapp
```

Step 3, Open Docker Desktop on your computer and push the image to Docker Hub.

Step 4, On the remote server, pull and run the image from Docker Hub:

```bash
$ docker pull yourorg/yourapp:latest
$ docker run -d -p 8080:8080 --name yourapp --restart always -e "SPRING_PROFILES_ACTIVE=prod" yourorg/yourapp:latest
```

That's it! You can now access the application at `http://<your-server-ip>:8080`.

For more details, refer to [Spring Boot Docker](https://spring.io/guides/topicals/spring-boot-docker/).