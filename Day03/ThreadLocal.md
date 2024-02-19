ThreadLocal 是 Java 中的一个类，用于在多线程环境中存储和访问线程局部变量。线程局部变量是指每个线程都拥有自己独立的变量副本，互不影响。   

简而言之，ThreadLocal 提供了一种在多线程程序中，每个线程都可以独立地访问自己的变量的机制。这些变量可以是同一类型的，但各个线程都有自己的独立副本，互相之间不会干扰。    

<img width="577" alt="Screenshot 2024-02-19 at 21 52 44" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/11e87419-0737-42f2-9996-846eea65353f">


```code
public class Example {
    private static ThreadLocal<String> threadLocal = new ThreadLocal<>();

    public static void main(String[] args) {
        // 在主线程中设置变量值
        threadLocal.set("Main Thread Value");

        // 启动一个新线程
        Thread newThread = new Thread(() -> {
            // 在新线程中访问变量值
            String value = threadLocal.get();
            System.out.println("New Thread Value: " + value);
        });

        newThread.start();

        // 在主线程中访问变量值
        String mainThreadValue = threadLocal.get();
        System.out.println("Main Thread Value: " + mainThreadValue);
    }
}

```
<img width="586" alt="Screenshot 2024-02-19 at 21 55 41" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/23908c3e-7ca7-485f-a0ca-c0979f39c711">

```code
package com.example.common;

import org.springframework.stereotype.Component;

//基于ThreadLocal封装工具类，用户保存和获取当前登陆用户id
public class BaseContext {
    public static ThreadLocal<Long> threadLocal = new ThreadLocal<>();
    public static void setThreadLocal(Long id){
        threadLocal.set(id);
    }
    public static Long getThreadLocal(){
        return threadLocal.get();
    }
}
```

共享状态： 使用 static 可以确保 threadLocal 在整个应用程序中是共享的，而不是每个类的实例都有自己的拷贝。这样可以确保所有线程都使用相同的 ThreadLocal 实例。

方便访问： 由于这些方法和字段是静态的，可以直接通过类名 BaseContext 访问，而不需要创建 BaseContext 类的实例。这样可以简化代码，特别是在没有需要实例化的理由时。

无需维护状态： 由于这是一个工具类，主要用于存储线程局部的信息，不需要维护实例级别的状态。使用静态方法和字段使得代码更加简洁。

ThreadLocal 适用性： ThreadLocal 通常在多线程环境中用于存储线程局部的状态。由于每个线程都有自己的 ThreadLocal 实例，使用静态方法和字段确保了所有线程共享相同的 ThreadLocal 实例。

所以一般工具类就用static方法。    
