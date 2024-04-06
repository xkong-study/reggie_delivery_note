Spring框架提供的缓存抽象允许开发者在不直接依赖于任何具体缓存实现（如Redis、EhCache、Caffeine等）的情况下，使用缓存功能。这种设计主要是为了提高代码的可移植性和灵活性，使得开发者可以根据需求或环境的变化选择最适合的缓存解决方案，而不需要修改业务代码。     

Spring缓存抽象在没有指定具体缓存实现的情况下，如何存储缓存数据取决于默认配置或是如何设置的缓存管理器（CacheManager）。在Spring框架中，如果没有明确指定缓存存储的具体实现，它通常会使用一个简单的内存缓存，这是基于ConcurrentHashMap的简单实现，不需要额外的配置即可使用。这种内存缓存适合开发和测试环境，但在生产环境中，你通常会选择一个更健壮的解决方案，比如Redis、EhCache或Caffeine等。      

是的，当你使用Spring框架的缓存抽象并选择内存作为缓存存储时，缓存数据实际上是存储在你的应用程序所运行的服务器内存中。这意味着缓存的生命周期与应用程序的生命周期相绑定：当应用程序启动时，缓存开始存在；当应用程序关闭或重启时，缓存中的数据将会丢失。     

内存缓存通常是通过Java的数据结构来实现的，比如ConcurrentHashMap，这使得访问缓存非常快速。      

**先不用redis进行缓存**

<img width="345" alt="截屏2024-04-05 09 53 28" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/d43826e6-66c7-4fea-8086-f0338901a634">

<img width="624" alt="截屏2024-04-05 09 55 00" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/15da28a5-4a99-4e41-b4aa-c1da9db712d6">

<img width="620" alt="截屏2024-04-05 09 56 43" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/e4df2190-0239-476f-9e21-ad5f9df0105b">

**CachPut用法**

<img width="436" alt="截屏2024-04-06 20 20 13" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/203fa28b-f175-4acc-9c2f-d14f0cbc5ccf">

**CachEvict用法**

<img width="346" alt="截屏2024-04-06 20 31 39" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/efff6a16-2138-44c7-8aeb-3965a69bcaab">

<img width="454" alt="截屏2024-04-06 20 47 50" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/d6cea0c6-b922-4c89-ba93-c0a413dc752f">

**Cachable用法**

<img width="367" alt="截屏2024-04-06 20 56 33" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/97f1eb27-4efc-4350-940a-771d199809ce">

<img width="645" alt="截屏2024-04-06 21 03 30" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/faf69844-37b7-44c8-aa60-109799e4fa5c">

**底层方法切换成redis**   

<img width="638" alt="截屏2024-04-06 21 11 22" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/2a1ffb43-9629-447f-b085-3eef12c35960">

**为什么springcache不可以使用condition作为返回结果？**           
       
condition主要判断是否存储数据但是不能返回数据。          

为什么condition不能用返回结果？               
执行时机：condition的评估发生在方法执行之前，这意味着此时方法的返回结果还未产生，因此无法在condition中访问result。                  

设计目的：condition的设计初衷是根据方法执行前的参数值来决定是否应用缓存逻辑。这样做是为了在执行重要的业务逻辑或资源密集型操作之前，基于当前的上下文和参数决定是否需要进行缓存操作。           
      
如何基于返回结果决定缓存逻辑？           
虽然不能直接在condition属性中使用返回结果，但Spring Cache提供了另一个属性unless，这个属性正好满足了基于方法返回结果来决定是否缓存该结果的需求。unless属性在方法执行之后进行评估，可以访问方法的返回值。                

例如，如果你只想缓存当方法返回的实体的id属性不为空时的结果，可以这样做：            

```code
@Cacheable(value = "entities", unless = "#result.id == null")
public Entity findEntityById(Long id) {
    // 方法实现
}
```

在这个例子中，unless属性用于指定一个条件，该条件基于方法的返回结果。只有当返回的Entity对象的id属性非空时，结果才会被缓存。    

虽然condition不能用于基于方法返回结果的条件判断，但通过使用unless属性，Spring Cache允许开发者在方法执行后根据返回结果来决定是否缓存该结果。这提供了一种灵活的方式，以基于执行后的状态来优化缓存行为。        

<img width="528" alt="截屏2024-04-06 21 38 02" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/6869d276-8bcd-493e-a425-c55b4669c865">

