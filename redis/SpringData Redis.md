<img width="659" alt="截屏2024-04-03 19 33 36" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/c42f228b-fd9f-47ff-a4f1-a23b8e74e2d9">

<img width="442" alt="截屏2024-04-03 19 35 47" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/55de859f-2680-462d-ba0f-29ac8990f98a">

如何切换数据库： select 1      
<img width="232" alt="截屏2024-04-03 19 37 04" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/fe7646c2-e320-47e4-8d6b-57563ccd8fc8">

RedisTemplate需要一个连接工厂（ConnectionFactory）实例，通常情况下，Spring Boot会自动配置它。你可以直接在你的服务或组件中注入RedisTemplate并使用它：     

<img width="498" alt="截屏2024-04-03 19 42 48" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/31a1680e-f4e6-4ddd-ae00-6e64a0c3b6cd">      

为了防止redis的key乱码需要配置：    
<img width="870" alt="截屏2024-04-03 19 49 10" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/346245a9-cbf9-4f42-8a7c-088d46d1a688">



RedisTemplate的序列化器可以提高Redis存储的效率和可读性，特别是对于键通常使用字符串，而值可能是复杂类型的情况。以下是如何在Spring Boot应用中配置RedisTemplate以使用StringRedisSerializer序列化键，和使用Jackson2JsonRedisSerializer序列化值的示例。     

1. 配置RedisTemplate   
你需要配置一个自定义的RedisTemplate Bean，以指定键和值的序列化方式。以下是一个配置示例：

```code
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.serializer.Jackson2JsonRedisSerializer;
import org.springframework.data.redis.serializer.StringRedisSerializer;

import com.fasterxml.jackson.databind.ObjectMapper;
import com.fasterxml.jackson.annotation.JsonAutoDetect;
import com.fasterxml.jackson.annotation.PropertyAccessor;
import com.fasterxml.jackson.databind.jsontype.impl.LaissezFaireSubTypeValidator;

@Configuration
public class RedisConfig {

    @Bean
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory redisConnectionFactory) {
        RedisTemplate<String, Object> template = new RedisTemplate<>();
        template.setConnectionFactory(redisConnectionFactory);

        // 使用StringRedisSerializer来序列化和反序列化redis的key值
        template.setKeySerializer(new StringRedisSerializer());
        template.setHashKeySerializer(new StringRedisSerializer());

        // 定义Jackson2JsonRedisSerializer序列化对象
        Jackson2JsonRedisSerializer<Object> jacksonSeial = new Jackson2JsonRedisSerializer<>(Object.class);

        ObjectMapper om = new ObjectMapper();
        // 指定要序列化的域，field,get和set,以及修饰符范围，ANY是都有包括private和public
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        // 指定序列化输入的类型，类必须是非final修饰的，final修饰的类，比如String,Integer等会抛出异常
        om.activateDefaultTyping(LaissezFaireSubTypeValidator.instance, ObjectMapper.DefaultTyping.NON_FINAL);

        jacksonSeial.setObjectMapper(om);

        // 值采用json序列化
        template.setValueSerializer(jacksonSeial);
        template.setHashValueSerializer(jacksonSeial);

        // 设置默认的序列化方式
        template.setDefaultSerializer(jacksonSeial);
        template.afterPropertiesSet();
        return template;
    }
}

```

String类型数据使用方式：    

<img width="856" alt="截屏2024-04-03 20 18 41" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/47cfe24e-54a4-4100-94b9-01501403d109">


Hash类型数据使用方式：  
用户id作为key     

<img width="552" alt="截屏2024-04-03 20 29 05" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/1c6cd48a-062a-43bd-b7b5-bc09d111f0fb">

List类型数据使用方式：   

<img width="549" alt="截屏2024-04-03 20 36 05" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/8f3fe157-0225-48eb-9359-93ed4826b60a">

<img width="575" alt="截屏2024-04-03 20 38 25" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/8f1c9b80-cadc-4c57-88f2-19873d95f857">

