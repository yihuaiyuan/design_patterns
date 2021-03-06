# design_patterns
## 什么是设计模式？
在软件工程中，设计模式（design pattern）是对软件设计中普遍存在（反复出现）的各种问题，所提出的解决方案。
## 为什么学设计模式？
设计模式可以帮助我们改善系统的设计，增强系统的健壮性、可扩展性，为以后铺平道路。
## 怎么学设计模式？
### 了解设计模式六大原则：
- 单一职责原则，每个类只负责单一的只能；
- 里氏替换原则，所有的父类都应该可以被子类替代；
- 接口隔离原则，接口最小化，接口应该定义最少的功能；
- 依赖倒置原则，抽象不应该依赖细节，细节依赖抽象；
- 迪米特原则，一个类应该不要依赖另一个类太多细节；
- 开闭原则，对修改关闭，对扩展开放。

### 了解类之间的关系和UML图

_**继承**_:指的是一个类（称为子类、子接口）继承另外的一个类（称为父类、父接口）的功能，并可以增加它自己的新功能的能力，继承是类与类或者接口与接口之间最常见的关系；在Java中此类关系通过关键字extends明确标识，在设计时一般没有争议性； 

![Generalization.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/58447361.jpg)

**_实现_**:指的是一个class类实现interface接口（可以是多个）的功能；实现是类与接口之间最常见的关系；在Java中此类关系通过关键字implements明确标识，在设计时一般没有争议性； 

![Realization.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/2093350975.jpg)

**_依赖_**:可以简单的理解，就是一个类A使用到了另一个类B，而这种使用关系是具有偶然性的、、临时性的、非常弱的，但是B类的变化会影响到A；比如某人要过河，需要借用一条船，此时人与船之间的关系就是依赖；表现在代码层面，为类B作为参数被类A在某个method方法中使用；

![Dependence.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/1499903217.jpg)

_**关联**_:他体现的是两个类、或者类与接口之间语义级别的一种强依赖关系，比如我和我的朋友；这种关系比依赖更强、不存在依赖关系的偶然性、关系也不是临时性的，一般是长期性的，而且双方的关系一般是平等的、关联可以是单向、双向的；表现在代码层面，为被关联类B以类属性的形式出现在关联类A中，也可能是关联类A引用了一个类型为被关联类B的全局变量； 

![Association.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/2139268290.jpg)

**_聚合_**:聚合是关联关系的一种特例，他体现的是整体与部分、拥有的关系，即has-a的关系，此时整体与部分之间是可分离的，他们可以具有各自的生命周期，部分可以属于多个整体对象，也可以为多个整体对象共享；比如计算机与CPU、公司与员工的关系等；表现在代码层面，和关联关系是一致的，只能从语义级别来区分；

![Aggregation.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/1781777859.jpg)

**_组合_**:组合也是关联关系的一种特例，他体现的是一种contains-a的关系，这种关系比聚合更强，也称为强聚合；他同样体现整体与部分间的关系，但此时整体与部分是不可分的，整体的生命周期结束也就意味着部分的生命周期结束；比如你和你的大脑；表现在代码层面，和关联关系是一致的，只能从语义级别来区分； 

![Composition.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/550490761.jpg)

如：

