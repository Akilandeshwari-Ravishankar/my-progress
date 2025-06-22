# Spring beans & its lifecycle

## What is a Bean?

Bean is a Java Object (POJO) managed by Spring IoC Container.

POJO = Plain Old Java Object

## How spring finds the beans?
- using @ComponentScan
- using @Bean
  
## When do beans get created/ initialized?
Beans get created during
- Eager initialization
   - start of the application
   - beans with Singleton scope    
- Lazy initialization
   - when needed
   - @Bean with Scope as prototype or request or session
   - @Lazy annotation

## What is Spring IoC Container?
IoC Container is where all beans are managed along with all dependencies of the beans. It is where bean creation, bean injection, bean deletion is managed. It is basically where lifecycle of beans are managed.
- contains all beans
- manages them

## What is Application Context & BeanFactory?
Application Context & BeanFactory are the implementations of Spring IoC Container.

## How to create beans?
Beans can be created in 2 ways:
- @Component -> uses default constructor to create bean
- @Configuration & @Bean

## How to check if beans are present in application?
1. Using actuators
   1. add dependency spring-boot-starter-actuator in pom.xml
   2. add management.endpoints.web.exposure.include=* which exposes all actuator endpoints
   3. hit https://localhost:8080/actuator/beans which lists down all the beans
3. Using object of application context
   1. ConfigurableApplicationContext applicationContext = SpringApplication.run(EcomApplication.class, args);
   2. applicationContext.getBean("beanName");

## Lifecycle of beans
![image](https://github.com/user-attachments/assets/e445d2ce-defe-46f8-97e7-b35ac3615c25)


