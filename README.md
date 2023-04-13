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


2) Java Database Connectivity Theory(JDBC)

Database data can be accessed by SQL Query. But from the users perspective we need click a button and data must be fetched. This connectivity between
java app & database is termed as JDBC.
->import the package.
->Load & register the driver(We need to register a driver(name: com.mysql.jdbc.Driver). class.forName(driver_name) helps us to load the driver.
->Establish the connection.(Connecting to the db with the help of url,username and pwd)(DriverManager.getConnection('url','username','pwd')
->Create the statement.(Statement st=con.createStatement();)
->Execute the query. (ResultSet rs = st.executeQuery(SELECT * FROM table_name))(rs.next())->moves the pointer to the first record.)
->Process results.(rs.getInt(1)+" "+rs.getString(2))
->Close connection.(st.close(),con.close())

In DB we have rows & columns whereas in the java world we have objects. How do we store objects in rows & columns?
That's where ORM (Object Relational Mapping) comes in.
We implement this ORM in Java using Hibernate.
JPA(Java Persistance API) is a specification introduced by Sun Microsys in order to maintain some standards.(Hibarnate, TopLink, iBatis)->tools to implement ORM
JPA is helpful when we need to switch between technologies.
It makes use of EntityManagerFactory & EntityManager objects in order to fetch data from database.

EntityManagerFactory emf = Persistance.createEntityManagerFactory("pu");(pu is the persistance unit name in persistence.xml)
EntityManager em = emf.createEntityManager();
Alien a = em.find(alien.class,2);

We need to use @Entity with the class Alien.

Creating record:
->Make object of Alien class.
->ob.setId(9);
->ob.setName(....

em.getTransaction.begin();

em.persist(ob);

em.getTransaction.commit();
SOPln(ob);

If we want to switch between any technology we will only be changing the dependancy.(min changes need to be made).

3) Spring Framework:-

Spring Framework includes technologies like:
Aspect-oriented programming (AOP)
Dependency injection (DI)
Plain Old Java Object (POJO)

IOC Container:

IoC container is one of the core features of Spring that provides a streamlined way to configure and manage Java objects. 
This container is responsible for managing the lifecycle of a defined Java object, significantly increasing the configurability of a Spring-based application.
IoC uses the dependency injection or dependency lookup patterns to provide the object reference during runtime.
Spring provides org.springframework.beans and org.springframework.context packages that can be used to facilitate these functions.

AOP Programming(Aspect-oriented)

 AOP complements object-oriented programming by providing a different way to structure the program, where OOP modularity is based on classes.
 In AOP, the main unit of modularity is an aspect (cross-cutting concern). This enables users to use AOP to create custom aspects.
 AOP breaks the program logic into distinct parts (called concerns). It is used to increase modularity by cross-cutting concerns.

A cross-cutting concern is a concern that can affect the whole application and should be centralized in one location in code as possible, 
such as transaction management, authentication, logging, security etc.

Spring MVC

A Spring MVC provides an elegant solution to use MVC in spring framework by the help of DispatcherServlet. 
Here, DispatcherServlet is a class that receives the incoming request and maps it to the right resource such as controllers, models, and views.
Client --request--> Web.xml --requests-->  Front-Controller(DispatcherServlet) --request--> @Controllers(sends back model & view name)
                                               (...-servlet.xml) 

Model - A model contains the data of the application. A data can be a single object or a collection of objects.
Controller - A controller contains the business logic of an application. Here, the @Controller annotation is used to mark the class as the controller.
View - A view represents the provided information in a particular format. Generally, JSP+JSTL is used to create a view page. Although spring also supports other view technologies such as Apache Velocity, Thymeleaf and FreeMarker.
Front Controller - In Spring Web MVC, the DispatcherServlet class works as the front controller. It is responsible to manage the flow of the Spring MVC application.

Flow:

All the incoming request is intercepted by the DispatcherServlet that works as the front controller.
The DispatcherServlet gets an entry of handler mapping from the XML file and forwards the request to the controller.
The controller returns an object of ModelAndView.
The DispatcherServlet checks the entry of view resolver in the XML file and invokes the specified view component.



Load the spring jar files or add dependencies in the case of Maven
Create the controller class
Provide the entry of controller in the web.xml file
Define the bean in the separate XML file
Display the message in the JSP page
Start the server and deploy the project.

4) Solid Design Principles

