ThreadLocal 是 Java 中的一个类，用于在多线程环境中存储和访问线程局部变量。线程局部变量是指每个线程都拥有自己独立的变量副本，互不影响。   

简而言之，ThreadLocal 提供了一种在多线程程序中，每个线程都可以独立地访问自己的变量的机制。这些变量可以是同一类型的，但各个线程都有自己的独立副本，互相之间不会干扰。    

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
