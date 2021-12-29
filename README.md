# SpringProfile
Sample spring project using Spring Profiles, automation Test and deploy in Cloud, through Docker image. 

# Steps for Configuration Docker image. 

## 1- Create a sample file "Dockerfile" and need to pass the parameters bellow

* FROM openjdk:8-jdk-alpine

* RUN addgroup -S spring && adduser -S spring -G spring

* USER spring:spring

* ARG JAR_FILE=target/*.jar

* COPY ${JAR_FILE} app.jar

* ENTRYPOINT ["java","-Xmx512m","-Dserver.port=${PORT}","-jar","/app.jar"]

* Xmx512m this values is important if you use the free version, for limited memory when do deploy heroku cloud

## 2- Follow the steps to create a docker image for the project, don't forget to create a docker image the project need to be .jar application and not .war 
## 2.1 - Create Docker Images

### Execute 

* "docker build -t image/name ." this step creates a Docker image, need space between final name image and dot ".", because need get root directory

* "docker image list" for confirmed if the create image

## 3 - Create a Docker Container

* "docker run imagem/name" this step need to pass some configurations for the enviroments variables. 

### Example: 

* -p 8080:8080 -e NAME_DATABASE_URL='jdbc:he:mem:name-project' -e NAME_DATABASE_USERNAME='sa' -e NAME_DATABASE_PASSWORD='' -e NAME_JWT_SECRET='123456'.

after to pass the enviroments variables go to docker and execute the command bellow. 

* docker run -p 8080:8080 -e NAME_DATABASE_URL='jdbc:he:mem:name-project' -e NAME_DATABASE_USERNAME='sa' -e NAME_DATABASE_PASSWORD='' -e NAME_JWT_SECRET='123456' image/name





# spring-profile