![uml_class_struct.jpg](http://www.yihuaiyuan.com/usr/uploads/2018/04/679423086.jpg)


车有两个继承类：小汽车和自行车，它们之间的关系为实现关系，使用带空心箭头的虚线表示；
小汽车为与SUV之间是继承关系，使用带空心箭头的实线表示；
小汽车与发动机之间是组合关系，使用带实心箭头的实线表示；
学生与班级之间是聚合关系，使用带空心箭头的实线表示；
学生与身份证之间为关联关系，使用一根实线表示；
学生上学需要用到自行车，与自行车是一种依赖关系，使用带箭头的虚线表示；

### 了解时序图
<a href="http://www.cnblogs.com/ywqu/archive/2009/12/22/1629426.html" target="_blank">UML建模之时序图（Sequence Diagram）</a>

### 了解24中设计模式
以下的代码示例均是为了实现设计模式而强制做的变化，实际编码中请注意，设计模式虽然很好，可以增强系统的扩展性、健壮性，但是如果为了使用设计模式而使用设计模式，往往得不偿失，使用了设计模式对代码的交接，bug的定位等问题都带来了一些麻烦，大家在使用时一定要注意使用设计模式带来的价值，以及造成的负面影响。
#### 创建型模式
创建型模式(Creational Pattern)对类的实例化过程进行了抽象，能够将软件模块中对象的创建和对象的使用分离。为了使软件的结构更加清晰，外界对于这些对象只需要知道它们共同的接口，而不清楚其具体的实现细节，使整个系统的设计更加符合单一职责原则。
创建型模式在创建什么(What)，由谁创建(Who)，何时创建(When)等方面都为软件设计者提供了尽可能大的灵活性。创建型模式隐藏了类的实例的创建细节，通过隐藏对象如何被创建和组合在一起达到使整个系统独立的目的。

 包含模式：
 - <a href= 'http://www.yihuaiyuan.com/php/223.html' target='_blank' > 简单工厂模式（Simple Factory）</a>
 - <a href= 'http://www.yihuaiyuan.com/php/224.html' target='_blank' > 工厂方法模式（Factory Method）</a>
 - <a href= 'http://www.yihuaiyuan.com/php/231.html' target='_blank' > 抽象工厂模式（Abstract Method）</a>
 - <a href= 'http://www.yihuaiyuan.com/php/235.html' target='_blank' > 建造者模式（Builder）</a>
 - <a href= 'http://www.yihuaiyuan.com/php/239.html' target='_blank' > 原型模式（Prototype）</a>
 - <a href= 'http://www.yihuaiyuan.com/php/217.html' target='_blank' > 单例模式（Singleton）</a>

#### 结构型模式
结构型模式(Structural Pattern)描述如何将类或者对象结合在一起形成更大的结构，就像搭积木，可以通过 简单积木的组合形成复杂的、功能更为强大的结构。

结构型模式可以分为类结构型模式和对象结构型模式：
- 类结构型模式关心类的组合，由多个类可以组合成一个更大的系统，在类结构型模式中一般只存在继承关系和实现关系。 
- 对象结构型模式关心类与对象的组合，通过关联关系使得在一 个类中定义另一个类的实例对象，然后通过该对象调用其方法。 根据“合成复用原则”，在系统中尽量使用关联关系来替代继 承关系，因此大部分结构型模式都是对象结构型模式。

 包含模式：
 - <a href= 'http://www.yihuaiyuan.com/php/251.html' target='_blank' > 代理模式(Proxy)</a>
 - <a href= 'http://www.yihuaiyuan.com/php/244.html' target='_blank' > 适配器模(Adapter)</a>
 - <a href= 'http://www.yihuaiyuan.com/php/252.html' target='_blank' > 装饰器模式(Decorator)</a>
 - <a href= 'http://www.yihuaiyuan.com/php/248.html' target='_blank' > 桥接模式(Bridge)</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 组合模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/254.html' target='_blank' > 享元模式(Flyweight)</a>
 - <a href= 'http://www.yihuaiyuan.com/php/255.html' target='_blank' > 外观模式(Facade)</a>
 
####行为型模式
行为型模式(Behavioral Pattern)是对在不同的对象之间划分责任和算法的抽象化。

行为型模式不仅仅关注类和对象的结构，而且重点关注它们之间的相互作用。

通过行为型模式，可以更加清晰地划分类与对象的职责，并研究系统在运行时实例对象 之间的交互。在系统运行时，对象并不是孤立的，它们可以通过相互通信与协作完成某些复杂功能，一个对象在运行时也将影响到其他对象的运行。

行为型模式分为类行为型模式和对象行为型模式两种：
- 类行为型模式：类的行为型模式使用继承关系在几个类之间分配行为，类行为型模式主要通过多态等方式来分配父类与子类的职责。
- 对象行为型模式：对象的行为型模式则使用对象的聚合关联关系来分配行为，对象行为型模式主要是通过对象关联等方式来分配两个或多个类的职责。根据“合成复用原则”，系统中要尽量使用关联关系来取代继承关系，因此大部分行为型设计模式都属于对象行为型设计模式。
                             
 包含模式：
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 观察者模式()</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 模板方法模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 命令模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 状态模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 职责链模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 解释器模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 中介者模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 访问者模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 策略模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 备忘录模式</a>
 - <a href= 'http://www.yihuaiyuan.com/php/.html' target='_blank' > 迭代器模式</a>
 
参考资料：
- http://design-patterns.readthedocs.io/zh_CN/latest/read_uml.html
- http://laravelacademy.org/resources/design-patterns
- http://www.cnblogs.com/zuoxiaolong/p/pattern26.html
- https://www.cnblogs.com/olvo/archive/2012/05/03/2481014.html
