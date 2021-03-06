# 原型模式
## 模式定义
原型模式（Prototype Pattern）是一种创建型设计模式，Prototype模式允许一个对象再创建另外一个可定制的对象，根本无需知道任何如何创建的细节。

## 模式结构
原型模式包含如下角色：

Prototype：抽象原型
Concrete Prototype：具体原型角色
![Prototype.png](http://www.yihuaiyuan.com/usr/uploads/2018/04/2192625860.png)

## 实例
比如我请求淘宝接口时，商品类需要new Goods($sign)->exec(),订单类需要new Orders($sign)->exec()，等等；但是商品和订单类都用到appId,appKey,token,param等参数，其中appId、appKen是一致的，token、params是不同的。那么我们构建一个淘宝的原型$tb = new TaoBaoPrototype(),商品类和订单类可以通过clone $tb来实现。


## 模式分析
原型模式使用克隆方法实现对象创建而不是使用标准的 new 方式。当我们需要创建多个类似的大对象时，如果直接通过new对象，开销很大，而且new完还得进行重复的初始化工作。使用原型模式，则是先创建好一个原型对象，然后通过clone这个原型对象来创建新的对象，这样就免去了重复的初始化工作，系统仅需内存拷贝即可。


## 原型模式的优点
原型模式具有在运行时刻增加和删除产品，可以改变值以指定新对象，可以改变结构以指定新对象，减少子类的构造，用类动态配置应用等优点
##  原型模式的缺点
原型模式的最主要缺点就是每一个类必须配备一个克隆方法。
而且这个克隆方法需要对类的功能进行通盘考虑，这对全新的类来说不是很难，但对已有的类进行改造时，不一定是件容易的事

## 模式扩展
可以将克隆方法封装到一个工厂方法里面，这样调用更加方便，也便于我们对克隆对象进行计数、销毁等操作。
## 总结

原型模式的主要思想是基于现有的对象克隆一个新的对象出来，一般是用对象内部提供的克隆方法，通过该方法返回一个对象的副本，这种创建对象的方式，相比我们之前说的几类创建型模式还是有区别的，之前的讲述的工厂方法模式与抽象工厂都是通过工厂封装具体的 new 操作的过程，返回一个新的对象，有的时候我们通过这样的创建工厂创建对象不值得，特别是以下的几个场景，可能使用原型模式更简单、效率更高：

- 如果说我们的对象类型不是刚开始就能确定，而是在运行时确定的话，那么我们通过这个类型的对象克隆出一个新的类型更容易。
- 有的时候我们可能在实际的项目中需要一个对象在某个状态下的副本，这个前提很重要，这点怎么理解呢，例如有的时候我们需要对比一个对象经过处理后的状态和处理前的状态是否发生过改变，可能我们就需要在执行某段处理之前，克隆这个对象此时状态的副本，然后等执行后的状态进行相应的对比，这样的应用在项目中也是经常会出现的。
- 当我们处理的对象比较简单，并且对象之间的区别很小，可能只是很固定的几个属性不同的时候，使用原型模式更合适。

参考资料：
- https://segmentfault.com/a/1190000007531872
- http://laravelacademy.org/post/2546.html
- http://www.imooc.com/article/16973
