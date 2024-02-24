这节视频解答了我的疑惑就是为什么java对象在springboot里面要设置成序列化形式。    

Serilizable相当于一个标记，就是只有标记了才能让虚拟机允许对象按照特定的方式存入文件中去。虚拟机会实现装载程序以特定的方式存入文件中去。方便我们下次读出来。          

在Spring Boot中，当一个类实现了Serializable接口，它表明这个类的实例对象可以被序列化，即可以将其转换成字节流，便于在网络上传输或者保存到持久存储中。

Serializable 接口是Java中的一个标记接口，它并没有包含任何方法，只是作为一个标记，表示这个类是可序列化的。这个接口的作用是告诉Java虚拟机这个类可以被序列化，并且可以通过Java的序列化机制进行处理。

当一个对象实现了Serializable接口，它可以被序列化为字节流，也可以从字节流反序列化回来。在Spring Boot或其他Java应用中，反序列化通常是由Java虚拟机自动处理的。具体来说，当你在Spring Boot中使用对象进行远程通信、将对象存储到缓存中或者保存到数据库时，Spring Boot内部的机制会负责对象的序列化和反序列化。这是通过Java的序列化机制来实现的，而不需要你手动编写反序列化的代码。

总之，当你在Spring Boot中将对象实现Serializable接口时，Spring Boot会自动处理对象的序列化和反序列化，你无需手动编写反序列化的代码。这样的设计简化了开发者的工作，使得对象的序列化和反序列化过程更加透明和方便

<img width="502" alt="Screenshot 2024-02-24 at 10 11 02" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/362b5385-cec9-48f4-a2ca-c6b1e37be373">
