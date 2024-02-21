https://blog.csdn.net/weixin_42516475/article/details/130115388


接口之间的继承在面向对象编程中是一种重要的机制，但它的含义与类的继承有所不同。在Java中，接口之间的继承是通过关键字 extends 来实现的，而类之间的继承使用 extends 关键字。

接口之间的继承有以下几个主要用途：

代码重用和组合: 通过继承接口，一个接口可以重用另一个接口中定义的方法签名，从而实现代码的组合和复用。
```code
public interface A {
    void methodA();
}

public interface B extends A {
    void methodB();
}
````
在这个例子中，接口 B 继承了接口 A，因此它不仅包含自己定义的 methodB() 方法，还包含了 methodA() 方法。

接口的多继承: 一个接口可以继承多个其他接口，这使得一个接口可以拥有多个父接口的特性。
```code
public interface A {
    void methodA();
}

public interface B {
    void methodB();
}

public interface C extends A, B {
    void methodC();
}
```
在这个例子中，接口 C 继承了接口 A 和 B，因此它包含了所有三个接口中定义的方法。

规范和实现分离: 接口之间的继承可以帮助实现规范和实现的分离。一个接口可以定义规范（方法签名），而具体的类可以实现这些规范。
总体而言，接口之间的继承提供了一种方式来组织和扩展代码，允许你定义和维护一组相关的方法，使得不同的类可以实现这些方法以满足自己的需求。     

接口继承通常用于定义规范和行为的层次结构，而接口实现用于提供具体的功能和行为。 

使用接口继承的场景：
代码重用和组合：当你想在多个接口中共享相同的方法签名时，可以使用接口继承。这样可以避免在每个接口中都重复定义相同的方法。

```code
public interface A {
    void methodA();
}

public interface B extends A {
    void methodB();
}
```

规范的层次结构：当你想要创建一种规范的层次结构，其中一些接口定义了基本的行为，而其他接口在此基础上添加更多的行为时，可以使用接口继承。

```code
public interface Shape {
    void draw();
}

public interface Circle extends Shape {
    void radius();
}
```

使用接口实现的场景：    

实现特定的功能：当一个类需要提供接口中定义的具体实现时，可以使用接口实现。这是为了确保类具有特定的行为。

```code
public class MyClass implements MyInterface {
    @Override
    public void myMethod() {
        // 具体实现
    }
}
```

多态性：当你想要使用多态性的概念，即一个对象可以被看作是实现了多个接口的实例时，可以使用接口实现。

```code
public class MyObject implements InterfaceA, InterfaceB {
    // 实现 InterfaceA 和 InterfaceB 的方法
}
```
综合来说，接口继承通常用于定义规范和行为的层次结构，而接口实现用于提供具体的功能和行为。在实际设计中，你可能会同时使用这两种机制，根据需要组合和继承接口，以实现灵活而可维护的代码结构。


