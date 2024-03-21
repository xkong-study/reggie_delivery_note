Spring Data JPA 方法命名约定的关键字及其含义：   
find…By, read…By, query…By, get…By：启动查询的基本关键字。你可以使用这些关键字中的任意一个开始你的方法名，Spring Data JPA 将生成一个基于方法名指定条件的查询。  
Count…By：返回符合条件的实体数量。    
Delete…By, remove…By：删除符合条件的实体。使用这些操作需要谨慎，因为它们会直接影响数据库。   
…OrderBy…：添加排序条件。例如，findByUsernameOrderByLastNameAsc 会根据 username 查找用户，并按 lastName 升序排序。    
And、Or：链接多个条件。例如，findByNameOrAge 会查找匹配指定 name 或 age 的实体。   
Between：查找某个范围内的实体，例如 findByAgeBetween。   
LessThan、GreaterThan：查找小于或大于指定值的实体。   
IsNull、IsNotNull、NotNull：查找属性值为 null 或非 null 的实体。   
Like、NotLike：查找属性值匹配或不匹配指定模式的实体。  
StartingWith、EndingWith、Containing：查找属性值以指定字符串开始、结束或包含指定字符串的实体。   
True、False：查找布尔属性为 true 或 false 的实体。   

例子：    
```code
List<User> findByName(String name);

List<User> findByAgeGreaterThanEqual(int age);

List<User> findByStatusTrue();

List<User> findByNameContainingIgnoreCase(String name);

List<User> findByAgeBetween(int start, int end);

User findByEmailAndPassword(String email, String password);

```
