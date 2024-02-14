### Map map = new HashMap();
Map是一个接口，HashMap是具体的实现类。
由于接口是类的蓝图，是一个抽象的概念，不能被实例化，因此接口需要由具体的类来实现。
这条代码指明：由HashMap类来实现接口Map中描述的方法。
HashMap map = new HashMap();
声明一个HashMap类型的map，由HashMap类实现。
为什么更推荐第一种用接口的声明方式？
这个问题等同于为什么要在编程中使用接口，而不是直接使用实现类。其实这就是面对对象编程 (OOP）的思想精髓。简单来说就是上层接口描述的功能不变，下层的具体实现可以不断修改替换。上层的调用者只用知道map的功能，不必关心map的具体实现。
例如，某天开发人员开发出一个各方面性能都优于Hashap的SuperMap类，则map可以直接改成由SuperMap来实现：Map map =newSuperMap0。对于外部调用者来说，使用的还是那个map，殊不知底层实现的升级已经让他们用上了优化版的map。如果一开始就定义map为Has Map类型，无法做出这样的优化，很明显 Hashap map =new SuperMap() 是条错误的代码。这就是使用接口声明的好处，增加系统灵活性，隔离性等。