Single Responsibility Principle (SRP)

The single responsibility principle states that every Java class must perform a single functionality. 
Implementation of multiple functionalities in a single class mashup the code and if any modification is required may affect the whole class.

Open-Closed Principle (OCP)

The open-closed principle states that according to new requirements the module should be open for extension but closed for modification. 
Eg:-public class VehicleInfo   
{  
public double vehicleNumber()   
{  
//functionality   
}  
}  
public class Car extends VehicleInfo   
{  
public double vehicleNumber()   
{  
return this.getValue();  
}  
public class Car extends Truck   
{  
public double vehicleNumber()   
{  
return this.getValue();  
}  


Liskov Substitution Principle (LSP)

It applies to inheritance in such a way that the derived classes must be completely substitutable for their base classes.
In other words, if class A is a subtype of class B, then we should be able to replace B with A without interrupting the behavior of the program.

Interface Segregation Principle (ISP)

The principle states that the larger interfaces split into smaller ones. Because the implementation classes use only the methods that are required. 
We should not force the client to use the methods that they do not want to use.


Dependency Inversion Principle (DIP)

The principle states that we must use abstraction (abstract classes and interfaces) instead of concrete implementations.

5) DTO(Data Transfer Objects)

DTO->An object that carries data between processes in order to reduce the number of method calls.
It is basically used to pass data with multiple attributes in one shot from client to server, to avoid multiple calls to a remote server.
Another advantage of using DTOs on RESTful APIs written in Java (and on Spring Boot), is that they can help to hide implementation details of domain objects (JPA entities). 
Exposing entities through endpoints can become a security issue if we do not carefully handle what properties can be changed through what operations.

ModelMapper determines how an object model maps to another.

Custom Exception Handling:-

Rest Controller Advice’s methods (annotated with @ExceptionHandler) are shared globally across multiple @Controller components to capture exceptions and translate them to HTTP responses. 
The @ExceptionHandler annotation indicates which type of Exception we want to handle. 
The exception instance and the request will be injected via method arguments.

By using two annotations together, we can:

control the body of the response along with status code
handle several exceptions in the same method

Validation:
Java Bean is validated using JSR380(a specification for the Java API for bean validation)
Properties of Bean must meet a criteria
Annotation like @Notnull, @Min, @Size etc. are used.
->Adding dependancy
->Apply annotations in your bean
->Enable the annotations from controller.

6) MyProject related

CSRF->Cross site request forgery->csrf.disable()
CORS->Cross origin Resource sharing->@CrossOrigin


->Created the "roles" entity and joined it with the users table using "id".
->User should login with the help of username(email -> findByEmail) and password.(Loading the user with the help of username in CustomUserDetailService)
->Password has been encrypted and stored in DB using BCryptPasswordEncoder();
->Implementing JWT(JSON Web Token)
->Used to secure REST APIs(Communication between client & server securely)
->It is a stateless authentication mechanism.(way to verify users by having much of session information such as user properties. It is also termed as token based authentication)

JWT is composed of 3 parts:
Header->Alg+token type
Payload->Data about the user
verify Signature->Encoded header+Encoded payload+key

Client -(request)(Sends Data)-> Server(Spring Boot Rest API)(validates)
Server sends a token back which needs to be stored and used for access to various APIs.(Token which is generated during login is used during the entire session)

