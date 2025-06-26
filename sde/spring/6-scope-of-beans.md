# Scope of Spring Bean
Spring Bean Scopes are of 4 types:
1. Singleton
2. Prototype
3. Request
4. Session
   
## Singleton
- Default scope
- Eager Initialization
- Bean object once created during application startup will be used everywhere
- ```@Scope("singleton")``` class level annotation or along with ```@Bean``` annotation in ```@Configuration``` class

## Prototype
- New object created each time
- Lazy initialized - created when needed
- ```@Scope("prototype")```

## Request
- One bean per HTTP request
- Lazy initialized - created when needed
- ```@Scope("request")```
- request scoped bean cannot be injected into a singleton scoped bean. To do so, we need to create a proxy
  - ```@Scope(value="request", proxyMode=ProxyMode.TARGET_CLASS)```

## Session
- One bean/object per http session
- Lazy initialized - created when needed
- ```@Scope("request")```
- When a user access api, session is created
- A session can have multiple requests
- Remains active till session is expired

