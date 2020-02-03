# spring-boot-angular-template
Sample Setup of a Spring Boot Gradle Project with Angular Frontend

# What is this for? 
I found a lot of solutions on the internet how to integrate Angular into a Spring Boot application but I didn't find them very
satisfying so I decided to share my own. 

# How does it work?
I make a Gradle Project where the Angular project is a subproject of the spring boot application (of course you can make additional
subprojects) and edit the output path of the npm build job to put the results to a folder where the root project will include them to the build 
using webjars. Then I add a configuration to the backend which serves the transpiled angular sources as static web resources.

# What tools do I use?
- Gradle
- NPM (for angular build)
- Java 11
- Spring Boot 6.0.1
//TODO: add version
- Angular x.x.x

# What are the steps to reproduce this?
1. First of, create a Spring Boot Application (I recommend using Spring initalizr) with your desired config (java version, spring version, dependencies,...)
2. Create an Angular Project inside (```ng new``` in the root directory of the project)
3. Edit angular.json by changing the output path to "build/ng-dist"
4. Edit package.json by adding a new script: ```"prodBuild": "ng build --prod=true"```
5. Add client as subproject to gradle project (see build.gradle files for build)
6. Add config in application.properties
7. Add a Resolver Class for the static resources

# What files are important if I want to do this without copying the project? 
- .\src\main\java\me\katakompe\springbootangulartemplate\configuration\WebViewResolver.java
- .\client\build.gradle
- .\build.gradle
- .\src\main\resources\application.properties
- .\settings.gradle