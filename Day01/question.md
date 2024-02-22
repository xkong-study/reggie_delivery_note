### Map map = new HashMap();
Map是一个接口，HashMap是具体的实现类。   
由于接口是类的蓝图，是一个抽象的概念，不能被实例化，因此接口需要由具体的类来实现。    
这条代码指明：由HashMap类来实现接口Map中描述的方法。   
HashMap map = new HashMap();    
声明一个HashMap类型的map，由HashMap类实现。   
为什么更推荐第一种用接口的声明方式？   
这个问题等同于为什么要在编程中使用接口，而不是直接使用实现类。其实这就是面对对象编程 (OOP）的思想精髓。简单来说就是上层接口描述的功能不变，下层的具体实现可以不断修改替换。上层的调用者只用知道map的功能，不必关心map的具体实现。     
例如，某天开发人员开发出一个各方面性能都优于Hashap的SuperMap类，则map可以直接改成由SuperMap来实现：Map map =newSuperMap0。对于外部调用者来说，使用的还是那个map，殊不知底层实现的升级已经让他们用上了优化版的map。如果一开始就定义map为Has Map类型，无法做出这样的优化，很明显 Hashap map =new SuperMap() 是条错误的代码。这就是使用接口声明的好处，增加系统灵活性，隔离性等。      

### 泛型（Generics）    
定义泛型方法： 使用 <T> 表示泛型类型参数，可以在方法签名中定义一个或多个泛型类型。    
泛型类： 类似地，你可以定义包含泛型类型参数的泛型类。      

### static 关键字    
静态方法： 使用 static 关键字声明一个方法为静态方法，它属于类而不是类的实例。   
无需实例化： 静态方法可以通过类名直接调用，而不需要先创建类的实例。   
全局可用： 静态方法可以在任何地方直接调用，因为它们属于类级别而不是实例级别。   
共享资源： 静态方法适用于不依赖于特定实例状态的操作，可以减少资源的使用。   

```code
public static <T> R<T> success(T object) {
    R<T> r = new R<>();  // 创建泛型类型为 T 的响应对象
    r.data = object;     // 设置响应对象的数据
    r.code = 1;          // 设置响应对象的代码
    return r;            // 返回成功的响应对象
}
```
<T>：定义泛型方法，表示该方法可以接受任意类型的对象。    
R<T>：返回类型，表示返回一个包含类型为 T 的数据的 R 对象。    
static：方法是静态的，可以通过类名直接调用。   
R<>：创建泛型类的实例，泛型类型由方法的类型参数 T 提供。   
成功响应：将传入的对象设置为响应数据，将响应码设置为1，最后返回包含成功信息的响应对象。  

### HttpServletRequest 
是 Java Servlet 规范中定义的接口，用于表示客户端发起的 HTTP 请求。它提供了许多方法，允许开发人员获取有关客户端请求的信息，如请求参数、头部信息、会话信息等。    

在Java的Web开发中，当用户通过浏览器访问网页时，浏览器会向服务器发送HTTP请求。服务器端的Servlet可以通过接收 HttpServletRequest 对象来获取关于这个HTTP请求的各种信息。这个对象包含了请求的各种属性和数据。      

例如，通过 HttpServletRequest 对象，你可以获取：      

请求的参数（GET或POST请求中的参数）    
请求的头部信息     
请求的URI（Uniform Resource Identifier）     
请求的方法（GET、POST等）    
客户端的IP地址    
请求的会话信息等     
在Servlet中，HttpServletRequest 对象通常作为方法的参数，通过容器（如Tomcat）自动传递给Servlet的相应方法（如 doGet() 或 doPost()）。    

### removeById(id)方法通常用于根据主键删除一条记录    
在典型的Java持久层框架中，比如MyBatis或者Hibernate，removeById(id)方法通常用于根据主键（通常是数据库表的主键）删除一条记录。这里的id是主键的值，而不是索引。

数据库表通常有一个主键列，它的作用是唯一标识表中的每一条记录。使用removeById(id)方法，你告诉持久层框架通过主键找到并删除对应的记录。

### 主键是一种约束，用于唯一标识表中的每一行，而索引是一种用于提高查询性能的数据结构。

### 子类实例不能直接访问父类中非静态的方法，而应该通过子类覆盖的方式来调用。

### 我之前学到的知识是service是通过mapper层来访问数据，mapper通过实体类进行增删改查的可是IService<Entity>打破了我的认知，他这个不就是直接操作实体类了吗

我理解你的困惑。在Spring框架中，尤其是当结合MyBatis或类似的ORM（对象关系映射）框架时，确实存在这样的层次结构和分工：

Mapper层（或DAO层）：负责定义与数据库交互的方法。在MyBatis中，这些方法通常直接映射到SQL语句。

Service层：负责实现业务逻辑。这一层调用Mapper层的方法来访问或修改数据。

IService<Entity> 可能看起来好像是直接操作实体类，但实际上这只是抽象层面的。IService<Entity> 通常定义了操作特定实体的通用业务逻辑接口，比如增加、删除、更新和获取实体的方法。然而，这些方法的实现通常会在Service层的实现类中，这个实现类会调用Mapper层来执行实际的数据库操作。

在 IService<Entity> 接口的实现类中，你会看到实体类 Entity 是如何被操作的。这个操作不是直接发生的，而是通过调用Mapper层的方法来间接完成的。所以，即使 IService<Entity> 看起来像是直接操作实体类，它背后的实现仍然依赖于Mapper层来与数据库进行交互。

这里的关键是区分接口定义和接口实现：

接口定义（IService<Entity>）：定义了一组操作实体的抽象方法，没有具体实现。

接口实现（比如DishServiceImpl）：提供了具体的业务逻辑，并通过Mapper层来实现接口定义中的抽象方法。

### 两个疑惑
```code
public interface CategoryService extends IService<Category>
@Autowired
    private CategoryService categoryService;
categoryService.save(category);
```
我有两个疑惑：
1.为什么接口可以直接声明categoryService对象？
2.为什么categoryService可以直接调用方法不需要new对象？


@Autowired 注解是用于依赖注入的。当你在一个类中使用 @Autowired 注解标记一个字段时，Spring 容器会尝试为这个字段注入一个合适的实例。这个实例通常是一个实现了该字段类型的类的实例。

如果你的接口有一个或多个实现类，并且这些实现类被Spring容器托管（例如使用 @Service、@Component 或其他注解标记），那么 Spring 就能够根据需要的接口类型自动注入合适的实现类。

例如，假设有一个 CategoryService 接口和一个名为 CategoryServiceImpl 的实现类:

```code
public interface CategoryService {
    void save(Category category);
}

@Service
public class CategoryServiceImpl implements CategoryService {
    @Override
    public void save(Category category) {
        // 实现具体的保存逻辑
    }
}
```

然后在其他类中，使用 @Autowired 注解注入 CategoryService:

```code
@Autowired
private CategoryService categoryService;
```
在运行时，Spring 会通过反射和动态代理等技术创建一个 CategoryServiceImpl 的实例，并将其注入到 categoryService 字段中。这样，你就可以通过 categoryService 对象调用 save 方法。

总体来说，虽然接口本身不能被直接实例化，但通过 Spring 的依赖注入机制，你可以方便地使用接口类型的字段，并让 Spring 在运行时为其提供具体的实现。这种实现背后涉及到 Spring 容器的管理和创建对象的机制。
