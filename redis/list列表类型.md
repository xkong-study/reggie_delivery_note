<img width="601" alt="截屏2024-04-02 20 51 15" src="https://github.com/xkong-study/reggie_delivery_note/assets/100473178/08182ca7-4386-4901-9566-bc6cf40555ca">

主要区别                       
阻塞与非阻塞：RPOP 是非阻塞的，而 BRPOP 是阻塞的。    
这意味着如果列表为空，RPOP 会立即返回 nil，而 BRPOP 会根据设定的超时参数等待，直到有元素可以被弹出或超时。       
单个 vs 多个列表：RPOP 只作用于单个列表，而 BRPOP 可以指定多个列表，它会按照指定的顺序检查每个列表，并从第一个非空列表中弹出元素。    
适用场景：RPOP 适用于简单的列表弹出操作。BRPOP 适用于需要等待队列中有元素可用的场景，如在生产者-消费者模型中阻塞等待任务。         
