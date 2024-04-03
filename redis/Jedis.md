<img width="669" alt="截屏2024-04-02 22 57 07" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/dc22aa46-5751-4640-a494-01a7bb432770">

步骤：  
1.获取连接：   
```code
Jedis jedis = new Jedis(host:,port:);
```

2.执行具体的操作:   
```code
jedis.set("username","xiaoming");
String name = jedis.get("username");
jedis.del("username");
jedis.hset("xkong","location","beijing");
String location = jedis.hget("xkong","loation");
Set<String> keys = jedis.keys("*");
for(String keys:key){
  System.out.println(key);
}
```

3.关闭连接:  
```code
jedis.close();
```
