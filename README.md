Annotations

RestController is used for making restful web services with the help of the @RestController annotation. 
This annotation is used at the class level and allows the class to handle the requests made by the client.
The main difference between the @restcontroller and the @controller is that the @restcontroller combination of the @controller and @ResponseBody annotation.


@Service: It is also used at class level. It tells the Spring that class contains the business logic.

@Component: It is a class-level annotation. It is used to mark a Java class as a bean. 
            A Java class annotated with @Component is found during the classpath. 
			The Spring Framework pick it up and configure it in the application context as a Spring Bean.
			
@Controller: The @Controller is a class-level annotation. It is a specialization of @Component. It marks a class as a web request handler. 
             It is often used to serve web pages. By default, it returns a string that indicates which route to redirect. 
			 It is mostly used with @RequestMapping annotation.
			 
@GetMapping: It maps the HTTP GET requests on the specific handler method. It is used to create a web service endpoint that fetches It is used instead of using: @RequestMapping(method = RequestMethod.GET)
@PostMapping: It maps the HTTP POST requests on the specific handler method. It is used to create a web service endpoint that creates It is used instead of using: @RequestMapping(method = RequestMethod.POST)
@PutMapping: It maps the HTTP PUT requests on the specific handler method. It is used to create a web service endpoint that creates or updates It is used instead of using: @RequestMapping(method = RequestMethod.PUT)
@DeleteMapping: It maps the HTTP DELETE requests on the specific handler method. It is used to create a web service endpoint that deletes a resource. It is used instead of using: @RequestMapping(method = RequestMethod.DELETE)
@PatchMapping: It maps the HTTP PATCH requests on the specific handler method. It is used instead of using: @RequestMapping(method = RequestMethod.PATCH)
@RequestBody: It is used to bind HTTP request with an object in a method parameter. Internally it uses HTTP MessageConverters to convert the body of the request. When we annotate a method parameter with @RequestBody, the Spring framework binds the incoming HTTP request body to that parameter.
@ResponseBody: It binds the method return value to the response body. It tells the Spring Boot Framework to serialize a return an object into JSON and XML format.
@PathVariable: It is used to extract the values from the URI. It is most suitable for the RESTful web service, where the URL contains a path variable. We can define multiple @PathVariable in a method.
@RequestParam: It is used to extract the query parameters form the URL. It is also known as a query parameter. It is most suitable for web applications. It can specify default values if the query parameter is not present in the URL.
@RequestHeader: It is used to get the details about the HTTP request headers. We use this annotation as a method parameter. The optional elements of the annotation are name, required, value, defaultValue. For each detail in the header, we should specify separate annotations. We can use it multiple time in a method
@RestController: It can be considered as a combination of @Controller and @ResponseBody annotations. The @RestController annotation is itself annotated with the @ResponseBody annotation. It eliminates the need for annotating each method with @ResponseBody.
@RequestAttribute: It binds a method parameter to request attribute. It provides convenient access to the request attributes from a controller method. With the help of @RequestAttribute annotation, we can access objects that are populated on the server-side.

We make Presentation Layer(Controllers) -> Service Layers -> DOU(Repo Layer) -> Database

We are using interface and implementation class so that there is lose coupling
(For eg: If we want a change in the business logic we need to make changes only in the implementation class)

@Autowired: It automatically creates an object for the implementation class of the interface and injects it in the variable declared.
            It cannot be used to inject primitive and string values.
			In one class if we inject the object of some other class then we use Autowire.
The IoC container constructs an object of the selected class and also injects all the dependency objects via a constructor, a property, or a function at execution time and disposes it at a suitable time. 
This approach helps to create and manage objects manually.

What happens in interface: Run time polymorphism happens and it calls the body of its child class.
