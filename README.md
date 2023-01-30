# Marat Nizamov's test task

Recently, I was asked to do a test task that involved setting up a local environment for application development and deployment. The objective was to create a continuous integration and continuous delivery (CI/CD) pipeline to automate the process of building and deploying a Spring Boot application to a Kubernetes cluster.

The first step was to install Minikube, a local Kubernetes cluster, on my machine. After this, I installed Jenkins, an open-source automation server, and configured it to work with the Minikube cluster. This allowed Jenkins to access the cluster and build Docker images. Check ```Dockerfile``` for details.

Next, I chose a simple Spring Boot application and added the Spring Boot Actuator to it. Most configuration was done in ```POM.xml```. This gave the application several production-ready features such as health and metrics endpoints.

To create the CI/CD pipeline, I used Jenkins to automate the process of building a Docker image of the application using Maven, pushing the image to Docker Hub, and deploying it to the Minikube cluster. The pipeline was defined in a ```Jenkinsfile``` located in my repository. K8s deploy manifest is ```deploymentservice.yaml```

Finally, I added readiness and liveness probes to the endpoints of the Spring Boot Actuator. These probes ensured that the application was healthy and available to handle incoming requests.

In conclusion, the project was a success and I was able to successfully create a CI/CD pipeline for a Spring Boot application using Minikube and Jenkins. The pipeline ensured that the application was built and deployed in an efficient and automated manner.

# Below you may find an info about application:

**A simple Spring Boot app to send hello world message to a user**

## How to Run Application

**Start the application using any of the commands mentioned below**

> **Note:** First two commands need to run inside the root folder of this project i.e inside the **spring-boot-hello-world** folder


- **Using maven** <br/>``` mvn spring-boot:run```


- **From jar file**
  Create a jar file using '**mvn clean install**' command and then execute
  <br/>```java -jar target/spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar```


- **Directly from IDE**
  <br/>```Right click on HelloWorldApplication.java and click on 'Run' option```
  <br/><br/>

> **Note:** By default spring boot application starts on port number 8080. If port 8080 is occupied in your system then you can change the port number by uncommenting and updating the **server.port** property inside the **application.properties** file that is available inside the **src > main > resources** folder.

<br/>

**Send an HTTP GET request to '/hello' endpoint using any of the two methods**

- **Browser or REST client**
  <br/>```http://localhost:8080/hello```


- **cURL**
  <br/>```curl --request GET 'http://localhost:8080/hello'```


## How to Run Unit Test Cases

**Run the test cases using any of the commands mentioned below**

> **Note:** These commands need to run inside the root folder of this project i.e inside the **spring-boot-hello-world** folder

- **To run all the test cases**
  <br/>```mvn test```


- **To run a particular test class**
  <br/>```mvn -Dtest=HelloWorldControllerTest test```
  <br/>or
  <br/>```mvn -Dtest=HelloWorldApplicationTests test```