如何解决微服务间的配置共享问题。通过将共享的配置放在以服务名命名的文件中，可以实现不同环境下的配置热更新。同时,还介绍了如何在不同的环境下读取正确的配置文件,并展示了配置文件的优先级。通过的学习,可以更好地掌握微服务配置管理的基本用法。     

引用共享配置：      
在环境特定的配置文件中，可以通过特定的配置引用语法来引入公共配置。这通常是通过配置文件中的特定标记来实现，如在YAML或Properties文件中引用公共配置的数据ID。            
比如在Spring Cloud应用中，可以在bootstrap.properties文件中使用如下语法引入公共命名空间的配置：                
```code
spring.cloud.nacos.config.shared-dataids=common.properties
spring.cloud.nacos.config.refreshable-dataids=common.properties
```
这里的common.properties就是存放在公共命名空间的一个配置文件。                

<img width="631" alt="截屏2024-04-24 22 36 22" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/547bb7e7-9db9-420e-bba4-95e056ccf5fa">

<img width="485" alt="截屏2024-04-24 22 36 52" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/655ce56d-a11a-4bc9-bee7-aa70b4f3349e">
