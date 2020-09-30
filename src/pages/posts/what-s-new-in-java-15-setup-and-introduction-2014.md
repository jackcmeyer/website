---
title: 'What''s new in Java 15: Setup and Introduction'
date: '2020-09-30T22:23:10.723Z'
excerpt: >-
  Java 15 reached General Availability on September 15, 2020. In this Java
  release, there were many new...
thumb_img_path: null
comments_count: 0
positive_reactions_count: 0
tags:
  - java
  - springboot
  - tutorial
canonical_url: 'https://dev.to/jackcmeyer/what-s-new-in-java-15-setup-and-introduction-2014'
template: post
---
Java 15 reached General Availability on September 15, 2020. In this Java release, there were many new language features that will improve the developer experience. In this series of blog posts, we will learn how to install Java 15, use it with our IDE, explore the new language features, and refactor existing code to make use of the new language features. 

## Installing Java 15
### macOS
On a macOS, the easiest way to install Java 15 is with [Brew](https://brew.sh/), a popular package manager for macOS. 

After installing Brew, open your favorite terminal and run the command: 


```sh
brew cask install adoptopenjdk15
```


To check if Java 15 was successfully installed, open your favorite terminal, and run the command:

```sh
java --version
```


The output should look like: 

```sh
$ java --version
openjdk 15 2020-09-15
OpenJDK Runtime Environment AdoptOpenJDK (build 15+36)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 15+36, mixed mode, sharing)
```


### Windows
To install OpenJDK 15 on Windows, first download the [OpenJDK 15 zip file](https://download.java.net/java/GA/jdk15/779bf45e88a44cbd9ea6621d33e33db1/36/GPL/openjdk-15_windows-x64_bin.zip).

Once the zip is finished downloading, extract the zip file to some location on your computer. 

After the zip is extracted, update your system's 
`JAVA_HOME`
 and 
`PATH`
 variables to point to OpenJDK 15 folder. 


```
JAVA_HOME=C:\path\to\jdk-15
PATH=...%JAVA_HOME%\bin;...
```


To check if Java 15 was successfully installed, restart the terminal, and then once it is restarted run the command:

```sh
java --version
```


The output should look like: 

```sh
$ java --version
openjdk 15 2020-09-15
OpenJDK Runtime Environment AdoptOpenJDK (build 15+36)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 15+36, mixed mode, sharing)
```


## Setting up the IDE
Once OpenJDK 15 has been installed, now it is time to configure the IDE to recognize and execute applications using Java 15. 

### IntelliJ
To start configuring Java 15 for a project in IntelliJ, open up or create a new Java project. 

Once the project is opened, navigate to 
`File -> Project Structure`
. This will open up the Project Structure window. In this window, make sure that the Language Level is set to "15 (Preview)".

## Spring Boot
[Spring Boot 2.4.0 M1](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.4.0-M1-Release-Notes# preliminary-support-for-jdk-15) added support for Java 15 language features. 

To try out Java 15, with a Spring Boot app, first go out to [Spring Initializr](https://start.spring.io/) and create a new project. To follow along with this blog series, the following dependencies are needed: 
- Spring Boot 2.4.0 (M3)
- Spring Web
- Spring Data JPA
- Validation
- Lombok 
- H2 Database

To quickly get started, use this [link](https://start.spring.io/# !type=maven-project&language=java&platformVersion=2.4.0.M3&packaging=jar&jvmVersion=15&groupId=com.jackcmeyer&artifactId=java15demo&name=java15demo&description=Demo%20application%20&packageName=com.jackcmeyer.java15demo&dependencies=validation,lombok,data-jpa,h2,web). This link pre-loads a configuration with the above dependencies on Spring Initializr.

Once the project is imported into some IDE, make sure that the 
`pom.xml`
 is configured properly to use Java 15 code. The two important pieces are the 
`java.version`
 and 
`maven-compiler-plugin`
 configurations. 

The 
`java.version`
 value should be 15. 

```xml
<project>
   ...
   <properties>
        ...
        <java.version>15</java.version>
        ...
    </properties>
    ...
</project>
```


The 
`maven-compiler-plugin`
 should have a source version value of 15, a target version value of 15, and enable preview options. 

```xml
<project>
    ...
    <build>
		<plugins>
			...
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<configuration>
					<source>15</source>
					<target>15</target>
					<compilerArgs>--enable-preview</compilerArgs>
				</configuration>
			</plugin>
            ...
		</plugins>
	</build>
    ...
</project>
```


## Conclusion
In this post we learned how to download Java 15, tell our IDE to use Java 15 language features, and how to use Spring Boot and Java 15. An example Spring Boot application can be found on my [GitHub profile](https://github.com/jackcmeyer/java15demo/tree/60fd072f55acad4f083abe0b0801a0e488f10c06).

*[This post is also available on DEV.](https://dev.to/jackcmeyer/what-s-new-in-java-15-setup-and-introduction-2014)*


<script>
const parent = document.getElementsByTagName('head')[0];
const script = document.createElement('script');
script.type = 'text/javascript';
script.src = 'https://cdnjs.cloudflare.com/ajax/libs/iframe-resizer/4.1.1/iframeResizer.min.js';
script.charset = 'utf-8';
script.onload = function() {
    window.iFrameResize({}, '.liquidTag');
};
parent.appendChild(script);
</script>    
