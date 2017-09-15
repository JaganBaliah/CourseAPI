Download Spring STS and extract the archive
===========================================
C:\Software Downloads\SpringSTS\sts-bundle\sts-3.8.3.RELEASE

Right click -> New -> Maven project - Skip architype selection

Group Id 	: io.jagan.springbootquickstart
Artiface Id : course-api
Version 	: 0.0.1 SNAPSHOT
Name 		: Course API

Add the below entries onto pom.xml
==================================
  <parent>
  	<groupId>org.springframework.boot</groupId>
  	<artifactId>spring-boot-starter-parent</artifactId>
  	<version>1.5.2.RELEASE</version>
  </parent>
  
  <dependencies>
  	<dependency>
  		<groupId>org.springframework.boot</groupId>
  		<artifactId>spring-boot-starter-web</artifactId>
  	</dependency>
  </dependencies>
  
  <properties>
  	<java.version>1.8</java.version>
  </properties>
  

What is Spring Boot?
====================
It makes it easy to create stand alone, production-grade Spring based applications that you can just run.
In short, it is bootstraping a spring application from scratch. 


Three ways of using Spring Boot
===============================

1. Above is a classic way for using Spring boot. 
Instead we can use New -> Spring Starter Project to automate most of the things done above

2. Another way is to use Spring Boot CLI
Goto below website and download zip file
https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started-installing-spring-boot.html   

Unzip the file "spring-boot-cli-1.5.2.RELEASE-bin.zip" and goto "bin" directory
Create a new "app.groovy" file and put the below contents in it:
	@RestController
	class AppCtrl {
		@RequestMapping("/")
		String app() {
			"Hello world"
		}
	}
In the command line, execute spring boot as shown below:
> spring run app.groovy

This will run the application and access http://localhost:8080/ to see "Hello world" being printed

3. Another way is to use Spring Initializr
Goto spring.io and head to Spring initializr

Group 		: io.jagan.springbootquickstart
Artifact 	: course-si-api
Description : Course SI API
Selected Dependencies : Web

Generate Project to get the zip file and then extract the zip file
Import -> Existing Maven Projects -> Provide the above extracted directory
Run the application as stand alone application and access http://localhost:8080/

Using application.properties
============================
  
For e.g., if the port on which container can be accessed need to be changed from 8080 to some other port,
then create application.properties in resource directory and include the below entry

-> server.port=8081  
  
  
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

@RestController for the class
@RequestMapping for the method with the url mapping information - @RequestMapping(name="/topics")


Resources for Topics:

	GET	/topics		Gets all topics
	GET	/topics/id	Gets the topic
	POST	/topics		Create new topic
	PUT	/topics/id	Updates the topic
	DELETE	/topics/id	Deletes the topic

Topic
	id
	name
	description

TopicController

	@RestController
	public class TopicController {

		@Autowired
		private TopicService topicService;

			GET		/topics		Gets all topics
			@RequestMapping(value="/topics")
				
			GET		/topics/id	Gets the topic
			@RequestMapping(value="/topics/{id}")
			public Topic getTopic(@PathVariable String id) {
				
			POST	/topics		Create new topic
			@RequestMapping(method=RequestMethod.POST, value="/topics")
			public void addTopic(@RequestBody Topic topic) {
			
			PUT		/topics/id	Updates the topic
			@RequestMapping(method=RequestMethod.PUT, value="/topics/{id}")
			public void updateTopic(@RequestBody Topic topic, @PathVariable String id) {
				
			DELETE	/topics/id	Deletes the topic
			@RequestMapping(method=RequestMethod.DELETE, value="/topics/{id}")
			public void deleteTopic(@PathVariable String id)


TopicService
	Provide all necessary methods
		

