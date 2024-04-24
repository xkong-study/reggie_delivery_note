<img width="422" alt="截屏2024-04-24 22 46 09" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/c6a32398-1151-487e-a2bd-d14d1fdb3f04">
要实现数据共享所以我们要整合nacos数据集群。    

2.搭建集群    

搭建集群的基本步骤：      
•搭建数据库，初始化数据库表结构      
•下载nacos安装包     
•配置nacos      
•启动nacos集群     
•nginx反向代理     


搭建Nacos集群涉及一系列步骤，确保高可用性和可扩展性。以下是详细的步骤来搭建Nacos集群：     

1. 环境准备  
操作系统：Linux或其他Unix-like系统。                
基础软件：Java环境（推荐Java 8或更高版本）。                  
数据库：MySQL数据库用于存储配置数据和服务发现数据。   

2. 数据库配置    
安装MySQL并创建一个数据库（如nacos_config_db）。          
导入Nacos的SQL脚本，该脚本通常在Nacos的安装包中可以找到，例如nacos-mysql.sql，用于创建必要的表和初始化数据。

3. Nacos服务器安装     
下载Nacos的二进制包从其官方GitHub仓库或其官网。     
解压缩到每个预定作为集群节点的服务器上。

4. 配置集群      
在Nacos的安装目录中找到conf/cluster.conf文件，并配置每个集群节点的IP地址和端口，例如：       
```code 
192.168.1.1:8848
192.168.1.2:8848
192.168.1.3:8848
```
配置application.properties文件，指定数据库连接，例如：        
```code 
spring.datasource.platform=mysql
db.num=1
db.url.0=jdbc:mysql://localhost:3306/nacos_config_db?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true
db.user=root
db.password=password
```
5. 启动服务器      
在每个节点上执行启动脚本。在Nacos的bin目录下运行startup.sh -m cluster来启动Nacos实例。           
确认每个节点都能正确启动并加入到集群中。

6. 验证集群状态
访问任一节点的Web UI界面，默认URL为http://<IP地址>:8848/nacos，并检查集群节点的状态。

7. 防火墙和安全          
确保集群节点之间的通信端口（默认是8848）在防火墙中开放。             
考虑使用安全组或其他网络安全工具来限制访问。

8. 高可用性和负载均衡      
可以通过Nginx或其他负载均衡器在Nacos集群前设置一个负载均衡器，以提高可用性和分配负载。      
配置健康检查，确保流量仅被分配到健康的Nacos节点。
