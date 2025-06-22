# Spring beans & Application Context

## What is a Bean?

Bean is a Java Object (POJO) managed by spring application.

POJO = Plain Old Java Object

## What is Spring IoC Container?
IoC Container is where all beans are managed along with all dependencies of the beans. It is where bean creation, bean injection, bean deletion is managed. It is basically where lifecycle of beans are managed.

## What is Application Context?
Application Context is the implementation of Spring IoC Container.

## How to create beans?
Beans can be created in 2 ways:
- @Component
- @Configuration & @Bean

## How to check if beans are present in application?
1. Using actuators
   1. add dependency spring-boot-starter-actuator in pom.xml
   2. add management.endpoints.web.exposure.include=* which exposes all actuator endpoints
   3. hit https://localhost:8080/actuator/beans which lists down all the beans
3. Using object of application context
   1. ConfigurableApplicationContext applicationContext = SpringApplication.run(EcomApplication.class, args);
   2. applicationContext.getBean("beanName");