->Injecting the dependancy(io.jsonwebtoken)
->Create JWTAuthenticationEntryPoint which implements Authentication entry point.
->Create JWTTokenHelper(Generation & Token Validator)
->JwtAuthenticationFilter extends OnceRequestFilter
  Get the jwt token from request.
  Validate token
  Get user from token.
  Load user assossiated with the token.
  Set spring security(setting authentication)
->Create JwtAuthResponse(store the response)
->Configure JWT in spring security config.
->Create login api to return token.
->Test the application.

Bearer Token->This is a single string which acts as the authentication of the API request, sent in an HTTP “Authorization” header. 
              Bearer tokens are a much simpler way of making API requests, since they don’t require cryptographic signing of each request.
              Sites that use the format are most likely implementing OAuth 2.0 bearer tokens.
			  The OAuth 2.0 Authorization Framework sets a number of other requirements to keep authorization secure, for instance requiring the use of HTTPS/TLS.			  
			  
			  
OncePerrequest: we might want to ensure that a specific filter is invoked only once per request. A common use case is when working with Spring Security. 
When a request goes through the filter chain, we might want some of the authentication actions to happen only once for the request.
We can extend the OncePerRequestFilter in such situations. Spring guarantees that the OncePerRequestFilter is executed only once for a given request.

HS512: The JWT specification supports several algorithms for cryptographic signing. 

Claims: It is an interface where we have several functions are defined.For eg:getSubhect, getExpiration

<T>:The special 'T' operator can be used to specify an instance of java.lang.Class (the 'type'). 
Static methods are invoked using this operator as well. 
	
7) Writing to CSV File:

The getConnection(String url) method of Java DriverManager class attempts to establish a connection to the database by using the given database URL. 
The appropriate driver from the set of registered JDBC drivers is selected.

PrintWriter:

The PrintWriter class of the java.io package can be used to write output data in a commonly readable form (text).
It extends the abstract class Writer.
We have created a print writer that will write data to the file represented by the FileWriter.
autoFlush is an optional parameter that specifies whether to perform auto flushing or not.

.getMetaData:

The metadata means data about data i.e. we can get further information from the data.
If you have to get metadata of a table like total number of column, column name, column type etc. , ResultSetMetaData interface is useful because 
it provides methods to get metadata from the ResultSet object.
	
8) Singleton
	
Create a static instance or object of the class.

Create a private constructor so that no other instance of the class can be created from elsewhere.

Create a public static method of getInstance which returns the static obj.

Firstly we won't be able the create another instance/object of that class due to the private constructor and secondly, the only way to get the object of that class 
is by calling the getInstance method.(className.methodName);


Singleton: Only 1 instance in JVM;
No matter how many times we call the function it always gives the same instance.

For eg:
If we want to take arguments we should not use singleton design pattern.
Also, for unit testing purposes it would be difficult since no instance variables, references are created in case of singleton.

Static Variables: Static variable is shared by all the objects.
                    There is only one copy of them in the main memory.  
				   (We will have a common variable shared by all the objects). 
				   Static variables must be called with their class_name and not with any object.
				   
Mutual Exclusion: It means that only one thread or process can execute a block of code (critical section) at a time.
Visibility: It means that changes made by one thread to shared data are visible to other threads.
Java’s synchronized keyword guarantees both mutual exclusion and visibility. 
If we make the blocks of threads that modify the value of the shared variable synchronized only one thread can enter the block and changes made by it will be reflected in the main memory. 
All other threads trying to enter the block at the same time will be blocked and put to sleep. 

In some cases, we may only desire visibility and not atomicity. 
The use of synchronized in such a situation is overkill and may cause scalability problems. 
Here volatile comes to the rescue. Volatile variables have the visibility features of synchronized but not the atomicity features. 
The values of the volatile variable will never be cached and all writes and reads will be done to and from the main memory. 
However, the use of volatile is limited to a very restricted set of cases as most of the times atomicity is desired.
