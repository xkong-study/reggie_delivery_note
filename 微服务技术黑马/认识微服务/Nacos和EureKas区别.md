https://www.cnblogs.com/davidgu/p/14526467.html

提供者分为临时实例和非临时实例：   
临时实例：没心跳了直接剔除配置中心。    
非临时实例：注册中心主动询问还健不健康了，不健康了标记一下但是不剔除。     
<img width="765" alt="截屏2024-04-22 20 39 37" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/e4c40944-2554-4390-a28e-4e12f8428961">

消费者：      
和EureKa的区别，这个消费者可以拉取更新服务器能及时的通知。      
<img width="788" alt="截屏2024-04-22 20 41 00" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/ba11594c-3b2b-4793-8521-28179487e0c3">

如何设计临时实例和非临时实例

<img width="696" alt="截屏2024-04-22 21 31 00" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/0ebd0cb4-8651-4794-859a-371d33e8b8bc">

<img width="491" alt="截屏2024-04-22 21 33 46" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/130d1089-ee47-4464-9c4a-fc8d258abc01">


在Nacos中，AP和CP是指分布式系统中数据一致性模型的两种选择。这两个模型的选择取决于系统对于一致性和可用性的要求。   

AP（Availability and Partition Tolerance）：       
AP模型强调系统的可用性和分区容忍性，即系统在遇到网络分区或故障时仍能保持可用状态。       
在AP模型中，系统可能会出现数据的部分不一致，但系统仍能保持可用，从而保证了服务的连续性。      
Nacos在AP模型下使用Raft算法实现数据一致性，确保了系统在网络分区或故障情况下的高可用性。        

CP（Consistency and Partition Tolerance）：     
CP模型强调数据的一致性和分区容忍性，即系统保证了数据的强一致性，但在网络分区或故障时可能会影响系统的可用性。              
在CP模型中，系统会等待数据一致性达到一定程度后再提供服务，从而确保了数据的完整性和一致性。      
Nacos在CP模型下使用Paxos算法实现数据一致性，虽然可能会影响系统的可用性，但能保证数据的强一致性。         
