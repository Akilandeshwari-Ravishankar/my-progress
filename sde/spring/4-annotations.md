# Annotations:
## Controller Annotations:
  1. ```Controller``` = user -> server -> dispatcher servlet -> contoller
  2. ```RequestMapping``` = contains path="/.." & method=Request.GET
  3. ```RequestBody``` = method parameter annotated as @RequestBody Employee employee -> pass employee json as request body
  4. ```ResponseBody``` = annotate explicitly to return only data not render ui
  5. ```RestController``` = @Controller + @ResponseBody = return only data rather than rendering ui
  6. ```GetMapping``` = @RequestMapping with method = Request.GET
  7. ```PutMapping``` = @RequestMapping with method = Request.PUT
  8. ```PostMapping``` = @RequestMapping with method = Request.POST
  9. ```DeleteMapping``` = @RequestMapping with method = Request.DELETE
  10. ```PathVariable``` = method parameter annotated with @PathVariable(name = "employeeId") Integer employeeId -> https://localhost:8080/employers/{employeeId}
  11. ```RequestParam``` = method parameter annotated with @RequestBody(name = "id") Integer employeeId -> https://localhost:8080/employers/getEmployee?id=123

## Core Annotations:
Most of them are class level annotations
  1. ```Component``` = spring managed bean -> no need to create/ initialize objects 
  2. ```Service``` = specialization of @Component -> indicates component that handles core business logic
  3. ```Repository``` = specialization of @Component -> indicates component that handles db interaction logic
  4. ```Autowired``` = dependency inject the component for us -> also called field injection/ autowiring
  5. ```Configuration``` = enable many explicit bean creations inside the annotated class. By default proxyBeanMethods & enforceUniqueMethods is true -> all are Singleton beans & no conflicting beans are present in configuration class.
  6. ```ComponentScan``` = annotation through which application finds the beans -> scans for the components/ beans present in the package of ```@SpringBootApplication``` annotated class
     1. ```@ComponentScan``` needs to be used along with ```@Configuration```
     2. ```java
        @ComponentScan(
          basePackages = {"com.example.package1", "com.example.package2"},
          excludeFilters = @ComponentScan.Filter(
            type = FilterType.ASSIGNABLE_TYPE,
            classes = {DeprecatedService.class}
          )
        )
        ```
  7. ```SpringBootApplication``` = @SpringBootConfiguration + @EnableAutoConfiguration + @ComponentScan
  8. ```Primary```
     - use this annotation to the bean to be considered by default while dependency injection when there are multiple beans of same type (ambiguity)
  9. ```Qualifier```
     - use this annotation when we need to inject a particular bean when there are multiple beans of same type (ambiguity)
  10. ```ConditionalOnProperty```
      - bean will be created conditionally
      - ```java
        @ConditionalOnProperty(
          prefix="noSqlConnection",
          value="enabled",
          havingValue="true",
          matchIfMissing=false)
        public class NoSqlConnection() {}
        ```
      - ```
        application.properties
        // bean will be created
        noSqlConnection.enabled=true
        ```
      - ```java
        // inject bean only if conditions match so keeping required to false
        @Autowired(required=false)
        NoSqlConnection noSqlConnection;
        ```
