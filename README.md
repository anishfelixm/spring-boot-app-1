# Spring Boot Project 1 : A Simple Server

In this project, I built a simple tomact server with a single controller which return the string "Hello World". This is like the 'hello world' to springboot. I learnt several concepts building this project.

I used [spring docs](https://docs.spring.io/spring-boot/tutorial/first-application/index.html) to get started with this. Firstly I learnt what's the point of dependency management. Dependency management is handled in this project by Maven. The dependencies are added under the \<dependencies\> block in pom.xml file which is extremely important for spring projects. For this project I used starter-web dependency. Then I created the class that starts the Spring Application, which here is the basicServer class. The SpringApplication.run() method is what's used to do this. The @SpringBootApplication annotation is very important as it lets Maven know where to start from. Then I created the controller using the @RestController annotation. SpringBoot makes all this set up quite easy. A @RequestMapping annotated method is needed so that the spring application knows where to reach out to when the url is called. In this project, There's only one mapping i.e. "/" which is the home mapping. When this mapping is called the subsequent path is mapped and the hello() method in controller is called which returns the "Hello World" string. So with this a localhost server, which is the inbuilt server <b>Tomcat</b> is created using Spring Boot. To check the server working, first get the application running using mvn spring-boot:run command and then on any web browser hit localhost:8080 .

I had to deal with several issues in the beginning, some of which I have noted down below. I also learnt about build plugins to create a jar compressed file which can be independently deployed on containers. This is added in the \<build\> block in pom.xml.


> ### Issue 1 
> Each springboot project needs to have a separate repository. Don't make a parent repo and then try to create child repositories. It took a long while for me to find out this is very complicated and involved git submodules.

> ### Issue 2
>  To connect the project to a github repo. First create an empty repo on github. On local system create your maven project. In the git tab, you can set your remote url to the repo we just created. This I found to be the easier way to add the project to Github.

> ### Issue 3
> Struggles with loading dependencies. Firstly make sure you have set the jdk right. For now atleast, I had better experience with oracle openjdk and azul zulu community jdk. Then after you add the dependencies,sometimes the system shows an error like :
> 
> Cannot access central (https://repo.maven.apache.org/maven2) in offline mode and the artifact org.springframework.boot:spring-boot-starter-parent:pom:3.5.6 has not been downloaded from it before. and 'parent.relativePath' points at wrong local POM
> 
> Just run mvn clean install -U . It will update the dependencies.