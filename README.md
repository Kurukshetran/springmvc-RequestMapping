# springmvc-RequestMapping
Locate an entire class or a particular handler method having @RequestMapping annotation based on mapped URL(s)

##### Purpose : 
Most of the time when we are new to an Web Application based on spring framework, we are left with only one choice for locating either the Controller class or handler method, which is manually searching through the workspace. This project demonstrates how we can use this code in order to locate the handlers just by accessing certain url's are described later.

##### How to Use : 

As demonstrated in this application, we just need to add "RequestMappingController" class to our codebase and make it eligible for spring's component scanning.
Once complete and server is up and running we can use url's as descibed.

###### In order to view all the mapping's in spring context:
<pre><code>http://localhost/SpringRequestMappingDoc/sp/mappingInfo/allMappings

Response :
[{"BeanName":"requestMappingController","DeclaringClass":"com.example.controller.RequestMappingController","MethodName":"getAllMappingInfo","AccessURL":["/mappingInfo/allMappings"]},{"BeanName":"requestMappingController","DeclaringClass":"com.example.controller.RequestMappingController","MethodName":"getSingleMappingInfo","AccessURL":["/mappingInfo/singleMapping"]},...</code></pre>

###### In order to view handler for single url:
<pre><code>http://localhost//SpringRequestMappingDoc/sp/mappingInfo/singleMapping?**path=/samplemethodone**

Response:
[{"BeanName":"sample","DeclaringClass":"com.example.controller.SampleController","MethodName":"sampleMethod1","AccessURL":["/samplemethodone"]}]</code></pre>


##### How it works :

When Spring MVC is configured using <mvc:annotation-driven/> in an xml bean definition file, internally a component called RequestMappingHandlerMapping gets registered with Spring MVC. This component or in general a HandlerMapping component is responsible for routing request URI's to handlers which are the controller methods annotated with @RequestMapping annotation. We use this component in order to provide either all the mappings or single mapping based on the url provided by the user.

