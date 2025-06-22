# Springboot project setup

1. go to https://start.spring.io/
2. select project (Gradle-groovy/kotlin or Maven)
3. select language (groovy, kotlin, java)
4. select springboot version
5. give project meta data - group, artifact, package names, packaging (jar or war), java version
   1. JAR - Java Archive - standalone applications
   2. WAR - Web Archive - web application
6. add dependencies (eg...)
   1. spring web
   2. spring data jpa
   3. h2 database
7. generate zip
8. extract & import project in IDE

## Understanding Layered Architecture
Users -> Application

Controller -> Service -> Repository -> DB

DTO, Utility, Entity, Config

