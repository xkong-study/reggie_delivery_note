## 注解：
将普通java类变成请求处理类(@RestController),将普通java类变成数据类(@Data),将普通方法变成请求方法（@PostMapping）,将普通的对象变为 Spring 管理的 Bean(@Component 或其派生注解如 @Service、@Repository、@Controller 等）,
,@Autowired帮助字段、构造方法、Setter 方法等告诉 Spring 容器在进行依赖注入时自动寻找匹配类型的 Bean。 将普通的 Java 类变成一个过滤器（Filter），并交由 Servlet 容器（如Tomcat、Jetty等）进行管理。  

![Screenshot 2024-02-15 at 14.06.35.png](https://img.xwyue.com/i/2024/02/15/65ce1a7350ae3.png)

![Screenshot 2024-02-15 at 14.11.34.png](https://img.xwyue.com/i/2024/02/15/65ce1b9fd9ae1.png)

![Screenshot 2024-02-15 at 14.16.11.png](https://img.xwyue.com/i/2024/02/15/65ce1cb36a6c4.png)

![Screenshot 2024-02-15 at 14.31.14.png](https://img.xwyue.com/i/2024/02/15/65ce203f2dd97.png)

Spring Boot 是一个基于 Java 的开发框架，它通常使用内嵌的 Servlet 容器来运行 Web 应用程序。默认情况下，Spring Boot 使用 Apache Tomcat 作为其内嵌的 Servlet 容器。      

Spring Boot 支持多种内嵌的 Servlet 容器，包括但不限于：    

Tomcat   
Jetty   
Undertow   

#### @Value
@Value 注解是Spring框架中用于从配置文件中读取值的注解，通常用于将配置文件中的属性值注入到Java类的字段或方法参数中。在这里，${Reggie.path} 表示从配置文件中获取名为 Reggie.path 的属性值。
