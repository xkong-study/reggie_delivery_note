1.默认的 DispatcherServlet 配置：            

作为中央控制器，负责将请求路由到相应的处理器（Controllers）。       
默认情况下，处理所有请求，映射到/。      

2.默认的静态资源处理：                 
默认情况下，Spring MVC 会让容器的默认 Servlet 处理静态资源请求，如图片、CSS 和 JavaScript 文件，通常映射到/static/、/public/、/resources/和/META-INF/resources/目录下的资源。

3.默认的 ViewResolvers 配置：         
BeanNameViewResolver 和 InternalResourceViewResolver 是默认配置的视图解析器。     
InternalResourceViewResolver 将视图名称解析为 JSP 页面。       

4.默认的 HttpMessageConverters：         
自动配置了一组 HttpMessageConverter 实例，用于支持 JSON、XML 和其他媒体类型的请求/响应体的读写。          

5.默认的异常处理：         
通过@ControllerAdvice和@ExceptionHandler提供全局异常处理机制。           
默认情况下，Spring MVC 配置了DefaultHandlerExceptionResolver，它能处理常见的异常，并将它们映射到相应的 HTTP 状态码。             

6.请求数据绑定：          
自动将请求参数绑定到控制器方法的参数，例如通过@RequestParam、@PathVariable、@RequestBody等注解。            

7.国际化和本地化：       
默认情况下，配置了LocaleResolver和LocaleChangeInterceptor来支持国际化，但通常需要自定义配置以适应特定需求。         
 
8.表单验证：          
支持使用@Valid或@Validated注解对表单输入进行验证，需要配合 JSR-303/JSR-349 Bean Validation API 使用。         

9.内容协商：         
通过请求的 Accept 头或请求参数决定响应的内容类型（如 JSON、XML），默认情况下启用内容协商视图解析。         
