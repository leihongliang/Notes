---
typora-copy-images-to: upload
---

 

# 自我介绍

面试官您好，我叫方武，本科毕业于安庆师范大学，在本科期间参加过全国大学生电子设计竞赛获得安徽省三等奖；现在是杭州电子科技大学电子信息专业的一名硕士研究生，发表了一篇软著；在就读硕士研究生期间逐渐萌生对Java大数据的浓厚兴趣，因而在校期间学习了java基础，常用数据结构与算法、jvm、并发、MySql、zookeeper、Kafka以及hadoop、hive、spark、flink等大数据处理主流框架；并自己动手做了两个项目去巩固学习到的知识，最开始做的是一个电商的离线数据仓库系统，通过这个项目我学习到了 1、源数据传输过程中的流量削峰与数据倾斜的解决；2、数仓的搭建流程以及kimiball维度建模方法；3、熟练的使用SQL进行指标分析；4、为保证集群安全进行了keberos用户认证和ranger权限管理同时进行了元数据管理与数据质量管理。第二个项目是基于flink实现的实时电商业务分析系统，通过这个项目学习到了flink CDC监控和捕捉数据的原理；维表与流表的动态分流；查询维表时的旁路缓存优化和异步I/O优化；在指标分析过程中熟练使用flink丰富的窗口机制与状态编程并防止了数据倾斜的发生；最后解决了flink 数据输出到MySql的重复消费问题，实现端到端的一致性语义；

 

# JavaSE

### 1、java创建对象创建有几种方式

> 海康、

![image-20220408191111123](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220408191111123.png)

以上五种；[Java创建对象有几种方式_JavaPub-rodert的博客-CSDN博客_java创建对象有哪几种方式](https://blog.csdn.net/qq_40374604/article/details/122016195)

 

### Java 语言的特点 (1)

（如果你简历上有提到 C++ 可能还会问你 Java 和 C++ 的区别）
1.简单易学；
2.面向对象（封装，继承，多态)；
3.平台无关性（ Java 虚拟机实现平台无关性）；
4.支持多线程（2011年之前 C++ 语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程程序设计，而 Java 语言却提供了多线程支持）；
5.可靠性；
6.安全性；
7.支持网络编程并且很方便（ Java 语言诞生本身就是为简化网络编程设计的，因此 Java 语言不仅支持网络编程而且很方便）；
8.编译与解释并存；
9.Java 语言最大的优势：实际上，跨平台已经不是 Java 最大的卖点了，目前市面上虚拟化技术已经非常成熟，比如你通过 Docker 就很容易实现跨平台了。各种 JDK 新特性也不是。Java 强大的生态(各种框架)才是。

 

### 什么是字节码?采用字节码的好处是什么? (1)

在 Java 中，JVM 可以理解的代码就叫做字节码（即扩展名为 .class的文件），它不面向任何特定的处理器，只面向虚拟机。Java 语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以， Java 程序运行时相对来说还是高效的（不过，和 C++，Rust，Go 等语言还是有一定差距的），而且，由于字节码并不针对一种特定的机器，因此，Java 程序无须重新编译便可在多种不同操作系统的计算机上运行。

 

### java 和 C++的区别? (1)

都是面向对象的语言，都支持封装、继承和多态
Java 不提供指针来直接访问内存，程序内存更加安全
Java 的类是单继承的，C++ 支持多重继承；虽然 Java 的类不可以多继承，但是接口可以多继承。
Java 有自动内存管理垃圾回收机制(GC)，不需要程序员手动释放无用内存。
C ++同时支持方法重载和操作符重载，但是 Java 只支持方法重载（操作符重载增加了复杂性，这与 Java 最初的设计思想不符）。

 

### final 有什么⽤？  (1)  ★★★

![image-20211207211114925](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207211114925.png)

 

### final finally finalize区别  (1)

final可以修饰类、变量、⽅法，修饰类表示该类不能被继承、修饰⽅法表示该⽅法不能被重写、修饰变量：如果是基本数据类型的变量，则其数值⼀旦在初始化之后便不能更改；如果是引⽤类型的变量，则在对其初始化之后便不能再让其指向另⼀个对象

finally⼀般作⽤在try-catch代码块中，在处理异常的时候，通常我们将⼀定要执⾏的代码⽅法finally代码块 中，表示不管是否出现异常，该代码块都会执⾏，⼀般⽤来存放⼀些关闭资源的代码。

finalize是⼀个⽅法，Object类的一个方法，该⽅法⼀般由垃圾回收器来调⽤，当我们调⽤System.gc() ⽅法的时候，由垃圾回收器调⽤finalize()，回收垃圾，是⼀个对象是否可回收的最后判断。

 

### this关键字的⽤法  (1)

![image-20211207211227252](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207211227252.png)

(1) this调用本类中的属性，也就是类中的成员变量，同时形参与成员变量重名时可以用this来区分；
(2) this调用本类中的其他方法；
(3) this调用本类中的其他构造方法，调用时要放在本构造方法的首行。

### super关键字的⽤法 (1)

![image-20211207211303195](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207211303195.png)

![image-20211207211317917](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207211317917.png)

### static存在的主要意义  (1)

> ![image-20211207211352088](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207211352088.png)

=======

 

![image-20220607105112029](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220607105112029.png)

（1）静态变量：又称为类变量，也就是说这个变量属于类的，类所有的实例都共享静态变量，可以直接通过类名来访问它。静态变量在内存中只存在一份；

（2）静态方法：静态方法在类加载的时候就存在了，它不依赖于任何实例。可以通过类名直接访问

> 所以静态方法必须有实现，也就是说它不能是抽象方法。只能访问所属类的静态字段和静态方法，方法中不能有 this 和 super 关键字；

![image-20220607105220814](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220607105220814.png)

（3）静态语句块：静态语句块在类初始化时运行一次；可以将只需要进行一次初始化的操作放在static中，用于优化程序性能

此外：

（4）静态内部类：非静态内部类依赖于外部类的实例，而静态内部类不需要。静态内部类不能访问外部类的非静态的变量和方法；

 

### 静态方法为什么不能调用非静态成员 (1)

这个需要结合 JVM 的相关知识，主要原因如下：
静态方法是属于类的，在类加载的时候就会分配内存，可以通过类名直接访问。而非静态成员属于实例对象，只有在对象实例化之后才存在，需要通过类的实例对象去访问。在类的非静态成员不存在的时候静态成员就已经存在了，此时调用在内存中还不存在的非静态成员，属于非法操作。

### 静态方法和实例有何不同 (1)

#### 1.调用方式

在外部调用静态方法时，可以使用 类名.方法名 的方式，也可以使用 对象.方法名 的方式，而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。

#### 2.访问类成员是否存在限制

静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），不允许访问实例成员（即实例成员变量和实例方法），而实例方法不存在这个限制。

 

### 比较 JVM 和 JDK 以及 JRE⭐⭐⭐ (1)

* JVM定义-Java二进制字节码的运行环境

  Java源代码 - 经过Javac编译成.class字节码-Java字节码再使用一个Java程序装进虚拟机就可以运行了

* JVM好处-

  一次编写，到处运行（JVM屏蔽了字节码与底层操作系统之间的差异，对外提供了一致的运行环境，JVM用解释的方法执行二进制字节码，达到代码的平台无关性）

  自动内存管理，垃圾回收功能（C和C++没有垃圾回收功能，很容易造成内存泄漏，所以JVM大大降低出错机会）

  数组下标越界检查（数组下标越界抛异常，如若编程不小心数组越界数组的新元素覆盖程序的其他部分会导致很严重的后果）

  多态（提升程序代码的可扩展性，JVM使用虚方法调用的机制实现了多态）

* **JVM 并不是只有一种！只要满足 JVM 规范，每个公司、组织或者个人都可以开发自己的专属 JVM。** 平时最常用的是HotSpot VM

* JRE 是 Java 运行时环境。它是运行已编译 Java 程序所需的所有内容的集合，包括 Java 虚拟机（JVM），Java 类库，java 命令和其他的一些基础构件。但是，它不能用于创建新程序。

* JDK 是 Java Development Kit 缩写，它是功能齐全的 Java SDK（软件开发工具包）。JDK已经成为使用最广泛的Java SDK它拥有 JRE 所拥有的一切，还有编译器（javac）和工具（如 javadoc 和 jdb）。它能够创建和编译程序。

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211123143929609.png" alt="image-20211123143929609" style="zoom:150%;" />

### 为什么说 Java 语言“解释与编译并存”⭐⭐ (1)

我们可以将高级编程语言按照程序的执行方式分为两种：

* **编译型** ：[编译型语言](https://zh.wikipedia.org/wiki/編譯語言) 会通过[编译器](https://zh.wikipedia.org/wiki/編譯器)将源代码一次性翻译成可被该平台执行的机器码。一般情况下，编译语言的执行速度比较快，开发效率比较低。常见的编译性语言有 C、C++。
* **解释型** ：[解释型语言](https://zh.wikipedia.org/wiki/直譯語言)会通过[解释器](https://zh.wikipedia.org/wiki/直譯器)一句一句的将代码解释（interpret）为机器代码后再执行。解释型语言开发效率比较快，执行速度比较慢。常见的解释性语言有 Python、JavaScript等等。

![编译型语言和解释型语言.png](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/%E7%BC%96%E8%AF%91%E5%9E%8B%E8%AF%AD%E8%A8%80%E5%92%8C%E8%A7%A3%E9%87%8A%E5%9E%8B%E8%AF%AD%E8%A8%80.png)

这是因为 Java 语言既具有编译型语言的特征，也具有解释型语言的特征。因为 Java 程序要经过先编译，后解释两个步骤，由 Java 编写的程序需要先经过编译步骤，生成字节码（`.class` 文件），这种字节码必须由 Java 解释器来解释执行。

### Java 基本类型有哪几种，各占多少位？⭐⭐(1)

Java 中有 8 种基本数据类型，分别为：

1. 6 种数字类型 ：`byte`、`short`、`int`、`long`、`float`、`double`

2. 1 种字符类型：`char`

3. 1 种布尔型：`boolean`。

   | 基本类型  | 位数 | 字节 | 默认值  |
   | :-------- | :--- | :--- | :------ |
   | `int`     | 32   | 4    | 0       |
   | `short`   | 16   | 2    | 0       |
   | `long`    | 64   | 8    | 0L      |
   | `byte`    | 8    | 1    | 0       |
   | `char`    | 16   | 2    | 'u0000' |
   | `float`   | 32   | 4    | 0f      |
   | `double`  | 64   | 8    | 0d      |
   | `boolean` | 1    |      | false   |

   基本数据类型直接存放在 Java 虚拟机栈中的局部变量表中，而包装类型属于对象类型，我们知道对象实例都存在于堆中。相比于对象类型， 基本数据类型占用的空间非常小。

 

### 包装类型的常量池技术了解吗(1)

Java 基本类型的包装类型大部分都实现了常量池技术（Java8在永久代   8之后在元空间；方法区的实现从永久代->元空间）
Byte
,Short
,Integer
,Long
这 4 种包装类默认创建了数值 [-128，127] 的相应类型的缓存数据，Character创建了数值在 [0,127] 范围的缓存数据，Boolean直接返回 True or False。如果超出对应范围仍然会去创建新的对象，缓存的范围区间的大小只是在性能和资源之间的权衡。两种浮点数类型的包装类 Float,Double并没有实现常量池技术。

 

### 自动装箱与拆箱了解吗？原理是什么？(1)

什么是自动拆装箱？
装箱：将基本类型用它们对应的引用类型包装起来；
拆箱：将包装类型转换为基本数据类型；

从字节码中，我们发现装箱其实就是调用了 包装类的valueOf()
方法，拆箱其实就是调用了 xxxValue()
方法。
因此，Integer i = 10等价于 Integer i = Integer.valueOf(10)

int n = i等价于 int n = i.intValue();

注意：如果频繁拆装箱的话，也会严重影响系统的性能。我们应该尽量避免不必要的拆装箱操作。

 

### Java 泛型，类型擦除⭐⭐⭐ (1)

Java 泛型了解么？什么是类型擦除？介绍一下常用的通配符？

* Java 泛型（generics） 是 JDK 5 中引入的一个新特性, 泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。泛型还避免了类型强转。

  泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。一般在创建对象时，将未知的类型确定为具体的类型。当没有指定泛型时，默认类型为Object类型。

* Java 的泛型是伪泛型，这是因为 Java 在运行期间，所有的泛型信息都会被擦掉，这也就是通常所说类型擦除。

* 泛型是通过类型擦除来实现的，编译器在编译时擦除了所有类型相关的信息(字节码不包含类型信息)，所以在运行时不存在任何类型相关的信息。例如：List\<String> 在运行时仅用一个 List 来表示。这样做的目的，是确保能和 Java 5 之前的版本开发二进制类库进行兼容（保证兼容以前的代码）。

* 类型擦除：**泛型信息只存在于代码编译阶段**，在进入 JVM 之前，与泛型相关的信息会被擦除掉。

* 在泛型类被类型擦除的时候，之前泛型类中的类型参数部分如果没有指定上限，如 < T > 则会被转译成普通的 Object 类型，如果指定了上限如 < T extends String > 则类型参数就被替换成类型上限。

  泛型一般有三种使用方式: 泛型类、泛型接口、泛型方法。

  **常用的通配符为： T，E，K，V，？**

  - ？ 表示不确定的 Java 类型
  - T (type) 表示具体的一个 Java 类型
  - K V (key value) 分别代表 Java 键值中的 Key Value
  - E (element) 代表 Element

  你的项目中哪里用到了泛型？

![image-20220625081102557](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220625081102557.png)

[(3条消息) Java 泛型，你了解类型擦除吗？_frank909的博客-CSDN博客_java类型擦除](https://blog.csdn.net/briblue/article/details/76736356)

###  == 和 equals() 的区别⭐⭐⭐(1)

> 注：这个问题经常问，面试官经常问为什么重写 equals()时要重写 hashCode() 方法？另外，这个问题经常结合着 HashSet 问。
>

  * ==：如果比较的对象是基本数据类型，则比较的是数值是否相等；如果比较的是引用数据类型，则比较的是对象的地址值是否相等。

  * equals 方法：用来比较两个对象的内容是否相等。注意：equals 方法不能用于比较基本数据类型的变量。如果没有对 equals 方法进行重写，则比较的是引用类型的变量所指向的对象的地址（此时等价于用”==“）。

    （很多类重写了 equals 方法，比如 String、**Integer** 等把它变成了值比较，所以一般情况下 equals 比较的是值是否相等）

![image-20220628125222058](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220628125222058.png)

**new  string("aaa") 的方式不会自定放入字符串常量池；而 s="aaa"会**

 

### **为什么要有** **hashCode？**

我们以“ HashSet 如何检查重复”为例⼦来说明为什么要有 hashCode？

当你把对象加入 `HashSet` 时，`HashSet` 会先计算对象的 `hashcode` 值来判断对象加入的位置，同时也会与其他已经加入的对象的 hashcode 值作比较，如果没有相符的 `hashcode`，`HashSet` 会假设对象没有重复出现。但是如果发现有相同 `hashcode` 值的对象，这时会调用 `equals()` 方法来检查 `hashcode` 相等的对象是否真的相同。如果两者相同，`HashSet` 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。这样我们就⼤⼤减少了 equals 的次数，相应就⼤⼤提⾼了执⾏速度。

 

### **为什么重写 equals() 就一定要重写 hashCode() 方法？**⭐⭐⭐⭐ (1)

* Hash表：存储键值对的数据结构，通过hash算法，将给定的key算出一个hash值，将value存到hash值对应的地方。下次查找key的时候，以同样的hash算法算出key的hash值，到相应的地方找到该value。实现O(1)时间复杂度的查找。

* Hash碰撞：存在两个不同的key，它们的hash值相等.

* 因为如果是糟糕的哈希算法就越容易碰撞，所以说有可能**两个对象有相同的 hashcode 值，它们也不一定是相等的**

  ![image-20211125161931363](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211125161931363.png)

* hashCode() 的作用是获取哈希码（int 整数），也称为散列码。这个哈希码的作用是确定该对象在哈希表中的索引位置。`hashCode()`定义在 JDK 的 `Object` 类中，这就意味着 Java 中的任何类都包含有hashCode()函数。

* HashSet 是根据对象的哈希值来确定元素在集合中的存储位置。保证元素唯一性的方式依赖于： hashCode 与 equals 方法。

 

**答**：hashCode()的默认行为是对堆上的对象产生独特值。**如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等**（即使这两个对象指向相同的数据），简单来说就是：如果 equals方法判断两个对象是相等的，那这两个对象的 hashCode值也要相等,所以必须重写hashCode方法。不重写的话 hashset就判不了重复了。

 

 

### 重载和重写的区别⭐⭐⭐⭐ (1)

* 重载：发生编译时，同一个类中同名的方法具有不同的参数列表，可做出不同的处理，不能根据返回类型进行区分【因为：函数调用时不能指定类型信息，编译器不知道你要调哪个函数】；
* 重写：发生在运行时，就是输入数据一样，是子类对父类的允许访问的方法的实现过程进行重新编写。**外部样子不能改变，内部逻辑可以改变。**

 

* | 区别点     | 重载     | 重写                                                         |
  | ---------- | -------- | :----------------------------------------------------------- |
  | 发生范围   | 同一个类 | 子类                                                         |
  | 参数列表   | 必须修改 | 一定不能修改                                                 |
  | 返回类型   | 可修改   | 方法的返回类型是 void 和基本数据类型，则返回值重写时不可修改。子类方法返回值类型应比父类方法返回值类型更小或相等 |
  | 异常       | 可修改   | 子类方法声明抛出的异常类应比父类方法声明抛出的异常类更小或相等； |
  | 访问修饰符 | 可修改   | 一定不能做更严格的限制（可以降低限制）                       |
  | 发生阶段   | 编译期   | 运行期                                                       |

 

### 深拷贝和浅拷贝以及引用拷贝⭐ (1)

* 引用拷贝：引用拷贝是对引用地址的拷贝；就是两个不同的引用指向同一个对象。

  `深拷贝`和`浅拷贝`都属于**对象拷贝**，会在堆上创建一个新的对象

* **浅拷贝**：

  - 对于**基本数据类型**进行值传递；在内存的另一个空间内存放，修改这个值不会影响到拷贝源的值

  - 对于**引用类型**：拷贝对象和原始对象引用同一个内部对象。浅克隆只是复制了对象的引用地址，两个对象指向同一个内存地址，所以修改其中任意的值，另一个值都会随之变化，这就是浅克隆。

  > 会在堆上创建一个新的对象（区别于引用拷贝的一点）

* **深拷贝**：

  - 对于**基本数据类型**进行值传递

  - 对于**引用类型**：深拷贝会完全复制整个对象，包括这个对象所包含的内部对象。深拷贝是将对象及值复制过来，两个对象修改其中任意的值另一个值不会改变，这就是深拷贝

  （实现的时候都是继承cloneable方法，重写clone方法：浅拷贝就是拷贝对象调用clone方法，返回原对象.clone即可；深拷贝其内部对象也要调用clone方法进行拷贝）

  [某大厂Java面试题：深拷贝和浅拷贝区别了解吗？什么是引用拷贝？_Java云海.的博客-CSDN博客_java深拷贝和浅拷贝面试题](https://blog.csdn.net/a1472750149/article/details/121620537?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~default-1-121620537-blog-108889116.pc_relevant_sortByAnswer&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~default-1-121620537-blog-108889116.pc_relevant_sortByAnswer&utm_relevant_index=1)

  <img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/shallow&deep-copy.png" alt="img" style="zoom:80%;" />

 

### 面向对象和面向过程的区别⭐⭐⭐ (1)

面向过程是直接将解决问题的步骤分析出来，然后用函数把步骤一步一步实现，然后再依次调用就可以了；

而面向对象是将构成问题的事物，分解成若干个对象，建立对象的目的不是为了完成一个步骤，而是为了描述某个事物在解决问题过程中的行为。以对象为中心，把数据及对数据的操作方法放在一起，作为一个相互依存的整体。对同类对象抽象出其共性，形成类。

[面向对象与面向过程的区别 - NYfor2018 - 博客园 (cnblogs.com)](https://www.cnblogs.com/NYfor2018/p/12442019.html)

* **区别**：

  > （1）编程思路不同：面向过程以实现功能的函数开发为主，而面向对象要首先抽象出类、属性及其方法，然后通过实例化类、执行方法来完成功能。
  >
  > （2）封装性：都具有封装性，但是面向过程是封装的是功能，而面向对象封装的是数据和功能。
  >
  > （3）面向对象具有继承性和多态性，而面向过程没有继承性和多态性，所以面向对象优势很明显。
  >
  > （4）性能：**面向过程性能比面向对象高。** 因为类调用时需要实例化，开销比较大，比较消耗资源。但是，**面向过程没有面向对象易维护、易复用、易扩展。**
  >
  > （5）**面向对象易维护、易复用、易扩展。** 因为面向对象有封装、继承、多态性的特性，所以可以设计出低耦合的系统，使系统更加灵活、更加易于维护。

 

### 成员变量与局部变量的区别⭐⭐⭐ (1)

* 从语法形式上看，成员变量是属于类的或类的实例的，而局部变量是在代码块或方法中定义的变量或是方法的参数；成员变量可以被 public,private,static 等修饰符所修饰，而局部变量不能被访问控制修饰符及 static 所修饰；但是，成员变量和局部变量都能被 final 所修饰。
* 从变量在内存中的存储方式来看,如果成员变量是使用 static 修饰的，那么这个成员变量是属于类的，如果没有使用 static 修饰，这个成员变量是属于实例的。成员变量存在于堆内存，局部变量则存在于栈内存。
* 从变量在内存中的生存时间上看，成员变量是对象的一部分，它随着对象的创建而存在，而局部变量随着方法的调用结束而自动消失。
* 从变量是否有默认值来看，成员变量如果没有被赋初值，则会自动以类型的默认值而赋值（一种情况例外:被 final 修饰的成员变量也必须显式地赋值），而局部变量则不会自动赋值。

 

### 创建一个对象用什么运算符?对象实体与对象引用有何不同? (1)

new 运算符，new 创建对象实例（对象实例在堆内存中），对象引用指向对象实例（对象引用存放在栈内存中）。
一个对象引用可以指向 0 个或 1 个对象（一根绳子可以不系气球，也可以系一个气球）;一个对象可以有 n 个引用指向它（可以用 n 条绳子系住一个气球）。

### 对象的相等与指向他们的引用相等,两者有什么不同? (1)

对象的相等，比的是内存中存放的内容是否相等。而引用相等，比较的是他们指向的内存地址是否相等。

 

### 一个类的构造方法的作用是什么? 若一个类没有声明构造方法，该程序能正确执行吗? 为什么?(1)

构造方法主要作用是完成对类对象的初始化工作。
如果一个类没有声明构造方法，也可以执行！因为一个类即使没有声明构造方法也会有默认的不带参数的构造方法。如果我们自己添加了类的构造方法（无论是否有参），Java 就不会再添加默认的无参数的构造方法了，这时候，就不能直接 new 一个对象而不传递参数了，

 

所以我们一直在不知不觉地使用构造方法，这也是为什么我们在创建对象的时候后面要加一个括号（因为要调用无参的构造方法）。如果我们重载了有参的构造方法，记得都要把无参的构造方法也写出来（无论是否用到），因为这可以帮助我们在创建对象的时候少踩坑。

### 构造方法有哪些特点？是否可被 override? (1)

特点：

- 名字与类名相同。

- 没有返回值，但不能用 void 声明构造函数。

- 生成类的对象时自动执行，无需调用。

构造方法不能被 override（重写）,但是可以 overload（重载）,所以你可以看到一个类中有多个构造函数的情况。

 

### 面向对象三大特性是什么 并解释这三大特性⭐⭐⭐⭐ (1)

* 封装：通常认为封装是把数据和操作数据的方法封装起来，同时提供⼀些可以被外界访问的属性的⽅法

* 继承：继承是从已有类得到继承信息创建新类的过程。提供继承信息的类被称为父类（超类/基类），得到继承信息的被称为子类（派生类）。通过使用继承，可以快速地创建新的类，可以提高代码的重用，程序的可维护性，节省大量创建新类的时间 ，提高开发效率。

  > 1. 子类拥有父类对象所有的属性和方法（包括私有属性和私有方法），但是父类中的私有属性和方法 子类是无法访问，**只是拥有**。因为在一个子类被创建的时候，首先会在内存中创建一个父类对象，然后在父类对象外部放上子类独有的属性，两者合起来形成一个子类的对象；
  > 2. 子类可以拥有自己属性和方法，即子类可以对父类进行扩展。
  > 3. 子类可以用自己的方式实现父类的方法。（重写）

* 多态：表示一个对象具有多种的状态。即⼀个引⽤变量到底会指向哪个类的实例对象，该引⽤变量发出的⽅法调⽤到底是哪个类中实现的⽅法，必须在由程序运⾏期间才能决定；

  在 Java 中有两种形式可以实现多态：继承（多个⼦类对同⼀⽅法的重写）和接⼝（实现接⼝并覆盖接⼝中同⼀⽅法）

  > 以继承为例：具体表现为父类的引用指向子类的实例
  >
  > 要实现多态需要做两件事：一是子类继承父类并重写父类中的方法，二是用父类型引用子类型对象，这样同样的引用调用同样的方法就会根据子类对象的不同而表现出不同的行为。

 

### **`String`、`StringBuffer` 和 `StringBuilder` 的区别。**⭐⭐⭐⭐ (1)

> 简单的来说：`String` 类中使用 `final` 关键字修饰字符数组来保存字符串，所以`String` 是不可变的。
>
> 被 `final` 关键字修饰的类不能被继承，修饰的方法不能被重写，修饰的变量是基本数据类型则值不能改变，修饰的变量是引用类型则不能再指向其他对象。

- String是不可变的，`String` 真正不可变有下面几点原因：

1. String使用字符数组来保存字符串，这个数组被 `final` 修饰且为私有的，并且`String` 类没有提供/暴露修改这个字符串的方法。

2. `String` 类被 `final` 修饰导致其不能被继承，进而避免了子类破坏 `String`    不可变

 

![image-20220705210736641](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220705210736641.png)

 

> 在 Java 9 之后，String 、`StringBuilder` 与 `StringBuffer` 的实现改用 byte 数组存储字符串 `private final byte[] value`

* `StringBuilder` 与 `StringBuffer`是可变的，`StringBuilder` 与 `StringBuffer` 都继承自 `AbstractStringBuilder` 类，在 `AbstractStringBuilder` 中也是使用字符数组保存字符串，不过没有使用 `final` 和 `private` 关键字修饰，最关键的是这个 `AbstractStringBuilder` 类还提供了很多修改字符串的方法比如 `append` 方法。

  > byte 数组初始容量为 16 ，扩容时：添加字符串长度+加上本身长度 <旧的容量x2+2 : 新的容量=旧的容量x2+2； 否则  新的容量=旧的容量+ 新添加字符串的长度。

* 比较：**线程安全性**

  `String` 中的对象是不可变的，也就可以理解为常量，线程安全。

  `StringBuffer` 对方法加了同步锁或者对调用的方法加了同步锁（ Synchronized），所以是线程安全的。

  > StringBuffer 中并不是所有方法都使用了 Synchronized 修饰来实现同步。

  `StringBuilder` 并没有对方法进行加同步锁，所以是非线程安全的。

* 比较：性能

  每次对 `String` 类型进行改变的时候，都会生成一个新的 `String` 对象，然后将指针指向新的 `String` 对象。

  `StringBuffer` 每次都会对 `StringBuffer` 对象本身进行操作，而不是生成新的对象并改变对象引用。

  相同情况下使用 `StringBuilder` 相比使用 `StringBuffer` 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

  执行效率：StringBuilder （单线程操作）> StringBuffer（多线程操作） > String（操作少量数据情况适用）

 

### 序列化和反序列化⭐⭐ (1)

- **序列化**： 将数据结构或对象转换成二进制字节流的过程

  **序列化的主要目的是通过网络传输对象或者说是将对象存储到文件系统、数据库、内存中。**

- **反序列化**：将在序列化过程中所生成的二进制字节流转换成数据结构或者对象的过程

- 在一个平台上序列化的对象可以在不同的平台上反序列化。序列化是为了解决在对象流进行读写操作时所引发的问题。

- 序列化的实现：

  > 将需要被序列化的类实现 Serializable 接口，该接口没有需要实现的方法，只是用于标注该对象是可被序列化的。然后使用一个输出流（如：FileOutputStream）来构造一个 ObjectOutputStream 对象，接着使用 ObjectOutputStream 对象的 writeObject(Object obj) 方法可以将参数为 obj 的对象写出，反序列化话则使用输入流。

![image-20220615093246594](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220615093246594.png)

 

> 序列化
>
> ```java
> public class SerializeDemo{
>     public static void main(String [] args) {
>         Employee e = new Employee();
>         e.name = "zhangsan";
>         e.address = "beiqinglu";
>         e.age = 20;
>         try {
>             // 创建序列化流对象
>             ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("employee.txt"));
>             // 写出对象
>             out.writeObject(e);
>             // 释放资源
>             out.close();
>             fileOut.close();
>             System.out.println("Serialized data is saved"); // 姓名，地址被序列化，年龄没有被序列化。
>         } catch(IOException i) {
>             i.printStackTrace();
>         }
>     }
> }
> ```
>
> 反序列化
>
> ```java
> public class DeserializeDemo {
>     public static void main(String [] args) {
>         Employee e = null;
>         try {
>             // 创建反序列化流
>             FileInputStream fileIn = new FileInputStream("employee.txt");
>             ObjectInputStream in = new ObjectInputStream(fileIn);
>             // 读取一个对象
>             e = (Employee) in.readObject();
>             // 释放资源
>             in.close();
>             fileIn.close();
>         }catch(IOException i) {
>             // 捕获其他异常
>             i.printStackTrace();
>             return;
>         }catch(ClassNotFoundException c) {
>                 // 捕获类找不到异常
>             System.out.println("Employee class not found");
>             c.printStackTrace();
>             return;
>         }
>         // 无异常,直接打印输出
>         System.out.println("Name: " + e.name); // zhangsan
>         System.out.println("Address: " + e.address); // beiqinglu
>         System.out.println("age: " + e.age); // 0
>     }
> }
> ```

 

### Java 序列化中如果有些字段不想进行序列化，怎么办？(1)

对于不想进行序列化的变量，使用 transient关键字修饰。
transient关键字的作用是：阻止实例中那些用此关键字修饰的的变量序列化；当对象被反序列化时，被 transient修饰的变量值不会被持久化和恢复。
关于 transient还有几点注意：
transient 只能修饰变量，不能修饰类和方法。transient 修饰的变量，在反序列化后变量值将会被置成类型的默认值。例如，如果是修饰 int 类型，那么反序列后结果就是 0。static 变量因为不属于任何对象(Object)，所以无论有没有 transient 关键字修饰，均不会被序列化。

 

### Java 中 IO 流分为几种? (1)

按照流的流向分，可以分为输入流和输出流；
按照操作单元划分，可以划分为字节流和字符流；
按照流的角色划分为节点流和处理流。
InputStream/Reader: 所有的输入流的基类，前者是字节输入流，后者是字符输入流。
OutputStream/Writer: 所有输出流的基类，前者是字节输出流，后者是字符输出流。
具体参看自己的笔记：java I-O

 

### 既然有了字节流,为什么还要有字符流?  (1)

问题本质想问：不管是文件读写还是网络发送接收，信息的最小存储单元都是字节，那为什么 I/O 流操作要分为字节流操作和字符流操作呢？

回答：字符流是由 Java 虚拟机将字节转换得到的，问题就出在这个过程还算是非常耗时，并且，如果我们不知道编码类型就很容易出现乱码问题。所以， I/O 流就干脆提供了一个直接操作字符的接口，方便我们平时对字符进行流操作。如果音频文件、图片等媒体文件用字节流比较好，如果涉及到字符的话使用字符流比较好

 

### 反射⭐⭐  (1)

面试官可能会问你什么是反射，它的优缺点是什么，有哪些应用场景。

* 什么是反射：**反射就是在运行时才知道要操作的类是什么，并且可以在运行时获取任意类的所有属性和方法，并调用对应的方法和属性。**Class 和 java.lang.reflect 一起对反射提供了支持。

* 反射机制优缺点：

  - **优点** ： 可以让代码更加灵活、为各种框架提供开箱即用的功能，提供了便利。

  - **缺点** ：让我们在运行时有了分析操作类的能力，这同样也增加了安全问题。比如可以无视泛型参数的安全检查（泛型参数的安全检查发生在编译时）。另外，反射的性能也要稍差点，不过，对于框架来说实际是影响不大的。

* 反射的应用场景

  工厂模式，使用反射机制，根据全限定类名获得某个类的 Class 实例。

  **注解** 的实现也用到了反射。

  框架中的动态代理的实现也依赖反射。

 

# Java异常

## 1. 异常类型

不会问的特别细。经常的问法是异常可以分为哪几种，然后你答了可检查异常和不可检查异常以后，会让你举例可检查异常有哪些，不可检查有哪些。

![image-20211125213416414](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211125213416414.png)

`Exception` 能被程序本身处理(`try-catch`)， `Error` 是无法处理的(只能尽量避免)。

受检查异常(必须处理) 和 不受检查异常(可以不处理)

如果受检查异常没有被 `catch`/`throw` 处理的话，就没办法通过编译。

非受检查异常：`RuntimeException` 及其子类都统称为非受检查异常（算术异常、空指针异常、数组越界异常）

受检查异常：`ClassNotFoundException`（类型转换异常）等

![image-20220222090336914](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220222090336914.png)

## finally 块中的代码什么时候被执行？

在 Java 语言的异常处理中，finally 块的作用就是为了保证无论出现什么情况，finally 块里的代码一定会被执行。由于程序执行 return 就意味着结束对当前函数的调用并跳出这个函数体，因此任何语句要执行都只能在 return 前执行（除非碰到 exit 函数），因此 finally 块里的代码也是在 return 之前执行的。

此外，如果 try-finally 或者 catch-finally 中有 return，那么 finally 块中的 return 将会覆盖别处的 return 语句，最终返回到调用者那里的是 finally 中 return 的值。

 

## finally是否一定会被执行到

不一定。下面列举两种执行不到的情况：

（1）当程序进入 try 块之前就出现异常时，会直接结束，不会执行 finally 块中的代码；

（2）当程序在 try 块中强制退出时也不会去执行 finally 块中的代码，比如在 try 块中执行 exit 方法。

 

## try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

会。程序在执行到 return 时会首先将返回值存储在一个指定的位置，其次去执行 finally 块，最后再返回。因此，对基本数据类型，在 finally 块中改变 return 的值没有任何影响，直接覆盖掉；而对引用类型是有影响的，返回的是在 finally 对 前面 return 语句返回对象的修改值。

 

## try-catch-finally 中那个部分可以省略？

catch 和 finally可以省略其中一个，但必须保留其中一个。try 只适合处理运行时异常，try+catch 适合处理运行时异常+普通异常。也就是说，如果你只用 try 去处理普通异常却不加以 catch 处理，编译是通不过的，因为编译器硬性规定，普通异常如果选择捕获，则必须用 catch 显示声明以便进一步处理。而运行时异常在编译时没有如此规定，所以 catch 可以省略，你加上 catch 编译器也觉得无可厚非。

 

## Error 和 Exception 的区别？★★★

Error 类和 Exception 类的父类都是 Throwable 类。主要区别如下：

Error 类： 一般是指与虚拟机相关的问题，如：系统崩溃、虚拟机错误、内存空间不足、方法调用栈溢出等。这类错误将会导致应用程序中断，仅靠程序本身无法恢复和预防；

Exception 类：表示程序可以处理的异常，可以捕获且可能恢复。遇到这类异常，应该尽可能处理异常，使程序恢复运行，而不应该随意终止异常；分为运行时异常（不收检查的异常）和受检查的异常。

### 运行时异常（不受检查的异常）与受检查的异常有和异同？

运行时异常：如：空指针异常、数组越界、方法传递参数错误、数据类型转换错误。可以编译通过，但是一运行就停止了，程序不会自己处理；

受检查异常：在编译期就能被发现；要么用 try … catch… 捕获，要么用 throws 声明抛出，交给父类处理；如I/O Exception、SQLException、ClassNotFindException;

 

> Exception又分为两类
>
> 　　　　CheckedException：（编译时异常） 需要用try——catch显示的捕获，对于可恢复的异常使用CheckedException。
>
> 　　　　UnCheckedException（RuntimeException）：（运行时异常）不需要捕获，对于程序错误（不可恢复）的异常使用RuntimeException。
>
> 常见的RuntimeException异常
>
> 　　illegalArgumentException：此异常表明向方法传递了一个不合法或不正确的参数。
>
> 　　illegalStateException：在不合理或不正确时间内唤醒一方法时出现的异常信息。换句话说，即 [Java](https://www.baidu.com/s?wd=Java&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YvnhckPhDduHRdPWP9njmv0ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EPHTYn1D3PHc1) 环境或 [Java](https://www.baidu.com/s?wd=Java&tn=44039180_cpr&fenlei=mv6quAkxTZn0IZRqIHckPjm4nH00T1YvnhckPhDduHRdPWP9njmv0ZwV5Hcvrjm3rH6sPfKWUMw85HfYnjn4nH6sgvPsT6KdThsqpZwYTjCEQLGCpyw9Uz4Bmy-bIi4WUvYETgN-TLwGUv3EPHTYn1D3PHc1) 应用不满足请求操作。
>
> 　　NullpointerException：空指针异常（我目前遇见的最多的）
>
> 　　IndexOutOfBoundsException：索引超出边界异常
>
> 常见的CheckedException异常
>
> 　　我们在编写程序过程中try——catch捕获到的一场都是CheckedException。
>
> 　　io包中的IOExecption及其子类，都是CheckedException。
>
>
>
> 举个简单的例子（看别人的，觉得很形象，很好理解）
>
> 　　Error和Exception就像是水池和水池里的水的区别
>
> 　　“水池”，就是代码正常运行的外部环境，如果水池崩溃（系统崩溃），或者池水溢出（内存溢出）等，这些都是跟水池外部环境有关。这些就是java中的error
>
> 　　“水池里的水”，就是正常运行的代码，水污染了、有杂质了，浑浊了，这些影响水质的因素就是Exception。

 

## throw 和 throws 的区别？

（1）throw：在方法体内部，表示抛出异常，由方法体内部的语句处理；throw 是具体向外抛出异常的动作，所以它抛出的是一个异常实例；

（2）throws：在方法声明后面，表示如果抛出异常，由该方法的调用者来进行异常的处理；表示出现异常的可能性，并不一定会发生这种异常。

 

## 常见的异常类有哪些？

- NullPointerException：当应用程序试图访问空对象时，则抛出该异常。
- SQLException：提供关于数据库访问错误或其他错误信息的异常。
- IndexOutOfBoundsException：指示某排序索引（例如对数组、字符串或向量的排序）超出范围时抛出。
- FileNotFoundException：当试图打开指定路径名表示的文件失败时，抛出此异常。
- IOException：当发生某种 I/O 异常时，抛出此异常。此类是失败或中断的 I/O 操作生成的异常的通用类。
- ClassCastException：当试图将对象强制转换为不是实例的子类时，抛出该异常。
- IllegalArgumentException：抛出的异常表明向方法传递了一个不合法或不正确的参数。

 

## 主线程可以捕获到子线程的异常吗？

线程设计的理念：“线程的问题应该线程自己本身来解决，而不要委托到外部”。

正常情况下，如果不做特殊的处理，在主线程中是不能够捕获到子线程中的异常的。

如果想要在主线程中捕获子线程的异常，可以使用 Thread 的静态方法完成设置

```java
Thread.setDefaultUncaughtExceptionHandler(new MyUncaughtExceptionHandle());
```

 

# Java容器

### Java 中常用的容器有哪些？

常见容器主要包括 Collection 和 Map 两种，Collection 存储着对象的集合，而 Map 存储着键值对（两个对象）的映射表

![image-20220224080818137](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220224080818137.png)

 

1. List 集合中对象按照索引排序有顺序，可以有重复对象，允许通过索引随机访问元素；查找元素的效率较高，插入元素和删除元素效率低，因为会引起其他元素位置发生变化

   实现类：LinkedList、ArrayList、Vector。

2. `Queue` 是单端队列，只能从一端插入元素，另一端删除元素，实现上一般遵循 **先进先出（FIFO）** 规则。

   实现类：LinkedList、PriorityQueue

3. Set 集合中存储的数据是无顺序的，但元素在集合中的位置是由元素的hashcode决定，即位置是固定的,并且没有重复对象。

   > 但它的实现类能对集合中的对象按照特定的方式排序，例如 Tree Set 类，可以默认顺序，也可以通过实现 Java.util.Comparator< Type >接口来自定义排序方式。

   实现类：HashSet、LinkedHashSet、Treeset。

4. Map中存储的数据是无序的。Map 中的每一个元素包含一个键和一个值，成对出现，键对象不可以重复，值对象可以重复；

   实现类：HashMap、HashTable、LinkedHashMap、SortMap。

 

### 说说 List, Set, Queue, Map 四者的区别？（1）

- `List`(对付顺序的好帮手): 存储的元素是有序的、可重复的。

- `Set`(注重独一无二的性质): 存储的元素是无序的、不可重复的。

  > 但Tree Set 类，可以默认顺序，也可以通过实现 Java.util.Comparator< Type >接口来自定义排序方式。

- `Queue`(实现排队功能的叫号机): 按特定的排队规则来确定先后顺序，存储的元素是有序的、可重复的。

- `Map`(用 key 来搜索的专家): 使用键值对（key-value）存储，Map 中的每一个元素包含一个键和一个值，成对出现，键对象不可以重复，值对象可以重复；

 

### Arraylist 和 Vector 的区别?

- `ArrayList` 是 `List` 的主要实现类，底层使用 `Object[ ]`存储，适用于频繁的查找工作，线程不安全 ；
- `Vector` 是 `List` 的古老实现类，底层使用`Object[ ]` 存储，线程安全的。

[(2条消息) 数组和链表的区别_博可睿的博客-CSDN博客_数组和链表的区别](https://blog.csdn.net/weixin_42438797/article/details/115339605)

### **`ArrayList` 和 `LinkedList` 的区别**★★★★★

答清楚每个分别采用什么数据结构，对比相应的优点和缺点

* 数据结构实现：ArrayList 是动态数组的数据结构实现，⽽ LinkedList 是双向链表的数据结构实现。
* 随机访问效率：ArrayList （get(i)方式）⽐ LinkedList 在随机访问的时候效率要⾼，因为 LinkedList 是线性的数据存储⽅式，所以需要移动指针从前往后依次查找。
* 增加和删除效率：在尾部增加和删除效率是一样的；**在中间的增加和删除操作**，一般情况下LinkedList 要⽐ ArrayList 效率要⾼，因为 ArrayList 增删操作要影响数组内的其他数据的下标，可能存在数组的扩容和复制； `LinkedList`需要遍历然后修改指针即可。 （数据量大（百万级的数据）可能ArrayList快，**数据量大时可能复制比遍历快**）
* 内存空间占⽤： ArrayList 的空 间浪费主要体现在list 列表的结尾会预留⼀定的容量空间，⽽ LinkedList 的空间花费则体现在它的每⼀个元素都需要消耗⽐ ArrayList 更多的空间（因为要存放直接后继和直接前驱）。
* 线程安全：ArrayList 和 LinkedList 都是不同步的，也就是不保证线程安全；

综合来说，在需要频繁读取集合中的元素时，更推荐使⽤ ArrayList，⽽在插⼊和删除操作较多时，更推荐使⽤ LinkedList。

 

###  说一说 ArrayList 的扩容机制吧 ★★★★★

详见笔主的这篇文章:[通过源码一步一步分析 ArrayList 扩容机制](https://snailclimb.gitee.io/javaguide/#/docs/java/collection/arraylist-source-code?id=_2-arraylist-核心源码解读)

1. 当使用 add 方法的时候首先调用 ensureCapacityInternal 方法，传入 size+1 进去，检查是否需要扩充 elementData 数组的大小

   > （minCapacity - elementData.length > 0是否成立，是则需要扩容）；这里minCapacity 就是size+1

   > **以无参数构造方法创建 `ArrayList` 时，实际上初始化赋值的是一个空数组。当真正对数组进行添加元素操作时，才真正分配容量。即向数组中添加第一个元素时，数组容量扩为 10。**此后添加不会扩容直到添加第 11 个元素，minCapacity(为 11)比 `elementData.length`（为 10）要大。进入 grow 方法进行扩容

2. 调用 grow 方法扩容；

3. 扩容逻辑**`int newCapacity = oldCapacity + (oldCapacity >> 1)`,所以 `ArrayList `每次扩容之后容量都会变为原来的 1.5 倍左右（`oldCapacity `为偶数就是 1.5 倍，否则是 1.5 倍左右）！**奇偶不同，比如 ：10+10/2 = 15, 33+33/2=49。如果是奇数的话会丢掉小数。

   如果新容量没达到指定需要的最小容量minCapacity ，则将此最小容量赋值给新容量。 如果新容量 newCapacity大于 MAX_ARRAY_SIZE,进入(执行) `hugeCapacity()` 方法来比较 minCapacity 和 MAX_ARRAY_SIZE，如果 minCapacity 也大于MAX_ARRAY_SIZE，则新容量则为`Integer.MAX_VALUE`，否则新容量大小则为 MAX_ARRAY_SIZE 即为 `Integer.MAX_VALUE - 8`。

4. ArrayList 中 copy 数组的核心就是 System.arraycopy 方法，将 original 数组的所有数据复制到 copy 数组中，这是一个本地方法。

   grow中调用arrays.copyOf 方法，arrays.copyOf 内部调用了 System.arraycopy 方法。

 

### Array 和 ArrayList 有何区别？什么时候更适合用 Array？

1. Array 可以容纳基本类型和对象，而 ArrayList 只能容纳对象(基本类型会自动装箱)；
2. Array 是指定大小的，而 ArrayList 大小是不固定的。
3. 数组是连续的内存空间；而链表可以是不连续的

**什么时候更适合使用 Array：**

1. 如果列表的大小已经指定，大部分情况下是存储和遍历它们而不是删除
2. 对于遍历基本数据类型， Collections 使用自动装箱，性能稍低
3. 如果你要使用多维数组，使用Array 比 List<> 更容易。

 

### 比较 `HashSet`、`LinkedHashSet` 和 `TreeSet` 三者的异同★★★★★

都是 `Set` 接口的实现类，都能保证元素唯一，并且都不是线程安全的。

* HashSet:

  基于哈希表实现

  1.HashSet中可以有一个Null元素，存入的元素是无序的。

  2.添加、删除操作时间复杂度都是O(1)。

* LinkedHashSet:

  基于链表和哈希表实现

  1.LinkedHashSet中可以有一个Null元素，元素严格按照放入的顺序排列，FIFO。

  2.添加、删除操作时间复杂度都是O(1)。

* TreeSet:

  基于树的结构实现

  1.TreeSet是中不可以有Null元素，根据元素的自然顺序或一定规则进行排序。

  2.添加、删除操作时间复杂度都是O(log(n)) 因为它是基于排序的 所以它最慢。

 

### comparable 和 Comparator 的区别  ★★★★★

- `comparable` 接口实际上是出自`java.lang`包，**Comparable为可排序的，它有一个 `compareTo(Object obj)`方法用来排序，实现该接口的类的对象自动拥有可排序功能**
- `comparator`接口实际上是出自 java.util 包，**Comparator为比较器，它有一个`compare(Object obj1, Object obj2)`方法用来排序，实现该接口可以定义一个针对某个类的排序方式**；也可作为参数进行传递（匿名内部类），比如TreeSet可以传入一个`comparator`进行自定义排序。

 

### 说一说 PriorityQueue

`PriorityQueue` 利用了二叉堆的数据结构来实现的，底层使用可变长的数组来存储数据

`PriorityQueue` 通过堆元素的上浮和下沉，实现了在 O(logn) 的时间复杂度内插入元素和删除堆顶元素。

`PriorityQueue` 是非线程安全的，且不支持存储 `NULL` 和 `non-comparable`（不可排序） 的对象。

`PriorityQueue` 默认是小顶堆，但可以接收一个 `Comparator` 作为构造参数，从而来自定义元素优先级的先后。

 

### HashMap 的实现原理/底层数据结构？JDK1.7 和 JDK1.8

**JDK1.7**：Entry数组 + 链表

解决Hash冲突：JDK1.8之前采⽤的是拉链法。若遇到哈希冲突，则将冲突的值加到链表中即可。

**JDK1.8**：Node 数组 + 链表/红黑树；

解决Hash冲突：当链表上的元素个数超过 8 个并且数组长度 >= 64 时自动把链表转化成红黑树（小于64先进行数组扩容），节点变成树节点，以提高搜索效率和插入效率到 O(logN)。

Entry 和 Node 都包含 key、value、hash、next 属性。只是改了名字；

> [hashmap中为何链表长度大于8才转换成红黑树 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/348756860)  概率值的问题；大于8概率小于千分之一

 

### HashMap 的 put 方法的执行过程？

当我们想往一个 HashMap 中添加一对 key-value 时，系统首先会计算 key 的 hash 值，然后根据 hash 值确认在 table 中存储的位置。若该位置没有元素，则直接插入。否则迭代该处元素链表并依次比较其 key 的 hash 值。如果两个 hash 值相等且 key 值相等，则用新的 Entry 的 value 覆盖原来节点的 value。如果两个 hash 值相等但 key 值不等 ，则进行插入操作。

 

### HashMap 的 get 方法的执行过程？

通过 key 的 hash 值找到在 table 数组中的索引处的 Entry，然后返回该 key 对应的 value 即可。

在这里能够根据 key 快速的取到 value 除了和 HashMap 的数据结构密不可分外，还和 Entry 有莫大的关系。HashMap 在存储过程中并没有将 key，value 分开来存储，而是当做一个整体 key-value 来处理的，这个整体就是Entry 对象。在存储的过程中，系统根据 key 的 HashCode 来决定 Entry 在 table 数组中的存储位置，在取的过程中同样根据 key 的 HashCode 取出相对应的 Entry 对象（value 就包含在里面）。

 

### HashMap 的 get 方法能否判断某个元素是否在 map 中？

HashMap 的 get 函数的返回值不能判断一个 key 是否包含在 map 中，因为 get 返回 null 有可能是不包含该 key，也有可能该 key 对应的 value 为 null。因为 HashMap 中允许 key 为 null，也允许 value 为 null。

 

### HashMap 多线程操作导致死循环问题★★★★★

注：jdk 1.8 后解决了这个问题，但是还是不建议在多线程下使用 `HashMap`,因为多线程下使用 `HashMap` 还是会存在其他问题比如数据丢失。并发环境下推荐使用 `ConcurrentHashMap`.

 

JDK7的HashMap头插法循环的问题：

B站：

https://www.bilibili.com/video/BV1n541177Ea?from=search&seid=525385675315291559&spm_id_from=333.337.0.0

CSDN：

https://blog.csdn.net/dgutliangxuan/article/details/78779448⭐

[HashMap头插法为什么会出现死循环 产生循环链表的影响是什么_littlehaes的博客-CSDN博客_头插法为什么会死循环](https://blog.csdn.net/littlehaes/article/details/105241194)

总结：

* **1.Hashmap在插入元素过多的时候需要进行Resize，**

  Resize的条件是 HashMap.Size >= Capacity * LoadFactor（负载因子，默认0.75）。

  > Resize:
  >
  > **1.扩容**:创建一个新的Entry空数组，长度是原数组的2倍。
  >
  > 2.**ReHash**：遍历原Entry数组，把所有的Entry重新Hash到新数组。为什么要重新Hash呢（1.7）？因为长度扩大以后，Hash的规则也随之改变。算出来的hash值也变。
  >
  > 源码是 俩个线程先进入Resize（）方法，然后进入transfer方法进行 Rehash();

* **ReHash在并发的情况下可能会形成链表环**。

  > 链表头插法的会颠倒原来一个散列桶里面链表的顺序。在并发的时候原来的顺序被另外一个线程a颠倒了，而被挂起线程b恢复后（因为顺序颠倒，所以线程b第一次的e和next的指向是有问题的，与原来相反）拿扩容前的节点和顺序继续完成第一次循环后，基于a线程扩容后的链表顺序（在a的扩容后的链表上操作）重新排列链表中的顺序，最终形成了环。进而使得后面 get 的时候，如若get到的位置恰好是带有循环链表的位置，会死循环，CPU成功到达100%。

 

### HashMap 的长度为什么是 2 的幂次方★★★★★

  因为map的存储需要进行哈希定位。Hash 值的范围很大，内存是放不下的，用之前还要先做对数组的长度取模运算，得到的余数才能用来要存放的位置也就是对应的数组下标。

- 当 length 为 2 的 n 次方时，h & (length – 1) 就相当于对 length 取模，而且速度比直接取模快得多，**这是 HashMap 在速度上的一个优化。而且每次扩容时都是翻倍。**


-     如果 length 不是 2 的次幂，会造成空间浪费，比如：length 为 15，则 length – 1 为 14，对应的二进制为 1110，在和hash进行与操作，最后一位都为 0 ，而 0001，0011，0101，1001，1011，0111，1101 这几个位置永远都不能存放元素了（不会有与操作得到这几个值），空间浪费相当大。更糟的是这种情况中，数组可以使用的位置比数组长度小了很多，这意味着进一步增加了碰撞的几率，减慢了查询的效率。

 


### HashMap HashTable以及ConcurrentHashMap的区别★★★★★

 

#### 1.HashMap 的底层实现：

>     数组的特点是：寻址容易，插⼊和删除困难；链表的特点是：寻址困难，但插⼊和删除容易；所以我们将数组和链表结合在⼀起，发挥两者各⾃的优势，使⽤⼀种叫做拉链法的⽅式可以解决哈希冲突。
>

JDK1.8 之前：

> HashMap底层是Entry数组 + 链表结合在一起使用   也就是 **链表散列**。
>
> 解决Hash冲突：JDK1.8之前采⽤的是拉链法。若遇到哈希冲突，则将冲突的值加到链表中即可。


JDK1.8:

>HashMap底层是Node 数组 + 链表/红黑树。
>
>相比于 JDK1.8 的 hash 方法 ，JDK 1.7 的 hash 方法的性能会稍差一点点，因为毕竟扰动了 4 次。
>
>JDK1.8 之后在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）时，将链表转化为红黑树，**以提高搜索效率和插入效率到 O(logN)**。
>
><img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/jdk1.8%E4%B9%8B%E5%90%8E%E7%9A%84%E5%86%85%E9%83%A8%E7%BB%93%E6%9E%84-HashMap.png" alt="jdk1.8之后的内部结构-HashMap" style="zoom:50%;" />
>
>JDK1.8主要解决或优化了以下问题：
>
>1. resize 扩容优化
>2. 引⼊了红⿊树，**⽬的是避免单条链表过⻓⽽影响查询效率**
>3. 解决了多线程死循环问题，但仍是⾮线程安全的，多线程时可能会造成数据丢失问题。

> Entry 和 Node 都包含 key、value、hash、next 属性。
>

回答hashmap原理时，先回答上面再加上put的执行过程；

 

#### 3.HashMap的扩容操作是怎么实现的?

①.在jdk1.8中，hashmap第一次调用put 方法时，会调用 resize 方法对 table 数组进行初始化，如果不传入指定值，默认大小为 16。

或者hashmap中的键值对数量⼤于阀值（HashMap.Size >= Capacity * LoadFactor）时，也会调⽤resize⽅法进⾏扩容；

②.每次扩展的时候，都是扩展2倍；

③.扩展后Node对象的位置要么在原位置，要么移动到**原偏移量+原数组长度**的位置。

具体过程：第一次调用 HashMap 的 put 方法时，会调用 resize 方法对 table 数组进行初始化，如果不传入指定值，默认大小为 16， 或者当该数组中元素个数⼤于其临界值(第⼀次为12) , 这个时候在扩容的同时也会伴随的桶上⾯的元素进⾏重新分发，这也是 JDK1.8版本的⼀个优化的地⽅，在1.7中，扩容之后需要重新去计算其Hash值，根据Hash值对其进⾏分发，但在1.8版本中，则是根据在同⼀个桶的位置中进⾏判断**(e.hash&oldCap)是否为0，如旧数组长度为16时，二进制 10000，e.hash&oldCap就计算了哈希值的第五位是否为0，为0时哈希值与新的数组长度-1 相与则原数组位置相同，为1时则相当在原位置最高位左边添加一个1，即原偏移量+原数组长度**；这也是 HashMap 中容量一定的是 2 的整数次幂带来的方便之处。

 

#### 4.HashMap 与 HashTable 有什么区别

- 底层数据结构：

  两者基本相似

  JDK1.8 以后的 HashMap 在解决哈希冲突时有了较⼤的变化，当链表⻓度⼤于阈值（默认为8）并且数组长度大于64时，将链表转化为红⿊树，以减少搜索时间。Hashtable 没有这样的机制。

- 线程安全：

  HashMap 是⾮线程安全的，HashTable 是线程安全的（所有操作都是粗暴的 synchronized）；HashTable 内部的⽅法基本都经过 synchronized 修饰。这相当于给整个哈希表加了一把大锁。（如果你要保证线程安全的话就使⽤ ConcurrentHashMap 吧！）；

- 效率：

  因为线程安全的问题，HashMap 要⽐ HashTable 效率⾼⼀点。另外，HashTable 基本被淘汰，不要在代码中使⽤它；

- 对Null key 和Null value的⽀持：

  HashMap 中，null 可以作为键，这样的键只有⼀个，可以有⼀个或多个键所对应的值为 null。 但是在 HashTable 中 put 进的键值只要有⼀个 null，直接抛NullPointerException。

- 初始容量⼤⼩和每次扩充容量⼤⼩的不同 ：

  ①创建时如果不指定容量初始值，Hashtable 默认的初始⼤⼩为11，之后每次扩充，容量变为原来的2n+1。HashMap 默认的初始化⼤⼩为16。之后每次扩充，容量变为原来的2倍。

  ②创建时如果给定了容量初始值，那么 Hashtable 会直接使⽤你给定的⼤⼩，⽽ HashMap 会将其扩充为2的幂次⽅⼤⼩。也就是说 HashMap 总是使⽤2的幂作为哈希表的⼤⼩。

  > 推荐使⽤：
  >
  > 在 Hashtable 的类注释可以看到，Hashtable 是保留类不建议使⽤，推荐在单线程环境下使⽤ HashMap 替代，如果需要多线程使⽤则⽤ ConcurrentHashMap 替代。

 

#### 5.HashMap 和 ConcurrentHashMap 的区别

- HashMap 不是线程安全的，而 ConcurrentHashMap 是线程安全的。

- ConcurrentHashMap 的具体实现；下面第七题

- HashMap的键值对允许有null，但是ConCurrentHashMap都不允许。

 

#### 6.ConcurrentHashMap 和 Hashtable 的区别

> ConcurrentHashMap 和 Hashtable 的区别主要体现在实现线程安全的⽅式上不同。
>
> HashTable 和 ConcurrentHashMap 相比，效率低。

**底层数据结构：**

JDK1.7的 ConcurrentHashMap 底层采⽤ 分段的数组+链表 实现，JDK1.8 采⽤的数据结构跟HashMap1.8的结构⼀样，数组+链表/红⿊⼆叉树。Hashtable 和 JDK1.8 之前的 HashMap 的底层数据结构类似都是采⽤ 数组+链表 的形式，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突⽽存在的；

**实现线程安全的⽅式（重要）：**

① 在JDK1.7的时候，ConcurrentHashMap（分段锁） 对整个桶数组进⾏了分割分段 (Segment)，而每个Segment元素，即每个分段则类似于一个Hashtable；这样，在执行 put 操作时首先根据 hash 算法定位到元素属于哪个 Segment，然后对该 Segment 加锁即可，Segment 实现了 ReentrantLock；因此， ConcurrentHashMap 在多线程并发编程中可以实现多线程 put操作。提⾼并发访问率。 （默认分配16个Segment，⽐Hashtable效率提⾼16倍。）

到了 JDK1.8 的时候已经摒弃了Segment的概念，⽽是直接⽤ Node 数组+链表+红⿊树的数据结构来实现，并发控制使⽤ synchronized 和 CAS 来操作。（JDK1.6以后 对 synchronized锁做了很多优化） 整个看起来就像是优化过且线程安全的 HashMap，虽然在JDK1.8中还能看到 Segment 的数据结构，但是已经简化了属性，只是为了兼容旧版本；

② Hashtable(同⼀把锁，即每次锁住整张表让线程独占，致使效率低下) :使⽤ synchronized 来保证线程安全，效率⾮常低下。当⼀个线程访问同步⽅法时，其他线程也访问同步⽅法，可能会进⼊阻塞或轮询状态，如使⽤ put 添加元素，另⼀个线程不能使⽤ put 添加元素，也不能使⽤ get，竞争会越来越激烈效率越低。

 

#### 7.ConcurrentHashMap 底层具体实现知道吗？实现原理是什么？

> JDK1.7 ：
>
> ⾸先将数据分为⼀段⼀段的存储，然后给每⼀段数据配⼀把锁，当⼀个线程占⽤锁访问其中⼀个段数据时，其他段的数据也能被其他线程访问。
>
> 在JDK1.7中，ConcurrentHashMap采⽤Segment + HashEntry数组的⽅式进⾏实现，结构如下：
>
> Segment 实现了 ReentrantLock ,所以 Segment 是⼀种可重⼊锁，扮演锁的⻆⾊。 HashEntry ⽤于存储键值对数据
>
> * ⼀个 ConcurrentHashMap ⾥包含⼀个 Segment 数组。Segment 的结构和HashMap类似，是⼀种数组和链表结构，⼀个Segment 包含⼀个 HashEntry 数组，**每个** **HashEntry 是⼀个链表结构的元素**，当对 HashEntry 数组的数据进⾏修改时，必须⾸先获得对应的 Segment的锁。就按默认的ConcurrentLevel 为 16 来讲，理论上就允许 16 个线程并发执行。所以，对于同一个 Segment 的操作才需考虑线程同步，不同的 Segment 则无需考虑。因此，ConcurrentHashMap 定位一个元素的过程需要进行两次 Hash 操作。第一次 Hash 定位到 Segment，第二次 Hash 定位到元素所在的链表的头部。
>
> ![image-20220403104517430](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220403104517430.png)
>
> ![image-20211127215157238](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211127215157238.png)
> 该类包含两个静态内部类 HashEntry 和 Segment ；前者⽤来封装映射表的键值对，后者⽤来充当锁的⻆⾊；
>
> Segment 是⼀种可重⼊的锁 ReentrantLock
>
>
>
> JDK1.8：
>
> 在JDK1.8中，放弃了Segment臃肿的设计，取⽽代之的是采⽤Node + CAS + Synchronized来保证并发安全进⾏实现，
>
> **synchronized只锁定当前链表或红⿊⼆叉树的⾸节点**，这样只要 hash 不冲突，就不会产生并发，效率又提升 N 倍。
>
> - **初始化**：多线程调用put方法初始化的时候，采用cas机制判断到底是哪个线程有资格进行初始化，其他线程均只能等待。cas原子性的设置标记位sizeCtl，同时标记位用volatile保证可见性
>
>   - sizeCtl=-1；有线程抢占到了初始化资格，正在初始化数组；
>
>   - sizeCtl=0；数组未初始化，并且没指定初始容量
>
>   - sizeCtl>0;  初始化完成代码扩容阈值，还未初始化代表数组的初始容量
>
> - **put** 插入时 当前node节点为空，没有线程对此Node进行插入操作；采用cas方式插入数据；不然Synchronized锁定当前节点
>
> - **扩容**：ConcurrentHashMap运用各类CAS操作，将扩容操作的并发性能实现最大化，在扩容过程中，就算有线程调用get查询方法，也可以安全的查询数据，若有线程进行put操作，还会协助扩容，利用sizeCtl标记位和各种volatile变量进行CAS操作达到多线程之间的通信、协助，在迁移过程中只锁一个Node节点，即保证了线程安全，又提高了并发性能。
>
> - **计算容量（size方法）**：分而治之的思想，若竞争不大直接CAS递增baseCount值即可；竞争激烈时采用计数桶countcell的方式，让线程并发计数；最后返回size大小：遍历各桶的个数+basesize
>
>   **注意**：他的实现过程是线程安全的；**但是获得的size大小可能和当前容量不一致**；因为中间可能有put数据；put数据和获取大小操作之间并不是原子的；
>
>   [ConcurrentHashMap是如何实现线程安全的_Static_lin的博客-CSDN博客_concurrenthashmap如何实现线程安全](https://blog.csdn.net/qq_41737716/article/details/90549847)
>
> ![Java8 ConcurrentHashMap 存储结构（图片来自 javadoop）](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/java8_concurrenthashmap.png)

[sizeCtl含义_Skuld66的博客-CSDN博客](https://blog.csdn.net/qq_39492864/article/details/119517701)

[ConcurrentHashMap中sizeCtl的说明 - 编程猎人 (programminghunter.com)](https://www.programminghunter.com/article/41662156232/)

#### 8.JDK1.8之后，HashMap头插法改为尾插法？

1.头插法在并发下有致命问题，在并发场景下可能导致链表成环的问题，get 数据时导致死循环；而在jdk1.8中采用尾插入法，在扩容时会保持链表元素原本的顺序，就不会出现链表成环的问题了。[HashMap头插法为什么会出现死循环 产生循环链表的影响是什么_littlehaes的博客-CSDN博客_头插法为什么会死循环](https://blog.csdn.net/littlehaes/article/details/105241194)

> 举例描述：一个链表 1指向3；现在要进行扩容，又有两个线程1、2；线程1完成扩容 因为头插法使3指向1，回到线程2 （e.next = newTable[i];）后，1又指向3;这样就造成了环形链表；get(5)的话就会在环中一直寻找，死循环

2.在 1.8 之前因为处理 hash 冲突的方式是用链表存放数据，使用头插法可以提升一定效率。但是在 1.8 之后这个效率提升就可有可无了，链表长度超过 7 就要考虑升级红黑树了，所以哪怕进行尾插遍历次数也会很有限，效率影响不大。

> 3.就是因为 1.8 之后数据结构的变动，当链表长度达到阈值，升级为红黑树后头插法就不适用了，因为构建红黑树需要进行比对更新序列，也就不能去说是头插法还是尾插了。

 

#### 9.HashMap的负载因子为什么系统默认是0.75（也可以在构造方法中重新指定）?

> **这是时间和空间的权衡**
>
> ![img](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/20200728111338715.jpeg)
>
> * 当负载因子是1.0的时候，数组填满才会扩容，意味着会出现大量的Hash的冲突，底层的红黑树变得异常复杂。对于查询效率极其不利。这种情况就是牺牲了时间来保证空间的利用率。
> * 负载因子是0.5的时候,Hash冲突也会减少，那么底层的链表长度或者是红黑树的高度就会降低。查询效率就会增加。但是，这时候空间利用率就会大大的降低；原本存储1M的数据，现在就意味着需要2M的空间。
> * 负载因子过大，虽然空间利用率上去了，但是时间效率降低了.
> * 负载因子太小，虽然时间效率提升了，但是空间利用率降低了.
> * 大致意思就是说负载因子是0.75的时候，空间利用率比较高，而且避免了相当多的Hash冲突，使得底层的链表或者是红黑树的高度比较低，提升了查询效率。桶中元素个数得概率服从参数为0.5得泊松分布，桶中元素达到8概率接近于0;

 

### 在Java8中为什么要使用红黑树来实现的HashMap？

它是一种不严格的平衡[二叉查找树](https://so.csdn.net/so/search?q=二叉查找树&spm=1001.2101.3001.7020)，它的定义是不严格符合平衡二叉查找树的定义的

它avl树都是通过平衡来二分查找。但对于插入删除等操作效率提高很多。红黑树不像avl树一样追求绝对的平衡，他允许局部很少的不完全平衡，这样对于效率影响不大，**但省去了很多没有必要的调平衡操作**，avl树调平衡有时候代价较大，所以效率不如红黑树，在现在很多地方都是底层都是红黑树的天下啦。

 

###  HashSet 的实现原理？

HashSet 的实现是依赖于 HashMap 的，HashSet 的值都是存储在 HashMap 中的。在 HashSet 的构造法中会初始化一个 HashMap 对象，HashSet 不允许值重复。因此，HashSet 的值是作为 HashMap 的 key 存储在 HashMap 中的，当存储的值已经存在时返回 false。

（hashmap的key不能重复，所以hashset值不能重复）

 

### LinkedHashMap 的实现原理?

LinkedHashMap 也是基于 HashMap 实现的，不同的是它定义了一个 Entry header，这个 header 不是放在 Table 里，它是额外独立出来的。

LinkedHashMap 通过继承 hashMap 中的 Entry，并添加两个属性 Entry before，after 和 header 结合起来组成一个双向链表，来实现按插入顺序或访问顺序排序。

 

### Iterator 怎么使用？有什么特点？

迭代器是一种设计模式，它是一个对象，它可以遍历并选择序列中的元素。迭代器通常被称为“轻量级”对象，因为创建它的代价小。Java 中的 Iterator 功能比较简单，并且只能单向移动：

1. 使用方法 iterator() 要求容器返回一个 Iterator。第一次调用 Iterator 的 next() 方法时，它返回序列的第一个元素。注意：iterator() 方法是 java.lang.Iterable 接口，被 Collection 继承。
2. 使用 next() 获得序列中的下一个元素。　
3. 使用 hasNext() 检查序列中是否还有元素。　　
4. 使用 remove() 将迭代器新返回的元素删除

 

### Iterator 和 ListIterator 有什么区别？

Iterator 可用来遍历 Set 和 List 集合，但是 ListIterator 只能用来遍历 List。Iterator 对集合只能是前向遍历，ListIterator 既可以前向也可以后向。ListIterator 实现了 Iterator 接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引等等。

 

### fail-fast 与 fail-safe 有什么区别？

- fail-fast机制在遍历一个集合时，当集合结构被修改，会抛出`ConcurrentModificationException`。（迭代器在遍历时直接访问集合中的内容,并且在遍历过程中使用一个`modCount`变量，集合结构被修改时，会改变这个值，从而使`expectmodCount`与modecount不等，抛出异常）。

- fail-safe 采用安全失败机制的集合容器,在遍历时不是直接在集合内容上访问的,而是先copy原有集合内容,在拷贝的集合上进行遍历。后续在原集合修改不被迭代器知道，因此不会抛出异常。

 

### Iterator 和 Enumeration 接口的区别？

与 Enumeration 相比，Iterator 更加安全，因为当一个集合正在被遍历的时候，它会阻止其它线程去修改集合。否则会抛出 ConcurrentModificationException 异常。这其实就是 fail-fast 机制。具体区别：

1. Iterator 有 fail-fast 机制，比 Enumeration 更安全；
2. Iterator 能够删除元素，Enumeration 并不能删除元素

 

### Collection 和 Collections 有什么区别？

Collection：是最基本的集合接口，一个 Collection 代表一组 对象，即 Collection 的元素。 List，Set 和 Queue都直接继承了这个接口。

Collections：是不属于 Java 的集合框架的，它是集合类的一个工具类/帮助类。此类不能被实例化， 服务于 Java 的 Collection 框架。它包含有关集合操作的静态多态方法，实现对各种集合的搜索、排序、线程安全等操作。

 

# JVM

## 一、内存区域

### 1.说一下 Jvm 的主要组成部分？及其作用？

1. 类加载器（ClassLoader）
2. 运行时数据区（Runtime Data Area）
3. 执行引擎（Execution Engine）
4. 本地库接口（Native Interface）

各组件的作用：首先通过类加载器（ClassLoader）会把 Java 代码转换成字节码并加载到内存，运行时数据区（Runtime Data Area）是字节码的运行场所，但是字节码文件只是 JVM 的一套指令集规范，并不能直接交给底层操作系统去执行，因此需要特定的命令解析器执行引擎（Execution Engine），将字节码翻译成底层系统指令，再交由 CPU 去执行，而这个过程中需要调用其他语言的本地库接口（Native Interface）来实现整个程序的功能。

### 2.谈谈对运行时数据区（内存）的理解 ★★★★★

![image-20220624181238536](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220624181238536.png)

运行时数据区包括：1.程序计数器、2.虚拟机栈、3.本地方法栈、4.堆、5.方法区

-  程序计数器（Program Counter Register）：当前线程所执⾏的字节码的⾏号指示器，字节码解析器的⼯作是通过改变这个计数器的值，来选取下⼀条需要执⾏的字节码指令，分⽀、循环、跳转、异常处理、线程恢复等基础功能，都需要依赖这个计数器来完成；是线程私有的；
-  Java 虚拟机栈（Java Virtual Machine Stacks）：描述的是Java方法执行的内存模型：每个方法在执行的同时都会创建一个帧栈（Stack Frame）用于存储局部变量表、操作数栈、动态链接、方法出口等信息。每一个方法从调用直至执行完成的过程，就对应着一个栈帧在虚拟机栈中入栈到出栈的过程。它的线程也是私有的，生命周期与线程相同。
-  本地⽅法栈（Native Method Stack）：与虚拟机栈的作⽤是⼀样的，只不过虚拟机栈是服务 Java ⽅法的，⽽本地⽅法栈是为虚拟机调⽤ Native⽅法服务的；
-  Java 堆（Java Heap）：Java 虚拟机中内存最⼤的⼀块，是被所有线程共享的，堆的唯一目的就是：存放对象实例，几乎所有的对象实例都在这里分配内存。Java 堆是垃圾收集器管理的主要区域，因此很多时候也被称做“GC”堆（Garbage Collected Heap）。从内存回收的角度看，由于现在收集器基本都采用分代收集算法，所以 Java 堆中还可以细分为：新生代和老年代。
-  方法区（Methed Area）：是各个线程共享的内存区域，它用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

 

### 为什么jdk1.8要把方法区从JVM里移到直接内存？

**原因一**：因为直接内存，JVM将会在IO操作上具有更高的性能，因为它直接作用于本地系统的IO操作。而非直接内存，也就是堆内存中的数据，如果要作IO操作，会先复制到直接内存，再利用本地IO处理。

**原因二**：整个永久代有一个 JVM 本身设置固定大小上线，无法进行调整，而元空间使用的是直接内存，受本机可用内存的限制；虽然元空间仍旧可能溢出，但是比原来出现的几率会小很多；

**原因三**：元空间里面存放的是类的元数据，这样加载多少类的元数据就不由 `MaxPermSize` 控制了, 而由系统的实际可用空间来控制，这样能加载的类就更多了。

 

[JAVA8 十大新特性详解 - bcombetter - 博客园 (cnblogs.com)](https://www.cnblogs.com/xingzc/p/6002873.html)

 

### StringTable为什么要放到堆？

因为永久代的回收频率比较低，只在`FullGC`的时候才会被回收，`FullGC`只会在老年代或者永久代空间不足时才会触发。如果有大量的字符串被创建，放在永久代，由于永久代的回收频率低，会导致永久代空间不足。
如果放到堆里，能够及时回收内存

 

### 3.堆和栈的区别是什么

- 堆和栈（虚拟机栈）是完全不同的两块内存区域，堆是线程共享的，栈是线程独享的。
- 堆的物理地址分配是不连续的。因此性能慢些。 栈使⽤的是数据结构中的栈，先进后出的原则，物理地址分配是连续的。所以性能快。

- 堆因为是不连续的，所以分配的内存是在运⾏期确认的，因此⼤⼩不固定。⼀般堆⼤⼩远远⼤于栈。 栈是连续的，所以分配的内存⼤⼩要在编译期就确认，⼤⼩是固定的。

- 堆存放的是对象的实例和数组。因此该区更关注的是数据的存储      栈存放：局部变量，操作数栈，返回结果。该区更关注的是程序⽅法的执⾏。

 

 


### 4.堆中存什么？栈中存什么？

堆中存的是对象。栈中存的是基本数据类型和堆中对象的引用。一个对象的大小是不可估计的，或者说是可以动态变化的，但是在栈中，一个**对象只对应了一个 4btye 的引用**（堆栈分离的好处）。

**为什么不把基本类型放在堆中？**

因为基本数据类型占用的空间一般是1~8个字节，需要空间比较少，而且因为是基本类型，所以不会出现动态增长的情况，长度固定，因此栈中存储就够了。如果把它存在堆中是没有什么意义的。基本类型和对象的引用都是存放在栈中，而且都是几个字节的一个数，因此在程序运行时，它们的处理方式是统一的。

 

### 5.为什么要把堆和栈区分出来呢？栈中不是也可以存储数据吗？

1. 从软件设计的角度看，栈代表了处理逻辑，而堆代表了数据。这样分开，使得处理逻辑更为清晰。

2. 堆与栈的分离，使得堆中的内容可以被多个栈共享（也可以理解为多个线程访问同一个对象）。这种共享的收益是很多的。一方面这种共享提供了一种有效的数据交互方式(如：共享内存)，另一方面，堆中的共享常量和缓存可以被所有栈访问，节省了空间。

3. 栈因为运行时的需要，比如：保存系统运行的上下文，需要进行地址段的划分。由于栈只能向上增长，因此就会限制住栈存储内容的能力。而堆不同，堆中的对象是可以根据需要动态增长的，因此栈和堆的拆分，**使得动态增长成为可能，相应栈中只需记录堆中的一个地址即可。**

**处理逻辑、共享、动态增长**可以

 

### 6. Java 中的参数传递时传值呢？还是传引用？

Java 在方法调用传递参数时进行的是传值调用。所以，如果是传引用的方法调用，也同时可以理解为“传引用值”的传值调用，即引用的处理跟基本类型是完全一样的。（可以理解为传递了一个地址值）

 

### 对象的访问定位的两种方式？★★★★★

**1. 使用句柄**

如果使用句柄的话，那么 Java 堆中将会划分出一块内存来作为句柄池，引用中存储的就是对象的句柄地址，而句柄中包含了对象实例数据与类型数据各自的具体地址信息。

**2. 直接指针**

如果使用直接指针访问（那么 Java 堆对象的布局中就必须考虑如何放置访问类型数据的相关信息），reference（引用） 中存储的直接就是对象的地址。

**3. 各自的优点**

1、 使用句柄来访问的最大好处是引用中存储的是稳定的句柄地址，在对象被移动时只会改变句柄中的实例数据指针，而引用本身不需要修改；

2、使用直接指针访问方式最大的好处就是速度快，它节省了一次指针定位的时间开销

 

## 二、垃圾回收

### 7.如何判断一个对象是否可以回收 ★★★★★

#### 1.引用计数法

给对象添加一个引用计数器，每当有一个地方引用它，计数器就加 1；当引用失效，计数器就减 1；任何时候 为 0 的对象就是不可能再被使用的。

**这个方法实现简单，效率高，但是目前主流的虚拟机中并没有选择这个算法来管理内存，其最主要的原因是它很难解决对象之间相互循环引用的问题（此时计数器不可能为0）。**

#### 2.可达性分析算法

这个算法的基本思想就是通过一系列的称为 **“GC Roots”** 的对象作为起点，从这些节点开始向下搜索，节点所走过的路径称为引用链，当一个对象到 GC Roots 没有任何引用链相连的话，则证明此对象是不可用的。

可作为 GC Roots 的对象包括下面几种:

- 虚拟机栈(栈帧中的本地变量表)中引用的对象
- 本地方法栈(Native 方法)中引用的对象
- 方法区中类静态属性引用的对象
- 方法区中常量引用的对象
- 所有被同步锁持有的对象

 

### 8.被标记为垃圾的对象一定会被回收吗？

即使在可达性分析算法中不可达的对象，也并非是“非死不可”，要真正宣告一个对象死亡，至少要经历两次标记过程。  

第一次标记：如果对象在进行可达性分析后发现没有与 GC Roots 相连接的引用链，那它将会被第一次标记；

第二次标记：第一次标记后接着会进行一次筛选，筛选的条件是此对象是否有必要执行 finalize() 方法。**( finalize() 方法是对象不被回收的最后机会)**在 finalize() 方法中没有重新与引用链建立关联关系的，将被进行第二次标记。第二次标记成功的对象将真的会被回收，如果对象在 finalize() 方法中重新与引用链建立了关联关系，那么将会逃离本次回收，继续存活。

ps:

当遇到以下两种情况时，虚拟机将视为“没有必要执行”：
1.对象覆盖finalize()方法
2.finalize()方法已经被虚拟机调用过

 

### 讲一下  创建一个对象的过程 ★★★★★

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/Java%E5%88%9B%E5%BB%BA%E5%AF%B9%E8%B1%A1%E7%9A%84%E8%BF%87%E7%A8%8B.dbe33c41.png" alt="Java创建对象的过程" style="zoom:150%;" />

* 类加载检查

  虚拟机遇到一条 new 指令时，首先将去检查这个指令的参数是否能在常量池中定位到这个类的符号引用，并且检查这个符号引用代表的类是否已被加载过、解析和初始化过。如果没有，那必须先执行相应的类加载过程。

* 分配内存

  在类加载检查通过后，接下来虚拟机将为新⽣对象分配内存。对象所需的内存⼤⼩在类加载完成后便可确定，为对象分配空间的任务等同于把⼀块确定⼤⼩的内存从 Java 堆中划分出来。

  分配⽅式有**指针碰撞和空闲列表**两种，选择哪种分配⽅式由Java堆是否规整决定，⽽Java堆是否规整⼜由所采⽤的垃圾收集器是否带有压缩整理功能决定。（复制算法和标记整理算法内存是规整的，标记清除算法则不是）

  <img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211130203727591.png" alt="image-20211130203727591" style="zoom: 150%;" />

  > **内存分配并发问题（补充内容，需要掌握）**：
  >
  > 虚拟机采用两种方式来保证频繁创建对象时的线程安全：
  >
  > * CAS+失败重试：CAS 是乐观锁的一种实现方式。所谓乐观锁就是，每次不加锁而是假设没有冲突而去完成某项操作，如果因为冲突失败就重试，直到成功为止。虚拟机采用 CAS 配上失败重试的方式保证更新操作的原子性。
  > * TLAB分配方案：为每一个线程预先在 Eden 区分配一块儿内存，JVM 在给线程中的对象分配内存时，首先在 TLAB 分配，当对象大于 TLAB 中的剩余内存或 TLAB 的内存已用尽时，再采用上述的 CAS 进行内存分配 。

* 初始化零值：
  内存分配完成后，虚拟机需要将分配到的内存空间都初始化为零值（不包括对象头），这⼀步操作保证了对象的**实例字段**在 Java 代码中可以不赋初始值就直接使⽤，程序能访问到这些字段的数据类型所对应的零值。

* 设置对象头:

  初始化零值完成之后，**虚拟机要对对象进⾏必要的设置**，例如这个对象是哪个类的实例、如何才能找到类的元数据信息、对象的哈希码、对象的 GC 分代年龄等信息。这些信息存放在对象头中。另外，根据虚拟机当前运⾏状态的不同，如是否启⽤偏向锁等，对象头会有不同的设置⽅式。

* 执⾏init⽅法:

  在上⾯⼯作都完成之后，从虚拟机的视⻆来看，⼀个新的对象已经产⽣了，但从 Java 程序的视⻆来看，对象创建才刚开始， <init> ⽅法还没有执⾏，所有的字段都还为零。所以⼀般来说，执⾏ new 指令之后会接着执⾏ <init> ⽅法，把对象按照程序员的意愿进⾏初始化，这样⼀个真正可⽤的对象才算完全产⽣出来。

 

### 9. Java中的引用 ★★★★★

在Java语言中，将引用又分为强引用、软引用、弱引用、虚引用 4 种，这四种引用强度依次逐渐减弱。

**1. 强引用（StrongReference）** 

在程序代码中普遍存在的，类似 Object obj = new Object() 这类引用，类似于**必不可少的生活用品**，只要强引用还存在，垃圾收集器永远不会回收掉被引用的对象。

**2．软引用（SoftReference）**

如果一个对象只具有软引用，类似于**可有可无的生活用品**。如果内存空间足够，垃圾回收器就不会回收它，如果内存空间不足了，就会回收这些对象的内存。只要垃圾回收器没有回收它，该对象就可以被程序使用。软引用可用来实现内存敏感的高速缓存。

**3．弱引用（WeakReference）**

如果一个对象只具有弱引用，类似于**可有可无的生活用品**。弱引用与软引用的区别在于：只具有弱引用的对象拥有更短暂的生命周期。在垃圾回收器线程扫描它所管辖的内存区域的过程中，一旦发现了只具有弱引用的对象，不管当前内存空间足够与否，都会回收它的内存。

**4．虚引用（PhantomReference）**

"虚引用"顾名思义，就是形同虚设，与其他几种引用都不同，虚引用并不会决定对象的生命周期。如果一个对象仅持有虚引用，那么它就和没有任何引用一样，在任何时候都可能被垃圾回收。

**虚引用主要用来跟踪对象被垃圾回收的活动，并返回一个通知**，虚引用必须和引用队列（ReferenceQueue）联合使用。当垃 圾回收器准备回收⼀个对象时，如果发现它还有虚引⽤，就会在回收对象的内存之前，把这个虚引⽤加⼊到与之关联的引⽤队列中。程序可以通过判断引⽤队列中是 否已经加⼊了虚引⽤，来了解被引⽤的对象是否将要被垃圾回收。程序如果发现某个虚引⽤已经被加⼊到引⽤队列，那么就可以在所引⽤的对象的内存被回收之前采取必要的⾏动。

 

### **10.谈谈对Java内存泄漏的理解**

在 Java 中，内存泄漏就是存在一些不会再被使用却没有被回收的对象，这些对象有下面两个特点：

1. 这些对象是可达的，即在引用链中，存在通路可以与其相连；
2. 这些对象是无用的，即程序以后不会再使用这些对象。

如果对象满足这两个条件，这些对象就可以判定为 Java 中的内存泄漏，这些对象不会被 GC 所回收，然而它却占用内存。

 

### 11. 内存泄漏的根本原因是什么

**长生命周期的对象持有短生命周期对象的引用**就很可能发生内存泄漏，尽管短生命周期对象已经不再需要，但是因为长生命周期持有它的引用而导致不能被回收，这就是 Java 中内存泄漏的发生场景。

 

### 12.举几个可能发生内存泄漏的情况

1. 静态集合类引起的内存泄漏，它们的生命周期与程序一致，则容器中的对象在程序结束之前将不能被释放，从而造成内存泄漏
2. 当集合里面的对象属性被修改后（更改了计算哈希值的字段），再调用 remove() 方法时不起作用（找不到对象）；
3. 各种连接：比如数据库连接（dataSourse.getConnection()），网络连接(socket) 和 IO 连接，除非其显式的调用了其 close() 方法将其连接关闭，否则是不会自动被 GC 回收的
4. 内部类：内部类的引用是比较容易遗忘的一种（内部类持有外部类），而且一旦没释放可能导致一系列的后继类对象没有释放；
5. 监听器：释放对象的时候没有删除监听器；
6. 单例模式：单例对象在初始化后将在 JVM 的整个生命周期中存在（以静态变量的方式），如果单例对象持有外部的引用，那么这个对象将不能被 JVM 正常回收，导致内存泄漏。

（回答三到四个即可，前四个）

 

### 13. 尽量避免内存泄漏的方法？

1. 尽量不要使用 static 成员变量，减少生命周期；
2. 及时关闭资源；
3. 不用的对象，可以手动设置为 null。

 

### 14.如何判断一个常量是废弃常量？

运行时常量池主要回收的是废弃的常量。那么，我们如何判断一个常量是废弃常量呢？

****🐛 修正（参见：[issue747  (opens new window)](https://github.com/Snailclimb/JavaGuide/issues/747)，[reference  (opens new window)](https://blog.csdn.net/q5706503/article/details/84640762)） ：

1. **JDK1.7 之前运行时常量池逻辑包含字符串常量池存放在方法区, 此时 hotspot 虚拟机对方法区的实现为永久代**
2. **JDK1.7 字符串常量池被从方法区拿到了堆中, 这里没有提到运行时常量池,也就是说字符串常量池被单独拿到堆,运行时常量池剩下的东西还在方法区, 也就是 hotspot 中的永久代 。**
3. **JDK1.8 hotspot 移除了永久代用元空间(Metaspace)取而代之, 这时候字符串常量池还在堆, 运行时常量池还在方法区, 只不过方法区的实现从永久代变成了元空间(Metaspace)**

若没有任何对象引用常量，也没有其他地方引用了这个常量，如果在这时候发生内存回收，而且必要的话，这个常量就会被系统“请”出常量池。

### 15 .如何判断一个类是无用的类？

方法区主要回收的是无用的类，那么如何判断一个类是无用的类的呢？

判定一个常量是否是“废弃常量”比较简单，而要判定一个类是否是“无用的类”的条件则相对苛刻许多。类需要同时满足下面 3 个条件才能算是 **“无用的类”** ：

- 该类所有的实例都已经被回收，也就是 Java 堆中不存在该类的任何实例。
- 加载该类的 `ClassLoader`（类加载器） 已经被回收。
- 该类对应的 `java.lang.Class` 对象没有在任何地方被引用，没有在任何地方通过反射访问该类的方法。

虚拟机可以对满足上述 3 个条件的无用类进行回收，这里说的仅仅是“可以”，而并不是和对象一样不使用了就会必然被回收。

 

**14 和15 主要是对方法区两部分内容的回收**

 

### 16.说一说JVM有哪些垃圾回收算法？★★★★★

**标记-清除算法：**从根集合（GC Roots）进行扫描，对存活的对象进行标记，标记完毕后，再扫描整个空间中未被标记的对象，进行回收。缺点：效率不⾼，会造成内存碎⽚。

**标记-复制算法：**按照容量划分两个⼤⼩相等的内存区域，当⼀块⽤完的时候将活着的对象复制到另⼀块上，然后再把已使⽤的内存空 间⼀次清理掉。缺点：内存使⽤率不⾼，只有原来的⼀半。不会造成内存碎片

**标记-整理算法：**标记⽆⽤对象，让所有存活的对象都向⼀端移动，然后直接清除掉未存活的对象。不会造成内存碎片

**分代算法：**根据对象存活周期的不同将内存划分为⼏块，⼀般是新⽣代和⽼年代

在新生代中，每次收集都会有大量对象死去而少量存活，所以可以选择”标记-复制“算法，只需要付出少量对象的复制成本就可以完成每次垃圾收集。而老年代的对象存活几率是比较高的，而且没有额外的空间对它进行分配担保，所以我们可以采用标记整理算法或标记复制算法。

 

### 17. HotSpot 为什么要分为新生代和老年代？

主要是为了进行分代垃圾回收；在新生代中，每次收集都会有大量对象死去而少量存活，所以可以选择”标记-复制“算法，只需要付出少量对象的复制成本就可以完成每次垃圾收集。而老年代的对象存活几率是比较高的，而且没有额外的空间对它进行分配担保，所以我们可以采用标记整理算法或标记复制算法。

 

### 18.什么是浮动垃圾

由于在应用运行的同时进行垃圾回收，所以有些垃圾可能在垃圾回收进行完成时产生，这样就造成了“Floating Garbage”，这些垃圾需要在下次垃圾回收周期时才能回收掉。所以，并发收集器一般需要20%的预留空间用于这些浮动垃圾。

 

### 19.什么是内存碎片？

由于不同 Java 对象存活时间是不一定的，因此，在程序运行一段时间以后，如果不进行内存整理，就会出现零散的内存碎片。碎片最直接的问题就是会导致无法分配大块的内存空间，以及程序运行效率降低。所以，在上面提到的基本垃圾回收算法中，“复制”方式和“标记-整理”方式，都可以解决碎片的问题。

 

### ***并行和并发的区别：

并发，指的是多个事情，在同一时间段内同时发生了。
并行，指的是多个事情，在同一时间点上同时发生了。

并发的多个任务之间是互相抢占资源的。
并行的多个任务之间是不互相抢占资源的、

只有在多CPU或者一个CPU多核的情况中，才会发生并行。否则，看似同时发生的事情，其实都是并发执行的。

 

### 20.说一下JVM有哪些垃圾回收器？★★★

下图展示了7种作⽤于不同分代的收集器， 其中⽤于回收新⽣代的收集器包括Serial、PraNew、Parallel Scavenge，回收⽼年代的收集器包括Serial Old、Parallel Old、 CMS，还有⽤于回收整个Java堆的G1收集器。不同收集器之间的连线表示它们可以搭配使⽤。

![image-20211204151930378](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211204151930378.png)

 

- Serial收集器（**复制算法**): 新⽣代单线程收集器，标记和清理都是单线程，优点是简单⾼效；
- ParNew收集器 (**复制算法**): 新⽣代多线程集器，实际上是Serial收集器的多线程版本，在多核CPU环境下有着⽐Serial更好 的表现；
- Parallel Scavenge收集器 (**复制算法**): 新⽣代多线程收集器，追求⾼吞吐量，⾼效利⽤ CPU。吞吐量 = ⽤户线程时间/(⽤户 线程时间+GC线程时间)，⾼吞吐量可以⾼效率的利⽤CPU时间，尽快完成程序的运算任务；
- Serial Old收集器 (**标记-整理算法**): ⽼年代单线程收集器，Serial收集器的⽼年代版本； （ps:它主要有两大用途：一种用途是在 JDK1.5 以及以前的版本中与 Parallel Scavenge 收集器搭配使用，另一种用途是作为 CMS 收集器的后备方案）
- Parallel Old收集器 (**标记-整理算法**)： ⽼年代多线程收集器，吞吐量优先，Parallel Scavenge收集器的⽼年代版本；
- CMS(Concurrent Mark Sweep)收集器（**标记-清除算法**）： ⽼年代并发收集器，以获取最短回收停顿时间为⽬标的收集器，具有⾼并发、低停顿的特点。CMS 使用的是标记-清除的算法实现的，所以在 GC 的时候会产生大量的内存碎片，当剩余内存不能满足程序运行要求时，系统将会出现 Concurrent Mode Failure，临时 CMS 会采用 Serial Old 回收器进行垃圾清除，此时的性能将会被降低。
- G1(Garbage First)收集器 (**标记-整理算法**)： Java堆并⾏收集器， **以极⾼概率满⾜** **GC** **停顿时间要求的同时,还具备⾼吞吐量性能特征**；**G1收集器是基于“标记-整理”算法实现**，也就是说不会产⽣内存碎⽚。此外，G1收集器不同于之前的收集器的⼀个重要特点是：G1回收的范围是整个Java堆(包括新⽣代，⽼年代)。

 

### 21.详细介绍下CMS收集器  ★★★★★

> CMS只会回收⽼年代和永久代（1.8开始为元数据区，需要设置CMSClassUnloadingEnabled），不会收集年轻代；年轻代只能配合Parallel New或Serial回收器； CMS是⼀种预处理垃圾回收器，它不能等到old内存⽤尽时回收，需要在内存⽤尽前，完成回收操作，否则会导致并发回收失败；所以CMS垃圾回收器开始执⾏回收操作，有⼀个触发阈值，默认是⽼年代或永久带达到92%；

 

**CMS（Concurrent Mark Sweep）收集器是一种以获取最短回收停顿时间为目标的收集器。**是基于 **“标记-清除”算法**实现的，整个过程分为四个步骤：

1. **初始标记(CMS-initial-mark)**  stop the word暂停所有的其他线程，记录下直接与 root 相连的对象，速度很快。

2. **并发标记(CMS-concurrent-mark)**，与⽤户线程同时运⾏；记录可达的对象；但在这个阶段结束，并不能保证记录了当前所有的可达对象。因 为是并发运⾏的，在运⾏期间⽤户线程可能会不断的更新引用；对于这些更新引用的地方，都是需要进⾏重新标记的， 否则有些对象就会被遗漏，发⽣漏标的情况。为了提⾼重新标记的效率，所以这个算法⾥会跟踪记录这些发⽣引⽤更新的地⽅。避免后面扫描整个⽼年代。

3. **重新标记(CMS-remark)** ，这个阶段会导致第⼆次stop the word， 重新标记阶段就是为了修正并发标记期间因为用户程序继续运行而导致标记产生变动的那一部分对象的标记记录。【这个阶段的停顿时间一般会比初始标记阶段的时间稍长，远远比并发标记阶段时间短】；

   [语言基础.pdf](file:///D:/程序猿/面试相关/语言基础.pdf)

   > 这个阶段，重新标记的内存范围是整个堆，包含_young_gen和_old_gen。为什么要扫描新⽣代呢，因为对于⽼年代中的对象，如果被新⽣代中的对象引⽤，那么就会被视为存活对象，即使新⽣代的对象已经不可达了，也会使⽤这些不可达的对象当做cms的“gc root”，来扫描⽼年代； 因此对于⽼年代来说，引⽤了⽼年代中对象的新⽣代的对象，也会被⽼年代视作“GC ROOTS”:当此阶段耗时较⻓的时候，可以加⼊参数-XX:+CMSScavengeBeforeRemark，在重新标记之前，先执⾏⼀次ygc，回收掉年轻带的⽆⽤对象，并将对象放⼊幸存带或晋升到⽼年代，这样再进⾏年轻带扫描时，只需要扫描幸存区的对象即可，⼀般幸存带⾮常⼩，这⼤⼤减少了扫描时间。
   >
   > 由于之前的预处理阶段是与⽤户线程并发执⾏的，这时候可能年轻带的对象对⽼年代的引⽤已经发⽣了很多改变，这个时候，remark阶段要花很多时间处理这些改变，会导致很⻓stop the word，所以通常CMS尽量运⾏Final Remark阶段在年轻代是⾜够⼲净的时候。另外，还可以开启并⾏收集：-XX:+CMSParallelRemarkEnabled。来提⾼这个阶段的效率。

4. **并发清除**：开启用户线程，同时 GC 线程开始对为标记的区域做清扫。

 

### 22.CMS收集器的优化

CMS垃圾回收器的优化：

1.减少remark阶段停顿，⼀般CMS的GC耗时 80%都在remark阶段，如果发现remark阶段停顿时间很⻓，可以尝试添加该参数：- XX:+CMSScavengeBeforeRemark，在执⾏remark操作之前先做⼀次ygc，⽬的在于减少ygen对oldgen的⽆效引⽤，降低remark时的开销。

2.内存碎⽚

CMS是基于标记-清除算法的，只会将标记为为存活的对象删除，并不会移动对象整理内存空间，会造成内存碎⽚，这时候 我们需要⽤到这个参数;-XX:CMSFullGCsBeforeCompaction=n  （设置在执行多少次Full GC后对[内存](https://so.csdn.net/so/search?q=内存&spm=1001.2101.3001.7020)空间进行压缩整理）

3. promotion failed与解决⽅法

过早提升与提升失败

        在 Minor GC 过程中，Survivor Unused 可能不⾜以容纳 Eden 和另⼀个 Survivor 中的存活对象， 那么多余的将被移 到⽼年 代， 称为过早提升（Premature Promotion）,这会导致⽼年代中短期存活对象的增⻓， 可能会引发严重的 性能问题。 再进⼀ 步， 如果⽼年代满了， Minor GC 后会进⾏ Full GC， 这将导致遍历整个堆， 称为提升失败 （Promotion Failure）。
     
    **过早提升的原因**

1. Survivor空间太⼩，容纳不下全部的运⾏时短⽣命周期的对象，如果是这个原因，可以尝试将Survivor调⼤，否 则端⽣命周 期的对象提升过快，导致⽼年代很快就被占满，从⽽引起频繁的full gc；

2. 对象太⼤，Survivor和Eden没有⾜够⼤的空间来存放这些⼤象；

   **提升失败原因**

   当提升的时候，发现⽼年代也没有⾜够的连续空间来容纳该对象。为什么是没有⾜够的连续空间⽽不是空闲空间呢？ ⽼年代容纳不下提升的对象有两种情况：

   1. ⽼年代空闲空间不够⽤了；

   2. ⽼年代虽然空闲空间很多，但是碎⽚太多，没有连续的空闲空间存放该对象；

      解决⽅法

      1. 如果是因为内存碎⽚导致的⼤对象提升失败，cms需要进⾏空间整理压缩；
      2. 如果是因为提升过快导致的，说明Survivor 空闲空间不⾜，那么可以尝试调⼤ Survivor；
      3. 如果是因为⽼年代空间不够导致的，尝试将CMS触发的阈值调低；
      4. 增加线程数

      CMS默认启动的回收线程数⽬是 `(ParallelGCThreads + 3)/4) `，这⾥的`ParallelGCThreads`是年轻代的并⾏收集线程数，感 觉 有 点怪怪的；

      年轻代的并⾏收集线程数默认是`(ncpus <= 8) ? ncpus : 3 + ((ncpus * 5) / 8)`，可以通过-XX:ParallelGCThreads= N 来调 整；

      如果要直接设定CMS回收线程数，可以通过`-XX:ParallelCMSThreads=n`，注意这个n不能超过`cpu`线程数，需要注意的是增 加 gc线程数，就会和应⽤争抢资源；

 

### 23.详细介绍下G1收集器（谈谈你对G1收集器的理解）

**G1设定的目标是以极高概率满足 GC 停顿时间要求的同时,还具备高吞吐量性能特征.**

#### 1.**G1垃圾回收器相关数据结构**/概念

**1.分区算法region**：在HotSpot的实现中，整个堆被划分成2048左右个Region。每个Region的⼤⼩在1-32MB之间，具体多⼤取决于堆的⼤⼩。内存回收是以region作为基本单位的；每个region都是可分代的，可以独立的作为伊甸园区、suivive区、老年代，还有⼀类 ⼗分特殊的Humongous；所谓的Humongous，就是⼀个对象的⼤⼩超过了某⼀个阈值——HotSpot中是Region的1/2，那么它会 被标记为Humongous

> 分代是按对象的生命周期划分；堆内存小的话，CMS和G1的暂停时间上差不多，但是随着堆内存容量越来越大G1的优势就更加明显

**2.记忆集（Remember Set)与卡表（Global Card Table）**

（跨代引用：堆空间通常被划分为新生代和老年代。由于新生代的垃圾收集通常很频繁，如果老年代对象引用了新生代的对象，那么回收新生代的话，需要扫描所有从老年代到新生代的所有引用，所以要避免每次YGC时扫描整个老年代，减少开销。）

在G1回收器里面，RS被用来记录从其他Region指向一个Region的指针情况。因此，一个Region就会有一个RS。**这种记录可以带来一个极大的好处：在回收一个Region的时候不需要执行全堆扫描，只需要检查它的RS就可以找到外部引用，而这些引用就是initial mark的根之一。**

那么，如果⼀个线程修改了Region内部的引⽤，就必须要去通知RS，更改其中的记录。为了达到这种⽬的，G1回收器引⼊ 了⼀种新的结构，CT(Card Table)——卡表。每⼀个Region，⼜被分成了固定⼤⼩的若⼲张卡(Card)。每⼀张卡，都⽤⼀ 个Byte来记录是否修改过，修改过则记为1，称之脏卡，卡表即这些byte的集合。实际上，如果把RS理解成⼀个概念模型，那么卡表CT就可以说是RS的⼀种 实现⽅式。所以在垃圾收集发生时，只要筛选出卡表中变脏的元素，就能轻易得出哪些卡对应内存块中包含引用指针，把它们加入GC roots中一并扫描。

> 在RS的修改上也会遇到并发的问题。因为⼀个Region可能有多个线程在并发修改，因此它们也会并发修改RS。为了避免这 样⼀种冲突，G1垃圾回收器进⼀步把RS划分成了多个哈希表。每⼀个线程都在各⾃的哈希表⾥⾯修改。最终，从逻辑上来 说，RS就是这些哈希表的集合。哈希表是实现RS的⼀种通常的⽅式之⼀。它有⼀个极⼤的好处就是能够去除重复。这意味 着，RS的⼤⼩将和修改的指针数量相当。⽽在不去重的情况下，RS的数量和写操作的数量相当。

#### 2.**回收过程：**

![image-20211204173048855](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211204173048855.png)

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211204104243832.png" alt="image-20211204104243832" style="zoom: 80%;" />

> **TAMS 是什么？**
>
> 要达到 GC 与用户线程并发运行，必须要解决回收过程中新对象的分配，所以 G1 为每一个 Region 区域设计了两个名为 TAMS（Top at Mark Start）的指针， 从 Region 区域划出一部分空间用于记录并发回收过程中的新对象。这样的对象认为它们是存活的，不纳入垃圾回收范围.

 

1、初始标记；初始标记阶段仅仅只是标记⼀下GC Roots能直接关联到的对象，*并且修改TAMS的值，让下⼀个阶段⽤户程序并发运⾏时，能在正确可⽤的Region中创建新对象*，这⼀阶段需要停顿线程，但是耗时很短。而且是借用进行minor GC 的时候同步完成的

2、并发标记； 并发标记阶段是从GC Root开始对堆中对象进⾏可达性分析，找出存活的对象，这阶段时耗时较⻓，但可与⽤户程序并发执⾏。⽤户线程可能会不断的更新引⽤域，所以 GC 线程⽆法保证可达性分析的实时性。所以这个算法⾥会跟踪记录这些发⽣引⽤更新的地⽅。

3、最终标记； 最终标记阶段则是为了修正在并发标记期间因⽤户程序继续运作⽽导致标记产⽣变动的那⼀部分标记记录 （结合**记忆集（RSet，Remembered Set）**）。

4、筛选回收：最后在筛选回收阶段⾸先对各个Region的回收价值和成本进⾏排序，根据⽤户所期望的GC停顿时间来制定 回收计划。

 

**G1垃圾收集器把整个堆划分为一个一个等大小的区域（region）。内存的回收和划分都以region为单位；同时，它也吸取了 CMS 的特点，把这个垃圾回收过程分为几个阶段，分散一个垃圾回收过程；而且，G1 也认同分代垃圾回收的思想，认为不同对象的生命周期不同，可以采取不同收集方式，因此，它也支持分代的垃圾回收。为了达到对回收时间的可预计性（用户期望的TIME），G1 在扫描了 region 以后，对其中的活跃对象的大小进行排序，首先会收集那些活跃对象小的 region，因为活跃对象小，里面可以认为多数都是垃圾，所以这种方式被称为 Garbage First（G1）的垃圾回收算法，即：垃圾优先的回收**。

 

G1垃圾回收器的特点

**并⾏与并发**：G1 能充分利⽤ CPU、多核环境下的硬件优势，使⽤多个 CPU（CPU 或者CPU 核⼼）来缩短 Stop-The-World 停顿时间。部分其他收集器原本需要停顿 Java 线程执⾏的 GC 动作，G1 收集器仍然可以通过并发的⽅式让 java 程序继续执⾏。

**分代收集**：虽然 G1 可以不需要其他收集器配合就能独⽴管理整个 GC 堆，但是还是保留了分代的概念。

**空间整合**：与 CMS 的“标记--清理”算法不同，G1 从整体来看是基于“标记整理”算法实现的收集器；从局部上来看是基于“复制”算法实现的。`Region`之间使用的是复制算法，能够对内存空间进行整理。

**可预测的停顿**：这是 G1 相对于 CMS 的另⼀个⼤优势，降低停顿时间是 G1 和 CMS 共同的关注点，但 G1 除了追求低停顿外，还能建⽴可预测的停顿时间模型，能让使⽤者明确指定在⼀个⻓度为 M 毫秒的时间⽚段内。

* 缺点：
  相比于`CMS`，`G1`还不具备全方位、压倒性优势。比如，`G1`为了垃圾收集产生的`内存占用`以及程序运行时的`额外执行负载`都比`CMS`要高。

在小内存应用上，CMS>G1.在大内存应用上G1>CMS.平衡点是6-8GB之间

![image-20220309202102303](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220309202102303.png)

#### 垃圾标记算法

**三色法和写屏障**

[【JVM】三色标记法与读写屏障_九师兄-CSDN博客_写屏障和读屏障](https://blog.csdn.net/qq_21383435/article/details/106311542?spm=1001.2101.3001.6650.6&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~default-6.no_search_link&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~default-6.no_search_link)

 

### 23.新生代垃圾回收器和老年代垃圾回收器都有哪些？有什么区别？

新⽣代回收器：Serial、ParNew、Parallel Scavenge

⽼年代回收器：Serial Old、Parallel Old、CMS

整堆回收器：G1

新⽣代垃圾回收器⼀般采⽤的是复制算法，复制算法的优点是效率⾼，缺点是内存利⽤率低；⽼年代回收器⼀般采⽤的是标记-整理的算法进⾏垃圾回收。

 

### 24.简述java内存分配 ★★★★★

**对象优先在 Eden 区分配**

大多数情况下，对象在新生代 Eden 区分配，当 Eden 区空间不够时，发起 Minor GC。

**大象直接进⼊⽼年代**

大对象是指需要连续内存空间的对象，最典型的大对象是那种很长的字符串以及数组。经常出现大对象会提前触发垃圾收集以获取足够的连续空间分配给大对象。由于新⽣代使⽤的是标记-复制算法来处理垃圾回收的，如果⼤对象直接在新⽣代分配就会导致 Eden 区和两个 Survivor 区之间发⽣⼤量的内存复制，此外因为分配担保机制的存在使得Minor GC之后，Survivor无法存放的对象会进入老年代；因此对于⼤对象都会直接在⽼年代进⾏分配

**长期存活对象将进⼊⽼年代**  为对象定义年龄计数器，对象在 Eden 出生并经过 Minor GC 依然存活，将移动到 Survivor 中，年龄就增加 1 岁，增加到一定年龄则移动到老年代中。-XX:MaxTenuringThreshold 用来定义年龄的阈值。

**动态对象年龄判定**----Hotspot 遍历所有对象时，按照年龄从小到大对其所占用的大小进行累积，当累积的某个年龄占用大小超过了 survivor 区的 50% 时（默认值是 50%，可以通过 `-XX:TargetSurvivorRatio=percent` 来设置），取这个年龄和 MaxTenuringThreshold 中更小的一个值，作为新的晋升年龄阈值”。

 

### 26.空间分配担保 ★★★★★

（1）在发生` Minor GC `之前，虚拟机先检查老年代最大可用的连续空间是否大于新生代所有对象总空间，如果条件成立的话，那么 `Minor GC `可以确认是安全的；

（2）如果不成立的话，虚拟机会查看 `HandlePromotionFailure` 设置值是否允许担保失败，如果允许那么就会继续检查老年代最大可用的连续空间是否大于历次晋升到老年代对象的平均大小，如果大于，将尝试着进行一次 `Minor GC`；如果小于，或者` HandlePromotionFailure` 设置不允许冒险，那么就要进行一次` Full GC`。

 

### **为什么要进行空间担保？**

　是因为新生代采用**复制收集算法**，假如大量对象在Minor GC后仍然存活（最极端情况为内存回收后新生代中所有对象均存活），而Survivor空间是比较小的，这时就需要老年代进行分配担保，把Survivor无法容纳的对象放到老年代。**老年代要进行空间分配担保，前提是老年代得有足够空间来容纳这些对象**，但一共有多少对象在内存回收后存活下来是不可预知的，**因此只好取之前每次垃圾回收后晋升到老年代的对象大小的平均值作为参考**。使用这个平均值与老年代剩余空间进行比较，来决定是否进行Full GC来让老年代腾出更多空间

 

 

### 25.简述分代垃圾回收器是怎么工作的 （垃圾回收机制）★★★★★

分代回收器有两个分区：⽼年代和新⽣代，新⽣代默认的空间占⽐总空间的 1/3，⽼年代的默认占⽐是 2/3。

新⽣代使⽤的是复制算法，新⽣代⾥有 3 个分区：Eden、From Survivor、To Survivor，它们的默认占⽐是 8:1:1，它的执⾏流 程如下：

- 把 Eden + From Survivor 存活的对象放⼊ To Survivor 区；
- 清空 Eden 和 From Survivor 分区； From Survivor 和 To Survivor 分区交换，
- From Survivor 变 To Survivor，To Survivor 变 From Survivor。

每次在 From Survivor 到 To Survivor 移动时都存活的对象，年龄就 +1，当年龄到达 15（默认配置是 15）时，升级为⽼年代。 ⼤对象也会直接进⼊⽼年代。（现在是动态机制）

⽼年代当空间占⽤到达某个值之后就会触发全局垃圾收回，⼀般使⽤标记整理的执⾏算法。以上这些循环往复就构成了整个分代垃圾回收的整体执⾏流程。

[分代垃圾回收机制及垃圾回收算法 - donleo123 - 博客园 (cnblogs.com)](https://www.cnblogs.com/donleo123/p/14567139.html)

 

### 28. JVM的一些参数

- **1. 堆设置**

-Xms：初始堆大小

-Xmx：最大堆大小

-XX:NewSize=n：设置年轻代大小

-XX:NewRatio=n：设置年轻代和年老代的比值。如:为3，表示年轻代与年老代比值为 1：3，年轻代占整个年轻代年老代和的 1/4

-XX:SurvivorRatio=n：年轻代中 Eden 区与两个 Survivor 区的比值。注意 Survivor 区有两个。如：3，表示 Eden：Survivor=3：2，一个Survivor区占整个年轻代的 1/5

-XX:MaxPermSize=n：设置持久代大小

 

- **2. 收集器设置**

-XX:+UseSerialGC：设置串行收集器

-XX:+UseParallelGC：设置并行收集器

-XX:+UseParalledlOldGC：设置并行年老代收集器

-XX:+UseConcMarkSweepGC：设置并发收集器

 

- **3. 垃圾回收统计信息**

-XX:+PrintGC：开启打印 gc 信息

-XX:+PrintGCDetails：打印 gc 详细信息

-XX:+PrintGCTimeStamps

-Xloggc:filename

 

- **4. 并行收集器设置**

-XX:ParallelGCThreads=n：设置并行收集器收集时使用的 CPU 数

-XX:MaxGCPauseMillis=n：设置并行收集最大暂停时间

-XX:GCTimeRatio=n：设置垃圾回收时间占程序运行时间的百分比

 

- **5. 并发收集器设置**

-XX:+CMSIncrementalMode：设置为增量模式。适用于单 CPU 情况

-XX:ParallelGCThreads=n：设置并发收集器年轻代收集方式为并行收集时，使用的 CPU 数。并行收集线程数

 

### JDK 监控和调优总结

#### JDK 命令行工具

这些命令在 JDK 安装目录下的 bin 目录下：

- **`jps`** (JVM Process Status）: 查看当前 Java 进程
- **`jstat`**（JVM Statistics Monitoring Tool）:  显示虚拟机运行数据
- **`jmap`** (Memory Map for Java) : 内存监控
- **`jhat`** (JVM Heap Dump Browser) : 用于分析 heapdump 文件（二进制文件，它保存了某一时刻JVM堆中对象使用情况）
- **`jstack`** (Stack Trace for Java) : 生成虚拟机当前时刻的线程快照
- **`jinfo`** (Configuration Info for Java) : 显示虚拟机配置信息;

#### JDK 可视化分析工具

- `JConsole`:Java 监视与管理控制台

jconsole：⽤于对 JVM 中的内存、线程和类等进⾏监控；

- `Visual VM`:多合一故障处理工具

VisualVM JDK ⾃带的全能分析⼯具。可以分析：内存快照、线程快照、程序死锁、监控内存的变化、gc 变化等

 

### 常⽤的 JVM 调优的参数

-Xms2g：初始化推⼤⼩为 2g；

-Xmx2g：堆最⼤内存为 2g；

-XX:NewRatio=4：设置年轻的和⽼年代的内存⽐例为 1:4；

-XX:SurvivorRatio=8：设置新⽣代 Eden 和 Survivor ⽐例为 8:2；

-XX:MaxPermSize=n：设置持久代大小

–XX:+UseParNewGC：指定使⽤ ParNew + Serial Old 垃圾回收器组合；

-XX:+UseParallelOldGC：指定使⽤ ParNew + ParNew Old 垃圾回收器组合；

-XX:+UseConcMarkSweepGC：指定使⽤ CMS垃圾回收器；

-XX:+PrintGC：开启打印 gc 信息；

-XX:+PrintGCDetails：打印 gc 详细信息

[面试官：如何进行 JVM 调优（附真实案例） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/488615913)

 

## 三、类文件结构和类加载

### 29.谈谈你对类文件结构的理解？有哪些部分组成？

```java
ClassFile {
    u4             magic; //Class 文件的标志
    u2             minor_version;//Class 的小版本号
    u2             major_version;//Class 的大版本号
    u2             constant_pool_count;//常量池的数量
    cp_info        constant_pool[constant_pool_count-1];//常量池
    u2             access_flags;//Class 的访问标记
    u2             this_class;//当前类
    u2             super_class;//父类
    u2             interfaces_count;//接口
    u2             interfaces[interfaces_count];//一个类可以实现多个接口
    u2             fields_count;//Class 文件的字段属性
    field_info     fields[fields_count];//一个类会可以有多个字段
    u2             methods_count;//Class 文件的方法数量
    method_info    methods[methods_count];//一个类可以有个多个方法
    u2             attributes_count;//此类的属性表中的属性数
    attribute_info attributes[attributes_count];//属性表集合
}
```

Class 文件没有任何分隔符，但是，无论是顺序还是数量，甚至于数据存储的字节序这样的细节，都是被严格限定的，哪个字节代表什么含义，长度是多少，先后顺序如何，都不允许改变。

1. 魔数（magic）：每个 Class 文件的头 4 个字节称为魔数（Magic Number），它的唯一作用是确定这个文件是否为一个能被虚拟机接受的Class 文件，即判断这个文件是否符合 Class 文件规范。
2. 文件的版本：minor_version （u2）和 major_version（u2）。

3. 常量池：constant_pool_count 和 constant_pool：常量池中主要存放两大类常量：字面量（Literal）和符号引用（Symbolic References）。
4. 访问标志：access_flags（u2）：用于识别一些类或者接口层次的访问信息。包括：这个 Class 是类还是接口、是否定义了 Public 类型、是否定义为 abstract 类型、如果是类，是否被声明为了 final 等等。

5. 类索引、父类索引与接口索引集合：this_class、super_class和interfaces。

6. 字段表集合：field_info、fields_count：字段表（field_info）用于描述接口或者类中声明的变量；fields_count 字段数目：表示Class文件的类和实例变量总数。

7. 方法表集合：methods、methods_count

8. 属性表集合：attributes、attributes_count

 

### 30.java的类加载机制 ★★★★★

虚拟机把描述类的数据从 Class 文件加载到内存，并对数据进行校验、转换解析和初始化，最终形成可以被虚拟机直接使用的 Java 类型，这就是虚拟机的类加载机制。

类从被加载到虚拟机内存中开始，到卸载出内存为止，它的整个生命周期包括：加载、验证、准备、解析、初始化、使用、卸载 7 个阶段。其中验证、准备、解析 3 个部分统称为连接

![image-20211207201955986](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207201955986.png)

 

### 31.类加载的执行过程？类加载各阶段的作用分别是什么？★★★★★

分以下五个步骤：

- 加载：根据查找路径找到相应的class文件，然后导入
- 验证：检查加载的 class ⽂件的正确性；包括文件格式校验、元数据验证、字节码验证、符号引用验证
- 准备：给类中的静态变量分配内存空间 并赋系统初始值；
- 解析：虚拟机将常量池中的符号引⽤替换成直接引⽤的过程。符号引⽤就理解为⼀个标示（字段或方法的全限定名等，在编译时不能知道具体地址，以符号代替），⽽直接引⽤直接指向内存中的地址；
- 初始化：对静态变量和静态代码块执⾏初始化⼯作。

具体过程及其作用：[类加载过程详解 | JavaGuide](https://javaguide.cn/java/jvm/class-loading-process/#解析)

 

### 32.描述⼀下JVM加载Class⽂件的原理机制

Java中的所有类，都需要由类加载器装载到JVM中才能运⾏。类加载的⼯作就是把class⽂件从硬盘读取到内存中。在写程序的时候，我们⼏乎不需要关⼼类的加载，因为这些都是隐式装载的，除⾮我们有特殊的⽤法，像是反射，就需要显式的加载所需要的类。

类装载⽅式，有两种 ：

     1.隐式装载， 程序在运⾏过程中当碰到通过new 等⽅式⽣成对象时，隐式调⽤类装载器加载对应的类到jvm中，
     
     2.显式装载， 通过class.forname()等⽅法，显式加载需要的类

Java类的加载是动态的，它并不会⼀次性将所有类全部加载后再运⾏，⽽是保证程序运⾏的基础类(像是基类)完全加载到jvm中， ⾄于其他类，则在**需要的时候才加载**。这当然就是为了节省内存开销。

**隐式、显式、动态**

 

### 33.什么是类加载器？类加载器有哪些？★★★★★

> 实现通过类的全限定名获取该类的⼆进制字节流的代码块叫做类加载器。

主要有⼀下四种类加载器:

- 启动类加载器(Bootstrap ClassLoader) ：这个类加载器是由 C++ 语言实现的，⽤来加载java核⼼类库，⽆法被java程序直接引⽤（调用c++语言使用）。
- 扩展类加载器(extensions class loader): 它⽤来加载 Java 的扩展库。Java 虚拟机的实现会提供⼀个扩展库⽬录。该类加载器在此⽬录⾥⾯查找并加载 Java 类。
- 应用程序类加载器（AppClassLoader）：面向我们用户的加载器，它根据 Java 应⽤的类路径（CLASSPATH）来加载 Java 类，一般情况下这个就是程序中默认的类加载器。
- ⽤户⾃定义类加载器，通过继承 java.lang.ClassLoader类的⽅式实现。

 

### 34.类与类加载器的关系？

类加载器虽然只用于实现类的加载动作，但它在 Java 程序中起到的作用却远远不限于类加载阶段。对于任意一个类，都需要由加载它的类加载器和这个类本身一同确立其在 Java 虚拟机中的唯一性。换句话说：比较两个类是否“相等”，只有在这两个类是由同一个类加载器加载的前提下才有意义，否则，即使这两个类来源于同一个 Class 文件，被同一个虚拟机加载，只要加载它们的类加载器不同，那么这两个类就必定不相等。

 

### 35.什么是双亲委派机制？工作过程？为什么要用双亲委派机制？★★★★★

#### 双亲委派模型的工作过程（定义）

如果一个类加载器收到了类加载请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成。每一个层次的类加载器都是如此，因此所有的加载请求最终都应该传送到顶层的启动类加载器中，只有当父类加载器反馈自己无法完成这个加载请求（它的搜索范围中没有找到所需的类）时，子加载器才会尝试自己去加载。（当父类加载器为 null 时，会使用启动类加载器 `BootstrapClassLoader` 作为父类加载器。）

![image-20211207213115709](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211207213115709.png)

#### 双亲委派模型的好处

双亲委派模型保证了 Java 程序的稳定运行，可以**避免类的重复加载**（JVM 区分不同类的方式不仅仅根据类名，相同的类文件被不同的类加载器加载产生的是两个不同的类），也保证了 **Java 的核心 API 不被篡改**。如果没有使用双亲委派模型，而是每个类加载器加载自己的话就会出现一些问题，比如我们编写一个称为 `java.lang.Object` 类的话，那么程序运行的时候，可能会被不同的类加载器加载，系统就会出现多个不同的 `Object` 类。

 

#### 关于源代码/主要代码实现

实现双亲委派的代码都集中在 java.lang.ClassLoader 的 loadClass() 方法中，逻辑清晰易懂：先检查是否已经被加载过，若没有加载则调用父加载器的 loadClass() 方法，若父加载器为空则默认使用启动类加载器作为父类加载器。如果父类加载失败，抛出 ClassNotFoundException 异常后，再调用自己的 findClass() 方法进行加载。

 

### 36.怎么实现一个自定义的类加载器？

自定义加载器的话，需要继承 `ClassLoader` 。如果我们不想打破双亲委派模型，就重写 `ClassLoader` 类中的 `findClass()` 方法即可，无法被父类加载器加载的类最终会通过这个方法被加载。但是，如果想打破双亲委派模型则需要重写 `loadClass()` 方法 。

 

### 37.怎么打破双亲委派机制？

1. 自定义一个类加载器；
2. 重写 loadClass() 方法
3. 重写 findClass() 方法

这里最主要的是重写 loadClass 方法，因为双亲委派机制的实现都是通过这个方法实现的，先找父加载器进行加载，如果父加载器无法加载再由自己来进行加载，重写了这个方法以后就能使用自己定义加载的方式了。

 

### 38.需要打破双亲委派机制的场景？

1. 一个典型的例子便是JNDI服务，JNDI现在已经是Java的标准服务，它的代码由启动类加载器去加载（在JDK 1.3时放进去的rt.jar），但JNDI需要调用由独立厂商实现并部署在应用程序的ClassPath下的JNDI接口提供者（SPI，Service Provider Interface）的代码，但启动类加载器不可能去加载ClassPath下的类。所以就使用了线程上下文类加载器就，JNDI服务使用线程上下文类加载器去加载所需要的代码，也就是父类加载器请求子类加载器去完成类加载的动作（应用程序类加载器）。

JNDI(Java Naming and Directory Interface)是一个[应用程序](https://baike.baidu.com/item/应用程序)设计的API，为开发人员提供了查找和访问各种命名和[目录服务](https://baike.baidu.com/item/目录服务/10413830)的通用、统一的接口。

（ ps:如果创建线程时未设置上下文类加载器，将会从父线程（`parent = currentThread()`）中获取，如果在应用程序的全局范围内都没有设置过，就默认是应用程序类加载器。）

2. Tomcat, 应用程序类加载器优先自行加载应用目录下的class,并不是先委派给父类加载器，加载不了才委派给父类。打破的目的是为了应用间的类隔离。

 

### 39. 为何 HotSpot 虚拟机要使用解释器与编译器并存的架构？

二者各有优势：当程序需要迅速启动和执行时，解释器可以首先发挥作用，省去编译的时间，立即执行；当程序运行后，随着时间的推移，编译器逐渐会发挥作用，把越来越多的代码编译成本地代码后，可以获取更高的执行效率。解释执行可以节约内存，而编译执行可以提升效率。在整个虚拟机执行架构中，解释器与编译器经常配合工作。

 

## 四、内存模型 --JAVA并发中

### 41.对Java内存（JMM）模型的理解

JMM 即 Java Memory Model，它定义了**主存（共享内存）、工作内存（线程私有）**的抽象概念，底层对应着 CPU 寄存器、缓存、硬件内存、 CPU 指令优化等。

**JMM体现在以下几个方面**

- 原子性 - 保证指令不会受到线程上下文切换的影响
- 可见性 - 保证指令不会受 cpu 缓存的影响
- 有序性 - 保证指令不会受 cpu 指令并行优化的影响

 

# JUC

## 1.进程和线程的区别？★★★★★

**进程：**是程序运行和资源分配的基本单位，一个程序至少有一个进程，一个进程至少有一个线程。进程在执行过程中拥有独立的内存单元。

**线程：**是进程的一个实体，是` cpu `调度和分派的基本单位，是比程序更小的能独立运行的基本单位。同一进程中的多个线程之间可以并发执行并**共享内存资源**。

**线程执行开销小，时间效率和空间效率线程比进程都要高；但不利于资源的管理和保护。**

[什么是协程？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/172471249)

 

## 2.程序计数器，虚拟机栈和本地方法栈为什么是私有的？堆和方法区为什么是线程共有的？

- 程序计数器私有主要是为了**线程切换后能恢复到正确的执行位置**。
- 为了**保证线程中的局部变量不被别的线程访问到**，虚拟机栈和本地方法栈是线程私有的。

- 其中堆是进程中最大的一块内存，主要用于存放新创建的对象 (几乎所有对象都在这里分配内存)，方法区主要用于存放已被加载的类信息、常量、静态变量、即时编译器编译后的代码等数据，为了高效的数据共享，所以它们是线程共享的。

 

## 3.并行和并发的区别？★★★★★

并发，指的是多个事情，在同一时间段内同时发生了。
并行，指的是多个事情，在同一时间点上同时发生了。

并发的多个任务之间是互相抢占资源的。
并行的多个任务之间是不互相抢占资源的、

只有在多CPU或者一个CPU多核的情况中，才会发生并行。否则，看似同时发生的事情，其实都是并发执行的。

 

## 4.为什么要使用多线程？

- **从计算机底层来说：** 线程可以比作是轻量级的进程，是程序执行的最小单位 , 线程间的切换和调度的成本远远小于进程。另外，多核 CPU 时代意味着多个线程可以同时运行，这减少了线程上下文切换的开销。
- **从当代互联网发展趋势来说：** 现在的系统动不动就要求百万级甚至千万级的并发量，而多线程并发编程正是开发高并发系统的基础，利用好多线程机制可以大大提高系统整体的并发能力以及性能。

 

## 5.什么是线程的上下文切换？

线程在执行过程中会有自己的运行条件和状态（也称上下文），当执行线程失去时间片时，需要保存当前线程的上下文，留待线程下次占用 CPU 的时候恢复现场，并加载下一个将要占用 CPU 的线程上下文。这就是所谓的 **上下文切换**。

 

## 6.创建线程有几种方式？ ★★★★★

1. 继承 Thread 类创建线程；

   > - 首先定义一个类来继承 Thread 类，重写 run 方法。
   > - 然后创建这个子类对象，并调用 start 方法启动线程。

2. 实现 Runnable 接口创建线程；

   > - 首先定义一个类实现 Runnable 接口，并实现 run 方法。
   > - 然后创建 Runnable 实现类对象，并把它作为 target 传入 线程的构造函数中
   > - 最后调用 start 方法启动线程。

3. 通过 Callable 和 Future 创建线程；

   > - 首先定义一个 Callable 的实现类，并实现 call 方法。call 方法是带返回值的。
   > - 然后通过 FutureTask 的构造方法，把这个 Callable 实现类传进去。
   > - 把 FutureTask 作为 Thread 类的 target ，创建 Thread 线程对象，并调用 start 方法启动线程
   > - 通过 FutureTask 的 get 方法获取线程的执行结果

4. 通过线程池创建线程。

[面试官问我：创建线程有几种方式？我笑了 - SegmentFault 思否](https://segmentfault.com/a/1190000037589073#item-2-6)

 

## 7.什么是线程死锁？如何避免死锁？ ★★★★★

线程死锁描述的是这样一种情况：多个线程同时被阻塞，它们中的一个或者全部都在等待某个资源被释放。由于线程被无限期地阻塞，因此程序不可能正常终止。

**操作系统中产生死锁必须具备以下四个条件：**

1. 互斥条件：该资源任意一个时刻只由一个线程占用。

2. 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放。

3. 不剥夺条件:线程已获得的资源在未使用完之前不能被其他线程强行剥夺，只有自己使用完毕后才释放资源。

4. 循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系。

 

**如何预防死锁？** 破坏死锁的产生的必要条件即可：

1. **破坏请求与保持条件** ：一次性申请所有的资源。
2. **破坏不剥夺条件** ：占用部分资源的线程进一步申请其他资源时，如果申请不到，可以主动释放它占有的资源。
3. **破坏循环等待条件** ：靠按序申请资源来预防。按某一顺序申请资源，释放资源则反序释放。破坏循环等待条件。

 

**如何避免死锁？**

避免死锁可以在资源分配时，借助于算法（比如银行家算法）对资源分配进行计算评估，使其进入安全状态。

[(3条消息) 单进程死锁示例_「已注销」的博客-CSDN博客_单进程死锁](https://blog.csdn.net/weixin_43553694/article/details/106139698?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~default-1-106139698-blog-112252222.pc_relevant_aa2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~default-1-106139698-blog-112252222.pc_relevant_aa2&utm_relevant_index=2)

[(3条消息) OS - 单进程死锁_无CCFA就不改名的博客-CSDN博客_单进程死锁](https://blog.csdn.net/singxsy/article/details/112252222)

## 8.`sleep()`和`wait()`方法区别和共同点？★★★★★

**共同点：**两者都可以暂停线程的执行

**区别**

- 两者最主要的区别在于：**`sleep()` 方法没有释放锁（只是让出了时间片），而 `wait()` 方法释放了锁**。

- sleep() 方法是thread类的可以在任何地方使用，而 wait() 方法属于object类，只能在同步方法或同步块中使用；wait() 通常被⽤于线程间交互/通信， sleep() 通常被⽤于暂停执⾏。

- `wait()` 方法被调用后，线程不会自动苏醒，需要别的线程调用同一个对象上的 `notify()`或者 `notifyAll()` 方法。`sleep()`方法执行完成后，线程会自动苏醒。或者可以使用 `wait(long timeout)` 超时后线程会自动苏醒。

 

## 9.为什么我们调用 start() 方法时会执行 run() 方法，为什么我们不能直接调用 run() 方法？★★★★★

new 一个 Thread，线程进入了新建状态。调用 `start()`方法，会启动一个线程并使线程进入了就绪状态，当分配到时间片后就可以开始运行了。 `start()` 会执行线程的相应准备工作，然后自动执行 `run()` 方法的内容，这是真正的多线程工作。 但是，直接执行 `run()` 方法，会把 `run()` 方法当成一个 main 线程下的普通方法去执行，并不会在某个线程中执行它，所以这并不是多线程工作。

 

## 10.说说线程的状态？

Thread 的源码中定义了6种状态：new（新建）、runnnable（运行）、blocked（阻塞）、waiting（等待）、time waiting （定时等待）和 terminated（终止）。

![image-20211208152836977](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211208152836977.png)

>  **“**阻塞状态”和“等待状态”的区别是：“阻塞状态”在等待着获取一个**排他锁**，这个事件将在另一个线程放弃这个锁的时候发生。 而“等待状态”则是在等待一段时间，或者唤醒动作的发生。 在程序等待进入同步区域的时候，线程将进入这种状态。

 

## 11.在Java程序中怎么保证多线程的安全性（并发编程的三个重要特性）？★★★

线程安全在三个方面体现：

- 原子性：提供互斥访问，同一时刻只能有一个线程能对数据进行操作，`synchronized` 可以保证代码片段的原子性；
- 可见性：一个线程对主内存的修改可以及时地被其他线程看到，`volatile` 关键字可以保证共享变量的可见性；
- 有序性：由于Java 在编译器以及运行期间的优化，代码的执行顺序未必就是编写代码时候的顺序。`volatile` 关键字可以禁止指令进行重排序优化，保证指令不会受 cpu 指令并行优化的影响（happens-before 原则（**前一个操作的结果对后续操作是可见的**））。

 

## Java 线程同步的几种方法？

1. 使用 Synchronized 关键字；
2. wait 和 notify；
3. 使用特殊域变量 volatile 实现线程同步；
4. 使用可重入锁实现线程同步；
5. 使用阻塞队列实现线程同步；
6. 使用信号量 Semaphore。

 

## 12.说一说自己对于 synchronized 关键字的了解以及底层原理 ★★★★★

**`synchronized` 关键字解决的是多个线程之间访问资源的同步性，`synchronized`关键字可以保证被它修饰的方法或者代码块在任意时刻只能有一个线程执行**。

`javap`反编译同步语句块,`synchronized` 同步语句块的实现使用的是 `monitorenter` 和 `monitorexit` 指令，其中 `monitorenter` 指令指向同步代码块的开始位置，`monitorexit` 指令则指明同步代码块的结束位置。

当执行 `monitorenter` 指令时，线程试图获取锁也就是获取 **对象监视器 `monitor`** 的持有权，如果锁的计数器为 0 则表示锁可以被获取，获取后将锁计数器设为 1 也就是加 1。如果获取对象锁失败，那当前线程就要阻塞等待，直到锁被另外一个线程释放为止。

在执行 `monitorexit` 指令后，将锁计数器设为 0，表明锁被释放。

 

( **ps1**：:在 Java 虚拟机(`HotSpot`)中，Monitor 是基于 C++实现的，由[ObjectMonitor  (opens new window)](https://github.com/openjdk-mirror/jdk7u-hotspot/blob/50bdefc3afe944ca74c3093e7448d6b889cd20d1/src/share/vm/runtime/objectMonitor.cpp)实现的。（同步代码块中？）每个对象中都内置了一个 `ObjectMonitor`对象。另外，`wait/notify`等方法也依赖于`monitor`对象，这就是为什么只有在同步的块或者方法中才能调用`wait/notify`等方法，否则会抛出`java.lang.IllegalMonitorStateException`的异常的原因。)

**ps2:**`synchronized` 修饰的方法并没有 `monitorenter` 指令和 `monitorexit` 指令，取得代之的确实是 `ACC_SYNCHRONIZED` 标识，该标识指明了该方法是一个同步方法。

 

## 13.谈一下对synchronized 关键字的使用  ★★★

**1.修饰实例方法:** 作用于当前对象实例，进入同步代码前要获得**当前对象实例的锁**     和synchronized (this) 一样

**2.修饰静态方法:** 也就是给当前类加锁，会作用于类的所有对象实例 ，进入同步代码前要获得 **当前 class 的锁**。因为静态成员不属于任何⼀个实例对象，是类成员

**3.修饰代码块** ：指定加锁对象，对给定对象加锁。

[synchronized（修饰方法和代码块） - 简书 (jianshu.com)](https://www.jianshu.com/p/bf7473e09432)

[(3条消息) Java中synchronized同步锁用法及作用范围_yx0628的博客-CSDN博客_java 同步锁](https://blog.csdn.net/yx0628/article/details/79086511)

 

## 14.单例模式之 双重检验+锁 方式实现单例模式的原理

单例模式有以下特点：
　　1、单例类只能有一个实例。
　　2、单例类必须自己创建自己的唯一实例。
　　3、单例类必须给所有其他对象提供这一实例。

```java
public class Singleton {
 
    private volatile static Singleton uniqueInstance;
 
    // private 在外部不能被new 实例化
    private Singleton() {
    }
 
    public  static Singleton getUniqueInstance() {
       //先判断对象是否已经实例过，没有实例化过才进入加锁代码
        if (uniqueInstance == null) {
            //类对象加锁
            synchronized (Singleton.class) {
                if (uniqueInstance == null) { // 第二次检验
                    uniqueInstance = new Singleton();
                }
            }
        }
        return uniqueInstance;
    }
}
```

使用 `volatile` 可以禁止` JVM `的指令重排，保证在多线程环境下也能正常运行

 

## 15.构造方法可以使用 synchronized 关键字修饰么？

**构造方法不能使用 synchronized 关键字修饰。**构造方法本身就属于线程安全的，不存在同步的构造方法这一说。

 

## 说说 JDK1.6 之后的 synchronized 关键字底层做了哪些优化，可以详细介绍一下这些优化吗？ ★★★★★★

JDK1.5之前，synchronized是属于重量级锁，重量级需要依赖于底层操作系统的Mutex Lock实现，Java 的线程是映射到操作系统的原⽣线程之上的。如果要挂起或者唤醒⼀个线程，都需要操作系统帮忙完成，⽽操作系统实现线程之间的切换时需要从⽤户态转换到内核态，这种切换的消耗非常大，所以性能相对来说并不好；

JDK1.6 对锁的实现引入了大量的优化，如偏向锁、轻量级锁、自旋锁、适应性自旋锁、锁消除、锁粗化等技术来减少锁操作的开销。

锁主要存在四种状态，依次是：无锁状态、偏向锁状态、轻量级锁状态、重量级锁状态，它们会随着竞争的激烈而逐渐升级。

**偏向锁：**

偏向锁认为，其实对于一个方法，是很少有两个线程来执行的，搞来搞去，其实也就一个线程在执行这个方法而已 ,所以它会偏向于第一个获得它的线程，如果在接下来的执行中，该锁没有被其他线程获取，那么持有偏向锁的线程就不需要进行同步。

偏向锁进入一个方法的时候是这样处理的：如果这个方法没有线程进来过，那么一个线程首次进入这个方法的时候，会采用CAS机制，把这个方法标记为有人在执行了，并且也会把该线程的 ID 也记录进去，相当于记录了哪个线程在执行。然后，但这个线程退出这个方法的时候，它不会改变这个方法的状态，而是直接退出来，懒的去改，因为它认为除了自己这个线程之外，其他线程并不会来执行这个方法。

有别人要来执行这个方法，偏向锁就失效了，而先升级为轻量级锁。

 

**轻量级锁：**

轻量级锁认为，当你在方法里面执行的时候，其实是很少刚好有人也来执行这个方法的，所以，当我们进入一个方法的时候根本就不用加锁,用CAS来记录操作做一个标记就行了。

也就是说，如果这个方法没人在执行，当我们进入这个方法的时候，采用**CAS**机制，把这个方法的状态标记为**已经有人在执行**，退出这个方法时，在把这个状态改为了**没有人在执行**了。

轻量级锁不是用来替代传统的重量级锁的，它的本意是在没有多线程竞争的前提下，减少传统的重量级锁使用操作系统帮忙产生的性能消耗，因为轻量级锁的加锁和解锁都是CAS 操作

如果真的遇到了竞争，我们就会认为**轻量级锁**已经不适合了，我们就会把轻量级锁升级为重量级锁了。

所以轻量级锁适合用在那种，很少出现多个线程竞争一个锁的情况，也就是说，适合那种多个线程总是**错开时间**来获取锁的情况。

 

**自旋锁和自适应自旋锁**：

- 重量级锁是某个线程拿不到锁就立刻进入阻塞状态；自旋锁就是，如果此时拿不到锁，它不马上进入阻塞状态，而是等待一段时间，看看这段时间有没其他人把这锁给释放了。怎么等呢？这个就类似于线程在那里做**空循环**，如果循环一定的次数还拿不到锁，那么它才会进入阻塞的状态。
- 自适应自旋锁--能够根据线程最近获得锁的状态来调整循环次数（等待时间）的自旋锁，我们称之为**自适应自旋锁**

**锁消除**

锁消除理解起来很简单，它指的就是虚拟机即使编译器在运行时，如果检测到那些共享数据不可能存在竞争，那么就执行锁消除。锁消除可以节省毫无意义的请求锁的时间。

**锁粗化**

我们编写代码时总是推荐将同步块的作用范围限制得尽量小。只在共享数据的实际作用域才进行同步，这样是为了使得需要同步的操作数量尽可能变小，如果存在锁竞争，那等待线程也能尽快拿到锁。

锁粗化就是告诉我们任何事情都有个度，有些情况下我们反而希望把很多次锁的请求合并成一个请求，以降低短时间内大量锁请求、同步、释放带来的性能损耗。

[一句话撸完重量级锁、自旋锁、轻量级锁、偏向锁、悲观、乐观锁等各种锁 ---- 不看后悔系列 (qq.com)](https://mp.weixin.qq.com/s/9zRmjH5Bgzo-EDIzZ5C7Hg)

 

## 17.谈一谈`synchronized` 和 `ReenTrantLock` 的区别？★★★★★

1、`synchronized `是和 for、while 一样的关键字，`ReentrantLock` 是类，这是二者的本质区别。既然 `ReentrantLock` 是类，那么它就提供了比 synchronized 更多更灵活的特性：如，等待可中断、可实现公平锁、可实现选择性通知（锁可以绑定多个条件）。

2、 `synchronized `依赖于 JVM 而 `ReenTrantLock `依赖于 API。synchronized 是依赖于 JVM 实现的，获取锁的线程执行完同步代码，会释放锁 ，并且在线程发生异常时会自动释放锁，因此不会发生异常死锁。ReenTrantLock 是 API 层面，需要 lock() 和 unlock 方法配合 try/finally 语句块来完成锁的释放;

> JDK1.6 为 synchronized 关键字进行了很多优化，但是这些优化都是在虚拟机层面实现的，并没有直接暴露给我们。

3、Synchronized：底层使用指令码方式来控制锁的，映射成字节码指令就是增加来两个指令：monitorenter和monitorexit；

`ReenTrantLock `依赖AbstractQueuedSynchronizer（AQS）类，AQS用的cas判断线程是否获取到锁，把所有的请求线程构成一个CLH队列。

4、ReenTrantLock是可中断锁，Synchronized是非中断锁，必须等待线程执行完成释放锁。

> 线程t1通过**lockInterruptibly()**方法获取到一个可重入锁，并执行一个长时间的任务，另一个线程通过interrupt()方法就可以立刻打断t1线程的执行，来获取t1持有的那个可重入锁。而通过ReentrantLock的lock()方法或者Synchronized持有锁的线程是不会响应其他线程的interrupt()方法的，直到该方法主动释放锁之后才会响应interrupt()方法

>  5、都是可重入锁，  **“可重入锁”** 指的是自己可以再次获取自己的内部锁。

**性能上面**：

- Synchronized优化前性能肯定差ReetrantLock很多 ( 为什么 - 从底层去讲)

- 优化后，在资源竞争不是很激烈的情况下，Synchronized的性能与ReetrantLock差不多，甚至优于ReetrantLock，但是在资源竞争很激烈的情况下，Synchronized的性能差ReetrantLock很多；Synchronized升级为重量级锁；

 

**为什么`ReenTrantLock` 是悲观锁**

仔细看代码发现ReentrantLock使用了setExclusiveOwnerThread方法，这个方法是将某一个线程设置为独占线程。就是我们常说的互斥锁。
该线程占用该方法以后就无法被其他线程占有，也就是线程的互斥。所以这不符合乐观锁的定义：“认为自己在使用数据时不会有别的线程修改数据”。

评论区：ReentrantLock用的AQS，AQS用的 cas 判断线程是否获取到锁，获取到就独占

## Synchronized与Lock的区别 ★★★★★

- `synchronized `是和 for、while 一样的关键字，Lock是接口，这是二者的本质区别。既然 lock 是接口，那么它就提供了比 synchronized 更多更灵活的特性

- Synchronized：底层使用的是两个指令：monitorenter和monitorexit；

  Lock：依赖AbstractQueuedSynchronizer（AQS）类，用的cas判断线程是否获取到锁，把所有的请求线程构成一个CLH队列。

- Synchronized，获取锁的线程执行完同步代码，会释放锁 ，并且在线程发生异常时会自动释放锁，因此不会发生异常死锁。Lock不会自动释放锁，需要 lock() 和 unlock 方法配合 try/finally 语句块来完成。

- Lock是可中断锁，Synchronized是非中断锁，必须等待线程执行完成释放锁。

  > 线程t1通过lockInterruptibly()方法获取到一个可重入锁，并执行一个长时间的任务，另一个线程通过interrupt()方法就可以立刻打断t1线程的执行，来获取t1持有的那个可重入锁。而通过ReentrantLock的lock()方法或者Synchronized持有锁的线程是不会响应其他线程的interrupt()方法的，直到该方法主动释放锁之后才会响应interrupt()方法

> Lock可以使用读锁提高多线程读效率
>
> 性能：Lock可以提高多个线程进行读操作的效率。（可以通过readwritelock实现读写分离），在资源竞争不是很激烈的情况下，Synchronized的性能要优于Lock，但是在资源竞争很激烈的情况下，Synchronized的性能会下降几十倍，但是Lock的性能能维持常态；

 

 

## 18.`Thread.interrupt() `方法的工作原理是什么？（你对`Thread.interrupt() `的理解）

（用于打断**阻塞**(sleep wait join…)的线程。

- 如果一个线程在运行中被打断，打断标记会被置为true。
- 如果是打断因sleep 、wait、 join方法而被阻塞的线程，**会将打断标记置为false**）

 

在 Java 中，**线程的中断 interrupt 只是改变了线程的中断状态，至于这个中断状态改变后带来的结果，那是无法确定的，有时它更是让停止中的线程继续执行的唯一手段**

1、对于 wait 中的等待 `notify、notifyAll` 唤醒的线程，其实这个线程已经“暂停”执行，因为它正在某一对象的休息室中，这时如果它的中断状态被改变（interrupt打断），那么它就会抛出异常。这个 `InterruptedException `异常不是线程抛出的，而是 wait 方法，也就是对象的 wait 方法内部会不断检查在此对象上休息的线程的状态，如果发现哪个线程的状态被置为已中断，则会抛出 `InterruptedException`，意思就是这个线程不能再等待了，其意义就等同于唤醒它了，然后执行 catch 中的代码。

2、 对于 sleep 中的线程，如果你调用了 `Thread.sleep`(一年)；现在你后悔了，想让它早些醒过来，调用 interrupt() 方法就是唯一手段，只有改变它的中断状态，让它从 sleep 中将控制权转到处理异常的 catch 语句中，然后再由 catch 中的处理转换到正常的逻辑。同样，对于 join 中的线程你也可以这样处理。

 

## 19.守护线程是什么？

守护线程（即 Daemon thread），是个服务线程，准确地来说就是服务其他的线程。当JAVA进程中有多个线程在执行时，只有当所有非守护线程都执行完毕后，JAVA进程才会结束。**但当非守护线程全部执行完毕后，守护线程无论是否执行完毕，也会一同结束。**

垃圾回收器线程就是一种守护线程

 

## 20.谈谈对`Volatile`关键字的理解  ★★★

**volatile 关键字是用来保证有序性和可见性的，但是不能保证原子性！！**这跟 Java 内存模型有关。

有序性：JVM 会在**不影响正确性**的前提下，可以**调整**语句的执行**顺序**，这被称为指令重排；但是在多线程模式下，可能会出现意想不到的效果，所以需要使用`Volatile`关键字禁止指令重排。

可见性：在当前的 Java 内存模型下，线程可以把变量保存**本地内存**中，而不是直接在主存中进行读写。就可能造成不同线程读取到的内容不一致的情况，所以需要使用`Volatile`关键字禁止从本地内存读取数据，每次加载数据都要经过主存。

**不能保证原子性：**

如自增操作：

- 从主内存将num读进工作内存中
- 在工作内存中进行加一
- 加一完成后赋值，写回主内存

    虽然这三步都是原子操作，但合起来不是原子操作，每一步执行的过程中都有可能被打断。

[volatile关键字——保证并发编程中的可见性、有序性 - spiritt - 博客园 (cnblogs.com)](https://www.cnblogs.com/seasail/p/12179350.html)

 

**`Volatile`的原理**

volatile的底层实现原理是**内存屏障**

**可见性：**

- **sfence**：即写屏障(Store Barrier)，在写指令之后插入写屏障，能让写入缓存的最新数据写回到主内存，以保证写入的数据立刻对其他线程可见
- **lfence**：即读屏障(Load Barrier)，在读指令前插入读屏障，可以让高速缓存中的数据失效，重新从主内存加载数据，以保证读取的是最新的数据。

**有序性(禁止指令重排的实现方式)：**

- 写屏障保证不会将**写屏障之前**的代码排在写屏障之后
- 读屏障保证不会将**读屏障之后**的代码排在读屏障之前

 

 

## 21.说说 synchronized 关键字和 volatile 关键字的区别？★★★★★

1. volatile 本质是在告诉 JVM当前变量在当前工作内存中的值是不确定的，需要从主存中读取；synchronized 则是锁定当前变量，只有当前线程可以访问该变量，其他线程被阻塞住。
2. volatile 仅能使用在变量级别；synchronized 则可以使用在变量、方法、和类级别的。**`volatile` 关键字**是线程同步的**轻量级实现**，所以 **`volatile`性能肯定比`synchronized`关键字要好**
3. **volatile 仅能实现变量的修改可见性，不能保证原子性；而 synchronized 则可以保证变量的修改可见性和原子性**。
4. volatile 不会造成线程的阻塞；synchronized 可能会造成线程的阻塞。
5. volatile 标记的变量不会被编译器优化；synchronized 标记的变量可以被编译器优化。

 

## 22.谈谈对 ThreadLocal 的理解？ ★★★★★

通常情况下，我们创建的变量是可以被任何⼀个线程访问并修改的。**如果想实现每⼀个线程都有⾃⼰的专属本地变量该如何解决呢？** JDK 中提供的 ThreadLocal 类正是为了解决这样的问题。

**ThreadLocal 类主要解决的就是让每个线程绑定自己的值**。如果你创建了一个`ThreadLocal`变量，那么访问这个变量的每个线程都会有这个变量的本地副本，他们可以使用 `get（）` 和 `set（）` 方法来获取默认值或将其值更改为当前线程所存的副本的值，从而避免了线程安全问题。

### `ThreadLocal `**的原理**

Thread类中维护了一个`threadLocals`  变量，它是 `ThreadLocalMap` 类型的变量 ,  我们可以把 `ThreadLocalMap` 理解为`ThreadLocal` 类实现的定制化的 `HashMap`；

默认情况下`threadLocals`  变量是 null，只有当前线程调⽤ ThreadLocal 类的 set 或 get ⽅法时才创建它们，实际上调⽤这两个⽅法的时候，我们调⽤的是 ThreadLocalMap 类对应的 get() 、 set() ⽅法。**最终的变量是放在了当前线程的 `ThreadLocalMap` 中，并不是存在 `ThreadLocal` 上，所以`ThreadLocal` 可以理解为只是`ThreadLocalMap`的封装，传递了变量值。**

**每个`Thread`中都具备一个`ThreadLocalMap`，**ThreadLocalMap 的 key 就是 ThreadLocal 对象，value 就是ThreadLocal 对象对应的值。

这样就避免了线程之间的竞争。

`ThrealLocal` 类中可以通过`Thread.currentThread()`获取到当前线程对象后，直接通过`getMap(Thread t)`可以访问到该线程的`ThreadLocalMap`对象。

```java
public T get() {
    //获得当前线程
    Thread t = Thread.currentThread();
    //每个线程 都有一个自己的ThreadLocalMap，
    //ThreadLocalMap里就保存着所有的ThreadLocal变量
    ThreadLocalMap map = getMap(t);
    if (map != null) {
        //ThreadLocalMap的key就是当前ThreadLocal对象实例，
        //多个ThreadLocal变量都是放在这个map中的
        ThreadLocalMap.Entry e = map.getEntry(this);
        if (e != null) {
            @SuppressWarnings("unchecked")
            //从map里取出来的值就是我们需要的这个ThreadLocal变量
            T result = (T)e.value;
            return result;
        }
    }
    // 如果map没有初始化，那么在这里初始化一下
    return setInitialValue();
}
```

 

### `ThreadLocal `内存泄露问题

`ThreadLocalMap` 中使用的 key 为 `ThreadLocal` 的弱引用, 而 value 是强引用。所以，如果 `ThreadLocal` 没有被外部强引用的情况下，在垃圾回收的时候，key 会被清理掉，而 value 不会被清理掉。这样一来，`ThreadLocalMap` 中就会出现 key 为 null 的 Entry。假如我们不做任何措施的话，value 永远无法被 GC 回收，这个时候就可能会产生内存泄露。`ThreadLocalMap` 实现中已经考虑了这种情况，在调用 `set()`、`get()`、`remove()` 方法的时候，会清理掉 key 为 null 的记录；使用完 `ThreadLocal`方法后 最好手动调用`remove()`方法.

**在调用 `get()`方法的时候，会执行`getEntry`方法中的`getEntryAfterMiss`方法。如果key为null，则调用expungeStaleEntry方法清理掉value**；在remove()和set()方法中，都会直接或者间接调用到这个方法进行value的清理

[ThreadLocal使用与原理_敖丙-CSDN博客_threadlocal](https://blog.csdn.net/qq_35190492/article/details/116431270)

 

### `ThreadLocal `的使用场景

- 经典的使用场景是使用`ThreadLocal`为每个线程分配一个 `JDBC` 连接 Connection。这样就可以保证每个线程的都在各自的 Connection 上进行数据库的操作，不会出现 A 线程关了 B线程正在使用的 Connection；

- 在调用 `API` 接口的时候传递了一些公共参数,可以用`ThreadLocal `代替，避免参数的显式层层传递。

 

## 23.为什么要使用线程池？★★★★★

**降低资源消耗**。通过重复利用已创建的线程降低线程创建和销毁造成的消耗。

**提高响应速度**。当任务到达时，任务可以不需要等到线程创建就能立即执行。

**提高线程的可管理性**。线程是稀缺资源，如果无限制的创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以进行统一的分配，调优和监控。

 

## 24.实现 Runnable 接口和 Callable 接口的区别  ★★★

`Runnable`自 Java 1.0 以来一直存在，但`Callable`仅在 Java 1.5 中引入,目的就是为了来处理`Runnable`不支持的用例。

1. **callable的核心是call方法，允许返回值，runnable的核心是run方法，没有返回值**
2. **call方法可以抛出异常，但是run方法不行**

 

## 25.执行 execute()方法和 submit()方法的区别是什么呢？ ★★★

- **`execute()`方法传入一个Runnable对象，用于提交不需要返回值的任务，所以无法判断任务是否被线程池执行成功与否；**
- **`submit()`方法可传入一个Callable 对象或者Runnable对象，用于提交需要返回值的任务。线程池会返回一个 `Future` 类型的对象，通过这个 `Future` 对象可以判断任务是否执行成功**，并且可以通过 `Future` 的 `get()`方法来获取返回值。
- **execute会直接抛出任务执行时异常，submit则不会抛出异常，但可以通过Future的get方法将任务执行时的异常重新抛出**

> `get()`方法（无参）会阻塞当前线程直到任务完成（让当前线程执行完当前任务，不被其他任务占有）。`get(long timeout，TimeUnit unit)`方法则会阻塞当前线程一段时间后立即返回，这时候有可能任务没有执行完。

 

## 26.如何创建线程池？ ★★★★★

**一、通过构造方法`ThreadPoolExecutor`实现**

![image-20211210143636233](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211210143636233.png)

**二、通过Executor 框架的工具类 Executors 来实现**

我们可以创建三种类型的 `ThreadPoolExecutor`：

- **FixedThreadPool**： 该方法返回一个固定线程数量的线程池。该线程池中的线程数量始终不变。当有一个新的任务提交时，线程池中若有空闲线程，则立即执行。若没有，则新的任务会被暂存在一个任务队列中，待有线程空闲时，便处理在任务队列中的任务。
- **SingleThreadExecutor：** 方法返回一个只有一个线程的线程池。若多余一个任务被提交到该线程池，任务会被保存在一个任务队列中，待线程空闲，按先入先出的顺序执行队列中的任务。
- **CachedThreadPool：** 该方法返回一个可根据实际情况调整线程数量的线程池。线程池的线程数量不确定，但若有空闲线程可以复用，则会优先使用可复用的线程。若所有线程均在工作，又有新的任务提交，则会创建新的线程处理任务。所有线程在当前任务执行完毕后，将返回线程池进行复用。

![image-20220611212535747](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220611212535747.png)

## 27.线程池的构造参数 ★★★★★

**`ThreadPoolExecutor` 的参数：**

- **`corePoolSize` :** (线程池的基本大小）：当提交一个任务到线程池时，如果当前 `poolSize < corePoolSize `时，线程池会创建一个线程来执行任务，即使其他空闲的基本线程能够执行新任务也会创建线程，等到需要执行的任务数大于线程池基本大小时就不再创建。
- **`maximumPoolSize` :** （线程池最大数量）：线程池允许创建的最大线程数。如果队列满了，并且已创建的线程数小于最大线程数，则线程池会再创建新的线程执行任务。
- **`workQueue`:** 当新任务来的时候会先判断当前运行的线程数量是否达到核心线程数，如果达到的话，新任务就会被存放在队列中。

- **`keepAliveTime`**（线程活动保持时间）：线程池的工作线程空闲后，保持存活的时间。所以，如果任务很多，并且每个任务执行的时间比较短，可以调大时间，提高线程的利用率。

- **` TimeUnit`**（线程活动保持时间的单位）：可选的单位有天（DAYS）、小时（HOURS）、分钟（MINUTES）、毫秒（MILLISECONDS）、微秒（MICROSECONDS，千分之一毫秒）和纳秒（NANOSECONDS，千分之一微秒）。

- **` threadFactory`**：用于设置创建线程的工厂，可以通过线程工厂给每个创建出来的线程设置更有意义的名字。

- **`RejectExecutionHandler`**（饱和策略）：队列和线程池都满了，说明线程池处于饱和状态，那么必须采取一种策略处理提交的新任务。这个策略默认情况下是 `AbortPolicy`，表示无法处理新任务时抛出异常。

 

## 28.线程池的阻塞队列有哪些？

1）、 `ArrayBlockingQueue`：是一个基于数组结构的有界阻塞队列，此队列按 FIFO（先进先出）原则对元素进行排序。

2）、`LinkedBlockingQueue`：一个基于链表结构的阻塞队列，此队列按 FIFO 排序元素，吞吐量通常要高于` ArrayBlockingQueue`。静态工厂方法 `Executors.newFixedThreadPool() `使用了这个队列。

3）、`SynchronousQueue`：一个不存储元素的阻塞队列。每个插入操作必须等到另一个线程调用移除操作，否则插入操作一直处于阻塞状态，吞吐量通常要高于` LinkedBlockingQueue`，静态工厂方法 `Executors.newCachedThreadPool `使用了这个队列。

4）、 `PriorityBlockingQueue`：一个具有优先级的无限阻塞队列。

 

##  29.阻塞队列的饱和策略？

1. `AbortPolicy`：直接抛出异常。
2. `CallerRunsPolicy`：在任务被拒绝添加后，会调用当前线程池的所在的线程(主线程)去执行被拒绝的任务。
3. `DiscardOldestPolicy`：丢弃队列里最早的一个任务，并执行当前任务。
4. `DiscardPolicy`：不处理，丢弃掉。

5. 实现RejectedExecutionHandler 接口自定义饱和策略。

 

## 30.对Java中Atomic原子类的理解

这里 Atomic 是指一个操作是不可中断的。即使是在多个线程一起执行的时候，一个操作一旦开始，就不会被其他线程干扰。所以，所谓原子类说简单点就是具有原子操作特征的类。

并发包 `java.util.concurrent `的原子类都存放在 `java.util.concurrent.atomic` 下。根据操作的数据类型，可以将 JUC 包中的原子类分为 4 类：

- 1.基本类型

  AtomicInteger：整型原子类

  AtomicLong：长整型原子类

  AtomicBoolean ：布尔型原子类

- 2.数组类型

  AtomicIntegerArray：整型数组原子类

  AtomicLongArray：长整型数组原子类

  AtomicReferenceArray ：引用类型数组原子类

- 3.引用类型

  AtomicReference：引用类型原子类

  AtomicStampedReference：原⼦更新带有版本号的引⽤类型。该类将整数值与引⽤关联起来，可以解决使⽤ CAS 进⾏原⼦更新时可能

  出现的 ABA 问题。

  AtomicMarkableReference ：原子更新带有标记位的引用类型

- 4.对象属性修改类型

  AtomicIntegerFieldUpdater：原子更新整型字段的更新器

  AtomicLongFieldUpdater：原子更新长整型字段的更新器

  AtomicReferenceFieldUpdater ：原⼦更新引⽤类型字段的更新器

 

## 31. atomic 的原理是什么？

Atomic 包中的类基本的特性就是在多线程环境下，当有多个线程同时对单个（包括基本类型及引用类型）变量进行操作时，具有排他性，即当多个线程同时对该变量的值进行更新时，仅有一个线程能成功（内部通过CAS实现），而未成功的线程可以进行等待而继续尝试，一直等到执行成功。

 

## 33.谈谈对乐观锁和悲观锁的理解?★★★★★

- **悲观锁**

总是假设最坏的情况，每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会阻塞直到它拿到锁，Java 中 synchronized 和` ReentrantLock` 等独占锁就是悲观锁思想的实现。

- **乐观锁**

总是假设最好的情况，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号机制和 `CAS `实现。在 Java 中` java.util.concurrent.atomic `包下面的**原子变量类**就是使用了乐观锁的一种实现方式 `CAS` 实现的。

- **悲观锁适用于写比较多的场景，乐观锁适用于读比较多的场景**

 

## 34. 乐观锁常见的两种使用方式？★★★★★

- **版本号机制**

一般是在数据表中加上一个数据版本号 version 字段，表示数据被修改的次数，当数据被修改时，version 值会加 1。当线程 A 要更新数据值时，在读取数据的同时也会读取 version 值，在提交更新时，若**刚才读取到的 version 值为当前数据库中的 version 值相等时才更新**，否则重试更新操作，直到更新成功。

- **`CAS`算法**

即 compare and swap（比较与交换），是一种有名的无锁算法。无锁编程，即不使用锁的情况下实现多线程之间的变量同步；`CAS` 算法涉及到三个操作数：

1、需要读写的内存值 V

2、进行比较的值 A（旧的预期值）

3、拟写入的新值 B

当且仅当 V 的值等于 A 时，`CAS` 通过原子方式用新值 B 来更新 V 的值，否则不会执行任何操作（比较和替换是一个原子操作）。一般情况下是一个自旋操作，即不断的重试（重新获得要比较的值）。

 

## 35.乐观锁（CAS）的缺点？★★★★★

1. **ABA问题**

   一个变量 V 初次读取的时候是 A 值，可能被改为其他值，然后又改回 A，再进行赋值，那 `CAS` 操作就会误认为它从来没有被修改过。

（解决：JDK 1.5 以后的`AtomicStampedReference` 类就提供了此种能力，其中的` compareAndSet `方法就是首先检查当前引用是否等于预期引用，并且当前标志是否等于预期标志，如果全部相等，则以原子方式将该引用和该标志的值设置为给定的更新值。）

2. **循环时间长，开销大**

  更新不成功会自旋 `CAS`（也就是不成功就一直循环执行直到成功，如果长时间不成功，会给 CPU 带来非常大的执行开销）

3. **只能保证一个共享变量的原子操作**

`CAS` 只对单个共享变量有效，当操作涉及跨多个共享变量时 `CAS` 无效。(解决： 但是从 JDK 1.5 开始，提供了 `AtomicReference `类来保证引用对象之间的原子性，你可以把多个变量放在一个对象里来进行 `CAS` 操作。)

 

##  `CAS` 和 `synchronized` 的使用场景？

- `CAS `是基于**乐观锁**的思想：乐观的估计，不怕别的线程来修改共享变量，就算改了也没关系，我吃亏点再重试呗。
- synchronized 是基于悲观锁的思想：悲观的估计，得防着其它线程来修改共享变量，我上了锁你们都别想改，我改完了解开锁，你们才有机会。

简单的来说 `CAS` 适用于写比较少，读比较多的情况下（多读场景，冲突一般较少），synchronized 适用于写比较多的情况下（多写场景，冲突一般较多）。

1. 对于资源竞争较少（线程冲突较轻）的情况，使用 synchronized 同步锁进行线程阻塞和唤醒切换以及用户态内核态间的切换操作额外浪费消耗 `cpu` 资源；而 `CAS` 基于硬件实现，不需要进入内核，不需要切换线程，操作失败重试机率较少，因此可以获得更高的性能。

2. 对于资源竞争严重（线程冲突严重）的情况，`CAS` 失败重试的概率会比较大，从而浪费更多的 CPU 资源，效率低于 synchronized。

 

## 36.说下同步器 AQS 的原理？  ★★★★★

AQS 的全称为：`AbstractQueuedSynchronizer`，这个类在 `java.util.concurrent.locks` 包下面。**AQS 是一个用来构建锁和同步器的框架**。使⽤ AQS 能简单且⾼效地构造出应⽤⼴泛的⼤量的同步器，⽐如我们提到的 ReentrantLock ， Semaphore ，其他的诸如ReentrantReadWriteLock ， SynchronousQueue；

AQS 核心思想是，采用了一个int类型的互斥变量state，0表示没有任务线程使用该资源，而大于等于1表示已经有线程正在持有锁资源。一个线程获取锁资源的时候，会判断state是否等于0（无锁状态），如果是，则把这个state更新为1，表示占用到锁，而这个过程中，如果多个线程同时做这样的操作，就会导致线程的安全性问题。因此AQS采用了CAS机制，来保证互斥变量state更新的原子性。如果请求的共享资源被占用，那么就需要一套线程阻塞等待以及被唤醒时锁分配的机制，这个机制 AQS 是用 CLH 队列锁实现的，即将暂时获取不到锁的线程加入到队列尾部中。

CLH(Craig,Landin,and Hagersten)队列是⼀个虚拟的双向队列（虚拟的双向队列即不存在队列实例，仅存在结点之间的关联关系）。AQS 是将每条请求共享资源的线程封装成⼀个CLH 锁队列的⼀个结点（Node）来实现锁的分配。

**CLH通过FIFO策略来完成获取资源线程的排队工作；当获得所得线程释放锁之后，会从这个双向链表的头部去唤醒下一个等待的线程再去竞争锁**。

![image-20211210212238181](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211210212238181.png)

 

> 公平锁和非公平锁
>
> 关于锁的的公平性和非公平行，AQS的处理方法是，在竞争锁资源的时候，公平锁要判断双向链表中是否有阻塞的线程，如果有则需要去排队等待。而非公平锁的处理方式是，不管双向链表中是否有阻塞的线程在排队等待，它都会去尝试去修改state变量去竞争锁，这个过程是非公平的。

[java之AQS的实现原理_请你吃鸡蛋面的博客-CSDN博客_javaaqs原理](https://blog.csdn.net/yangzhanghui/article/details/123558543)

 

## 37. AQS 对资源的共享模式有哪些？

1、Exclusive（独占）：只有一个线程能执行，如：`ReentrantLock`，又可分为公平锁和非公平锁：

- 公平锁：按照线程在队列中的排队顺序，先到者先拿到锁
- ⾮公平锁：当线程要获取锁时，⽆视队列顺序直接去抢锁，谁抢到就是谁的

2、Share（共享）：多个线程可同时执行，如：`CountDownLatch`、`Semaphore`、 `CyclicBarrier`、`ReadWriteLock`

 

## 38. `AQS` 底层使用了模板方法模式，你能说出几个需要重写的方法吗？

同步器的设计是基于模板⽅法模式的，如果需要⾃定义同步器（模板⽅法模式很经典的⼀个应⽤）：

1. 使⽤者继承 AbstractQueuedSynchronizer 并重写指定的⽅法。（这些重写⽅法很简单，⽆⾮是对于共享资源 state 的获取和释放）

2. 在⾃定义同步组件的实现中，调⽤其模板⽅法，⽽这些模板⽅法会调⽤使⽤者重写的⽅法。

需要重写的模板方法：

```java
isHeldExclusively()//该线程是否正在独占资源。只有用到condition才需要去实现它。
tryAcquire(int)//独占方式。尝试获取资源，成功则返回true，失败则返回false。
tryRelease(int)//独占方式。尝试释放资源，成功则返回true，失败则返回false。
tryAcquireShared(int)//共享方式。尝试获取资源。负数表示失败；0表示成功，但没有剩余可用资源；正数表示成功，且有剩余资源。
tryReleaseShared(int)//共享方式。尝试释放资源，成功则返回true，失败则返回false。
```

 

## 39.说下对信号量 Semaphore 的理解？

**Semaphore (信号量)**可以指定多个线程同时访问某个资源。

> `synchronized `和 `ReentrantLock `都是一次只允许一个线程访问某个资源，

在信号量上定义两种操作： acquire（获取） 和 release（释放）。当一个线程调用acquire操作成功时，信号量减1，release（释放）实际上会将信号量的值加1，然后唤醒等待的线程。信号量的数量是一定的，因此semaphore经常用于限制获取某种资源的线程数量。

 

##  40.用过 `CountDownLatch` 么？什么场景下用的？

`CountDownLatch` 可以理解为一个计数器，它的作用就是 允许 多个线程阻塞在一个地方，直至所有线程的任务都执行完毕。之前在项目中，有一个使用多线程读取多个文件处理的场景，我用到了 `CountDownLatch` 。具体场景是下面这样的：

我要读取处理 6 个文件，这 6 个任务都是没有执行顺序依赖的任务，但是我们需要返回给用户的时候需要将这几个文件的处理的结果进行统计整理。

为此我们定义了一个线程池和 count 为 6 的`CountDownLatch`对象 。使用线程池处理读取任务，每一个线程处理完之后就将 count-1，调用`CountDownLatch`对象的 `await()`方法阻塞，直到所有文件读取完之后（count为0时通过），才会接着执行后面的逻辑。

 

## 41.`CountDownLatch` 和 `CyclicBarrier` 有什么区别？★★★

**CountDownLatch** **（倒计时器）：** CountDownLatch 是⼀个同步⼯具类，⽤来协调多个线程之间的同步。这个⼯具通常⽤来控制线程等待，它可以让某⼀个线程等待直到倒计时结束，再开始执⾏。

**CyclicBarrier** **(循环栅栏)：** CyclicBarrier 和 CountDownLatch ⾮常类似，它也可以实现线程间的计数等待，但是它的功能⽐ CountDownLatch 更加复杂和强⼤。 CyclicBarrier 的字⾯意思是可循环使⽤（ Cyclic ）的屏障（ Barrier ）。它要做的事情是，让⼀组线程到达⼀个屏障（也可以叫同步点）时被阻塞，直到最后⼀个线程到达屏障时，屏障才会开⻔，所有被屏障拦截的线程才会继续⼲活。 CyclicBarrier 默认的构造⽅法是 CyclicBarrier(int parties) ，其参数表示屏障拦截的线程数量，每个线程调⽤ await() ⽅法告诉 CyclicBarrier 我已经到达了屏障，然后当前线程被阻塞。

 

1. `CountdownLatch`适用于所有线程通过某一点后通知方法,而`CyclicBarrier`则适合让所有线程在同一点同时执行
2. `CountdownLatch`利用CAS来阻塞和通知线程 , 而`CyclicBarrier`则利用`ReentrantLock`的Condition来阻塞和通知线程
3. `countDownLatch` 是计数器，只能使用一次，而 `CyclicBarrier` 的计数器提供 `reset` 功能，可以多次使用

[CountdownLatch和CyclicBarrier的区别使用场景与具体实现 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/139020914)

**`CountDownLatch` 应用场景：**

让一个线程等待：某一线程在开始运行前等待 n 个线程执行完毕：启动一个服务时，主线程需要等待多个组件加载完毕，之后再继续执行。

**`CyclicBarrier` 应用场景：**

`CyclicBarrier` 可以用于多线程计算数据，最后合并计算结果的应用场景。多个线程等待 直至 多个线程一起执行

 

## 42. 说下对 `ReentrantReadWriteLock` （读写锁）的理解？

`ReentrantReadWriteLock` 允许多个读线程同时访问，但是不允许写线程和读线程、写线程和写线程同时访问。读写锁内部维护了两个锁：一个是用于读操作的 `ReadLock`，一个是用于写操作的 `WriteLock`。读写锁 `ReentrantReadWriteLock` 可以保证多个线程可以同时读，所以在读操作远大于写操作的时候，读写锁就非常有用了。

`ReentrantReadWriteLock` 基于 AQS 实现，它的自定义同步器（继承 AQS）需要在同步状态 state 上维护多个读线程和一个写线程，该状态的设计成为实现读写锁的关键。

`ReentrantReadWriteLock` 很好的利用了高低位。来实现一个32位整型控制两种状态的功能，读写锁将变量切分成了两个部分，高 16 位表示读，低 16 位表示写。

- **`ReentrantReadWriteLock` 的特点：**

1、写锁可以降级为读锁，但是读锁不能升级为写锁；

2、 不管是 `ReadLock` 还是 `WriteLock` 都支持 Interrupt，（语义与 `ReentrantLock` 一致）；

3、`WriteLock` 支持 Condition 并且与 `ReentrantLock` 语义一致，而 `ReadLock `则不能使用 Condition，否则抛出 `UnsupportedOperationException` 异常；

4、 默认构造方法为非公平模式 ，开发者也可以通过指定 fair 为 true 设置为公平模式

5、 读锁里面加写锁，会导致死锁，即持有读锁的情况下去获取写锁，会导致获取写锁永久等待

6、写锁里面是可以加读锁的，这就是锁的降级，即持有写锁的情况下可以去获取读锁

[Java并发控制：ReentrantLock Condition使用详解 - hongdada - 博客园 (cnblogs.com)](https://www.cnblogs.com/hongdada/p/6150699.html)

> 在Condition中，用await()替换wait()，用signal()替换notify()，用signalAll()替换notifyAll()，传统线程的通信方式，Condition都可以实现，这里注意，Condition是被绑定到Lock上的，要创建一个Lock的Condition必须用newCondition()方法。

 

## 43. 谈谈对`StampedLock`的理解

一个更高效同时可以避免写饥饿的读写锁---`StampedLock`。`StampedLock`实现了不仅多个读不互相阻塞，同时在读操作时不会阻塞写操作。

它的核心思想在于，在读的时候如果发生了写，应该通过重试的方式来获取新的值(**读取完毕后需要做一次 戳校验，如果校验通过，表示这期间确实没有写操作，数据可以安全使用，如果校验没通过，需要重新获取读锁，保证数据安全。**( `tryOptimisticRead() `方法（乐观读）))，而不应该阻塞写操作。这种模式也就是典型的无锁编程思想，和`CAS`自旋的思想一样。这种操作方式决定了`StampedLock`在读线程非常多而写线程非常少的场景下非常适用，同时还避免了写饥饿情况的发生。

 

## 44.说下对 Fork和Join 并行计算框架的理解？

Fork/Join 并行计算框架主要解决的是分治任务。分治的核心思想是“分而治之”：将一个大的任务拆分成小的子任务的结果聚合起来从而得到最终结果。

Fork/Join计算框架主要包含两部分，一部分是分治任务的线程池`ForkJoinPool`，另一部分是分治任务`ForkJoinTask`。`ForkJoinPool `支持任务窃取机制，**空闲队列会窃取忙队列的任务**,能够让所有的线程的工作量基本均衡，不会出现有的线程很忙，而有的线程很闲的情况，所以性能很好。

`ForkJoinPool `中的任务队列采用的是双端队列，工作线程正常获取任务和“窃取任务”分别是从任务队列不同的端消费，这样能避免很多不必要的数据竞争。

 

## 45. JDK 中提供了哪些并发容器？

JDK 提供的这些容器大部分在 `java.util.concurrent` 包中。

1. `ConcurrentHashMap`：线程安全的 `HashMap`；
2. `CopyOnWriteArrayList`：线程安全的 List，在读多写少的场合性能非常好，远远好于 Vector；
3. `ConcurrentLinkedQueue`：高效的并发队列，使用链表实现。可以看做一个线程安全的 `LinkedList`，这是一个非阻塞队列；
4. `BlockingQueue`：这是一个接口，JDK 内部通过链表、数组等方式实现了这个接口。表示阻塞队列，非常适合用于作为数据共享的通道；
5. `ConcurrentSkipListMap`：跳表的实现。这是一个 Map，使用跳表的数据结构进行快速查找。

 

## 谈谈对 CopyOnWriteArrayList 的理解？

CopyOnWrite容器即写时复制的容器。通俗的理解是**当我们往一个容器添加元素的时候，不直接往当前容器添加，而是先将当前容器进行Copy，复制出一个新的容器，然后新的容器里添加元素，添加完元素之后，再将原容器的引用指向新的容器。**

CopyOnWriteArrayList 读取操作没有任何同步控制和锁操作，理由就是内部数组 array 不会发生修改，只会被另外一个 array 替换，因此可以保证数据安全。

CopyOnWriteArrayList 写入操作 add() 方法在添加集合的时候加了锁（reentrantlock），保证了同步，避免了多线程写的时候会 copy 出多个副本出来。

**缺点：数据一致性问题**。CopyOnWrite容器只能保证数据的最终一致性，不能保证数据的实时一致性。所以如果你希望写入的的数据，马上能读到，请不要使用CopyOnWrite容器。**【当执行add或remove操作没完成时，get获取的仍然是旧数组的元素】**

 

## 46.谈谈对 `ConcurrentSkipListMap` 的理解？

跳表是一种可以用来**快速查找**的数据结构,是线程安全的有序的哈希表,而就查询的性能而言，跳表的时间复杂度也是 O(logn) 。跳表的本质是同时维护了多个链表，并且链表是**分层**的,它将已排序的数据分布在多层链表中，层与层之间的相等元素也会相连。

![image-20211211145730687](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211211145730687.png)

先往右找，找不到再向下一层，然后继续往右找。

 

# Hadoop

## Hadoop 基础

 

### **介绍下 Hadoop**  ★★★★★

`Hadoop`是一个分布式系统基础架构，主要是为了解决**海量数据的存储和海量数据的分析计**算问题。

`hadoop`的核心组件包括：

`HDFS`（具有高可靠性、高吞吐量的分布式文件系统，用于数据存储），`MapReduce`（处理业务逻辑运算），YARN（负责作业调度与集群资源管理），Common（辅助工具，为其它`Hadoop`模块提供基础设施）。

 

### **Hadoop主要分哪几个部分？他们有什么作用？** ★★★★★

**HDFS**

HDFS是一个文件系统，用于存储文件，通过目录树来定位文件。

其次，它是分布式的，由很多服务器联合起来实现其功能，集群中的服务器有各自的角色。

HDFS 的使用场景：适合一次写入，多次读出的场景。一个文件经过创建、写入和关闭之后就不需要改变。

**MapReduce**

MapReduce是一个分布式运算程序的编程框架。MapReduce核心功能是将用户编写的业务逻辑代码和自带默认组件整合成一个完整的分布式运算程序，并发运行在一个Hadoop集群上。

MapReduce将计算过程分为两个阶段：**Map**和**Reduce**  Map阶段并行处理输入数据，Reduce阶段对Map结果进行汇总

**YARN**

Yarn 是一个资源调度平台，负责为运算程序提供服务器运算资源，相当于一个分布式的操作系统平台，而MapReduce等运算程序则相当于运行于操作系统之上的应用程序。

**Common**

Hadoop体系最底层的一个模块，为Hadoop各子项目提供各种工具，如：配置文件和日志操作等。

 

### **Hadoop的特点**

**1）高可靠性**

Hadoop底层维护多个数据副本，即使Hadoop某个计算元素或存储出现故障时，也不会导致数据的丢失

**2）高扩展性**

在集群间分配任务数据，可方便的扩展数以千计的节点

**3）高效性**

在MapReduce的思想下，Hadoop是并行工作，加快任务处理速度

**4）高容错性**

能够自动将失败的任务重新分配

 

### 说下Hadoop生态圈组件及其作用

**1）Zookeeper**：是一个开源的分布式应用程序协调服务,基于zookeeper可以实现同步服务，配置维护，命名服务。

**2）Flume**：一个高可用的，高可靠的，分布式的海量日志采集、聚合和传输的系统。

**3）Hbase**：是一个分布式的、面向列的开源数据库, 利用Hadoop HDFS作为其存储系统。

**4）Hive**：基于Hadoop的一个数据仓库工具，可以将结构化的数据档映射为一张数据库表，并提供简单 的sql 查询功能，本质是将sql语句转换为MapReduce任务进行运行。

**5）Sqoop**：将一个关系型数据库中的数据导进到Hadoop的 HDFS中，也可以将HDFS的数据导进到关系型数据库中。

 

### **Hadoop 1.x，2.x，3.x的区别**

![image-20220227225547590](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220227225547590.png)

**Hadoop 1.x阶段**，Hadoop中的MapReduce同时处理业务逻辑运算和资源的调度，耦合性较大；

**Hadoop 2.x阶段**，增加了Yarn。Yarn只负责资源的调度，MapReduce只负责运算；

**Hadoop 3.x**相比于Hadoop 2.x阶段在组成上没有变化;  3支持Java8，2只支持7；端口号改变

 

### **Hadoop集群工作时启动哪些进程？它们有什么作用？** ★★★★★

**1）NameNode**

就是Master，Hadoop的主管、管理者

（1）管理HDFS的名称空间；

（2）配置副本策略；

（3）管理数据块（Block）映射信息；

（4）处理客户端读写请求。

**2）DataNode**

就是Slave。NameNode下达命令，DataNode执行实际的操作。

（1）存储实际的数据块；

（2）执行数据块的读/写操作。

**3）Secondary NameNode**

Secondary NameNode并非NameNode的热备。当NameNode挂掉的时候，它并不能马上替换NameNode并提供服务。而是提供周期检查点和清理任务，减少NN启动时间。

（1）辅助NameNode，分担其工作量，如定期合并Fsimage和Edits，并推送给NameNode

（2）SecondaryNameNode中保存了一份和namenode一致的镜像文件（fsimage）和编辑日志（edits）；在紧急情况下，可辅助恢复NameNode

**4）ResourceManager（JobTracker）**

整个集群资源（内存、CPU等）的老大。负责集群中所有资源的统一管理和分配，它接受来自各个节点（NodeManager）的资源汇报信息，并把这些信息按照一定的策略分配给各个应用程序（即ApplicationMaster）。

（1）与客户端交互，处理来自客户端的请求。

（2）启动和管理ApplicatinMaster，并在它运行失败时重新启动它。

（3）管理NodeManager，接受来自NodeManager的资源管理汇报信息，并向NodeManager下达管理命令（比如杀死Contanier）等。

（4）资源管理与调度，接收来自ApplicationMaster的资源申请请求，并为之分配资源（核心）。

**5）NodeManager（TaskTracker）**

NodeManager是YARN中单个节点的代理（单个节点服务器资源老大），（它需要与应用程序的ApplicationMaster和集群管理者ResourceManager交互；它从ApplicationMaster上接收有关Container的命令并执行（比如启动、停止Contaner）；向ResourceManager汇报各个Container运行状态和节点健康状况，并领取有关Container的命令（比如清理Container）。NodeManager管理的是Container而不是任务，一个Container中可能运行着各种任务，但是对NodeManager而言是透明的，它只负责Container相关操作，比如管理Container的生命周期，即启动Container、监控Container和清理Container等）。

（1）管理单个节点上的资源

（2）处理来自ResourceManager的命令

（3）处理来自ApplicationMaster的命令

**6）DFSZKFailoverController**（高可用状态下）

高可用时它负责监控NameNode的状态，并及时的把状态信息写入Zookeeper。它通过一个独立线程周期性的调用NameNode上的一个特定接口来获取NameNode的健康状态。ZKFC也有选择谁作为Active NameNode的权利，因为最多只有两个节点，选择策略比较简单（先到先得，轮换）。

**7）JournalNode**（高可用状态下）

高可用情况下存放NameNode的editlog文件

 

### **Hadoop小文件处理问题** ★★★★★

> 小米、海康

小文件指的是那些size比HDFS的block size小的多的文件。Hadoop适合处理少量的大文件，而不是大量的小文件。

**1、小文件导致的问题**

HDFS 上每个文件都要在 NameNode 上创建对应的元数据（这个元数据的大小约为 150byte），这样当小文件比较多的时候，就会产生很多的元数据文件，一方面会大量占用 NameNode 的内存空间，另一方面就是元数据文件过多，使得寻址索引速度变慢。

其次，访问大量小文件速度远远小于访问几个大文件。HDFS最初是为流式访问大文件开发的，如果访问大量小文件，可能需要不断的从一个datanode跳到另一个datanode，严重影响性能。

小文件过多，在进行 MR 计算时，会生成过多切片，需要启动过多的 MapTask。每个 MapTask 处理的数据量小，导致 MapTask 的处理时间比启动时间还小，白白消耗资源。

 

- **在源头预防hadoop大量小文件**

  比如 flume sink 到hdfs时，可配置参数：

  hdfs.rollInterval=3600，hdfs.rollSize=134217728，hdfs.rollCount =0

  文件在达到128M时会滚动生成新文件、文件创建超3600秒时会滚动生成新文件、表示不基于事件个数

  > 会先比较时间，时间没到比较其他的；

- **Hadoop自带的解决方案**（1、2、3）

1. Hadoop Archive或者HAR，是一个高效地将小文件放入HDFS块中的文件存档工具，它能够将多个小文件打包成一个HAR文件，这样在减少namenode内存使用的同时，仍然允许对文件进行透明的访问。
2. Sequence file ；Sequence file由一系列的二进制key/value组成，如果为key小文件名，value为文件内容，则可以将大批小文件合并成一个大文件。
3. CombineFileInputFormat是一种新的inputformat，用于将多个文件合并成一个单独的split，另外，它会考虑数据的存储位置。
4. 开启 uber 模式，实现 JVM 重用（计算方向）， 默认情况下，每个 Task 任务都需要启动一个 JVM 来运行，如果 Task 任务计算的数据 量很小，我们可以让同一个 Job 的多个 Task 运行在一个 JVM 中，不必为每个 Task 都开启 一个 JVM

 

## HDFS

### **HDFS文件写入和读取流程** （存储机制）★★★★★

> 阿里×3，阿里社招，腾讯x2，字节x2，百度，拼多多x2，浩鲸云，小米，流利说，顺丰，网易云音乐×2，有赞×2，祖龙娱乐，360×2，商汤科技，招银网络，深信服，多益，大华，快手，电信云计算，转转，美团x5，shopee×2：回答越详细越好，猿辅导×2，科大讯飞，恒生电子，搜狐，京东，头条，富途
>

#### 写流程

![image-20220228101749112](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220228101749112.png)

1）客户端会先对文件分块，然后通过Distributed FileSystem模块向NameNode请求上传文件，NameNode检查目标文件是否已存在，父目录是否存在。

2）NameNode返回是否可以上传。

3）如果可以上传，客户端请求第一个 block上传到哪几个datanode服务器上。

4）NameNode返回3个datanode节点，分别为dn1、dn2、dn3。

5）客户端通过FSDataOutputStream模块向dn1请求上传数据，dn1收到请求会继续调用dn2，然后dn2调用dn3，将这个通信管道建立完成。

6）dn1、dn2、dn3逐级应答客户端。

7）客户端开始往dn1上传第一个block，FSDataOutputStream会将文件分割成packets数据包，然后将这些packets写到其内部的一个叫做data queue(数据队列)中，然后以packet为单位发送数据，dn1收到一个packet就会传给dn2，dn2传给dn3；**dn1每传一个packet会放入一个应答队列等待应答**。

> 如果一个packet在发送后，已经收到了所有DN返回的ack确认消息，这个packet会在ackquene中删除！ 假如一个packet在发送后，在收到某个DN返回的ack确认消息时超时，就是写入失败时：
>
> - 首先，Pipeline数据流管道会被关闭，ack queue中的packets会被添加到data queue的前面以确保不会发生packets数据包的丢失；
>
> - 接着，在正常的DataNode节点上的以保存好的block的ID版本会升级——这样发生故障的DataNode节点上的block数据会在节点恢复正常后被删除；失效节点也会被从Pipeline中删除；
>
> - 最后，重新建立管道流，剩下的数据会被写入到Pipeline数据流管道中的其他两个节点中。
>
> - 如果Pipeline中的多个节点在写数据是发生失败，那么只要写成功的block的数量达到**dfs.replication.min(默认为1)**，那么就任务是写成功的，然后NameNode后通过一步的方式将block复制到其他节点，最后事数据副本达到**dfs.replication参数**配置的个数。
>
>   只要有一个DN节点收到了数据，DN上报NN已经收完此块，NN就认为当前块已经传输成功！

8）当一个block传输完成之后，客户端再次请求NameNode上传第二个block的服务器。（重复执行3-7步）。

> 注：发送完成信号的时机取决于集群是强一致性还是最终一致性，强一致性则需要所有DataNode写完后才向NameNode汇报。最终一致性则其中任意一个DataNode写完后就能单独向NameNode汇报，HDFS一般情况下都是强调最终一致性

 

[[Hadoop深入学习：解析HDFS的写文件流程 - 飞翔的荷兰人 - ITeye博客](https://www.iteye.com/blog/flyingdutchman-1900536)](https://blog.csdn.net/axjzf/article/details/80691586)

#### 读流程

![image-20220228102509966](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220228102509966.png)

（1）客户端通过 DistributedFileSystem 向 NameNode 请求下载文件，NameNode 通过查 询元数据，找到文件块所在的 DataNode 地址。

（2）client 挑选一台 DataNode（就近原则，然后随机）服务器，请求读取数据。

（3）DataNode 开始传输数据给客户端（从磁盘里面读取数据输入流，以 Packet 为单位来做发送校验，校验不通过会从别的datanode读取）。

（4）客户端以 Packet 为单位接收，先在本地缓存，然后写入目标文件。

 

### HADOOP副本选择策略

NameNode节点选择一个DataNode节点去存储block副本的过程就叫做**副本存放**，这个过程的策略其实就是在可靠性和读写带宽间的权衡。

第一个副本在Client所处的节点上。 如果客户端在集群外，随机选一个。

第二个副本在另一个机架的随机 一个节点

第三个副本在第二个副本所在机架的 随机节点

 

### 详细说下HDFS  ★★★★★

> 详细说下hdfs--海康

1、HDFS是一个分布式文件系统，为海量数据提供存储，可将巨大的数据集分派到一个由普通计算机组成的集群中的多个节点进行存储，降低了硬件的成本

2、HDFS组成架构（下一题）

3、优缺点

优点：

- **高容错性**

  数据自动保存多个副本。它通过增加副本的形式，提高容错性

-  **适合处理大数据**

  数据规模：能够处理数据规模达到GB、TB、甚至PB级别的数据；

  文件规模：能够处理百万规模以上的文件数量，数量相当之大。

- **可构建在廉价机器上，降低硬件成本。**

缺点：

- **不适合低延时数据访问**

- **无法高效的对大量小文件进行存储**

- **不支持并发写入、文件随机修改**

  一个文件只能有一个写，不允许多个线程同时写；

  仅支持数据append（追加），不支持文件的随机修改

 

### **HDFS组成架构**

> 京东，美团，电信云计算，猿辅导，网易，作业帮
>

**1）Client ：就是客户端**

（1）文件切分。文件上传HDFS的时候，Client将文件切分成一个一个的Block，然后进行存储；

（2）与NameNode交互，获取文件的位置信息；

（3）与DataNode交互，读取或者写入数据；

（4）Client提供一些命令来管理HDFS，比如启动或者关闭HDFS；

（5）Client可以通过一些命令来访问HDFS；

**2） NameNode **：就是Master，它是一个主管、管理者

（1）管理HDFS的名称空间；

（2）管理数据块（Block）映射信息；

（3）配置副本策略；

（4）处理客户端读写请求。

**3） DataNode **：就是Slave。NameNode下达命令，DataNode执行实际的操作

（1）存储实际的数据块；

（2）执行数据块的读/写操作。

**4） Secondary NameNode** ：并非NameNode的热备。当NameNode挂掉的时候，它并不能马上替换NameNode并提供服务

（1）辅助NameNode，分担其工作量；定期合并Fsimage和Edits，并推送给NameNode；

（2）在紧急情况下，可辅助恢复NameNode。

 

### **HDFS的容错机制**

> 腾讯，一点资讯
>

**针对 DataNode失效 问题**

每个DataNode以固定的周期向NameNode 发送心跳信号，通过这种方法告诉 NameNode 它们在正常工作。如果在一定的时间内 NameNode 没有收到 DataNode 心跳，就认为该 DataNode 宕机了。

**针对 网络故障 而导致无法收发数据的问题**

HDFS提供了ACK的机制，在发送端发送数据后，如果没有收到ACK并且经过多次重试后仍然如此，则认为网络故障；

**针对 数据损坏(脏数据) 问题**

在传输数据的时候，同时会发送总和检验码，当数据存储到硬盘时，总和检验码也会被存储。

所有的 DataNode 都会定期向 NameNode 发送数据块的存储状况。在发送数据块报告前，会先检查总和校验码是否正确，如果数据存在错误就不发送该数据块的信息。

 

### **HDFS如何保证数据不丢失？/DataNode节点保证数据完整性的方法**？★★★★★

> 百度

- **先答工作机制，保证datanode 节点可用；**
- **其次传输过程中有ACK应答机制**
- **然后再说校验**

**数据的读取和写入都要进行校验**

1）数据在写入之后会进行校验和的计算，之后DataNode周期性的进行校验和计算，将计算结果与第一次进行对比，若相同表示无数据丢失，若不相同表示有数据丢失，丢失后将进行数据修复；

2）数据读取之前对数据进行校验，与第一次的结果进行对比，若相同表示数据没有丢失，可以读取，若不相同表示数据有所丢失，到其他副本读取数据。

**DataNode 节点保证数据完整性的方法：**

（1）当 从DataNode 读取 Block 的时候，它会计算 CheckSum。

（2）如果计算后的 CheckSum，与 Block 创建时值不一样，说明 Block 已经损坏。

（3）Client 读取其他 DataNode 上的 Block。

（4）DataNode 在其文件创建后周期验证 CheckSum。

 

### Datanode的工作机制 ★★★★★

（1）一个数据块在 DataNode 上以文件形式存储在磁盘上，包括两个文件，一个是数据本身，一个是元数据,包括数据块的长度，块数据的校验和，以及时间戳。

（2）DataNode 启动后向 NameNode 注册，通过后，周期性（6 小时）的向 NameNode 上 报所有的块信息。

（3）Datanode和NameNode保持一个心跳，心跳是每 3 秒一次，心跳返回结果带有 NameNode 给该 DataNode 的命令, 如复制块 数据到另一台机器，或删除某个数据块。如果超过10 分钟没有收到某个 DataNode 的心跳， 则认为该节点不可用。

（4）集群运行中可以安全加入和退出一些机器。

**DataNode 节点保证数据完整性的方法（数据损坏）**

（1）当 从DataNode 读取 Block 的时候，它会计算 CheckSum。

（2）如果计算后的 CheckSum，与 Block 创建时值不一样，说明 Block 已经损坏。

（3）Client 读取其他 DataNode 上的 Block。

（4）DataNode 在其文件创建后周期验证 CheckSum。

 

> ###  HDFS中datanode怎么存储数据的
>
> > 华为
>
> 1、datanode以**数据块**的形式存储HDFS文件，DataNode 将数据块存储到本地文件系统目录中，具体的目录可以通过配置 hdfs-site.xml 里面的 **dfs.datanode.data.dir** 参数。在典型的安装配置中，一般都会配置多个目录，并且把这些目录分别配置到不同的设备上；
>
> 2、**datanode的工作机制**

 

 

### NameNode和Secondary NameNode 它的工作机制是怎样的？/checkpoint流程？★★★★★

（1）Fsimage文件：HDFS文件系统元数据的一个**永久性的检查点**，其中包含HDFS文件系统的所有目录和文件inode的序列化信息。

（2）Edits文件：存放HDFS文件系统的所有更新操作的路径，文件系统客户端执行的所有写操作首先会被追加记录到Edits文件中。

> **思考：** NameNode中的元数据是存储在哪里的？
>
> 首先，我们做个假设，如果存储在NameNode节点的磁盘中，因为经常需要进行随机访问，还有响应客户请求，必然是效率过低。因此，元数据需要存放在内存中。但如果只存在内存中，一旦断电，元数据丢失，整个集群就无法工作了。因此产生在磁盘中备份元数据的FsImage。这样又会带来新的问题，当在内存中的元数据更新时，如果同时更新FsImage，就会导致效率过低，但如果不更新，就会发生一致性问题，一旦NameNode节点断电，就会产生数据丢失。因此，引入Edits文件（只进行追加操作，效率很高）。每当元数据有更新或者添加元数据时，修改内存中的元数据并追加到Edits中。这样，一旦NameNode节点断电，可以通过FsImage和Edits的合并，合成元数据。 但是，如果长时间添加数据到Edits中，会导致该文件数据过大，效率降低，而且一旦断电，恢复元数据需要的时间过长。因此，需要定期进行FsImage和Edits的合并，如果这个操作由NameNode节点完成，又会效率过低。因此，引入一个新的节点SecondaryNamenode，专门用于FsImage和Edits的合并。

![image-20220401134509370](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220401134509370.png)

**NameNode**

（1）第一次启动 NameNode 格式化后，创建 Fsimage 和 Edits 文件。如果不是第一次启动，直接加载编辑日志和镜像文件到内存。

（2）客户端对元数据进行增删改的请求。

（3）NameNode 在编辑日志中记录修改（记录操作日志，更新滚动日志）。

（4）NameNode 在内存中对元数据进行增删改。

**Secondary NameNode**

1. Secondary NameNode 询问 NameNode 是否需要 checkpoint。直接带回 NameNode 是否检查结果；

   > 定时时间到或者Edits中数据满了（100万条） 会直接触发

2. Secondary NameNode 请求执行 checkpoint；

3. NameNode 滚动正在写的 edits 日志：生产一份新的Edits 日志，后续有客户端请求，记录这个新的日志

4. 将滚动前的编辑日志和镜像文件拷贝到 Secondary NameNode；

5. Secondary NameNode 加载编辑日志和镜像文件到内存，进行合并；

6. 生成新的镜像文件 fsimage.chkpoint；

7. 拷贝 fsimage.chkpoint 到 NameNode；

8. NameNode 将 fsimage.chkpoint 重新命名成 fsimage；

 

### NameNode高可用   ★★★★★

![image-20220620144820560](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220620144820560.png)

就是配置双 NameNode，一个作为活动的NameNode（Active），一个作为备份的NameNode（Standby）。备份的NameNode的命名空间与活动的NameNode是实时同步的，所以当活动的NameNode发生故障而停止服务时，备份NameNode可以立即切换为活动状态，而不影响HDFS集群服务。

2. 监控 NameNode 状态采用 zookeeper，两个 NameNode 节点分别有一个进程（ZKFC ）监控程序；ZKFailoverController主要职责

       1）健康监测：周期性的向它监控的NN发送健康探测命令，从而来确定某个NameNode是否处于健康状态。

   2）会话管理：如果NN是健康的，zkfc就会在zookeeper中保持一个打开的会话，如果NameNode同时还是Active状态的，那么zkfc

还会在Zookeeper中占有一个类型为短暂类型的znode，当这个NN挂掉时，这个znode将会被删除，然后备用的NN，将会得到这把锁，

升级为主NN，同时标记状态为Active。

  3）当宕机的NN新启动时，它会再次注册zookeper，发现已经有znode锁了，便会自动变为Standby状态，如此往复循环，保证高可靠，需要注意，目前仅仅支持最多配置2个NN。

  4）master选举：如上所述，通过在zookeeper中维持一个短暂类型的znode，来实现抢占式的锁机制，从而判断那个NameNode为Active状态

> 防止脑裂会强制给原本的 Active NameNode 节点发送强制关闭请求，之后将 备用的 NameNode 设置为 Active。强制：kill -9、shell脚本

2. **元数据信息同步在 HA 方案中采用的是“共享存储”**。每次写文件时，需 要将日志（edit log）同步写入共享存储，（fsimage还是在磁盘）这个步骤成功才能认定写文件成功。然后备份节点定期从共享存储同步日志，以便进行主备切换。

**共享存储通过QJM实现**

Quorum Journal方案中有两个重要的组件。

**JournalNoe（JN）** ：运行在N台独立的物理机器上，它将editlog文件保存在JournalNode的本地磁盘上，同时JournalNode还对外提供RPC接口QJournalProtocol以执行远程读写editlog文件的功能。

**QuorumJournalManager(QJM)** ：运行在NmaeNode上，（目前HA集群只有两个Namenode），通过调用RPC接口QJournalProtocol中的方法向JournalNode发送写入、排斥、同步editlog。

> Quorum Journal方案依赖于这样一个概念：HDFS集群中有2N+1个JN存储editlog文件，这些editlog 文件是保存在JN的本地磁盘上的。每个JN对QJM暴露QJM接口QJournalProtocol，允许Namenode读写editlog文件。当Namenode向共享存储写入editlog文件时，它会通过ＱＪＭ向集群中所有的ＪＮ发送写editlog文件请求，当有一半以上的ＪＮ返回写操作成功时，即认为写成功。这个原理是基于Paxos算法的。
>

#### 脑裂

同时出现两个namenode的情况

为了预防脑裂的情况，HDFS提供了三个级别的隔离机制（fencing）:

- 共享存储隔离：同一时间只允许一个Namenode向JournalNodes写入editlog数据。

- 客户端隔离：同一时间只允许一个Namenode响应客户端的请求。

- Datanode隔离：同一时间只允许一个Namenode向Datanode下发指令，如删除、复制数据块指令等等。


同时进行主备切换时，让原本Active 状态的namenode强制下线；

 

### HDFS的block为什么是128M？增大或减小有什么影响？ ★★★★★

> 2.7.3之前64m；

##### 为什么要分块、设置数据块的好处：

（1）一个文件的大小可以大于集群任意节点磁盘的容量

（2）容易对数据进行备份，提高容错能力

（3）使用抽象块概念而非整个文件作为存储单元，大大简化存储子系统的设计

**为什么block不能设置过大，也不能设置过小**

一个mapreduce一次只能处理一个块的数据，如果块设置过大，程序在处理这块数据时，会非常慢；

如果设置过小，一方面存放大量小文件会占用NameNode中大量内存来存储元数据，而NameNode的内存是有限的，不可取；另一方面块过小，寻址时间增长，导致程序一直在找block的开始位置。

因此，块适当设置大一些，减少寻址时间，传输一个有多个块组成的文件的时间**主要取决于磁盘的传输速度**。

**块大小多少合适**

如果寻址时间约为10ms，而传输速率为100MB/s，**为了使寻址时间仅占传输时间的1%**，我们要将块大小设置约为100MB。默认的块大小128MB。

![image-20220426220008134](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220426220008134.png)

**如果增加文件块大小，那就需要增加磁盘的传输速率；所以块大小主要由磁盘传输率决定。**

 

### **HDFS的数据一致性靠什么保证？**

1、hdfs的namenode/secondnamenode机制 保证元数据一致

2、心跳机制

namenode与datanode之间通过心跳（每3秒一次可以在配置文件中设置）信息来确认并更新datanode的元数据信息。

3、安全校验

为了避免网络传输造成的数据错误问题，HDFS采用了校验和机制。各个node之间数据备份和数据读取，校验通过数据备份成功，否则备份失败，重新备份

4、安全模式

HDFS在初始化阶段会进入安全模式，在安全模式下namenode不允许操作。namenode会与连接的datanode进行安全检查，只有当安全的数据块比值达到设定的阈值才会退出安全模式，

5、回滚机制

在hdfs升级或者执行数据写入时，相关的数据将会被保留备份，如果成功，则更新备份，失败，则使用备份信息。

6、回收站

当数据文件从hdfs中删除时，文件并没有消失，而是转存/trash目录下。如果误删除的话，可以在该目录下找回文件，文件的存储时间可以配置fs.trash.interval。超过该时间namenode将该文件的元数据删除，同时datanode上的文件将会被删除。

 

### hdfs有几种存储类型★★★

> 字节

Hadoop中的文件格式大致上分为行式存储和列式存储两类

**面向行**

- 同一行的数据存储在一起，即连续存储。SequenceFile,MapFile。
- 采用这种方式，如果只需要访问行的一小部分数据，亦需要将整行读入内存。
- 面向行的存储适合于整行数据需要同时处理的情况。

**面向列**

- 整个文件被切割为若干列数据，每一列数据一起存储。Parquet , RCFile,ORCFile。

- 面向列的格式使得读取数据时，可以跳过不需要的列，适合于只处于行的一小部分字段的情况。

- 同一列中的数据属于同一类型，压缩效果显著；自由的压缩算法选择：不同列的数据具有不同的数据类型，适用的压缩算法也就不尽相同

  > 同时不适合流式写入，因为一旦写入失败，当前文件无法恢复，而面向行的数据在写入失败时可以重新同步到最后一个同步点
  >
  > 柱状格式（ORC等）无法决定何时冲洗。由于Flume无法控制将列式内存缓冲区写入存储器的时间，所以Flume采用的是面向行的存储格式

https://blog.csdn.net/Shockang/article/details/115739955

## MapReduce

### **介绍下MapReduce**? 优缺点？

> 字节x2，美团，小米
>

MapReduce 是一个**分布式运算程序**的编程框架，它的核心功能是**将用户编写的业务逻辑代码和自带默认组件整合成一个完整的分布式运算程序**，并发运行在一个 Hadoop 集群上。

一个完整的mapreduce程序有三类实例进程

- MRAppMaster：负责整个程序的协调过程

- MapTask：负责map阶段的数据处理

- ReduceTask：负责reduce阶段的数据处理

**优点**

**1）MapReduce 易于编程**

它简单的实现一些接口，就可以完成一个分布式程序，这个分布式程序可以分布到大量廉价的 PC 机器上运行。也就是说你写一个分布式程序，跟写一个简单的串行程序是一模一样的。就是因为这个特点使得 MapReduce 编程变得非常流行。

**2）良好的扩展性**

当你的计算资源不能得到满足的时候，你可以通过简单的增加机器来扩展它的计算能力。

**3）高容错性**

MapReduce 设计的初衷就是使程序能够部署在廉价的 PC 机器上，这就要求它具有很高的容错性。比如其中一台机器挂了，它可以把上面的计算任务转移到另外一个节点上运行， 不至于这个任务运行失败，而且这个过程不需要人工参与，而完全是由 Hadoop 内部完成的。

**4）适合** **PB** **级以上海量数据的离线处理**

可以实现上千台服务器集群并发工作，提供数据处理能力。

**缺点**

**1）不擅长实时计算**

MapReduce无法毫秒或者秒级内返回结果。

**2）不擅长流式计算**

流式计算的输入数据是动态的，而MapReduce的输入数据集是静态的，不能动态变化。这是因为MapReduce 自身的设计特点决定了数据源必须是静态的。

**3）不擅长** **DAG（有向无环图）计算**

多个应用程序存在依赖关系，后一个应用程序的输入为前一个的输出。在这种情况下，MapReduce并不是不能做，而是使用后，每个MapReduce作业的输出结果都会写入到磁盘， 会造成大量的磁盘 IO，导致性能非常的低下。

 

### 怎么去编写MR程序（以wordcount为例）

1、编写map程序

- 继承父类Mapper
- 获取一行的数据，以分隔符进行切分，然后解析成K,V :（word,1）

2、编写reduce程序

- 继承父类reduce
- 对相同key的value进行累加

3、编写driver驱动类

-  获取配置信息以及获取 job 对象
- 关联本 Driver 程序的 jar
-  关联 Mapper 和 Reducer 的 jar
- 设置 Mapper 输出的 kv 类型
-  设置最终输出 kv 类型
- 设置输入和输出路径
-  提交 job

 

### **MapReduce工作原理/工作机制** ★★★★★

**map阶段**

inputFile 被切割为多个 split 文件，然后通过 RecordReader 按行读取内容并解析成K-V的形式交给用户编写map方法 ，数据被 map()方法 处理完之后交给 OutputCollect 收集器，然后写入默认大小为100M的环形缓冲区， 当缓冲区达到阈值的时候（80%）需要将缓冲区的数据以一个临时文件的方式溢写到磁盘，在写入磁盘之前，线程首先根据reduce任务的数目将数据划分为相同数目的分区，也就是一个reduce任务对应一个分区的数据，并进行区内快速排序，如果此时设置了Combiner，会将排序后的结果进行Combine操作。当整个 map task 结束后再对磁盘中这个 maptask 产生的所有临时文件做合并，然后进行一次归并排序，生成最终的正式输出文件，然后等待 reduce task 的拉取。

**reduce阶段**

ReduceTask 启动线程（Fetcher ）去 对应的分区copy 数据，在此过程中后台会启动两个 merge 线程，分别为 inMemoryMerger 和 onDiskMerger，inMemoryMerger 先将数据拉取到内存，当内存中的数据达到一定阈值时,inMemoryMerger将内存中的数据 merge 到磁盘，onDiskMerger将磁盘中的数据进行 merge。待数据 copy 完成之后，进行一个最终的sort归并排序，纯粹的 sort 阶 段，完成之后就是 reduce ，调用用户定义的 reduce 函数进行处理。

> 合并的过程中会产生许多的中间文件（写入磁盘了），但MapReduce会让写入磁盘的数据尽可能地少，并且最后一次合并的结果并没有写入磁盘，而是直接输入到reduce函数。

 

> ### **Reduce怎么知道去哪里拉Map结果集**
>
> MRAPPMaster负责任务的调度与监控，当map执行结束后，会汇报给MRAPPMaster。[reduce](https://so.csdn.net/so/search?q=reduce&spm=1001.2101.3001.7020)中的一个线程会定期询问MRAPPMaster以便获取map输出的位置。
>
> ### **分区中的数据怎么知道它对应的reduce是哪个呢**？
>
> 根据 reduce个数进行分区，reduce会被分配一个分区号，哈希取模定位到具体分区；ReduceTask 根据自己的分区号去拉取对应分区的数据
>
> > 其实map任务一直和nodemanager（TaskTracker）保持联系，而nodemanager又一直和 ResourceManager 保持心跳。所以ResourceManager中保存了整个集群中的宏观信息。只要reduce任务向ResourceManager 获取对应的map输出位置就ok了哦。
>
> ### **怎么拉取Map结果集**
>
> **每个节点都会启动一个常驻的HTTP server，其中一项服务就是响应Reduce拖取Map数据**。Reduce任务通过HTTP向各个Map任务拖取它所需要的数据。当有MapOutput的HTTP请求过来的时候，HTTP server就读取相应的Map输出文件中对应这个Reduce部分的数据通过网络流输出给Reduce。

 

### **MapReduce的Shuffle过程及其优化** ★★★★★

从Map输出到Reduce输入的整个过程可以广义地称为Shuffle。Shuffle横跨Map端和Reduce端，主要包括以下过程：

1. **Collect 阶段**：将 MapTask 的结果输出到默认大小为 100M 的环形缓冲区， 保存的是 key/value等。
2. **Spill 阶段**：当内存中的数据量达到一定的阀值的时候，就会将数据写入本地磁盘，在将数据写入磁盘之前，线程首先根据reduce任务的数目将数据划分为相同数目的分区，然后对区内数据进行一次快排，如果 配置了 combiner，还会将有相同分区号和 key 的数据进行聚合。
3. **MapTask 阶段的 Merge**：把所有溢出的临时文件进行一次合并然后做一个归并排序，以确保**一个** MapTask 最终只产生一个中间数据文件。
4. **Copy 阶段**：ReduceTask 启动 Fetcher 线程到已经完成 MapTask 的节点上复制一份属于自己的数据，这些数据默认会保存在内存的缓冲区中，当内存的缓冲区达到一定的阀值的时候，就会将数据写到磁盘之上。
5. **ReduceTask 阶段的 Merge**：在 ReduceTask 远程复制数据的同时，会在后台开启两个线程对内存到本地的数据文件进行合并操作；
6. **sort** ：对数据进行一个最终的归并排序；由于各个MapTask已经实现对自己的处理结果进行了局部排序，因此，ReduceTask只需对所有数据进行一次归并排序即可。

 

**MapReduce Shuffle后续优化方向**

- 压缩：对数据进行压缩，减少写读数据量；
- 减少不必要的排序：并不是所有类型的Reduce需要的数据都是需要排序的，排序这个过程如果不需要最好还是不要的好；
- 内存化：Shuffle的数据不放在磁盘而是尽量放在内存中，除非逼不得已往磁盘上放；**当然了如果有性能和内存相当的第三方存储系统，那放在第三方存储系统上也是很好的；这个是个大招；**

  > - 网络框架：netty的性能据说要占优了；
  > - 本节点上的数据不走网络框架：对于本节点上的Map输出，Reduce直接去读吧，不需要绕道网络框架。

 

###  环形缓冲区实现细节/MapReduce为什么一定要有环型缓冲区

环形缓冲区分为三块，空闲区、数据区、索引区。初始位置取名叫做“赤道”。初始状态的时候，数据和索引都为0，所有空间都是空闲状态。

环形缓冲区写入的时候，有个细节：数据是从赤道的右边开始写入，索引（每次申请4kb）是从赤道是左边开始写。这个设计很有意思，这样两个文件各是各的，互不干涉。

在数据和索引的大小到了mapreduce.map.sort.spill.percent参数设置的比例时（默认80%，这个是调优的参数），会有两个动作：

1、对写入的数据进行原地排序，并把排序好的数据和索引spill到磁盘上去；

2、在空闲的20%区域中，重新算一个新的赤道，然后在新赤道的右边写入数据，左边写入索引；

3、当20%写满了，但是上一次80%的数据还没写到磁盘的时候，程序就会panding一下，等80%空间腾出来之后再继续写。

如此循环往复，永不停歇，直到所有任务全部结束。整个操作都在内存，形状像一个环，所以才叫环形缓冲区。

**为什么要有环形缓冲区？**

1、使用环形缓冲区，便于写入缓冲区和写出缓冲区同时进行。

2、环型缓冲区不会等缓冲区满了再spill ，可以防止阻塞

3、每个Map任务不断地将键值对输出到在内存中构造的一个环形数据结构中，**使用环形数据结构是为了更有效地使用内存空间，在内存中放置尽可能多的数据**。

4、环形缓冲区不需要重新申请新的内存，始终用的都是这个内存空间。大家知道MR是用java写的，而Java有一个最讨厌的机制就是Full GC。环形缓冲区从头到尾都在用那一个内存，不断重复利用，因此完美的规避了Full GC导致的各种问题，同时也规避了频繁申请内存引发的其他问题。

5、环形缓冲区同时做了两件事情：1、**排序**；2、索引。在这里一次排序，将无序的数据变为有序，**写磁盘的时候顺序写，读数据的时候顺序读，效率高非常多**！在这里设置索引区也是为了能够持续的处理任务。每读取一段数据，就往索引文件里也写一段，这样在排序的时候能加快速度。

> 索引的作用：加快区内排序；会记录每个分区的元信息包括在临时文件 中的偏移量，这样reduce task拉取数据的时候速度快些

 

### **MapReduce怎么确定MapTask的数量？**

**MapTask数量影响因素**；map个数就是切片的个数

影响map个数（split个数）的主要因素有：

- **文件的大小。**当块（dfs.block.size）为128m时，如果输入文件为128m，会被划分为1个split；当块为256m，会被划分为2个split。

- **文件的个数。**FileInputFormat按照文件分割split，**并且只会分割大文件，即那些大小超过HDFS块的大小的文件**。如果HDFS中dfs.block.size设置为128m，而输入的目录中文件有100个，则划分后的split个数至少为100个。

- **splitSize的大小。**分片是按照splitszie的大小进行分割的，一个split的大小在没有设置的情况下，默认等于hdfs block的大小

**MapTask的数量计算原则为：**

![image-20220228192505527](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220228192505527.png)

 

> **CombineTextInputFormat切片机制**
>
> （1）虚拟存储过程
>
> 将输入目录下所有文件大小，依次和设置的 setMaxInputSplitSize 值比较，如果不大于设置的最大值，逻辑上划分一个块。如果输入文件大于设置的最大值且大于两倍，那么以最大值切割一块；当剩余数据大小超过设置的最大值且不大于最大值 2 倍，此时将文件均分成 2 个虚拟存储块（防止出现太小切片）。例如 setMaxInputSplitSize 值为 4M，输入文件大小为 8.02M，则先逻辑上分成一个4M。剩余的大小为 4.02M，如果按照 4M 逻辑划分，就会出现 0.02M 的小的虚拟存储文件，所以将剩余的 4.02M 文件切分成（2.01M 和 2.01M）两个文件。
>
> （2）切片过程：
>
> （a）判断虚拟存储的文件大小是否大于 setMaxInputSplitSize 值，大于等于则单独形成一个切片。
>
> （b）如果不大于则跟下一个虚拟存储文件进行合并，共同形成一个切片。
>
> （c）测试举例：有 4 个小文件大小分别为 1.7M、5.1M、3.4M 以及 6.8M 这四个小文件，则虚拟存储之后形成 6 个文件块，大小分别为：
>
> 1.7M，（2.55M、2.55M），3.4M 以及（3.4M、3.4M）
>
> 最终会形成 3 个切片，大小分别为：
>
> （1.7+2.55）M，（2.55+3.4）M，（3.4+3.4）M

 

### 确定reduce个数

参数1：hive.exec.reducers.bytes.per.reducer（默认为1G) ---------------------- 每个reduce任务处理的数据量
参数2：hive.exec.reducers.max（默认为999） ---------------------- 每个任务最大的reduce数目

- 计算reducer数的公式
  N=min(参数2，总输入数据量/参数1)
- **set mapred.reduce.tasks=13;**  直接set

 

### **MapReduce数据倾斜产生的原因及其解决方案**/-->看hive中的部分

> 腾讯，大华，多益，冠群驰骋，网易
>

**数据倾斜产生的原因**

- key 分布不均匀，某一个key的条数比其他key多太多；
- 业务数据自带的特性；
- 建表时考虑不全面；
- 可能某些 HQL 语句自身就存在数据倾斜问题。

**解决方案：**

- 数据预处理，找到异常数据
- 对分布不均匀的数据，进行单独计算，首先对key做一层hash，把数据打散，让它的并行度变大，之后进行汇集
- 提前在 map 进行 combine，减少传输的数据量（适合使用combine的场景）

 

### MapReduce用了几次排序，分别是什么？ ★★★★★

> 美团，米哈游
>

在Map任务和Reduce任务的过程中，**一共发生了3次排序**

1）当map函数产生输出时，会首先写入内存的环形缓冲区，当达到设定的阀值，在刷写磁盘之前，后台线程会将缓冲区的数据划分成相应的分区。在每个分区中，后台线程按键进区内**快速排序**

2）在Map任务完成之前，磁盘上存在多个已经分好区，并排好序的溢写文件，这时溢写文件将被合并成一个已分区且已排序的输出文件。由于溢写文件已经经过第一次排序，所有合并文件只需要再做一次**归并排序**即可使输出文件整体有序。

3）在reduce阶段，需要将多个Map任务的输出文件copy到ReduceTask中后合并，由于经过第二次排序，所以合并文件时只需再做一次**归并**排序即可使输出文件整体有序

在这3次排序中**第一次是内存缓冲区做的内排序，使用的算法使快速排序**，**第二次排序和第三次排序都是在文件合并阶段发生的，使用的是归并排序**。

=====reduce个数与分区数的关系

> ![image-20220621134938797](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621134938797.png)

====

### **MapReduce压缩方式**

**压缩的好处和坏处**

压缩的优点：**以减少磁盘 IO、减少磁盘存储空间，数据规模很大的情况下，压缩尤为重要**

压缩的缺点：增加 CPU 开销。

**压缩原则** （1）运算密集型的 Job，少用压缩 （2）IO 密集型的 Job，多用压缩

 

**Gzip 压缩**     优点：压缩率比较高； 缺点：不支持 Split；压缩/解压速度一般；

**Bzip2 压缩**     优点：压缩率高；**支持 Split**； 缺点：压缩/解压速度慢。

**Lzo 压缩**     优点：压缩/解压速度比较快；**支持 Split**； 缺点：压缩率一般；想支持切片需要额外创建索引，Hadoop不自带

**Snappy 压缩** 优点：压缩和解压缩速度快； 缺点：不支持 Split；压缩率一般；

 

压缩速率：snappy>Lzo>GZip>BZip2

支持切片：BZip2、Lzo

压缩率：BZip2>GZip>Lzo>Snappy

**特殊：Lzo、Snappy ，hadoop本身不支持，需要自行安装，并且Lzo需要建立索引。**

 

**压缩位置：**

**输入端采用压缩**

在有大量数据并计划重复处理的情况下，应该考虑对输入进行压缩。然而，你无须显示指定使用的编解码方式。Hadoop自动检查文件扩展名，如果扩展名能够匹配，就会用恰当的编解码方式对文件进行压缩和解压。否则，Hadoop就不会使用任何编解码器。

**mapper输出端采用压缩**

当map任务输出的中间数据量很大时，应考虑在此阶段采用压缩技术。这能显著改善内部数据Shuffle过程，而Shuffle过程在Hadoop处理过程中是资源消耗最多的环节。如果发现数据量大造成网络传输缓慢，应该考虑使用压缩技术。可用于压缩mapper输出的快速编解码器包括LZO或者Snappy。

**reducer输出采用压缩**

在此阶段启用压缩技术能够减少要存储的数据量，因此降低所需的磁盘空间。当mapreduce作业形成作业链条时，因为第二个作业的输入也已压缩，所以启用压缩同样有效。

 

### **在写 MR 时，什么情况下可以使用规约** （combiner）

规约（combiner）是不能够影响任务的运行结果的局部汇总，适用于求和类，不适用于求平均值

 

## Yarn

### **介绍下YARN**/YARN的架构？★★★★★

> 字节x3，网易云音乐×2，蘑菇街x2，美团，小鹏汽车，一点资讯，头条，快手，央视网，海康x2，转转，滴滴，作业帮
>

> YARN是一个资源调度平台，负责为运算程序提供服务器运算资源，相当于一个**分布式的操作系统平台**， 而**MapReduce等运算程序则相当于运行于操作系统之上的应用程序**。
>

YARN 作为一个资源管理、任务调度的框架，负责为运算程序提供服务器运算资源，主要包含ResourceManager、NodeManager、 ApplicationMaster和Container模块。

1）ResourceManager（RM）主要作用如下：

- 与客户端交互，处理来自客户端的请求。
- 启动和管理ApplicatinMaster，并在它运行失败时重新启动它。
- 管理NodeManager，接受来自NodeManager的资源管理汇报信息，并向NodeManager下达管理命令（比如杀死Contanier）等。
- 资源管理与调度，接收来自ApplicationMaster的资源申请请求，并为之分配资源（核心）。

2）NodeManager（NM）主要作用如下：

- 管理单个节点上的资源

- 处理来自ResourceManager的命令

- 处理来自ApplicationMaster的命令

3）ApplicationMaster（AM）作用如下：

- 为应用程序申请资源并分配给内部的任务
- 任务的监督与容错

4）Container

- Container是YARN中的资源抽象，它封装了某个节点上的多维度资源，如内存、CPU、磁盘、网络等。

 

### YARN的工作机制/**YARN 的任务提交流程是怎样的?** ★★★★★

![image-20220401215019637](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220401215019637.png)

1）MapReduce程序提交到客户端所在的节点。

2）YarnRunner向ResourceManager申请一个Application。

3）RM 将该应用程序的资源路径以及application_id返回给YarnRunner。

4）该程序将运行所需资源提交到 HDFS 上； **jar 包、切片信息和配置文件**

5）程序资源提交完毕后，申请运行 mrAppMaster。

6）RM 将用户的请求初始化成一个 Task。将该Task添加到容量调度器中

7）其中一个NodeManager 领取到 Task 任务。

8）该 NodeManager 创建容器 Container，并产生 MRAppmaster。

9）Container 从HDFS 上拷贝资源到本地。

10）MRAppmaster 向RM 申请运行 MapTask 资源。

11）RM 将运行 MapTask 任务分配给其他的（另外两个？？） NodeManager，其他的（另两个？） NodeManager 分别领取任务并创建容器。

12）MRAppmaster 向（两个？）接收到任务的NodeManager 发送程序启动脚本，这些（两个？） NodeManager分别启动 MapTask， MapTask 对数据分区排序。

13）MrAppMaster 等待所有 MapTask 运行完毕后，向 RM 申请容器，运行 ReduceTask。

14）ReduceTask 向 MapTask 获取相应分区的数据。

15）程序运行完毕后，MRAppmaster 会向 RM 申请注销自己。

 

### yarn的调度器

> 转转，滴滴，作业帮，大华(2021.07)， soul(2021.09)，陌陌(2021.10)
>

Hadoop 作业调度器主要有三种：**FIFO、容量（Capacity Scheduler）和公平（Fair Scheduler）**。Apache Hadoop3.1.3 默认的资源调度器是 容量调度器Capacity Scheduler，CDH 框架默认调度器是 Fair Scheduler。

**1、先进先出调度器（FIFO）**

FIFO调度器（First In First Out）：单队列，根据提交作业的先后顺序，先来先服务

优点：简单易懂

缺点：不支持多队列，生成环境很少使用

**2、容量调度器（Capacity Scheduler）**

默认的容量调度器；核心调度策略：优先选择资源利用率低的队列

- 多队列：可将yarn资源分为多个队列；每个队列可配置一定的资源量，每个队列一般采用**FIFO**调度策略


- 容量保证：管理员可为每个队列设置资源最低保证和资源使用上限


- 灵活性：如果一个队列中的资源有剩余，可以暂时共享给那些需要资源的队列，而一旦该队列有新的应用程序提交，则其它队列借调的资源会归还给该队列


- 多租户：支持多用户共享集群和多应用程序同时运行；为了防止同一用户的作业独占队列中的资源，该调度器会对同一用户提交的作业所占资源进行限定

**3、公平调度器（Fair Scheduler）**

**同队列所有任务共享资源，在时间尺度上获得公平的资源。**

与容量调度器相同点：多队列、容量保证、灵活性、多用户。

与容量调度器不同点：

核心调度策略不同

- 容量调度器：优先选择资源利用率低的队列

- 公平调度器：**会优先为资源缺额大的作业分配资源**

  > 缺额：某一时刻一个作业应获资源和实际获取资源的差距叫缺额。

每个队列可以单独设置资源分配方式

- 容量调度器：FIFO、DRF

- 公平调度器：FIFO、FAIR、DRF

DRF（Dominant Resource Fairness），选择DRF策略对不同应用进行不同资源（CPU和内存）的一个不同比例的限制（为每个应用设置资源占比）

 

### **YARN中Container是如何启动的？**

**ApplicationMaster**提交需求，通过心跳，把需求发送给RM；

**ApplicationMaster**获取Container：通过心跳，拿到申请好的Container；

**ApplicationMaster**每申请到一个Container ，与 NM 通信，NM 启动这个Container；

 

### YARN容错机制

**任务失败**

当mrAppMaster被告知，一个任务失败的时候，会重新调度该任务。mrAppMaster会尝试避免在以前失败过的nodeManager重新调度该任务。此外，一个任务失败的次数超过4次，将不会再重新调度。

**ApplicationMaster运行失败**

在YARN中，ApplicationMaster有几次尝试次数，最多尝试次数由：mapreduce.am.max-attempts和 yarn.resourcemanager.am.max-attempts确定，默认为2。

**NodeManager运行失败**

当NodeManager由于奔溃或者非常缓慢运行而失败，会停止向ResourceManager发送心跳信息。则如果10分钟内（由yarn.resourcemanager.nm.liveness-monitor.expiry-interval-ms来设置，以ms为单位）没收到心跳信息，ResourceManager会认为该NodeManager不可用，将其下线并将起从自己的节点池中移除。

**ResourceManager运行失败**

在YARN中，ResourceManager失败是个致命的问题，如果失败，任何任务和作业都无法启动。所以我们需要配置高可用；我们需要配置一对ResourceManager，在主ResourceManager失败后，备份ResourceManager可以继续运行。

将所有的ApplicationMaster的运行信息保存到一个高可用的状态存储中（由ZooKeeper或者HDFS备份），这样备份ResourceManager就可以恢复出失败的ResourceManager状态

ResourceManager在主备切换由故障转移器（failover controller）处理。默认情况，failover controller自动工作，由ZooKeeper的Leader选举，保证同一时刻只有一个主ResourceManager。

 

### YARN高可用

YARN ResourceManager 的高可用与 HDFS NameNode 的高可用类似但是 ResourceManager 不像 NameNode ，没有那么多的元数据信息需要维护，所以它的状态信息可以直接写到Zookeeper 上，并依赖 Zookeeper 来进行主备选举。

- 同样是基于zookeeper的ZKFC实现监控RM的健康状态，并执行选举作用；在zookeeper指定目录下创建一个临时节点，创建成功则认为获取了锁，成为Active的RM；没获取成功的成为stand by。。。

- RM会把job的信息存放在zookeeper的/rmstore目录下，active RM会向这个目录写app的信息。当active RM挂掉之后，standby RM会通过zkfc切换为active状态，然后从zookeeper的/rmstore目录下读取相应的作业信息，恢复集群的工作；

 

# Hive

## **Hive是什么？**

> 海康

Hive是**基于Hadoop的一个数据仓库工具**，可以将结构化的数据文件映射为一张表，并提供类SQL查询功能。

Hive的**本质是将HQL转化成MapReduce程序**

- Hive处理的数据存储在HDFS

- Hive分析数据底层的实现是MapReduce

- 执行程序运行在Yarn上

 

可以再说一下hive的架构

 

## **Hive架构**

> 腾讯微众，好未来，恒生(2021.09)

![image-20220324103719024](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220324103719024.png)

**用户接口：Client**

CLI（command-line interface）、JDBC/ODBC(jdbc 访问 hive)、WEBUI（浏览器访问 hive）

**元数据：Metastore**

元数据包括：表名、表所属的数据库（默认是 default）、表的拥有者、列/分区字段、表的类型（是否是外部表）、表的数据所在目录等；

> 默认存储在自带的 derby 数据库中，推荐使用 MySQL 存储 Metastore

**Hadoop**

使用 HDFS 进行存储，使用 MapReduce 进行计算，程序运行在yarn上

**驱动器：Driver**

（1）解析器（SQL Parser）：将 SQL 字符串转换成抽象语法树 AST（**abstract syntax tree**）（这一步一般都用第三方工具库完成，比如 antlr；）对 AST 进行语法分析，比如表是否存在、字段是否存在、SQL语义是否有误。

（2）编译器（Physical Plan）：将 AST 编译生成逻辑执行计划。

（3）优化器（Query Optimizer）：对逻辑执行计划进行优化。

（4）执行器（Execution）：把逻辑执行计划转换成可以运行的物理计划，提交执行。对于 Hive 来说，就是 MR/Spark。

 

 

## **说下为什么要使用Hive？Hive的优缺点？Hive的作用是什么？** ★★★★★

 

> **1、为什么要使用Hive（hive的作用）？**
>
> **Hive是Hadoop生态系统中比不可少的一个工具，它提供了一种SQL(结构化查询语言)方言，可以查询存储在Hadoop分布式文件系统（HDFS）中的数据或其他和Hadoop集成的文件系统**，如HBase（Hadoop数据仓库）这样的数据库中的数据。
>
> 大多数数据仓库应用程序都是使用关系数据库进行实现的，并使用SQL作为查询语言。**Hive降低了将这**些应用程序转移到Hadoop系统上的难度。凡是会使用SQL语言的开发人员都可以很轻松的学习并使用Hive。如果没有Hive，那么这些用户就必须学习新的语言和工具，然后才能应用到生产环境中。
>
>
>
> **2、Hive优缺点**
>
> **优点**
>
> 1）**操作接口采用类SQL语法，提供快速开发的能力（简单、容易上手）。**
>
> 2）**避免了去写MapReduce，减少开发人员的学习成本**。
>
> 3）Hive的执行延迟比较高，因此Hive常用于数据分析，对实时性要求不高的场合。
>
> 4）**Hive优势在于处理大数据**，对于处理小数据没有优势，因为Hive的执行延迟比较高。
>
> 5）**Hive支持用户自定义函数，用户可以根据自己的需求来实现自己的函数。**
>
> **缺点**
>
> 1）Hive的HQL表达能力有限
>
> - 迭代式算法无法表达
> - 数据挖掘方面不擅长，由于MapReduce数据处理流程的限制，效率更高的算法却无法实现。
>
> Hive不是一个完整的数据库。Hadoop以及HDFS的设计本身约束和局限性地限制了Hive所能胜任的工作。
>
> 2）**其中最大的限制就是Hive不支持行级别的更新、插入或者删除操作。但是用户可以通过查询生成新表或者将查询结果导入到文件中**。
>
> 3）同时，因为Hadoop是面向批处理的系统，而MapReduce任务（job）的启动过程需要消耗较长的时间，所以**Hive查询延时比较严重**。传统数据库中在秒级别可以完成的查询，在Hive中，即使数据集相对较小，往往也需要执行更长的时间。效率比较低。

 

## hive和数据仓库的区别

数据仓库的目的是构建**面向分析**的集成化数据环境，为企业提供决策支持（Decision Support）。它出于**分析性报告和决策支持的目的**而创建。

> 为需要业务智能的企业，提供指导业务流程改进、监视时间、成
>
> 本、质量以及控制。

**数据仓库存在的意义在于对企业的所有数据进行汇总，为企业各个部门提供统一的， 规范的数据出口。**

 

Hive是**基于Hadoop的一个数据仓库工具**，可以将结构化的数据文件映射为一张表，并提供类SQL查询功能。

 

## Hive和传统数据库区别 ★★★

由于 Hive 采用了类似 SQL 的查询语言 HQL(Hive Query Language)，因此很容易将 Hive 理  解为数据库。其实从结构上来看，Hive 和数据库除了拥有类似的查询语言，再无类似之处。

Hive 是基于 Hadoop 的一个数据仓库工具，可以将结构化的数据文件映射为一张表，并 提供类 SQL 查询功能。 Hive 本质：将 HQL 转化成 MapReduce 程序。

传统数据库：基本就是数据得存储与查找。

1、数据存储位置。Hive是建立在Hadoop之上的，所有的Hive的数据都是存储在HDFS中的。而数据库则可以将数据保存在块设备或本地文件系统中。

2、数据格式。Hive中没有定义专门的数据格式，由用户指定，需要指定三个属性：列分隔符，行分隔符，以及读取文件数据的方法。数据库中，存储引擎定义了自己的数据格式。所有数据都会按照一定的组织存储。

3、数据更新。Hive不支持行级别的更新、插入或者删除操作。而数据库中的数据通常是需要经常进行修改。

4、执行延迟。Hive在查询数据的时候，需要扫描整个表(或分区)，因此延迟较高，只有在处理大数据是才有优势。数据库在处理小数据是执行延迟较低。

5、索引。Hive没有，数据库有

6、可扩展性。Hive高，数据库低

7、数据规模。Hive大，数据库小

 

## **Hive内部表和外部表的区别？**  ★★★★★

内部表（managed table）：未被external修饰

外部表（external table）：被external修饰

**区别：**

1）内部表数据由Hive自身管理，外部表数据由HDFS管理；

2)  创建内部表时，会将数据移动到数据仓库指向的路径；若创建外部表，仅记录数据所在的路径，不对数据的位置做任何改变，减少数据的传输。

> 内部表数据存储的位置是hive.metastore.warehouse.dir（默认：/user/hive/warehouse），外部表数据的存储位置由自己制定（如果没有LOCATION，Hive将在HDFS上的/user/hive/warehouse文件夹下以外部表的表名创建一个文件夹，并将属于这个表的数据存放在这里）；

3）删除内部表会直接删除元数据（metadata）及存储数据；删除外部表仅仅会删除元数据，HDFS上的文件并不会被删除；

4）对内部表的修改会将修改直接同步给元数据，而对外部表的表结构和分区进行修改，则需要修复（MSCK REPAIR TABLE table_name;）就是相当于手动更新元数据，不然修改后可能访问不到数据。

 

## **为什么内部表的删除，就会将数据全部删除，而外部表只删除表结构?** **为什么用外部表更好？** ★★★★★

**原因是：方便共享数据源**，相对来说更加安全些，数据组织也更加灵活 （如果别的表要用到，但是数据已删除，就不好办了）

**外部表的优点**

1）外部表不会加载数据到Hive的默认仓库（挂载数据），减少了数据的传输。

2）使用外部表，Hive不会修改元数据，不用担心数据损坏或丢失。

3）Hive在删除外部表时，删除的只是表结构，而不会删除数据，能和其他外部表共享数据

**场景选择**

在公司中绝大多数场景都是外部表。

自己使用的临时表，才会创建内部表。

 

## hive的数据类型

Hive支持原始数据类型和复杂类型，原始类型包括数值型，[Boolean](https://so.csdn.net/so/search?q=Boolean&spm=1001.2101.3001.7020)，字符串，时间戳。复杂类型包括数组，map，struct。下面是Hive数据类型的一个总结

![image-20220614160455383](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614160455383.png)

 

**类型转换**

Hive的类型层次中，可以根据需要进行隐式的类型转换，例如TINYINT与INT相加，则会将TINYINT转化成INT然后INT做加法。隐式转换的规则大致可以归纳如下：

（1）任何整数类型都可以隐式地转换为一个范围更广的类型，如 TINYINT 可以转换成INT，INT 可以转换成 BIGINT。

（2）所有整数类型、FLOAT 和 STRING 类型都可以隐式地转换成 DOUBLE。

（3）TINYINT、SMALLINT、INT 都可以转换为 FLOAT。

（4）BOOLEAN 类型不可以转换为任何其它的类型。

也可以使用CAST进行显式的类型转换，例如`CAST('1' as INT)`,如果转换失败，CAST返回NULL。

 

**复杂类型**

ARRAY和MAP

ARRAY和MAP类型与Java中的数据和映射表。数组的类型声明格式为`ARRAY<data_type>`,元素访问通过0开始的下标，例如`arrays[1]`访问第二个元素。
MAP通过`MAP<primitive_type,data_type>`来声明，key只能是基本类型，值可以是任意类型。map的元素访问则使用`[]`,例如`map['key1']`.

STRUCT

STRUCT则封装一组有名字的字段（named filed）,其类型可以是任意的基本类型，元素的访问使用点号。

```sql
create table myhive.complex
(id int,
profession ARRAY<string>,
info map<string,string>,
address struct<province:string, city:string, district:string>)
row format delimited fields terminated by ' '
collection items terminated by '#'
map keys terminated by ':';
```

 

## **Hive建表语句？创建表时使用什么分隔符？**

```sql
CREATE [EXTERNAL] TABLE [IF NOT EXISTS] table_name
[(col_name data_type [COMMENT col_comment], ...)]
[COMMENT table_comment]
[PARTITIONED BY (col_name data_type [COMMENT col_comment], ...)]
[CLUSTERED BY (col_name, col_name, ...)]
[SORTED BY (col_name [ASC|DESC], ...)] INTO num_buckets BUCKETS]
[ROW FORMAT row_format]
[STORED AS file_format]
[LOCATION hdfs_path] [TBLPROPERTIES (property_name=property_value, ...)]
[AS select_statement]
```

CREATE TABLE 创建一个指定名字的表。如果相同名字的表已经存在，则抛出异常； 用户可以用 IF NOT EXISTS 选项来忽略这个异常。

（2）EXTERNAL 关键字可以让用户创建一个外部表，在建表的同时可以指定一个指向实 际数据的路径（LOCATION），在删除表的时候，内部表的元数据和数据会被一起删除，而外 部表只删除元数据，不删除数据。

（3）COMMENT：为表和列添加注释。

（4）PARTITIONED BY：创建分区表

（5）CLUSTERED BY：创建分桶表

（6）SORTED BY：不常用，对桶中的一个或多个列另外排序

（7）ROW FORMAT

（8）STORED AS：指定存储文件类型 常用的存储文件类型：SEQUENCEFILE（二进制序列文件）、TEXTFILE（文本）、RCFILE（列式存储格式文件）。如果文件数据是纯文本，可以使用 STORED AS TEXTFILE。如果数据需要压缩，使用 STORED AS SEQUENCEFILE。

（9）LOCATION：指定表在HDFS上的存储位置。

（10）AS：后跟查询语句，根据查询结果创建表。

（11）LIKE：允许用户复制现有的表结构，但是不复制数据。

 

 

![image-20220613154930430](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220613154930430.png)

 

**分隔符：**

首先我们明确，我们是在建表的时候就指定了导入数据时的分隔符的，建表的时候会有三种场景需要考虑：

  1、正常建表(default)；

  2、指定特定的特殊符号作为分隔符；

  3、使用多字符作为分隔符；

一、正常建表，采用默认的分隔符：

  hive 默认的字段分隔符为ascii码的控制符\001,建表的时候用fields terminated by '\001'。

二、指定特定的特殊符号作为分隔符：

```sql
CREATE TABLE test(id int, name string ,tel string) ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t'LINES TERMINATED BY '\n'STORED AS TEXTFILE;
```

上面使用了'\t'作为了字段分隔符，'\n'作为换行分隔符。如果有特殊需求，可以自己动手改一下这两个符号就行了。

三、使用多字符作为分隔符：

假设我们使用【##】来作为字段分隔符，【\n】作为换行分隔符，则这里有两个方法：

1、使用MultiDelimitSerDe的方法来实现：

```sql
CREATE TABLE test(id int, name string ,tel string) ROW FORMAT SERDE 'org.apache.hadoop.hive.contrib.serde2.MultiDelimitSerDe' WITH SERDEPROPERTIES ("field.delim"="##") LINES TERMINATED BY '\n'STORED AS TEXTFILE;
```

2、使用RegexSerDe的方法实现：

```sql
CREAET TABLE test(id int, name string ,tel string) ROW FORMAT SERDE 'org.apache.hadoop.hive.contrib.serde2.RegexSerDe' WITH SERDEPROPERTIES ("input.regex" = "^(.*)\\#\\#(.*)$") LINES TERMINATED BY '\n'STORED AS TEXTFILE;
```

 

## hive join及其原理  ★★★

### 1、map join

适用于小表 join 大表；因为需要将小表加载进内存；分两步：

1、启动一个 local task 扫描小表B、将其转换成hashtable的数据结构，写入本地文件，然后加载到分布式缓存中

2、然后启动另一个task，是一个没有reduce阶段的MR；启动MapTasks扫描大表a, 在Map阶段，根据a的每一条记录去和DistributeCache中b表对应的HashTable关联，并直接输出结果；

### 2、common join（reduce join）

就是普通的reduce join; 分三步：

**Map**：生成键值对，以`JOIN ON`条件中的列作为`Key`，如果Join有多个关联键，则以这些关联键的组合作为key。以`JOIN`之后所关心的列作为`Value`，在`Value`中还会包含表的 Tag 信息，用于标明此`Value`对应于哪个表。

**Shuffle**：根据`Key`的值进行 Hash，按照Hash值将键值对发送至不同的Reducer中.

**Reduce**：Reducer通过 Tag 来识别不同的表中的数据，根据`Key`值进行`Join`操作

### 3、BUCKET MAP JOIN

Map side join固然得人心，但终会有“小表”条件不满足的时候(小表也不小)。这就需要bucket map join了。Bucket map join需要待连接的两个表在**连接字段上进行分桶**；**一个表的bucket数是另一个表bucket数的整数倍**；

具体的：

1. 设置属性`hive.optimize.bucketmapjoin= true`控制hive 执行bucket map join；
2. 对小表的每个分桶文件建立一个hashtable，并分发到所有做连接的map端；
3. map端接受了N（N为小表分桶的个数） 个小表的hashtable，做连接 操作的时候，只需要将小表的一个hashtable 放入内存即可，然后将大表的对应的split 拿出来进行连接，所以其内存限制为小表中最大的那个hashtable 的大小

### 4、SMB join （sort-merge-buket join）

其实是BUCKET MAP JOIN的一种优化；

对于bucket map join中的两个表，**如果每个桶内分区字段也是有序的，且分桶个数一致**；则还可以进行sort merge bucket map join

这样在做桶的局部连接的时候；变成了高效的归并排序(merge-sort)；因此可以进一步提升map端连接的效率；

 

## **Hive数据倾斜以及解决方案**★★★★★★

### **什么是数据倾斜**

数据倾斜主要表现在，map/reduce程序执行时，reduce节点大部分执行完毕，但是有一个或者几个reduce节点运行很慢，导致整个程序的处理时间很长，这是因为某一个key的条数比其他key多很多(有时是百倍或者千倍之多)，这条Key所在的reduce节点所处理的数据量比其他节点就大很多，从而导致某几个节点迟迟运行不完甚至执行失败。

**原因：**

在map和reduce两个阶段中，最容易出现数据倾斜的就是reduce阶段，因为map到reduce会经过shuffle阶段，如果经过shuffle，**大量的key进入到同一个reduce中**，就会导致数据倾斜。

在map端同样可能发生数据倾斜；一个任务中，数据文件在进入map阶段之前会进行切分，默认是128M一个数据块，但是如果**当对文件使用GZIP压缩等不支持文件分割操作的压缩方式**时，MR任务读取压缩后的文件时，是对它切分不了的，该压缩文件只会被一个任务所读取，如果有一个超大的不可切分的压缩文件被一个map读取时，就会发生map阶段的数据倾斜。

所以，从本质上来说，**发生数据倾斜的原因有两种：**

**一是任务中大量的key的进入同一个reduce**：包括空值过多，表jion、不同数据类型引发的数据倾斜、数据本身key就过多造成的数据倾斜等

**二是任务读取不可分割的大文件**。

 

### **数据倾斜的解决方案**

#### 1、空值引发的数据倾斜

(场景：如日志中，常会有信息丢失的问题，比如日志中的 user_id，如果取其中的 user_id 和 用户表中的user_id 关联，会碰到数据倾斜的问题。所有null值会集中在一个reduce)

**解决：**

第一种：可以直接不让null值参与join操作，即不让null值有shuffle阶段，因为null值join不上，对最终结果无影响。

```sql
select * from
log a join user b on a.user_id is not null and a.user_id = b.user_id
union all
select * from
log c where c.user_id is null;
```

第二种：因为null值参与shuffle时的hash结果是一样的，那么我们可以给null值随机赋值，这样它们的hash结果就不一样，就会进到不同的reduce中。

```sql
select * from
log a left outer join user b
on case when a.user_id is null
   then concat('hive',rand())
   else a.user_id end = b.user_id
```

 

#### 2、表join时发生的数据倾斜（不是空值引起）

两表进行join时，如果**表连接的键**存在倾斜，那么在 Shuffle 阶段必然会引起数据倾斜。

##### 大表join小表

采用MapJoin 解决；**适用于小表JOIN大表的场景**（默认开启这个功能）；在Map阶段完成join操作，这避免了 Shuffle，从而避免了数据倾斜；

**需要将小表（默认25mb以下）加载进map端的内存，然后在map端内存中进行join。**

`hive.auto.convert.join=true` 默认值为true，自动开启MAPJOIN优化。

`hive.mapjoin.smalltable.filesize=2500000` 默认值为2500000(25M)

##### 大表join大表

1、尝试参数：

`set hive.skewjoin.key=100000;`

`set hive.optimize.skewjoin=true`;

在 Join 过程中 Hive 会将计数超过阈值 hive.skewjoin.key（默认 100000）的倾斜 key 对应的行临时写进文件中，然后再启动另一个 job 做 map join 生成结果；

2、**动态一分为二**，即对倾斜的键值和不倾斜的键值分开处理，不倾斜的正常join即可，**倾斜的把他们找出来做mapjoin**，最后union all其结果即可。

 

#### 3、count（distinct ） 引发的数据倾斜

这种主要是 **count distinct  只会进入一个reduce，考虑用 sum...group by 代替**

```sql
select a,count(distinct b) from t group by a;
使用sum...group by 代替。
如select a,sum(1) from (select a, b from t group by a,b) group by a;
```

 

#### 4、不同数据类型引发的数据倾斜

对于两个表join，表a中需要join的字段key为int，表b中key字段既有string类型也有int类型。当按照key进行两个表的join操作时，默认的Hash操作会按int型的id来进行分配，这样所有的string类型都被分配成同一个id，结果就是所有的string类型的字段进入到一个reduce中，引发数据倾斜；

（场景：场景：用户表中user_id字段为int，log表中user_id字段既有string类型也有int类型。当按照user_id进行两个表的Join操作时）

**解决：**

如果key字段既有string类型也有int类型，默认的hash就都会按int类型来分配，那我们直接把int类型都转为string就好了，这样key字段都为string，hash时就按照string类型分配了

 

#### 5、确实无法减少数据量引发的数据倾斜，业务数据本身的特性（热点key）

此时可进行参数调节；比如： GroupBy 、join 操作后，(进行 count 或者 sum 聚合时，)可进行参数调节；

> 也可能group by 维度过小，如果满足业务需求，可调大粒度尝试下

**参数调节**

1、不影响最终业务逻辑的情况下，开启map端预聚合

```
hive.map.aggr = true // Map 端部分聚合，相当于Combiner
```

2、**有数据倾斜的时候进行负载均衡**，当选项设定为true，生成的查询计划会有两个MR Job。第一个MR Job中，Map 的输出结果集合会随机分布到Reduce中，每个Reduce做部分聚合操作，并输出结果，这样处理的结果是相同的Group By Key有可能被分发到不同的Reduce中，从而达到负载均衡的目的；第二个MR Job再根据预处理的数据结果按照Group By Key分布到Reduce中（这个过程可以保证相同的Group By Key被分布到同一个Reduce中），最后完成最终的聚合操作。

```
hive.groupby.skewindata=true
```

3、调整reduce的内存大小，使用`mapreduce.reduce.memory.mb`这个配置

4、合理调整reduce个数

 

#### 6、最后不可拆分大文件引发的数据倾斜

**当对文件使用GZIP压缩等不支持文件分割操作的压缩方式，在日后有作业涉及读取压缩后的文件时，该压缩文件只会被一个任务所读取**。如果该压缩文件很大，则处理该文件的Map需要花费的时间会远多于读取普通文件的Map时间，该Map任务会成为作业运行的瓶颈。这种情况也就是Map读取文件的数据倾斜

这种数据倾斜问题没有什么好的解决方案，只能将使用GZIP压缩等不支持文件分割的文件转为bzip和zip等支持文件分割的压缩方式

 

### 数据倾斜的排查与定位

**1. 通过时间判断**

如果某个 reduce 的时间比其他 reduce 时间长的多，则很有可能发生了数据倾斜；大部分 task 在 1 分钟之内完成，只有 r_000000 这个 task 执行 20 多分钟了还没完成。（也是mr web页面）

**2. 通过任务 mr web页面  Counter 判断**

Counter 会记录整个 job 以及每个 task 的统计信息；通过输入记录数，普通的 task counter 如下，输入的记录数是 13 亿多；而 task=000000 的 counter，其输入记录数是 230 多亿。是其他任务的 100 多倍

![image-20220325141841498](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220325141841498.png)

**找到哪个task 数据倾斜后，下一步是定位 SQL 代码**

1.**确定任务卡住的 stage**

- 通过 jobname 确定 stage：

**一般 Hive 默认的 jobname 名称会带上 stage 阶段，如下通过 jobname 看到任务卡住的为 Stage-4：**

![image-20220325142041792](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220325142041792.png)

- 如果 jobname 是自定义的，那可能没法通过 jobname 判断 stage。需要借助于任务日志并参考执行计划确定；

> 通过hive的任务日志，找到找到**执行特别慢的那个 task**，然后找到发生数据倾斜的字段；
>
> 比如Hive 在 join 的时候，会把 join 的 key 打印到日志中。如下：
>
> ![image-20220613191727180](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220613191727180.png)
>
> 上图中的关键信息是：**struct<_col0:string, _col1:string, _col3:string>**
>
> 这时候，需要参考该 SQL 的执行计划。通过参考执行计划，可以断定该阶段为 Stage-4 阶段

2.**确定 SQL 执行代码**

确定了执行阶段，即 stage。通过SQL执行计划，则可以判断出是执行哪段代码时出现了倾斜；（比如这个 stage 中进行连接操作的表别名是 d）

[实操 | Hive 数据倾斜问题定位排查及解决 - 腾讯云开发者社区-腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1880491)

 

## **Hive 优化**  ★★★★★

优化的根本思想

- 尽早尽量过滤数据，减少每个阶段的数据量
- 减少job数
- 解决数据倾斜问题

 

### 1、SQL的优化

- **笛卡尔积**

  尽量避免笛卡尔积，join的时候不加on条件，或者无效的 on条件，Hive只能使用1个reducer来完成笛卡尔积。

- **order by全局排序优化**

  全局排序，这会导致所有map端数据都进入一个reducer中

  可以 使用distribute by（按指定字段分发到不同reduce） +  sort by ; 在多个reduce上进行排序；最后汇总到一个reduce进行排序；

- **列裁剪和分区裁剪**

  所谓列裁剪就是在查询时只读取需要的列，分区裁剪就是只读取需要的分区。这样做以减少扫描的数据量。

- **谓词下推**

  它就是将SQL语句中的where谓词逻辑都尽可能提前执行，减少下游处理的数据量

 

### 2、数据倾斜优化

上面的数据倾斜场景

 

### 3、合理设置Map数

**复杂文件增加Map数**

**原理**：文件都很大，任务逻辑复杂，map执行非常慢的时候，可以考虑增加Map数，来使得每个map处理的数据量减少，从而提高任务的执行效率。

![image-20220614210417383](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614210417383.png)

**小文件进行合并，减少map数**

- 在map执行前合并小文件，减少map数：CombineHiveInputFormat具有对小文件进行合并的功能（系统默认的格式）。


- Map-Reduce的任务结束时合并小文件的设置


```sh
// 在map-only任务结束时合并小文件，默认true
SET hive.merge.mapfiles = true;
 
// 在map-reduce任务结束时合并小文件，默认false
SET hive.merge.mapredfiles = true;
 
// 合并文件的大小，默认256M
SET hive.merge.size.per.task = 268435456;
 
//当输出文件的平均大小小于该值16m时，启动一个独立的map-reduce任务进行文件merge
SET hive.merge.smallfiles.avgsize = 16777216;
 
```

 

### 4、合理设置Reduce数

**Reduce** **个数也并不是越多越好**

- 增大reduce个数，使单个Reduce 任务处理数据量大小会减小；但是过多的启动和初始化 Reduce 也会消耗时间和资源；
- 有多少个 Reduce，就会有多少个输出文件，如果生成了很多个小文件，那么如果这些小文件作为下一个任务的输入，则也会出现小文件过多的问题；
- 在设置Reduce个数的时候也需要考虑：处理大数据量利用合适的 Reduce 数；使单个Reduce 任务处理数据量大小要合适。

![image-20220614211537760](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614211537760.png)

### **5、**并行执行

通过设置参数hive.exec.parallel值为true，就可以开启并发执行。不过，在共享集群中，需要注意下，如果job中并行阶段增多，那么集群利用率就会增加。建议在**数据量大,sql很长**的时候使用,数据量小,sql比较小的开启有可能还不如之前快。

```shell
//打开任务并行执行，默认为false
set hive.exec.parallel=true;
 
//同一个sql允许最大并行度，默认为8。
set hive.exec.parallel.thread.number=16;
```

 

### 6、列式存储

因为每个字段的数据聚集存储，在查询只需要少数几个字段的时候，能大大减少读取的数据量；列式存储可以针对性地设计更好的设计压缩算法。

TEXTFILE和SEQUENCEFILE的存储格式都是基于行存储的；

ORC和PARQUET是基于列式存储的。

 

### 7、压缩（选择快的）

```shell
// 启用中间数据压缩 set hive.exec.compress.intermediate=true
 
// 启用最终数据压缩 set mapreduce.map.output.compress=true
 
// 设置压缩方式
set mapreduce.map.outout.compress.codec=
 
org.apache.hadoop.io.compress.DefaultCodec
org.apache.hadoop.io.compress.GzipCodec
org.apache.hadoop.io.compress.BZip2Codec
org.apache.hadoop.io.compress.Lz4Codec
```

 

### 8、**JVM重用**

默认使用一个单独JVM来执行一个map和Reduce任务。这时JVM的启动过程可能会造成相当大的开销，尤其是执行的job包含有**成百上千task任务**的情况。JVM重用可以使得JVM实例在同一个job中重新使用N次。

缺点是，开启JVM重用将一直占用使用到的task插槽，以便进行重用，直到任务完成后才能释放

```shell
set mapreduce.job.jvm.numtasks=10
```

###  9、fetch 抓取

Hive中对某些情况的查询可以不必使用MapReduce计算。
例如：SELECT * FROM employees （limit num）; 在这种情况下，Hive可以简单地读取employee对应的存储目录下的文件，然后输出查询结果到控制台。

 

## **Hive的三种自定义函数是什么？实现步骤与流程？它们之间的区别？作用是什么？**  ★★★★★

**作用：当Hive提供的内置函数无法满足你的业务处理需要时，此时就可以考虑使用用户自定义函数，来进行方便的扩展**（UDF： user-defined function）。

根据用户自定义函数类别分为以下三种：

**UDF**（User-Defined-Function）：一进一出

**UDAF**（User-Defined Aggregation Function）：聚集函数，多进一出

- 类似于：count/max/min

**UDTF**（User-Defined Table-Generating Functions）：一进多出

- 如lateral view  explode()

**实现步骤与流程**

第一步：继承UDF或者UDAF或者UDTF，实现特定的方法,实现既定逻辑（当然首先要maven环境下，并导入依赖）

> 数仓项目中的UDTF：
>
> 主要initialize 和 process 两个方法；
>
> initialize 主要执行输入参数合法性校验，以及返回值名称和类型
>
> process  执行具体逻辑

第二步：将写好的类打包为jar，如 myudtf.jar；并上传打服务器

第三步：将 jar 包添加到 hive 的 classpath，利用`add jar /opt/module/data/myudtf.jar`注册该jar文件；

第四步：创建临时函数与开发好的 java class 关联，create temporary function mylength as 'com.HDU.StringLength'

第五步：在select中使用mylength()。

**数仓项目中使用了自定义的UDTF**；为了获取动作日志表：action字段中包括多个字段，需要将他解析出来

输入：json 数组字符串

输出：每个json 数组元素作为一行输出

![image-20220809211854081](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220809211854081.png)

```java
public class ExplodeJSONArray extends GenericUDTF {
 
    @Override
    public StructObjectInspector initialize(StructObjectInspector argOIs) throws UDFArgumentException {
 
        // 1 输入参数合法性检查
        if (argOIs.getAllStructFieldRefs().size() != 1){
            throw new UDFArgumentException("ExplodeJSONArray 只需要一个参数");
        }
 
        // 2 第一个参数必须为string  校验输入参数个数
        if(!"string".equals(argOIs.getAllStructFieldRefs().get(0).getFieldObjectInspector().getTypeName())){
            throw new UDFArgumentException("json_array_to_struct_array的第1个参数应为string类型");
        }
 
        // 3 定义返回值名称和类型
        List<String> fieldNames = new ArrayList<String>();
        List<ObjectInspector> fieldOIs = new ArrayList<ObjectInspector>();
 
        fieldNames.add("items");
        fieldOIs.add(PrimitiveObjectInspectorFactory.javaStringObjectInspector);
 
        return ObjectInspectorFactory.getStandardStructObjectInspector(fieldNames, fieldOIs);
    }
 
    public void process(Object[] objects) throws HiveException {
 
        // 1 获取传入的数据
        String jsonArray = objects[0].toString();
 
        // 2 将string转换为json数组
        JSONArray actions = new JSONArray(jsonArray);
 
        // 3 循环一次，取出数组中的一个json，并写出
        for (int i = 0; i < actions.length(); i++) {
 
            String[] result = new String[1];
            result[0] = actions.getString(i);
            forward(result);
        }
    }
 
    public void close() throws HiveException {
 
    }
}
 
```

 

 

## **Hive的cluster by 、sort by、distribute by、order by 区别？** ★★★★★

**sort by** ：不是全局排序，（对桶/分区中的一个或多个列另外排序），其在数据进入reducer前完成排序。

**distribute by** ：分区排序，按照指定的字段对数据进行划分输出到不同的reduce中。结合sort by 使用；DISTRIBUTE BY语句要写在SORT BY语句之前；sort by为每个reduce产生一个排序文件

**cluster by** ：创建分桶表；除了具有 distribute by 的功能外还兼具 sort by 的功能，但是排序**只能是升序排序**

**order by** ：会对输入做全局排序，因此只有一个reducer（多个reducer无法保证全局有序）。只有一个reducer，会导致当输入规模较大时，需要较长的计算时间。

 

## **Hive分区和分桶的区别** ★★★★★

**定义上**

分区表实际上就是对应一个 HDFS 文件系统上的独立的文件夹，该文件夹下是该分区所有的数据文件。**Hive 中的分区就是分目录**，**一个分区名对应一个目录名**，把一个大的数据集根据业务需要分割成小的数据集。在查询时通过 WHERE 子句中的表达式选择查询所需要的指定的分区，这样的查询效率会提高很多。

对于一张表或者分区，Hive 可以**进一步组织成桶**，也就是更为细粒度的数据范围划分。

分桶规则: **Hive 的分桶采用对分桶字段的值进行哈希，然后除以桶的个数取模的方式决定该条记录存放在哪个桶当中**

**区别**

- **分桶随机分割数据库，分区是非随机分割数据库**。不同于分区对列直接进行拆分，桶往往使用列的哈希值对数据打散，并分发到各个不同的桶中从而完成数据的分桶过程

- 分区是对应HDF上的目录（粗粒度），分桶是对应目录里的文件（细粒度）。桶是更为细粒度的数据范围划分，**分桶的比分区获得更高的查询处理效率，使取样更高效。**

 


> 注意：普通表（外部表、内部表）、分区表这三个都是**对应HDFS上的目录**，**桶表对应是目录里的文件。**

>  ```sql
> create table  分桶表的表名 ( 字段名1 数据类型,字段名 2  数据类型2 , ....    )
> clustered by ( 分桶字段 )  into  分桶的个数  buckets
> row format delimited
> fields terminated by '\001'       --指定字段分隔符
> collection items terminated by '\002'  -- 指字集合的分隔符
> map keys terminated by '\003'    --指定map的分隔符
> lines terminated by '\n'   --指定行的分隔符
>  ```

 

## **Hive的执行流程**  ★★★★★

> Hive元数据存放在MySQL里。
> Hive的表数据存在HDFS上的。

主要过程:
①一个客户端发送一条HQL语句给Hive的驱动器driver。
②Hive的驱动器driver里面有:解析器、编译器、优化器、执行器等。这些主要完成HQL查询语句从词法分析、语法分析、编译、优化以及查询计划的生成。这一步完成了hql翻译成MR。
③ driver生成相应的MapReduce jar包，结合元数据里提供的对应的文件路径，把jar包提交到Hdoop的Yarn上面执行(提交给ResourceManager执行task) 。最后将执行结果输出到客户端，让用户看到结果。

 

## Hive SQL 编译成 MapReduce 过程  ★★★★★

编译 SQL 的任务是在COMPILER（编译器**组件**）中完成的。Hive将SQL转化为MapReduce任务，整个编译过程分为六个阶段：

![image-20220325101013231](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220325101013231.png)

1. **词法、语法解析**: 解析器，完成 SQL 词法，语法解析（判断语法是否有误，表是否存在等），将 SQL 转化为抽象语法树 AST Tree；

   > 一般调用第三方工具如Antlr，Antlr是一种语言识别的工具，可以用来构造领域语言。使用Antlr构造特定的语言只需要编写一个语法文件，定义词法和语法替换规则即可，Antlr完成了词法分析、语法分析、语义分析、中间代码生成的过程。

2. **语义解析**: 遍历 AST Tree，抽象出查询的基本组成单元 QueryBlock，包括三个部分：输入源，计算过程，输出。简单来讲一个QueryBlock就是一个子查询

3. **生成逻辑执行计划**: 遍历 QueryBlock，翻译为执行操作树 OperatorTree；

   > Hive最终生成的MapReduce任务，Map阶段和Reduce阶段均由OperatorTree组成。基本的操作符包括：TableScanOperator、 SelectOperator、  FilterOperator 、JoinOperator 、GroupByOperator 、ReduceSinkOperator；各算子间数据的传输是流式过程，每一个Operator对一行数据完成操作后之后将数据传递给下一个Operator计算。

4. **优化逻辑执行计划**: 逻辑层优化器进行 OperatorTree 变换，比如合并 Operator，达到减少 MapReduce Job，减少数据传输及 shuffle 数据量；

5. **生成物理执行计划**: 遍历 OperatorTree，翻译为 MapReduce 任务；

6. **优化物理执行计划**: 物理层优化器进行 MapReduce 任务的变换，生成最终的执行计划。比如：谓词下推（where提前执行，减小下游数据量），在 mapper 上执行 Join、优化 Union，使Union只在 map 端执行等。

 

## **Hive使用的时候会将数据同步到HDFS，小文件问题怎么解决的？** ★

**1、哪里会产生小文件**

- 源数据本身有很多小文件


- 动态分区插入数据，产生大量的小文件，从而导致下一个任务map数量剧增。

  > 很多场景需要将表根据数据内容进行动态分区，Hive在向分区表写入数据时，在mapreduce任务中每个map会为该map任务中的数据对应的动态分区生成文件，如果每个map中的数据对应的分区有10个，有4000个map，则这次写入会生成4000*10个文件。

- reduce个数越多, 小文件越多（个数和输出文件是对应的）。若这些小文件作为下一个文件的输入，也会产生小文件问题。

**2、小文件太多造成的影响**

- 小文件过多会导致namenode元数据特别大, 占用太多内存


- 对 hive 来说，在进行查询时，每个小文件都会当成一个块，启动一个Map任务来完成，而一个Map任务启动和初始化的时间远远大于逻辑处理的时间，就会造成很大的资源浪费。而且，同时可执行的Map数量是受限的。

**3、解决方案**：

1、**从源端限制小文件的产生**

- 使用Sequencefile作为表存储格式，不要用textfile。由一系列的二进制key/value组成，如果为key小文件名，value为文件内容，则可以将大批小文件合并成一个大文件；可以一定程度上减少小文件；

-  减少reduce的数量(可以使用参数进行控制)。

- 少用动态分区，用时记得按distribute by分区。可以在插入语句后加一句DISTRIBUTE BY rand() 将数据随机分配给Reduce，这样可以使得每个Reduce处理的数据大体一致.

2、**对于已有的小文件**

- 使用hadoop archive命令把小文件进行归档

- 通过参数进行调节

  - 设置map输入合并小文件的相关参数：**CombineHiveInputFormat**

  - 设置map输出和reduce输出文件进行合并的相关参数

    ![image-20220806165222202](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220806165222202.png)

 

## **Hive的union和union all的区别**

Union ：对两个结果集进行并集操作，不包括重复行，同时进行默认规则的排序；

Union All ：对两个结果集进行并集操作，包括重复行，不进行排序。

 

## **Hive的join操作原理，left join、right join、inner join、outer join的异同？**

inner join

等值连接，只返回两个表中联结字段相等的行

outer join(外连接) 可分为左外连接left outer join和右外连接right outer join

left join

左联接，返回包括左表中的所有记录和右表中联结字段相等的记录

right join

右联接，返回包括右表中的所有记录和左表中联结字段相等的记录

 

 

## **Hive的存储引擎和计算引擎**

**1、计算引擎**

目前**Hive支持MapReduce、Tez和Spark三种计算引擎**。

在低版本（Hive 1.1之前）中，Hive支持MapReduce、Tez两种计算引擎。

在高版本（Hive 1.1之后）中，Hive支持MapReduce、Tez和Spark三种就算引擎

**2、存储引擎**

Hive的文件存储格式（存储引擎）有四种： TEXTFILE 、 SEQUENCEFILE 、 ORC 、 PARQUET ，前面两种是**行式存储**，后面两种是**列式存储**。如果为textfile的文件格式，直接load，不需要走MapReduce；如果是其他的类型就需要走MapReduce了，因为其他的类型都涉及到了文件的压缩，这需要借助MapReduce的压缩方式来实现。

TEXTFILE ：按行存储，不支持块压缩，默认格式，数据不做压缩，磁盘开销大，加载数据的速度最高

SequenceFile ：

- Hadoop API提供的一种二进制文件，以<key,value>的形式序列化到文件中
- 存储方式：行存储

> RCFILE ：
>
> - 数据按行分块，每块按列存储，结合了行存储和列存储的优点
> - RCFile 保证同一行的数据位于同一节点，因此元组重构的开销很低
> - RCFile 能够利用列维度的数据压缩，并且能跳过不必要的列读取
>

ORCFile ：

- 存储方式：数据按行分块 每块按照列存储

- 压缩快，快速列存取

- 效率高，使用了索引

  > 压缩率比rcfile高，**是rcfile的改良版本**

- 使用ORC文件格式可以提高hive读、写和处理数据的能力

PARQUET ：按列存储，相对于ORC，Parquet压缩比略低，查询效率略低

**总结**

压缩比：ORC > Parquet > textFile（textfile没有进行压缩）

查询速度：三者几乎一致

 

## **Hive的开窗函数（分析）有哪些**  ★★★

> 分析函数用于计算基于组的某种聚合值，它和聚合函数的不同之处是：**对于每个组返回多行，而聚合函数对于每个组只返回一行**。
>
> 开窗函数`over`指定了分析函数工作的**数据窗口**大小，这个数据窗口大小可能会随着行的变化而变化！
>
> 基础结构如下：
>
> ` 分析函数（如:sum(),max(),row_number()...） + 窗口子句（over函数）`

应用场景: 比如执行一些**计算、取值、排序**任务。

![image-20220806161200706](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220806161200706.png)

**1、sum :** 求和，窗口函数和聚合函数的不同，sum()函数可以根据每一行的窗口返回各自行对应的值，有多少行记录就有多少个sum值

**2、NTILE(n)**：把有序窗口的行分发到指定数据的组中，各个组有编号，编号从 1 开始，对于每一行，NTILE 返回此行所属的组的编号。注意：n 必须为 int 类型。

**3、ROW_NUMBER：的应用场景非常多**，比如获取分组内排序第一的记录

**4、RANK** **和** **DENSE_RANK** **函数**

- RANK()：生成数据项在分组中的排名，**排名相等会在名次中留下空位**
- DENSE_RANK()：生成数据项在分组中的排名，**排名相等会在名次中不会留下空位**

> **5、CUME_DIST** **函数**
>
> - cume_dist：返回小于等于 当前值的行数/分组内总行数
>
> **6、PERCENT_RANK** **函数**
>
> - percent_rank：分组内当前行的RANK值-1/分组内总行数-1
> - 注意：一般不会用到该函数，可能在一些特殊算法的实现中可以用到吧
>

**7、LAG和** **LEAD** **函数**

- LAG(col,n,DEFAULT)：用于统计窗口内往上第n行值
- 第一个参数为列名，第二个参数为往上第n行（可选，默认为1），第三个参数为默认值（当往上第n行为NULL时候，取默认值，如不指定，则为NULL）

**LEAD** **函数则与** **LAG** **相反：**

- LEAD(col,n,DEFAULT)：用于统计窗口内往下第n行值
- 第一个参数为列名，第二个参数为往下第n行（可选，默认为1），第三个参数为默认值（当往下第n行为NULL时候，取默认值，如不指定，则为NULL）

**8、FIRST_VALUE** **和** **LAST_VALUE** **函数**

FIRST_VALUE：取分组内排序后，截止到当前行，第一个值

**LAST_VALUE** **函数则相反：**

LAST_VALUE：取分组内排序后，截止到当前行，最后一个值

这两个函数还是经常用到的（往往和排序配合使用），比较实用！

 

###  分析函数中加Order By和不加Order By的区别？

当为**排序函数**，如row_number(),rank()等时，over中的order by只起到窗口内排序作用。不加order by 就不排序

当为**聚合函数**，如max，min，count等时，over中的order by不仅起到窗口内排序，还起到窗口内从当前行到之前所有行的聚合（多了一个范围）。

比如对**聚合函数sum**来说，不加order by score的话，**就是针对一整个分区进行sum求和。加上order by后，就是根据当前行到之前所有行聚合**

 

## metastore是什么

**metadata** 是元数据，表名，字段名...等;

**Metastore是一个服务**；作用是：客户端连接metastore服务，metastore再去连接MySQL数据库来存取元数据。有了metastore服务，就可以有多个客户端同时连接，而且这些客户端不需要知道MySQL数据库的用户名和密码，只需要连接metastore 服务即可

Hive的元数据存储(Metastore三种配置方式) -- Hive保存元数据的方式

* 内嵌模式（Embedded） : 内嵌模式使用的是内嵌的 Derby数据库来存储元数据，不需要额外起Metastore服务；一次只能一个客户端连接，适用于用来实验，不适用于生产环境。
* 本地模式（Local）: 本地安装mysql 替代derby存储元数据 。hive服务和metastore服务运行在同一个进程中；也就是说当你启动一个hive 服务，里面默认会帮我们启动一个metastore线程服务。
* 远程模式（Remote）: 远程安装mysql 替代derby存储元数据  Hive服务和metastore在不同的进程内；需要单独手动启动metastore服务

 

## HiveServer2

HiveServer2(HS2)是一种**能使远程客户端执行Hive查询的服务**。

HiveServer的核心是基于thrift协议，thrift负责hive的查询服务，thrift是构建跨平台的rpc框架；

 

# Kafka

## **为什么要用消息队列 **★ ☆★☆★

1. 应用解耦

   通过消息队列，可独立的扩展或修改消息队列两边的处理过程，只要确保它们遵守同样的接口约束，实现了解耦。

2. 缓冲和流量削峰

   可以使用消息队列进行缓冲，能够使关键组件顶住突发访问造成流量高峰压力，而不会因为突发的超负荷的请求而完全崩溃。

3. 异步通信

   很多时候，用户不想也不需要立即处理消息。消息队列提供了异步处理机制，允许用户把一个消息放入队列，但并不立即处理它。想向队列中放入多少消息就放多少，然后在需要的时候再去处理它们。

4. 消息通讯

 

## **发布订阅的消息系统那么多，为啥选择** **kafka?/Kafka的优点 ** ★ ☆★☆★

**(1)** **多个生产者**

KafKa 可以无缝地支持多个生产者，不管客户端使用一个主题，还是多个主题。**Kafka** **适合从多个前端系统收集数据**，并以统一的格式对外提供数据。

**（2）多个消费者**

Kafka 支持多个消费者从一个单独的消息流中读取数据，并且消费者之间互不影响。并且**多个消费者可以组成一个消费者组，共享一个消息流**。

**（3）持久性、可靠性**

消息被持久化到本地磁盘，并且支持数据备份防止数据丢失

**（4）可扩展性**

可扩展多台 broker。用户可以先使用单个 broker，到后面可以扩展到多个 broker

**（5）高吞吐、低延迟**

Kafka 可以轻松处理百万千万级消息流，同时还能保证 **亚秒级** 的消息延迟。

**（6）高并发**     支持数千个客户端同时读写。

**（7）容错性：**允许集群中节点故障

 

## **介绍下Kafka，Kafka的作用？kafka的组件？适用场景？**★ ☆★☆★

Kafka 是一个**分布式**的基于**发布/订阅模式**的**消息队列**（Message Queue），主要应用于大数据实时处理领域。

> **作用：**
>
> 提供以发布和订阅的方式处理数据
>
> 以高容错的方式存储消息流（kafka以文件的方式来存储消息流）
>
> 可以在消息发布的时候进行异步处理

**讲一下普通消息队列的功能**

**Kafka提供 发布和订阅的方式处理数据，同时以高容错的方式存储消息流**，并可在消息发布的时候进行异步处理；

**2、优势**

**高吞吐量、低延迟：**kafka每秒可以处理几十万条消息，它的延迟最低只有几毫秒；

**可扩展性：**kafka集群支持热扩展；

**持久性、可靠性：**消息被持久化到本地磁盘，并且支持数据备份防止数据丢失；

**容错性：**允许集群中节点故障（若副本数量为n,则允许n-1个节点故障）；

**高并发：**支持数千个客户端同时读写。

 

**组件：**

![image-20220320162817060](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220320162817060.png)

- Producer ：消息生产者，就是向 kafka broker 发消息的客户端；
- Consumer ：消息消费者，向 kafka broker 取消息的客户端；其中生产者和消费者都是面向主题的
- Broker ：一台 kafka 服务器就是一个 broker。一个集群由多个 broker 组成。一个 broker可以容纳多个topic

**使用场景：**

> 1）在系统或应用程序之间构建可靠的用于传输实时数据的管道-------消息队列功能
>
> 2）构建实时的流数据处理程序来变换或处理数据流-------数据处理功能

**日志收集：**一个公司可以用Kafka可以收集各种服务的log数据，通过kafka以统一接口服务的方式开放给各种consumer；

**消息系统：**解耦生产者和消费者、缓存消息等；

**用户活动跟踪：**kafka经常被用来记录web用户或者app用户的各种活动，如浏览网页、搜索、点击等活动，这些活动信息被各个服务器发布到kafka的topic中，然后消费者通过订阅这些topic来做实时的监控分析或者保存到数据库做离线分析；

> **运营指标：**kafka也经常用来记录运营监控数据。包括收集各种分布式应用的数据，生产中各种操作的集中反馈，比如报警和报告等；

**流式处理：**结合flink 和 spark streaming使用

 

## 说一下kafka的架构 ★ ☆★☆★

1）Producer：消息生产者，就是向kafka broker发消息的客户端；

2）Consumer：消息消费者，向kafka broker取消息的客户端；

3）Consumer Group（CG）：消费者组，由多个consumer组成。消费者组内每个消费者负责消费不同分区的数据，一个分区只能由一个消费者消费；消费者组之间互不影响。所有的消费者都属于某个消费者组，即消费者组是逻辑上的一个订阅者。

4）Broker ：一台kafka服务器就是一个broker。一个集群由多个broker组成。一个broker可以容纳多个topic。

5）Topic ：主题的概念，生产者和消费者面向的都是一个topic；

6）Partition：为了实现扩展性，一个非常大的topic可以分布到多个broker（即服务器）上，即一个topic可以分为多个partition。

7）Replica：副本，为保证集群中的某个节点发生故障时，该节点上的partition数据不丢失，且kafka仍然能够继续工作，kafka提供了副本机制，一个topic的每个分区都有若干个副本，其中包括一个leader和若干个follower。

8）leader：每个分区多个副本的“主”，生产者发送数据的对象，以及消费者消费数据的对象都是leader。

9）follower：每个分区多个副本中的“从”，实时从leader中同步数据，保持和leader数据的同步。leader发生故障时，某个follower会成为新的leader。

 

## Kafka的优缺点 ★ ☆★☆★

**优点：**

- 高吞吐量、低延迟：kafka每秒可以处理几十万条消息，它的延迟最低只有几毫秒；
- 可扩展性：kafka集群支持热扩展；
- 持久性、可靠性：消息被持久化到本地磁盘，并且支持数据备份防止数据丢失；
- 容错性：允许集群中节点故障（若副本数量为n,则允许n-1个节点故障）；
- 高并发：支持数千个客户端同时读写。
- **支持多个生产者和消费者**
- 对CPU和内存的消耗比较小
- 对网络开销也比较小

**缺点：**

- Kafka采用异步批量发送的方式，所以数据达不到真正的实时
- 可能会丢失数据或重复消费，如果kafka消费者消费完数据，来不及提交 offset，会造成数据重复消费；如果数据没有消费完成就提交了offset , 会出现丢数据的问题。
- 消息可能会乱序，Kafka单个partition内部的消息是有序的，但是一个topic有多个partition的话，就不能保证有序了；topic一般需要人工创建，部署和维护成本高

 

## **kafka** **如何做到高吞吐量和性能的？**/kafka为什么快？★ ☆★☆★

[Socket缓冲区_summer_west_fish的博客-CSDN博客_socket缓冲区](https://blog.csdn.net/summer_fish/article/details/121740570)

**1、磁盘顺序写**

kafka 写数据的时候，是以**磁盘顺序写而不是随机写**的方式来写的。也就是说，**仅仅将数据追加到文件的末尾**，速度远快于随机写（顺序写不需要硬盘磁头的寻道时间，只需很少的扇区旋转时间）。

**2、充分利用page cache页缓存技术**

操作系统(linux)本身有一层缓存，叫做 **page cache**，是在 **内存里的缓存**，我们也可以称之为 **os cache**，意思就是操作系统自己管理的缓存。

Kafka 在写入磁盘文件的时候，可以直接写入这个 os cache 里，也就是仅仅写入内存中，接下来由操作系统自己决定什么时候把 os cache 里的数据真的刷入磁盘文件中。通过这一个步骤，就可以将磁盘文件**写性能**提升很多了，因为其实这里相当于是在写内存，不是在写磁盘；

![image-20220320185412657](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220320185412657.png)

> 这样并不保证数据一定完全写入磁盘。从这一点看，可能会造成机器宕机时，Page Cache内的数据未写入磁盘从而造成数据丢失。但是这种丢失只发生在机器断电等造成操作系统不工作的场景，而这种场景完全可以由**Kafka层面的复本机制**去解决。
>

**基于上面两点，kafka** **就实现了写入数据的超高性能**。

**3、零拷贝技术**

![image-20220321212503071](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321212503071.png)

读取数据时，需要一个程序要把文件内容发送到网卡设备；首先这个程序是工作在用户空间，文件和网卡属于硬件资源，两者之间有一个内核空间。所以需要**先将文件复制到内核空间的缓冲区cache中，再复制到用户空间，最后再复制到内核空间的socket缓存区然后通过网卡发送出去**；

![image-20220321212536944](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321212536944.png)

**而零拷贝先将文件复制到内核空间的缓存区cache中，内核缓冲区仅将文件描述符（内存地址、地址偏移量等）和数据长度记录到对应的socket缓冲区；然后从内核缓冲区直接拷贝数据到网卡；省去了用户空间和内核空间之间的复制；也不用将所有数据拷贝到socket缓冲区**；**还省去了用户态和内存态之间之间的切换；**

![image-20220321212555615](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321212555615.png)

**这个过程大大的提升了数据消费时读取文件数据的性能**。Kafka 从磁盘读数据的时候，会先看看 os cache 内存中是否有，如果有的话，其实读数据都是直接读内存的。

> **4、文件分段**

> kafka 的队列topic被分为了多个区partition，每个partition又分为多个段segment，所以一个队列中的消息实际上是保存在N多个片段文件中。
>
> 通过分段的方式，每次文件操作都是对一个小文件的操作，非常轻便，同时也增加了并行处理能力。
>

**4、批量发送**

Kafka 允许进行批量发送消息，先将消息缓存在内存中，然后一次请求批量发送出去，比如可以指定缓存的消息达到某个量的时候就发出去，或者缓存了固定的时间后就发送出去，如100条消息就发送，或者每5秒发送一次，这种策略将大大减少服务端的I/O次数。

**5、数据压缩**

Kafka 还支持对消息集合进行压缩，Producer可以通过GZIP或Snappy格式对消息集合进行压缩，压缩的好处就是减少传输的数据量，减轻对网络传输的压力，Producer压缩之后，在Consumer需进行解压，虽然增加了CPU的工作，但在对大数据处理上，瓶颈在网络上而不是CPU，所以这个成本很值得。

 

##  **kafka** **和** **zookeeper** **之间的关系**

[(1条消息) Kafka之副本信息、Leader 选举流程、故障处理细节、分区副本分配、手动调整分区副本存储、Leader Partition 负载平衡、增加副本、文件存储机制、文件清理策略、高效读写数据_爱上口袋的天空的博客-CSDN博客_kafka副本leader选举](https://blog.csdn.net/K_520_W/article/details/124064693)

Kafka集群中有一个broker会被选举为Controller，**负责管理集群broker的上下线，所有topic的分区副本分配和leader选举等工作**。Controller的管理工作都是依赖于Zookeeper的。也就是说ZK是辅助Controller的管理工作的；并且Controller的选举也依赖于Zookeeper。

下面我具体介绍一下：

**0.Controller选举**

在一个kafka集群中，有多个broker节点，但是它们之间需要选举出一个leader，其他的broker充当follower角色。集群中第一个启动的broker会通过在zookeeper中创建临时节点 /controller 来让自己成为控制器，其他broker启动时也会在zookeeper中创建临时节点，但是发现节点已经存在，所以它们会收到一个异常，意识到控制器已经存在，那么就会在zookeeper中创建watch对象，便于它们收到控制器变更的通知。

**1.broker注册**

**Broker是分布式部署并且之间相互独立，但是需要有一个注册系统能够将整个集群中的Broker管理起来**，此时就使用到了Zookeeper。在Zookeeper上会有一个专门**用来进行Broker服务器列表记录**的节点  `/brokers/ids`

每个Broker在启动时，都会到Zookeeper上进行注册，即到/brokers/ids下创建属于自己的节点，如/brokers/ids/[0...N]。

Kafka使用了全局唯一的数字来指代每个Broker服务器，不同的Broker必须使用不同的Broker ID进行注册，创建完节点后，**每个Broker就会将自己的IP地址和端口信息记录**到该节点中去。其中，Broker创建的节点类型是临时节点，一旦Broker宕机，则对应的临时节点也会被自动删除。

**2.topic注册**

在 Kafka 中，所有 Topic 与 Broker 的对应关系都由 ZooKeeper 来维护，在 ZooKeeper 中，通过建立专属的节点来存储这些信息，其路径为 `/brokers/topics/{topic_name}`

**3.leader选举**

基于 ZooKeeper，Kafka 为每一个 Partition 找一个节点作为 Leader，其余备份作为 Follower

当 Producer Push 的消息写入 Partition（分区）时，作为 Leader 的 Broker（Kafka 节点）会将消息写入自己的分区，同时还会将此消息复制到各个 Follower，实现同步。如果某个 Follower挂掉，Leader 会再找一个替代并同步消息；如果 Leader 挂了，Follower 们会选举出一个新的 Leader 替代，继续业务，这些都是由 ZooKeeper 完成的。

![image-20220726214912409](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220726214912409.png)

**4.消费者注册**

每个消费者服务器启动时，都会到Zookeeper的指定节点下创建一个属于自己的消费者节点，如/consumers/[group_id]/ids/[consumer_id]，完成节点创建后，消费者就会将自己订阅的Topic信息写入该临时节点。

**5.分区与消费者的关系**

在Kafka中，规定了**每个消息分区 只能被同组的一个消费者进行消费**，因此，需要在Zookeeper上记录消息分区与Consumer之间的关系，每个消费者一旦确定了对一个消息分区的消费权力，需要将其Consumer ID写入到Zookeeper对应消息分区的临时节点上

```sh
/consumers/[group_id]/owners/[topic]/[broker_id-partition_id]
```

其中，[broker_id-partition_id]就是一个消息分区的标识，节点内容就是该消息分区上消费者的Consumer ID。

 

## **生产者向** **Kafka** **发送消息的执行流程介绍一下？**

（1）生产者要往 Kafka 发送消息时，需要先创建 **ProducerRecoder**对象

（2）**ProducerRecoder** 对象可包含目标 **topic**，**分区内容**，以及指定的 **key** 和**value**,  在发送 ProducerRecoder 时，生产者会先把键和值对象序列化成字节数组，然后在网络上传输。

（3）生产者在将消息发送到某个 Topic ，需要经过**拦截器**、**序列化器**和**分区器**（Partitioner）。

（4）如果消息 **ProducerRecord** 没有指定 partition 字段，那么**就需要依赖分区器**。**分区器的作用就是为消息分配分区**。

1. 若没有指定分区，且消息的 key 不为空，则使用 murmur 的 Hash 算法（非加密型 Hash 函数，具备高运算性能及低碰撞率）来计算分区分配。

2. 若没有指定分区，且消息的 key 也是空，则用**轮询**的方式选择一个分区。

（5）分区选择好之后，会将消息添加到一个记录批次中，这个批次的所有消息都会被发送到相同的 **Topic** 和 **partition** 上。然后会有一个独立的线程负责把这些记录批次发送到相应的 broker 中。

（6）**broker** 接收到 Msg 后，会作出一个响应。如果成功写入 Kafka 中，就返回一个 **RecordMetaData** 对象，它包含 Topic 和 Partition 信息，以及记录在分区的 offset。

（7）若写入失败，就返回一个错误异常，生产者在收到错误之后尝试重新发送消息，几次之后如果还失败，就返回错误信息。

 

## 生产者分区分配策略**？**

> 通过 **消息键** 和 **分区器** 来实现，分区器为键生成一个 offset，然后使用 offset 对主题分区进行取模，为消息选取分区，这样就可以保证包含同一个键的消息会被写到同一个分区上。
>

1. 如果在发消息的时候指定了分区，则消息投递到指定的分区。
2. 如果 ProducerRecord 没有指定分区，且消息的 key 不为空，则使用 Hash 算 法来计算分区分配（将key的hash值与topic的partition数进行模得到partition值）。
3. 如果 ProducerRecord 没有指定分区，且消息的 key 也是空，则用 **轮询** 的方式选择一个分区

 

## **消费者分区分配策略**?

**1.range分区策略**

Range分配策略是**面向每个主题**的，首先会对同一个主题里面的分区按照序号进行排序，并把消费者线程按照字母顺序进行排序。然后用分区数除以消费者线程数量来判断每个消费者线程消费几个分区。如果除不尽，那么前面几个消费者线程将会多消费一个分区。

**2.RoundRobin分配策略**

RoundRobin策略的原理是将消费组内所有消费者以及消费者所订阅的所有topic的partition按照字典序排序，然后通过轮询算法逐个将分区以此分配给每个消费者。

**3.Sticky分配策略**

**这种分配策略是在kafka的0.11.X版本才开始引入的，是目前最复杂也是最优秀的分配策略。**

Sticky分配策略的原理比较复杂，它的设计主要实现了两个目的：

- 分区的分配要尽可能的均匀；
- 分区的分配尽可能的与上次分配的保持相同。

如果这两个目的发生了冲突，优先实现第一个目的。

 

## kafka的文件存储机制？ ★ ☆★☆★

Kafka 中消息是以 **topic** 进行分类的，生产者生产消息，消费者消费消息，都是面向 topic的。

topic 是逻辑上的概念，而 partition 是物理上的概念，一个topic 有多个partition ，每个 partition 对应于一个 log 文件，该 log 文件中存储的就是 producer 生产的数据。Producer 生产的数据会被不断追加到该log 文件末端，且每条数据都有自己的 offset。

> 消费者组中的每个消费者，都会实时记录自己消费到了哪个 offset，以便出错恢复时，从上次的位置继续消费。

由于生产者生产的消息会不断追加到 log 文件末尾，为防止 log 文件过大导致数据定位效率低下，Kafka 采取了**分片**和**索引**机制，将每个 partition 分为多个 segment。Kafka 会根据 log.segment.bytes 的配置来决定单个 Segment 文件的大小，当写入数据达到这个大小时就会创建新的 Segment 。

每个 segment主要包含三个文件——“.log”文件、“.index”文件和”.timeindex“文件。**这三个文件以当前 segment 的第一条消息的 offset 命名**。

**“.index”文件存储大量的索引信息，“.log”文件存储大量的数据，索引文件中的元数据指向对应数据文件中 message 的物理偏移地址。**

Kafka 中还维护了 timeindex，保存了 Timestamp 和 Offset 的关系，在一些场景需要根据 timestamp 来定位消息。

> **timeindex** **中的一个（** **timestampX，offsetY **）**元素的含义是所有创建时间大于** **timestampX** **的消息的** **Offset** **都大于** **offsetY**。

 

**log文件中的记录格式：**

（BatchRecords是Kafka数据的存储单元，一个BatchRecords中包含多个Record（即我们通常说的一条消息），".log"文件中存的就是BatchRecords）。

BatchRecords字段表格

![image-20220321102136015](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321102136015.png)

而每条消息由多个Header信息（Header是Key-Value形式的），key数组、数据值(value)数组等组成；

![image-20220321102629059](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321102629059.png)

[Kafka消息（存储）格式及索引组织方式 - 杭州.Mark - 博客园 (cnblogs.com)](https://www.cnblogs.com/hzmark/p/kafka_message_format.html)

 

## 如何根据offset找到对应的message？ ★☆★☆★

通过 Offset 从存储层中获取 Message 大致分为两步：

**第一步**  根据 Offset 以二分法找到所属的 Segment 文件，因为Segment 的文件名就是它包含的数据的起始 Offset 。

**第二步**  根据索引信息（.Index）来快速定位目标数据在 Segment 中的位置，否则就要读取整个 Segment 文件了，

详细过程如下:

- 在index文件中找到小于等于目标offset的最大offset对应的索引项（因为是稀疏索引）；
- 根据这个offset定位log文件：从这个offset对应的position开始，向下遍历寻找到目标的offset

![image-20220321101445136](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321101445136.png)

Kafka 并不会为每个 Record 都保存一个索引，而是根据 log.index.interval.bytes （默认4KB）等配置 **构建稀疏索引信息**，就是每写入4kb文件创建一个索引。**在0.9版本之后，offset 已经直接维护在kafka集群的__consumer_offsets这个topic中 , 之前存在zookeeper中。**

 

## **kafka** **如何实现消息是有序的？** ★ ☆★☆★

**生产者**：通过分区的 leader 负责数据以先进先出的顺序写入，来保证消息顺序性。

**消费者**：同一个分区内的消息只能被一个 **group 里**的一个消费者消费，保证分区内消费有序。

kafka 每个 partition 中的消息在写入时都是有序的，消费时， 每个 partition 只能被每一个消费者组中的一个消费者消费，保证了消费时也是有序的。**这样就保证了单分区局部有序。**

整个 kafka 不保证有序。**如果为了保证** **kafka** **全局有序，那么设置一个生产者，一个分区，一个消费者；或者通过指定Key将数据都发送到一个分区。**

 

## **Kafka的一条message中包含了哪些信息？**

![image-20220321105444668](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321105444668.png)

 

具体字段解释如下：

CRC32：4个字节，消息的校验码。

magic：1字节，魔数标识，与消息格式有关，取值为0或1。当magic为0时，消息的offset使用绝对offset且消息格式中没有timestamp部分；当magic为1时，消息的offset使用相对offset且消息格式中存在timestamp部分。所以，magic值不同，消息的长度是不同的。

attributes： 1字节，消息的属性。其中第0~ 2位的组合表示消息使用的压缩类型，0表示无压缩，1表示gzip压缩，2表示snappy压缩，3表示lz4压缩。第3位表示时间戳类型，0表示创建时间，1表示追加时间。

timestamp： 时间戳，其含义由attributes的第3位确定。

key length：消息key的长度。

key：消息的key。

value length：消息的value长度。

value：消息的内容

**(ps:消息不同于记录)**

[Kafka的消息格式 - devos - 博客园 (cnblogs.com)](https://www.cnblogs.com/devos/p/5100611.html)

 

 

## **说说** **kafka** **的默认消息保留策略？**

broker 默认的消息保留策略分为两种：

1. 日志片段通过 log.segment.bytes 配置（默认是 1GB），小于配置的大小即会被保留；

2. 日志片段通过 log.segment.ms 配置 （默认 7 天），小于配置的时间被保留。

 

## Kafka文件清理策略？

Kafka 中提供的日志清理策略有 delete 和 compact 两种。

**数据清理方式一：删除**

启用删除策略：

`log.cleanup.policy=delete`

直接删除，删除后的消息不可恢复。可配置以下两个策略：

- 清理超过指定时间清理：`log.retention.hours=16 `
- 超过指定大小后，删除旧的消息：`log.retention.bytes=1073741824 `

为了避免在删除时阻塞读操作，采用了copy-on-write形式的实现，删除操作进行时，读取操作的二分查找功能实际是在一个静态的快照副本上进行的，这类似于Java的CopyOnWriteArrayList。

**数据清理方式二：压缩**

将数据压缩，只保留每个key最后一个版本的数据。

这种策略只适合特俗场景，比如消息的key是用户ID，消息体是用户的资料，通过这种压缩策略，整个消息集里就保存了所有用户最新的资料

 

## 说下Kafka中的分区？★ ☆★☆★

1. **分区**

   Kafka 中消息是以 **topic** 进行分类的，topic 是逻辑上的概念，而 partition 是物理上的概念，一个topic被分成多个partition ，每个 partition 对应于一个 log 文件，每条记录都以追加的形式写入。

2. **分区的作用**

   - **便于合理使用存储资源**    可以把海量的数据按照分区切割成一块一块数据存储在多台Broker上。合理控制分区的分布，可以实现负载均衡的效果。

   - **partiton为kafka提供了数据容错性**；Kafka 为一个 Partition 生成多个**副本**，并且把它们分散在不同的 Broker。如果一个 Broker 故障了，Consumer 可以在其他 Broker 上找到 Partition 的副本，继续获取消息。

   - **提高并行度**    生产者可以以分区为单位发送数据；消费者可以以分区为单位进行消费数据，这样就提高了并行度。

3. **数据写入partition**

   - 如果在发消息的时候指定了分区，则消息投递到指定的分区。

   - 如果 ProducerRecord 没有指定分区，且消息的 key 不为空，则使用 Hash 算 法来计算分区分配（将key的hash值与topic的partition数进行取余得到partition值）。

   - 如果 ProducerRecord 没有指定分区，且消息的 key 也是空，则用 **轮询** 的方式选择一个分区

   - 自定义规则;   Kafka 支持自定义规则，一个 Producer 可以使用自己的分区指定规则

当一条记录写入 Partition 的时候，它就被追加到 log 文件的末尾，并被分配一个序号，称为 Offset偏移量，Offset 是一个递增的、不可变的数字，由 Kafka 自动维护。

4. **从partition读取数据**

消费者根据offset读取分区内的数据

- Consumer 须自己从Topic 的 Partition 依次拉取消息。

- 同一个分区内的消息只能被一个 **group 里**的一个消费者消费。

 

 

## kafka如何保证数据不丢失？ ★ ☆★☆★

kafka是实现异步消息通讯的中间件，整个架构由Producer Consumer Broker组成

所以保证消息不丢失从这三个方面考虑和实现

**一，Producer确保消息发送成功**

Producer默认是异步发送消息

第一种方法 把异步发送改为同步发送，这样就能实时知道消息发送的结果

第二种方法 添加异步或回调函数，监听消息发送的结果，如果失败可以在回调中重试

第三种方法 Producer本身提供了一个retries的机制，如果因为网络问题，或者broker故障 导致发送失败，会进行重试

**二，Broker端 确保发送来的数据不丢失，只需要把这个消息持久化到磁盘。**
但是Kafka为了提高性能，采用的是异步批量，先写入缓存再刷写到磁盘的机制，就是有一定的消息量和时间间隔要求的，刷磁盘的这个动作是操作系统来调度的，如果在刷盘之前系统就崩溃了，就会数据丢失。它没有同步刷盘的机制。

针对这个问题，需要**Partition的副本机制，acks机制来解决**。Partition的副本机制是针对每个数据分区的高可用策略，每个副本集会包含唯一的一个leader和多个follower,leader负责处理事务类型的请求，follower负责同步leader的数据。

同时Kafka提供了一个 acks的参数，**Producer可以设置这个参数**，去结合broker的副本机制来共同保障数据的可靠性。

acks=0 表示producer不需要等待broker的响应，就认为消息发送成功了(可能存在数据丢失)

acks=1 表示broker的leader  Partition收到消息之后  不等待其他的follower Partition的同步就给Producer发一个确认，假设leader
挂了(可能存在数据丢失)

acks=-1 表示broker的leader Partition收到消息之后 并且等待 **ISR列表中**的follower同步完成，再给Producer返回一个确认(保证数据不丢失)

> Isr列表中只有一个leader时，也会丢数据；但是可以通过设置避免这样的情况发生：min.insync.replicqas>=2；

**三，Consumer 必须要能够消费这个消息。**
其实只要Producer和Broker的消息能得到保证，消费端不太可能出现不能丢失消费的问题，除非Consumer没有消费完这个消息就提交了offset，这个我们可以采用 手动提交offset的方式，等到消费者确定消费完成后再提交offset，保证数据不丢失；

 

> 使用[Kafka](https://bugjia.net/tags/apache-kafka)自带的kafka-consumer-groups.sh脚本可随意设置消费者组(consumer group)，这是0.11.0.0版本提供的新功能，设置的前提是：consumer group状态是inactive的，即不能是处于正在工作中的状态。
> 重设位移的流程由下面3步组成：
> 1、确定位移重设策略——当前支持8种设置规则：
> --to-earliest：把位移调整到分区当前最小位移
> --to-latest：把位移调整到分区当前最新位移
> --to-current：把位移调整到分区当前位移
> --to-offset <offset>： 把位移调整到指定位移处
> --shift-by N： 把位移调整到当前位移 + N处，注意N可以是负数，表示向前移动
> --to-datetime <datetime>：把位移调整到大于给定时间的最早位移处，datetime格式是yyyy-MM-ddTHH:mm:ss.xxx
> --by-duration <duration>：把位移调整到距离当前时间指定间隔的位移处，duration格式是PnDTnHnMnS
> --from-file <file>：从CSV文件中读取调整策略

 

## **Kafka如何尽可能保证数据可靠性和一致性？**★ ☆★☆★

### 数据可靠性（也可以回答前面的数据不丢失）

1. topic分区副本策略

   一个topic会被分成多个partition，为一个 Partition 生成多个副本（默认为3），并且把它们分散在不同的 Broker。在众多的分区副本里面有一个副本是 Leader，其余的副本是 follower，所有的读写操作都是经过 Leader 进行的，同时 follower 会定期地去 leader 上的复制数据。当 Leader 挂了的时候，其中一个 follower 会重新成为新的 Leader。Kafka 的分区多副本架构是 Kafka 可靠性保证的核心，把消息写入多个副本可以使Kafka 在发生崩溃时仍能保证消息的持久性

2. ISR机制

   每个分区的Leader 维护了一个动态的 **ISR** 列表（in-sync replica(ISR)）,**ISR** **是指与** **leader** **副本保持同步状态的副本集合**。当然 leader 副本本身也是这个集合中的一员。 当 ISR 中的 **全部follower 完成数据同步之后， leader 就会给 follower 发送 ack** ,如果其中一个 follower 长时间未向 leader 同步数据，该 follower 将会被踢出 ISR 集合（该时间阈值由 replica.log.time.max.ms 参数设定）。当 leader 发生故障后，就会从ISR 集合中重新选举出新的 leader。

3. ACK应答机制

   为保证producer发送的数据，能可靠的发送到指定的topic，topic的每个partition收到producer发送的数据后，都需要向producer发送ack（acknowledgement确认收到），如果producer收到ack，就会进行下一轮的发送，否则重新发送数据。

   Kafka为用户提供了三种可靠性级别（acks参数）：

   - **acks=0**

   producer不等待broker的ack，broker一接收到还没有写入磁盘就已经返回。

   当**broker故障时**，有可能**丢失数据**。

   - **acks=1**

   producer等待broker的ack，partition的leader落盘成功后返回ack。

   如果在follower同步成功之前leader故障，那么将会**丢失数据**。

   - **acks=-1(all)**

   producer等待broker的ack，partition的leader和ISR中的所有follower全部落盘成功后才返回ack。

   > 如果在**follower同步完成后**，broker**发送ack之前leader发生故障**，此时kafka从ISR中重新选举一个leader，生产者没有收到ack重新发送一份到新leader上，则造成**数据重复**。
>
   > 如果**ISR中只剩一个leader**时，此时**leader发生故障**，可能会造成**数据丢失**。
>
   > 如果**一个follower故障**，该节点被踢出ISR，只要ISR中所有节点都同步即可返回ack，**不影响**。

 

### 数据一致性

1. 故障处理 --通过LEO和HW保证各副本数据之间的一致性

   **LEO：每个副本的最后一个Offset** 。（每个副本有一个自己的LEO，follwer的LEO不能大于leader）

   **HW：所有副本中最小的LEO** （只有一个）

   - **follower故障**

   follower发生故障后会被临时踢出ISR，待该follower恢复后，follower会读取本地磁盘记录的上次的HW， 并**将log文件高于HW的部分截取掉**，从HW开始向leader进行同步。等**该follower的*LEO***大于等于该Partition的HW，即follower追上leader之后，就可以重新加入ISR了。

   - **leader故障**

   leader发生故障之后，会从ISR中选出一个新的leader，之后，为保证多个副本之间的数据一致性，其余的follower会**先将各自的log文件高于HW的部分截掉，然后从新的leader同步数据**。

   > 注意：**这只能保证副本之间的数据一致性**，并不能保证数据不丢失或者不重复。（是否丢数据是acks保证）

2. unclean.leader.election.enable 设为false(0.11版本之后已经默认为false)；表示非ISR中的副本不能够参与选举；因为非ISR列表中的follwer数据落后leader很多，如果将其选举为leader，会极大可能出现副本之间的数据不一致。

 

 

## **Kafka支持什么语义，怎么实现Exactly Once？** ★ ☆★☆★

Kafka支持的**消费语义**有以下几种：

- at most once：最多消费一次，消息可能会丢失

  有可能消费者在消费的时间段内就提交了offset，从而导致了offset已经提交了，但是数据库还没进行保存或者保存未成功。下一次再消费的时候就会认为offset已经成功了，就会造成丢数据。

- at least once：至少消费一次，会重复消费

  数据已经保存在数据库，但是这个时候服务器宕机了，从而导致offset不能提交成功；下次消费的时候，会从上一次成功的offset开始消费，相同的数据会再次写入数据库，也就是至少一次；会重复消费，但至少不会丢数据。

- exactly once：正好一次，**不丢失，不重复**

 

### **exactly once的实现（单个分区内的exactly once）**

单个分区内的exactly once可以通过幂等性+At Least Once语义实现

0.11版本的Kafka，引入了一项重大特性：**幂等性**。所谓的幂等性就是**指Producer不论向Server发送多少次重复数据，Server端都只会持久化一条**。**幂等性结合At Least Once语义，就构成了Kafka的ExactlyOnce语义**。

**精确一次（Exactly Once） = 幂等性 +至少一次**（ack=-1 + 分区副本数>=2 + ISR最小副本数量>=2） 。

> kafka如何实现幂等性
>
> 要启用幂等性，只需要将Producer的参数中enable.idompotence设置为true即可。
>
> 开启幂等性的Producer在初始化的时候会被分配一个PID，发往同一Partition的消息会附带Sequence Number。而Broker端会对<PID, Partition, SeqNumber>做缓存，当具有相同主键的消息提交时，Broker只会持久化一条。**其 中PID是Kafka每次重启都会分配一个新的；Partition 表示分区号；Sequence Number是单调自增的。所以幂等性只能保证的是在单分区单会话内不重复。**

 

 

### **Kafka消费者怎么保证Exactly Once**

关闭自动提交位移，确认消息处理完成后，由应用程序手动提交位移，可以解决数据丢失的情况，不能解决数据重复的情况

此时需要事务机制的支持；

需要Kafka消费端将消费过程和提交offset过程做原子绑定。即在一个事务中处理消费数据和提交消费偏移量；要么都成功要么都失败；此时可以借助一个支持事务的外部系统（比 如MySQL）。

 

 

## 发布订阅模式的两种？

**1、点对点模式**（一对一，消费者主动拉取数据，消息收到后消息清除）

消息生产者生产消息发送到Queue中，然后消息消费者从Queue中取出并且消费消息。

消息被消费以后，Queue中不再有存储，所以消息消费者不可能消费到已经被消费的消息。Queue支持存在多个消费者，但是对一个消息而言，只会有一个消费者可以消费。

![image-20220321200014184](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321200014184.png)

**2、发布/订阅模式**（一对多，消费者消费数据之后不会清除消息）

消息生产者（发布）将消息发布到topic中，同时有多个消息消费者（订阅）消费该消息。和点对点模式不同，**发布到topic的消息会被所有订阅者消费。**

![image-20220321200049703](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321200049703.png)

 

## **Kafka的offset管理**

消费者在消费的过程中需要记录自己消费了多少数据，即消费 Offset。

通常有如下几种 Kafka Offset 的管理方式：

- HBASE、Redis 等外部 NOSQL 数据库：这一方式可以支持大吞吐量的 Offset 更新，但它最大的问题在于：用户需要自行编写 HBASE 或 Redis 的读写程序，并且需要维护一个额外的组件。

- ZOOKEEPER：老版本的位移offset是提交到zookeeper中的，目录结构是：` /consumers/<group.id>/offsets/ <topic>/<partitionId> `，但是由于 ZOOKEEPER 的写入能力并不会随着 ZOOKEEPER 节点数量的增加而扩大，因而，当存在频繁的 Offset 更新时，ZOOKEEPER 集群本身可能成为瓶颈。因而，不推荐采用这种方式。

- Kafka自身的一个特殊Topic（__consumer_offsets）中：这种方式支持大吞吐量的Offset更新，又不需要手动编写 Offset 管理程序或者维护一套额外的集群，因而是迄今为止最为理想的一种实现方式

 

## **offset更新/提交方式**

自动提交offset

设置enable.auto.commit=true，更新的频率根据参数【auto.commit.interval.ms】来定。

手动提交offset

- commitSync（同步提交）：必须等待offset提交完毕（失败重试），再去消费下一批数据。
- commitAsync（异步提交） ：发送完提交offset请求后，就开始消费下一批数据了（不失败重试，有可能会提交失败）。

 

## **正在消费一条数据，Kafka挂了，重启以后，消费的offset是哪一个** ★ ☆★☆★

主要是看各分区下是否已经有提交的offset和**``auto.offset.reset `**的配置，这个参数有三种配置方式：

- earliest ：当各分区下有已提交的 Offset 时，从提交的 Offset开始消费；无提交的Offset 时，从头开始消费；
- latest ： 当各分区下有已提交的 Offset 时，从提交的 Offset 开始消费；无提交的 Offset时，消费该分区下新产生的数据；
- none ： Topic 各分区都存在已提交的 Offset 时，从 Offset 后开始消费；只要有一个分区不存在已提交的 Offset，则抛出异常。

[Kafka之重新消费数据_jannals的博客-CSDN博客_kafka重新消费](https://blog.csdn.net/usagoole/article/details/82813091)

 

## **Kafka为什么同一个消费者组的消费者不能消费相同的分区？**

> 网易
>

Kafka通过消费者组机制同时实现了发布/订阅模型和点对点模型。多个组的消费者消费同一个分区属于多订阅者的模式，自然没有什么问题；而在单个组内某分区只交由一个消费者处理的做法则属于点对点模式。其实这就是设计上的一种取舍，如果Kafka真的允许组内多个消费者消费同一个分区，也不是什么灾难性的事情，只是没什么意义，而且还会重复消费消息。通常情况下，我们还是希望一个组内所有消费者能够分担负载，让彼此做的事情没有交集，做一些重复性的劳动纯属浪费资源。就如同电话客服系统，每个客户来电只由一位客服人员响应。那么请问我就是想让多个人同时接可不可以？当然也可以了，技术上没什么困难，只是这么做没有任何意义罢了，既拉低了整体的处理能力，也造成了人力成本的浪费。总之，这种设计不是出于技术上的考量而更多还是看效率等非技术方面。

 

## **Kafka的消费者和消费者组有什么区别？为什么需要消费者组？**

顾名思义，**消费者**就是从kafka集群消费数据的客户端；

所谓 **消费者组** ，其实就是一组 消费者 的集合；

如果这个时候 kafka 上游生产的数据很快，超过了这个 某个 消费者的消费速度，那么就会导致数据堆积，那么我们只能加强 消费者 的消费能力，所以也就有了 消费者组 。

我们采用了一个 消费组 来消费这个 topic 而不是单个消费者消费这个topic，众人拾柴火焰高，其消费能力那是按倍数递增的，所以这里我们一般来说都是采用 消费者组 来消费数据，而不会是 单消费者 来消费数据的。

![image-20220321202828415](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220321202828415.png)

> 注意：
>
> 一个topic可以被多个消费者组消费，但是每个消费者组消费的数据是互不干扰的，也就是说，每个消费组消费的都是完整的数据 。
>
> 一个分区只能被同一个消费组内的一个消费者消费，而不能拆给多个消费者消费，也就是说如果你某个消费者组内的消费者数比该 Topic 的分区数还多，那么多余的消费者是不起作用的

**扩展一下：**

**1）是不是一个消费组的消费者越多其消费能力就越强呢？**

如果你想要加强消费者组的能力，除了添加消费者，分区的数量也是需要跟着增加的，只有这样他们的并行度才能上的去，消费能力才会强。

消费者组内的消费者数量大于topic分区数时；会有消费者空闲，白白浪费资源。

**2）为了提高消费组的消费能力，我是不是可以随便添加分区和消费者呢？**

答案当然是否定的；一般来说我们建议消费者数量和分区数量是一致的，当我们的消费能力不够时，就必须通过调整分区的数量来提高并行度，但是，我们应该尽量来避免这种情况发生。

如果发生这种情况，这个时候kafka会进行分区再均衡，来为这个分区分配消费者，分区再均衡期间该Topic是不可用的，并且作为一个被消费者，分区数的改动将影响到每一个消费者组 ，所以在创建 topic 的时候，我们就应该考虑好分区数，来尽量避免这种情况发生。

 

## **Kafka读取消息是推还是拉的模式？有什么好处？** ★ ☆★☆★

consumer采用pull（拉）模式从broker中读取数据。

push（推）模式很难适应消费速率不同的消费者，因为这样消息发送速率是由broker决定的。它的目标是尽可能以最快速度传递消息，但是这样很容易造成consumer来不及处理消息，典型的表现就是网络拥塞。而pull模式则可以根据consumer的消费能力以适当的速率消费消息。

pull模式不足之处是，如果kafka没有数据，消费者可能会陷入循环中，一直返回空数据。针对这一点，Kafka的消费者在消费数据时会传入一个时长参数timeout，如果当前没有数据可供消费，consumer会等待一段时间之后再返回，这段时长即为timeout。

 

## 查看Kafka有没有消息积压方式★ ☆★☆★

在Kafka 的bin目录下提供了 kafka-consumer-groups.sh 脚本。此脚本用于管理消费情况。

查询消费者组

bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
查询消费者组详情

bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group groupname

![image-20220609222945072](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220609222945072.png)

消费积压情况分析

LogEndOffset

下一条将要被加入到日志的消息的位移

CurrentOffset

当前消费的位移

LAG

消息堆积量

消息堆积量：消息中间件服务端中所留存的消息与消费掉的消息之间的差值即为消息堆积量也称之为消费滞后量

 

## kafka消息积压，kafka消费能力不足怎么处理？ ★ ☆★☆★

1）如果是Kafka消费能力不足，则可以考虑增加topic的分区数，并且同时提升消费者组消费者的数量，消费者数=分区数（必须）

2）如果是下游的数据处理不及时：提高每批次拉取的数据量，批次拉取的数据过少，使处理的数据小于生产的数据，也会造成数据积压；

 

## Kafka监控实现？

几种监控工具对比：

- Kafka Manager：雅虎出品，可管理多个Kafka集群，是目前功能最全的管理工具。但是注意，当你的Topic太多，监控数据会占用你大量的带宽，造成你的机器负载增高。其监控功能偏弱，不满足需求。
- **Kafka Offset Monitor**：程序以一个jar包的形式运行，部署较为方便。只有监控功能，使用起来也较为安全。有webui
- Kafka Web Console：监控功能较为全面，可以预览消息，监控Offset、Lag等信息，不建议在生产环境中使用。
- Burrow：是LinkedIn开源的一款专门监控consumer lag的框架。支持报警，只提供HTTP接口，没有webui。
- Availability Monitor for Kafka：微软开源的Kafka可用性、延迟性的监控框架,提供JMX接口，用的很少。

 

## **Kafka中的数据能彻底删除吗？**

如果用kafka-topics.sh的delete命令删除topic，会有两种情况：

1）如果当前topic没有使用过即没有传输过信息：可以彻底删除。

2）如果当前topic有使用过即有过传输过信息：并没有真正删除topic只是把这个topic标记为删除（marked for deletion）。

要彻底把情况2中的topic删除必须把kafka中与当前topic相关的数据目录和zookeeper与当前topic相关的路径一并删除。

 

## Kafka在哪些地方会有选举，用到了什么工具支持？

Kafka中的选举大致可以分为三大类：**控制器的选举（先到先得）**、**分区leader的选举（ISR）**以及**消费者相关的选举**

**控制器的选举**

(1) 在 kafka 集群中，会有多个 broker 节点，集群中第一个启动的 broker 会通过在 zookeeper 中创建临时节点 **/controller** 来让自己成为控制器，其他 broker 启动时也会在 zookeeper 中创建临时节点，但是发现节点已经存在，所以它们会收到一个异常，意识到控制器已经存在，那么就会在 zookeeper 中创建 **watch** 对象，便于它们收到控制器变更的通知。

(2) 如果集群中有一个 broker 发生异常退出了，那么控制器就会检查这个 broker是否有分区的副本 leader ，如果有那么这个分区就需要一个新的 leader，此时控制器就会去遍历其他副本，决定哪一个成为新的 leader，同时更新分区的 ISR 集合。

(3) 如果有一个 broker 加入集群中，那么控制器就会通过 Broker ID 去判断新加入的 broker 中是否含有现有分区的副本，如果有，就会从分区副本中去同步数据。

(4) 集群中每选举一次控制器，就会通过 zookeeper 创建一个 **controller epoch**，每一个选举都会创建一个更大，包含最新信息的 epoch，如果有 broker 收到比这个 epoch 旧的数据，就会忽略它们，kafka 也通过这个 epoch 来防止集群产生“脑裂”。

**分区副本的leader选举**

分区leader副本的选举由Kafka Controller负责具体实施

基本思路是按照AR（Assigned Repllicas：分区中的所有副本）集合中副本的顺序查找第一个存活的副本，并且这个副本在ISR集合（ in-sync replica  与leader同步的集合.,通过replica.lag.time.max.ms 参数参数配置，在这个时间内leader收到通知，认为它同步）中。一个分区的AR集合在分配的时候就被指定，并且只要不发生重分配的情况，集合内部副本的顺序是保持不变的，而分区的ISR集合中副本的顺序可能会改变。

参数unclean.leader.election.enable（现在默认为false）

这个参数为false时**只能是副本在ISR中时才能被当选为leader**；为true时，若ISR中没有可用副本，可将AR中**第一个存活**的副本当选为leader（尽管他不在ISR中）。

**消费者选主**

在kafka的消费端，会有一个消费者协调器以及消费组，组协调器GroupCoordinator需要为消费组内的消费者选举出一个消费组的leader。这个选举的算法也很简单，分两种情况分析。如果消费组内还没有leader，那么第一个加入消费组的消费者即为消费组的leader。如果某一时刻leader消费者由于某些原因退出了消费组，那么会重新选举一个新的leader，这个重新选举leader的过程又更“随意”了，相关代码如下：

```java
private val members = new mutable.HashMap[String, MemberMetadata] var
leaderId = members.keys.head
```

在GroupCoordinator中消费者的信息是以HashMap的形式存储的，其中key为消费者的member_id，而value是消费者相关的元数据信息。leaderId表示leader消费者的member_id，它的取值为HashMap中的第一个键值对的key，这种选举的方式基本上和随机无异。

 

## Kafka怎么防止controller脑裂

控制器（controller）其实就是一个broker ，只不过具有一般broker没有的功能，相当于整个kafka集群的**master**，负责分区副本leader的选举，topic的创建、删除、broker的上线、下线等。

可能由于网络问题，同时有两个broker认为自己是controller，这时候其他的broker就会发生脑裂，不知道该听从谁的。

**通过controller epoch来解决。**

每当新的controller产生时就会通过Zookeeper生成一个全新的、数值更大的controller epoch标识。其他broker在知道当前controller epoch后，如果收到由控制器发出的包含较旧epoch的消息，就会忽略它们。

 

## Kafka工作原理？ ★ ☆★☆★

### Kafka数据的写入流程

在消息发送的过程中，涉及到了两个线程——main线程和Sender线程，以及一个线程共享变量——RecordAccumulator。**主线程**负责创建消息ProducerRecord，然后通过分区器、序列化器、拦截器作用之后缓存到累加器RecordAccumulator中，Sender线程不断从RecordAccumulator中拉取消息发送到Kafka broker；并写入对应topic的分区副本**leader** 中，follwer会从leader中同步数据。

[深入理解kafka——RecordAccumulator 和 InFlightRequests - 码出地球 - 博客园 (cnblogs.com)](https://www.cnblogs.com/leonandyou/p/15563776.html#:~:text=RecordAc,erBatch。)

### 保存数据

Kafka 中消息是以 **topic** 进行分类的，生产者生产消息，消费者消费消息，都是面向 topic的。

topic 是逻辑上的概念，而 partition 是物理上的概念，一个topic 有多个partition ，每个 partition 对应于一个 log 文件，该 log 文件中存储的就是 producer 生产的数据。Producer 生产的数据会被不断追加到该log 文件末端，且每条数据都有自己的 offset。

由于生产者生产的消息会不断追加到 log 文件末尾，为防止 log 文件过大导致数据定位效率低下，Kafka 采取了**分片**和**索引**机制，将每个 partition 分为多个 segment。Kafka 会根据 log.segment.bytes 的配置来决定单个 Segment 文件的大小，当写入数据达到这个大小时就会创建新的 Segment 。

每个 segment主要包含三个文件——“.log”文件、“.index”文件和”.timeindex“文件。**这三个文件以当前 segment 的第一条消息的 offset 命名**。

**“.index”文件存储大量的索引信息，“.log”文件存储大量的数据，索引文件中的元数据指向对应数据文件中 message 的物理偏移地址。**

Kafka 中还维护了 timeindex，保存了 Timestamp 和 Offset 的关系，在一些场景需要根据 timestamp 来定位消息。

> 在 Log 中的 Message ，主要包含消息体、消息大小、Offset、压缩类型……等等！
>
> - Offset：Offset 是一个占 8byte 的有序 id 号，它可以唯一确定每条消息在 Parition 内的位置！
> - 消息大小：消息大小占用 4byte，用于描述消息的大小。
> - 消息体：消息体存放的是实际的消息数据（被压缩过），占用的空间根据具体的消息而不一样。
>

### **消费数据**

消息存储在 Log 文件后，消费者就可以进行消费了。Kafka 采用的是点对点的模式，消费者主动的去Kafka 集群拉取消息，与 Producer 相同的是，消费者在拉取消息的时候也是找 Leader 去拉取。多个消费者可以组成一个消费者组（Consumer Group），同一个消费组者的消费者可以消费同一 Topic 下不同分区的数据，但是不会组内多个消费者消费同一分区的数据！

可以谈一下上面的《根据offset找到对应的massage？》

[kafka3.x原理详解看这篇就够了 - rainple - 博客园 (cnblogs.com)](https://www.cnblogs.com/rainple/p/15914065.html#:~:text=2）kafka最新的定义：kafka是一个开源的分布式事件流平台（event stream,platform），主要用高性能数据管道，流分析，数据集成和关键任务等领域 2、消息队列)https://www.cnblogs.com/rainple/p/15914065.html#:~:text=2）

 

# zookeeper

## **介绍下Zookeeper是什么？**作用？优缺点？应用场景？ ★ ☆★☆★

Zookeeper是一个开源的分布式的，为分布式应用提供协调服务的Apache项目。是一个由一个领导者（Leader），多个跟随者（Follower）组成的集群。

Zookeeper从设计模式角度来理解，是一个基于观察者模式设计的分布式服务管理框架，它负责存储和管理大家都关心的数据，然后接受观察者的注册，一旦这些数据的状态发生了变化，Zookeeper就负责通知已经在Zookeeper上注册的那些观察者做出相应的反应。

### 作用

Zookeeper作用包括**存储数据（文件系统）和监听（监听通知机制**）

Zookeeper提供的服务包括：分布式数据发布/订阅功能、统一命名服务、统一配置管理、统一集群管理、服务器节点动态上下线、软负载均衡等。它致力于为那些高吞吐的大型分布式系统提供一个高性能、高可用、且具有严格顺序访问控制能力的分布式协调服务。

> **分布式数据发布/订阅功能**
>
> 一个典型的发布/订阅模型系统定义了一种一对多的订阅关系，能让多个订阅者同时监听某一个主题对象，当这个主题对象自身状态变化时，会通知所有订阅者，使他们能够做出相应的处理。
>
> **命名服务**
>
> 在分布式系统中，通常需要一个全局唯一的名字，如生成全局唯一的网站名称等，Zookeeper可以通过顺序节点的特性来生成全局唯一ID，从而可以对分布式系统提供命名服务。
>
> **统一配置管理**
>
> 分布式环境下，配置文件同步非常常见。 一般要求一个集群中，所有节点的配置信息是一致的，比如 Kafka 集群。对配置文件修改后快速同步到各个节点上；
>
> 配置管理可由zookeeper实现；可将配置信息写入zookeeper的一个znode  ，各个客户端服务器监听这个Znode。 一旦Znode中的数据被修改，ZooKeeper将通知各个客户端服务器。
>
> **统一集群管理**
>
> 分布式环境中，实时掌握每个节点的状态是必要的。 可根据节点实时状态做出一些调整。
>
> ZooKeeper可以实现实时监控节点状态变化；可将节点信息写入ZooKeeper上的一个ZNode。 监听这个ZNode可获取它的实时状态变化
>
> **服务器节点动态上下线**
>
> 服务器启动时在zookeeper的节点注册信息；客户端监听这个节点就可以知道服务器的工作情况。
>
> **软负载均衡**
>
> 在Zookeeper中记录每台服务器的访问数，让访问数最少的服务器去处理最新的客户端请求。
>
> **master选举**
>
> **分布式锁**

 

### 优点

- 集群中只要有**半数以上**节点存活，Zookeeper集群就能正常服务。所以Zookeeper适合安装奇数台服务器。

- 更新请求顺序执行，来自同一个Client的更新请求按其发送顺序依次执行。

- 数据更新原子性，一次数据更新要么成功，要么失败。

- 可扩展性：可以通过部署更多机器来加强zk的性能

  > 实时性，一旦一个事务被成功应用后，Zookeeper可以保证客户端立即可以读取到这个事务变更后的最新状态的数据。？？

### 缺点

- zookeeper的选举过程缓慢，而zookeeper对网络隔离非常敏感。一旦出现网络隔离，zookeeper就要发起选举流程

  > 网络隔离：两个或两个以上的计算机或网络，不相连、不相通、相互断开

- zookeeper的性能是有限的

  > 本身不是为高可用性设计，master撑不住高流量容易导致系统宕机

- 不支持机架感知

 

## **Zookeeper的选举策略？ **★ ☆★☆★

> 半数机制：集群中半数以上机器存活，集群可用。所以Zookeeper适合安装奇数台服务器。
>
> Zookeeper虽然在配置文件中并没有指定Master和Slave。但是，Zookeeper工作时，是有一个节点为Leader，其他则为Follower，Leader是通过内部的选举机制临时产生的。

### **都是初次启动时的选举策略**

假设有五台服务器组成的Zookeeper集群，它们的**id从1-5**，**同时它们都是最新启动的**，也就是没有历史数据，假设这些服务器依序启动：

1）服务器1启动，发起一次选举。服务器1投自己一票。此时服务器1票数一票，不够半数以上（3票），选举无法完成，服务器1状态保持为LOOKING；

2）服务器2启动，再发起一次选举。服务器1和2分别投自己一票并交换选票信息：此时服务器1发现服务器2的ID比自己目前投票推举的（服务器1）大，更改选票为推举服务器2。此时服务器1票数0票，服务器2票数2票，没有半数以上结果，选举无法完成，服务器1，2状态保持LOOKING

3）服务器3启动，发起一次选举。此时服务器1和2都会更改选票为服务器3。此次投票结果：服务器1为0票，服务器2为0票，服务器3为3票。此时服务器3的票数已经超过半数，服务器3当选Leader。服务器1， 2更改状态为FOLLOWING，服务器3更改状态为LEADING；

4）服务器4启动，发起一次选举。此时服务器1，2，3已经不是LOOKING状态，不会更改选票信息。此时服务器3为3票，服务器4为1票。此时服务器4服从多数，更改选票信息为服务器3，并更改状态为FOLLOWING；

5）服务器5启动，同4一样为FOLLOWING状态。

### **leader故障下线时重新选举**

**SID**：服务器ID。用来唯一标识一台ZooKeeper集群中的机器，每台机器不能重复，和myid一致。

**ZXID**：事务ID。ZXID是一个事务ID，用来标识一次服务器状态的变更。在某一时刻，集群中的每台机器的ZXID值不一定完全一致，这和ZooKeeper服务器对于客户端“更新请求”的处理逻辑有关。

**Epoch**：每个Leader任期的代号。每完成一次选举这个数据就会增加

**选举Leader规则： ①EPOCH大的直接胜出 ②EPOCH相同，事务id大的胜出 ③事务id相同，服务器id大的胜出**

 

## leader和follower的区别

**领导者Leader**

Leader在集群中只有一个节点，可以说是老大，是zookeeper集群的中心，负责协调集群中的其他节点。从性能的角度考虑，leader可以选择不接受客户端的连接。

**主要作用**

1）发起与提交写请求。

所有的跟随者Follower与观察者Observer节点的写请求都会转交给领导者Leader执行（读不会，就是事务请求会）。Leader接受到一个写请求后，首先会发送给所有的Follower，统计Follower写入成功的数量。当有超过半数的Follower写入成功后，Leader就会认为这个写请求提交成功，通知所有的Follower commit这个写操作，保证事后哪怕是集群崩溃恢复或者重启，这个写操作也不会丢失。

2）与**Learner（Follower与Observer）**保持心跳

3）崩溃恢复时负责恢复数据以及同步数据到Learner

 

**跟随者Follower**

Follow在集群中有多个

**主要作用**

1）与老大Leader保持心跳连接

2）当Leader挂了的时候，经过投票后成为新的leader。leader的重新选举是由Follower们内部投票决定的。

3）向leader发送消息与请求

4）处理leader发来的消息与请求

 

## Zookeeper的数据结构/**Zookeeper的节点类型有哪些？分别作用是什么？** ★ ☆★☆★

**数据结构**

Zookeeper数据模型的结构与Unix文件系统很类似，整体上可以看作一棵树，每个节点称作一个ZNode。每一个ZNode默认能够存储1MB的数据，每个ZNode都可以通过其路径唯一标识。

![image-20220323101404892](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220323101404892.png)

**Znode有两种类型：**

短暂（ephemeral）：客户端和服务器端断开连接后，创建的节点自己删除

持久（persistent）：客户端和服务器端断开连接后，创建的节点不删除

**Znode有四种形式的目录节点（默认是persistent ）**

1）持久化目录节点（PERSISTENT）

    客户端与zookeeper断开连接后，该节点依旧存在

2）持久化顺序编号目录节点（PERSISTENT_SEQUENTIAL）

    客户端与zookeeper断开连接后，该节点依旧存在，只是Zookeeper给该节点名称进行顺序编号

3）临时目录节点（EPHEMERAL）

    客户端与zookeeper断开连接后，该节点被删除

4）临时顺序编号目录节点（EPHEMERAL_SEQUENTIAL）

    客户端与zookeeper断开连接后，该节点被删除，只是Zookeeper给该节点名称进行顺序编号

**创建znode时设置顺序标识，znode名称后会附加一个值就是顺序号，顺序号是一个单调递增的计数器，由父节点维护**

**在分布式系统中，顺序号可以被用于为所有的事件进行全局排序，这样客户端可以通过顺序号推断事件的顺序**

 

**都有监听功能；持久化节点更多用于数据存储，持久化顺序节点可对多个事件进行排序；临时节点主要功能是分布式锁；**

 

## **Zookeeper架构**

**Zookeeper集群角色**

**Leader（领导者）**

负责处理事务请求，投票的发起和决议，即时更新状态和数据。

**Follower（跟随者）**

Follower角色接受客户端请求并返回结果，参与Leader发起的投票和选举，但不具有写操作的权限。

**Observer（观察者）**

Observer角色接受客户端连接，将写操作转给Leader，但Observer不参与投票（即不参加一致性协议的达成），只同步Leader节点的状态，Observer角色是为集群系统扩展而生的。

![image-20220322211315143](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220322211315143.png)

**Clinet（客户端）**

连接Zookeeper集群的使用者，请求的发起者，独立于Zookeeper集群的角色。

 

## 既然有了Follower，为什么还要有Observer呢？

虽然通过Client直接连接到ZooKeeper集群的性能已经很好了，但该架构在面对超大规模的Client时，需添加ZooKeeper集群的Server数量。

随着Server的添加，ZooKeeper集群的写性能必定下降（ZooKeeper的ZNode变更是要过半数投票通过，随着机器的添加，因为网络消耗等原因必定导致投票成本添加，从而导致写性能的下降。）

Observer是一种新型的ZooKeeper节点，提供ZooKeeper的可扩展性，同时Observer不參与投票，仅仅是简单的接收投票结果，并向leader 同步消息。因此我们添加再多的Observer也不会影响集群的写性能；另一方面，Observer不參与投票，所以他们不属于ZooKeeper集群的关键部位，即使他们Failed，或者从集群中断开，也不会影响集群的可用性。

 

## **Zookeeper的zab协议**   ★ ☆★☆★

**我首先介绍一下zab协议，然后讲一下zab协议的实现流程；**

### 定义

> Zab协议 的全称是 **Zookeeper Atomic Broadcast** （Zookeeper原子广播），**通过 Zab 协议来保证分布式事务的最终一致性。**

**Zab 是特别为 Zookeeper 设计的支持崩溃恢复的原子广播协议**，在 Zookeeper 中主要依赖 Zab 协议实现数据一致性；

> Zab借鉴了Paxos算法，但又不像Paxos那样，是一种通用的分布式一致性算法。

基于该协议，Zookeeper 实现了一种主备模型（Leader 与 Follower）的系统架构保证集群中各个副本之间的数据一致性。

### zab协议的两种模式

#### 消息广播模式

正常工作下的模式

- 客户端发起一个写操作请求
- Leader 服务器处理客户端请求后将请求转换为 Proposal，同时为每个 Proposal 分配一个全局唯一 ID，即  ZXID
- Leader 服务器与每个 Follower 之间都有一个队列，Leader 将消息发送到该队列，并且根据FIFO策略发送消息
- Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。
- Leader 服务器收到半数以上的 Follower 的 ACK 后，即认为消息发送成功，可以发送commit消息。
- Leader向所有Follower广播commit消息，同时自身也会完成事务提交。Follower 接收到commit消息后，会将上一条事务提交。

#### 崩溃恢复模式

**一旦 Leader 服务器出现崩溃或者由于网络原因导致 Leader 服务器失去了与过半 Follower 的联系，那么就会进入崩溃恢复模式。**

崩溃恢复主要包括两部分：**Leader选举** 和 **数据恢复**

**ZAB协议为了保证数据一致性**，规定了 **如果⼀个事务Proposal在⼀台机器上被提交处理成功，那么应该在所有的机器上都被提交处理成功**

**所以Zab 协议崩溃恢复需满足以下2个要求**

1）Zab 协议需要确保那些**已经在 Leader 服务器上提交（Commit）的事务最终被所有的服务器提交**。
2）Zab 协议需要确保**丢弃那些只在 Leader 上被提出而没有被提交的事务**。

**Leader选举**：

根据上述要求，Zab协议需要保证选举出来的Leader需要满足以下条件：

（1）**新选举出来的Leader不能包含未提交的Proposal**。**即新Leader必须都是已经提交了Proposal的Follower服务器节点**。

（2）**新选举的Leader节点中含有最大的zxid**。这样做的好处是可以避免Leader服务器检查Proposal的提交和丢弃工作。

**数据恢复：**

1）完成 Leader 选举后（新的 Leader 具有最高的zxid），在正式开始工作之前（接收事务请求，然后提出新的 Proposal），Leader 服务器会首先确认事务日志中的所有的 Proposal 是否已经被集群中过半的服务器 Commit，即 **是否完成数据同步**。

> 2）Leader 服务器需要确保所有的 Follower 服务器能够接收到每一条事务的 Proposal ，并且能将所有已经提交的事务 Proposal 应用到内存数据中。等到 Follower 将所有尚未同步的事务 Proposal 都从 Leader 服务器上同步并且应用到内存数据中以后，Leader 才会把该 Follower 加入到真正可用的 Follower 列表中。

 

## **ZAB是以什么算法为基础的？ZAB流程/原理？**★ ☆★☆★

ZAB是在Paxos算法基础上进行了扩展改造而来的。

zookeeper在实现ZAB流程的时候分为三个步骤：

1、选举阶段

选举阶段使用的是 Fast Leader Election（FLE）；在选举的过程中会对每个Follower节点的ZXID进行对比只有**highestZXID的Follower才可能当选Leader；**   **并且ledaer 没有未提交的Proposal**；

> **ZAB协议中使用ZXID作为事务编号，ZXID为64位数字**，低32位为一个递增的计数器，每一个客户端的一个事务请求使Leader产生新的事务后该计数器都会加1，高32位为Leader周期epoch编号，当新选举出一个Leader节点时Leader会取出本地日志中最大事务Proposal的ZXID解析出对应的epoch把该值加1作为新的epoch，将低32位从0开始生成新的ZXID；ZAB使用epoch来区分不同的Leader周期；

2、恢复阶段

在election阶段选举出来的Leader已经具有最新的ZXID，所有本阶段的主要工作是根据Leader的事务日志对Follower节点数据进行更新；这一阶段 Follower 发送他们的 lastZxid 给 Leader，Leader 根据 lastZxid 决定如何同步数据。Follower 收到 TRUNC 指令会终止 `Leader.lastCommitedZxid` 之后的 Proposal ，收到 DIFF 指令会从leader同步接收新的 Proposal，SNAP：Follower数据太老，Leader将发送快照SNAP指令给Follower同步数据。

半数以上的Follower完成数据同步之后，即进入广播阶段

3、广播阶段

- 客户端发起一个写操作请求
- Leader 服务器处理客户端请求后将请求转换为 Proposal，同时为每个 Proposal 分配一个全局唯一 ID，即  ZXID
- Leader 服务器与每个 Follower 之间都有一个队列，Leader 将消息发送到该队列，并且根据FIFO策略发送消息
- Follower 接收到 Proposal 后，会首先将其以事务日志的方式写入本地磁盘中，写入成功后向 Leader 反馈一个 Ack 响应消息。
- Leader 服务器收到半数以上的 Follower 的 ACK 后，即认为消息发送成功，可以发送commit消息。
- Leader向所有Follower广播commit消息，同时自身也会完成事务提交。Follower 接收到commit消息后，会将上一条事务提交。

[Zookeeper一致性协议——ZAB - Jacian - 博客园 (cnblogs.com)](https://www.cnblogs.com/Jacian/p/14212401.html#选举阶段leader-election)

[zab协议流程图总结_luonanqin的博客-CSDN博客_zab协议流程](https://blog.csdn.net/luonanqin/article/details/78314096)

 

## zookeeper脑裂问题

脑裂就是一个集群中同时出现了两个master的场景；

1. **半数机制：**这样的方式可以确保Leader的唯一性,要么选出唯一的一个Leader，要么选举失败，**不会选出两个master**。

2. **假设某个Leader假死**，其余的followers选举出了一个新的Leader。这时，旧的Leader复活并且仍然认为自己是Leader，这个时候它向其他followers发出写请求也是会被拒绝的。

   因为每当新Leader产生时，会生成一个epoch标号(标识当前属于那个Leader的统治时期)，这个epoch是递增的，followers如果确认了新的Leader存在，知道其epoch，就会拒绝epoch小于现任Leader epoch的所有请求。

 

## **Zookeeper从三台扩容到七台怎么做？**

1）先检查三台设备的状态，两台为follower，一台为leader；

2）修改节点数量，由三台增加到七台，修改相应的zoo.cfg文件；

3）完成相关配置后，启动对应zk实例，确认启动ok，节点四到七依次验证实例状态；

4）在leader节点上查看目前状态同步的follower数，确认新增节点已经成功加入集群；

5）确认新增节点加入集群后，滚动更新原有集群的配置，并重启，这个时候会触发一次新的leader选举，epoch标号最大的默认优先当选新的leader，当epoch标号相同，zxid最新的默认优先当选新的leader，当zxid相同，myid最大的优先当选新的leader。

 

## 基于zookeeper的分布式锁？ ★ ☆★☆★

> 锁是多线程代码中的概念，只有当**多任务**访问同一个**互斥**的**共享资源**时才需要
>
> 在我们进行单机应用开发，涉及并发同步的时候，我们往往采用synchronized或者Lock的方式来解决多线程间的代码同步问题，这时多线程的运行都是在同一个JVM之下。但当我们的应用是分布式集群工作的情况下，属于**多JVM下的工作环境**，JVM之间已经无法通过多线程的锁解决同步问题。那么就需要一种更加高级的锁机制，**来处理种跨机器的进程之间的数据同步问题**——这就是分布式锁

**如何使用Zookeeper实现分布式锁**

大致思想为：每个客户端对某个方法加锁时，在 Zookeeper 上与该方法对应的**指定节点的目录下（如：/locks节点下）**，生成一个唯一的**临时有序节点**（就是以loks节点为父节点）。 判断是否 获取锁的方式很简单，只需要判断是否为有序节点中序号最小的一个，是，则获取到锁，不是则对前一个节点进行监听。 当释放锁的时候，只需将这个临时节点删除即可。同时，其可以避免服务宕机导致的锁无法释放，而产生的死锁问题（服务器宕机会将这个节点删除）。

基于zookeeper的分布式锁又分为**排他锁和共享锁**

**排他锁**，又称写锁或独占锁。如果事务T1对数据对象O1加上了排他锁，那么在整个加锁期间，只允许事务T1对O1进行读取或更新操作，其他任务事务都不能对这个数据对象进行任何操作，直到T1释放了排他锁。

定义锁：通过Zookeeper上的数据节点来表示一个锁

2）获取锁：客户端通过调用 create 方法创建表示锁的临时节点，可以认为创建成功的客户端获得了锁，同时可以让没有获得锁的节点在该节点上注册Watcher监听，以便实时监听到lock节点的变更情况

3）释放锁：以下两种情况都可以让锁释放

- 当前获得锁的客户端发生宕机或异常，那么Zookeeper上这个临时节点就会被删除
- 正常执行完业务逻辑，客户端主动删除自己创建的临时节点

![image-20220323143956152](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220323143956152.png)

**共享锁**，又称读锁。如果事务T1对数据对象O1加上了共享锁，那么当前事务只能对O1进行读取操作，其他事务也只能对这个数据对象加共享锁，直到该数据对象上的所有共享锁都被释放。

共享锁与排他锁的区别在于，加了排他锁之后，数据对象只对当前事务可见，而加了共享锁之后，数据对象对所有事务都可见。

1）定义锁：通过Zookeeper上的数据节点来表示一个锁，是一个类似于/lockpath/[hostname]-请求类型-序号的**临时顺序节点**

2）获取锁：客户端通过调用 create 方法创建表示锁的临时顺序节点，如果是读请求，则创建/lockpath/[hostname]-R-序号节点，如果是写请求则创建 /lockpath/[hostname]-W-序号节点

3）判断读写顺序：大概分为4个步骤

① 创建完节点后，获取 /lockpath 节点下的所有子节点，并对该节点注册子节点变更的Watcher监听

② 确定自己的节点序号在所有子节点中的顺序

③

对于读请求：

- 如果没有比自己序号更小的子节点，或者比自己序号小的子节点都是读请求，那么表明自己已经成功获取到了共享锁，同时开始执行读取逻辑
- 如果有比自己序号小的子节点有写请求，那么等待

对于写请求，**如果自己不是序号最小的节点**，那么等待

④ 接收到Watcher通知后，重复步骤①

4）释放锁：与排他锁逻辑一致

 

**（羊群效应）改进**：[基于Zookeeper实现分布式锁 - kosamino - 博客园 (cnblogs.com)](https://www.cnblogs.com/jing99/p/11607094.html)

![image-20220726163514589](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220726163514589.png)

## **master选举使用场景及结构**

选主原理介绍：Zookeeper的节点有两种类型，持久节点跟临时节点。临时节点有个特性，就是如果注册这个节点的机器失去连接（通常是宕机），那么这个节点会被zookeeper删除。选主过程就是利用这个特性，在服务器启动的时候，去zookeeper特定的一个目录下注册一个临时节点（这个节点作为master，谁注册了这个节点谁就是master），注册的时候，如果发现该节点已经存在，则说明已经有别的服务器注册了（也就是有别的服务器已经抢主成功），那么当前服务器只能放弃抢主，作为从机存在。同时，抢主失败的当前服务器需要订阅该临时节点的删除事件，以便该节点删除时（也就是注册该节点的服务器宕机了或者网络断了之类的）进行再次抢主操作。（从机具体需要去哪里注册服务器列表的临时节点，节点保存什么信息，根据具体的业务不同自行约定。）选主的过程，其实就是简单的争抢在zookeeper注册临时节点的操作，谁注册了约定的临时节点，谁就是master。

 

## zookeeper的watch机制？★ ☆★☆★

> 在 ZooKeeper 中，引入了 Watch 机制来实现了分布式的通知功能。ZooKeeper 允许客户端向服务端注册一个 Watch 监听，当服务端的一些事件触发了这个 Watch ，那么就会向指定客户端发送一个事件通知，来实现分布式的通知功能。

**ZooKeeper的Watch架构**

客户端先向ZooKeeper服务端成功注册想要监听的节点状态，就是注册一个watcher（其中客户端注册 watcher 有三种方式，调用客户端 API 可以分别通过 getData、exists、getChildren 实现），同时客户端本地会存储该监听器相关的信息（watcher对象）在WatchManager中，当ZooKeeper服务端监听的数据状态发生变化时，ZooKeeper就会主动通知发送相应事件信息给相关会话客户端，客户端线程从watchManager中回调watcher对象执行相应的功能。

![image-20220324092135223](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220324092135223.png)

 

> ***ZooKeeper的Watch特性***
>
> 1. Watch是一次性的，每次都需要重新注册，并且客户端在会话异常结束时不会收到任何通知，而快速重连接时仍不影响接收通知。
>
> 2. Watch的回调执行都是顺序执行的，并且客户端在没有收到关注数据的变化事件通知之前是不会看到最新的数据，另外需要注意不要在Watch回调逻辑中阻塞整个客户端的Watch回调
>
> 3. Watch是轻量级的，**WatchEvent**是最小的通信单元，结构上只包含通知**状态、事件类型**和节点路径。ZooKeeper服务端只会通知客户端发生了什么，并不会告诉具体内容。

 

   下表列举了常见的连接状态和事件类型

![image-20220323153012451](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220323153012451.png)

 

## zookeeper的发布订阅功能

**发布订阅基本概念**

**发布订阅模式可以看成一对多的关系**：多个订阅者对象同时监听一个主题对象，这个主题对象在自身状态发生变化时，会通知所有的订阅者对象，使他们能够自动的更新自己的状态。

发布订阅模式在分布式系统的典型应用有：**配置管理和服务发现**。

**配置管理：**是指如果集群中机器拥有某些相同的配置，并且这些配置信息需要动态的改变，我们可以使用发布订阅模式，对配置文件做统一的管理，让这些机器各自订阅配置文件的改变，当配置文件发生改变的时候这些机器就会得到通知，把自己的配置文件更新为最新的配置

**服务发现：**是指对集群中的服务上下线做统一的管理，每个工作服务器都可以作为数据的发布方，向集群注册自己的基本信息，而让模型机器作为订阅方，订阅工 作服务器的基本信息，当工作服务器的基本信息发生改变时如上下线，服务器的角色和服务范围变更，监控服务器就会得到通知，并响应这些变化。

 

## Zookeeper 读写数据流程 ★ ☆★☆★

### 读流程

当Client向zookeeper发出读请求时，无论是Leader还是Follower，都直接返回查询结果。

**Zookeeper并不保证读取的是最新数据**

如果是对zk进行读取操作，在follower上读取到的数据可能是过期的旧数据，不是最新的数据。

想要数据强一致 客户端应该调用zk api的sync方法 强制从leader节点读取

### 写流程

zookeeper写入操作分为两种情况，① 写入请求直接发送到leader节点，② 写入请求发送到Follower节点，这两种情况有略微的区别。

**写入请求直接发送到Leader节点时的操作步骤如下：**

- 1.Client向Leader发出写请求。
- 2.Leader将数据写入到本节点，并将数据发送到所有的Follower节点；
- 3.等待Follower节点返回ACK；
- 4.当Leader接收到一半以上节点(包含自己)返回写成功的信息之后，返回写入成功消息给client;

**写入请求发送到Follower节点的操作步骤如下：**

- 1.Client向Follower发出写请求
- 2.Follower节点将请求转发给Leader
- 3.Leader将数据写入到本节点，并将数据发送到所有的Follower节点
- 4.等待Follower节点返回ACK
- 5.当Leader接收到一半以上节点(包含自己)返回写成功的信息之后，返回写入成功消息给原来的Follower
- 6.原来的Follower返回写入成功消息给Client

 

## Paxos算法及其与ZAB的联系和区别？

Paxos算法是分布式技术大师Lamport提出的，主要目的是通过这个算法，让参与分布式处理的每个参与者逐步达成一致意见。用好理解的方式来说，就是在一个选举过程中，让不同的选民最终做出一致的决定。

在Paxos算法中，有三种角色：

Proposer
Acceptor
Learners
在具体的实现中，一个进程可能 同时充当多种角色 。比如一个进程可能 既是Proposer又是Acceptor又是Learner 。Proposer负责提出提案，Acceptor负责对提案作出裁决（accept与否），learner负责学习提案结果。

**为了避免单点故障，会有一个Acceptor集合，Proposer向Acceptor集合发送提案，Acceptor集合中的每个成员都有可能同意该提案且每个Acceptor只能批准一个提案，只有当一半以上的成员同意了一个提案，就认为该提案被选定了。**

Paxos的目标：保证最终有一个value会被选定，当value被选定后，进程最终也能获取到被选定的value。

### 提议过程

**Prepare阶段：**

**Proposer**会选择一个提案，并且编号为**M0**,然后向**Acceptor**集合中发送**M0**编号的**Prepare**请求，如果这个时候**Acceptor**集合中的某个**Acceptor**收到了这个请求，并且编号**M0**比当前已经相应的所有的提案的最大编号还要大，那么**Acceptor**就需要反馈自己处理的最大编号，并且不会再去响应低于**M0**编号的任何请求。如果没有响应过请求，则会直接响应当前的**M0**编号的请求。

**Accept阶段:**

同样的，当**Proposer**发出的提案请求收到了来自整个**Acceptor**集合中的过半**Acceptor**的响应，那么就代表该提案可以生成，这个时候如果响应中过半是无任何提案信息的，则代表当前的提案的取值可以是任意值，如果响应中过半是其他的提案信息，那么则从中找到最大编号的提案的值，这里称为**V0**，组成**[M0,V0]**的**Acceptor**请求，再次发送给整个**Acceptor**集合。这个时候**Acceptor**如果没有通过大于**[M0,V0]**编号的提案，那么则会视为自动同意该提案，同样如果得到了过半数的同意，则当前提案视为通过。

当然在整个过程中，每个**Proposer**都有自己的周期定时生成不同的提案，并且严格按照上述过程运行，最终一定能保证算法的正确性，同样的，如果**Proposer**已经要生成更大编号的提案，**Accept**将收到的最大的编号信息通知给上一个同意的最大提案的**Proposer**，让其放弃自己的提案，选择最新的最大编号的提案即可。

### 联系

1. **过半原则**

### 区别

> 1. Paxos算法中，新选举产生的主进程会进行两个阶段的工作；第一阶段称为读阶段：新的主进程和其他进程通信来收集主进程提出的提议，并将它们提交。第二阶段称为写阶段：当前主进程开始提出自己的提议。
> 2. ZAB协议在Paxos基础上添加了同步阶段，此时，新的Leader会确保存在过半的Follower已经提交了之前Leader周期中的所有事物Proposal。这一同步阶段的引入，能够有效保证，Leader在新的周期中提出事务Proposal之前，所有的进程都已经完成了对之前所有事务Proposal的提交。

总的来说，ZAB协议和Paxos算法的本质区别在于两者的设计目的不一样：ZAB协议主要用于构建一个高可用的**分布式数据主备系统**，而Paxos算法则用于构建一个**分布式的一致性状态机系统**。

 

# Spark

## 介绍下spark/定义及特点

spark是一个分布式的数据处理的统一计算引擎，Spark不仅仅可以做类似于MapReduce的离线数据计算，还可以做实时数据计算，并且它还可以实现类似于Hive的SQL计算，等等，所以说它是一个统一的计算引擎

特点：

- 速度快（基于内存）、
- 易用性（Spark支持Java、Python和Scala的API）、
- 通用性（Core、SQL、Streaming、MLlib、GraphX），其中，spark core是用于离线批处理，spark streaming实时流处理，spark SQL是类sql，MLIB是机器学习框架，GraphX是图计算；
- 兼容性：你可以在Hadoop YARN、Mesos或Kubernetes上使用Spark集群。

 

## spark和MR对比 ★★★★★

- **spark既可以做离线计算， 又可以做实时计算，hadoop只能做离线计算**

- **Spark处理数据是基于内存的，而MapReduce是基于磁盘处理数据的。**

  MapReduce是将中间结果保存到磁盘中，减少了内存占用，牺牲了计算性能。Spark是将计算的中间结果保存到内存中，提高了处理数据的性能。

- **Spark在处理数据时构建了DAG有向无环图，减少了shuffle和数据落地磁盘的次数**。

  多个MR只能 串联，且MR任务之间基于磁盘交互，迭代计算效率低下；而Spark 拥有高效的调度算法，是基于 DAG有向无环图的 计算，多个任务间的通信基于内存  ，同时减少了shuffle和数据落地磁盘的次数（遇到shuffle算子才会有shuffle、spark只有在shuffle时落地磁盘，MR shuffle和多任务之间都要落地）。

- **Spark** **容错性高**

  Spark 引进了弹性分布式数据集 RDD (Resilient DistributedDataset) 的抽象，它是分布在一组节点中的只读对象集合，这些集合是弹性的，如果数据集一部分丢失，则可以根据“血统”（即允许基于数据衍生过程）对它们进行重建。另外在RDD 计算时可以通过 CheckPoint 来实现容错。而MapReduce的容错可能只能重新计算，成本较高。

- **Spark** **更加通用**

  mapreduce 只提供了Map和Reduce两种操作，Spark提供的数据集操作类型有很多，大致分为：Transformations和Actions两大类。Transformations包括Map、Filter、FlatMap、GroupByKey、 ReduceByKey等多种操作类型，Actions包括reduce、collect、count、save、aggregate等操作。此外spark支持SQL、图论、机器学习;

-  **Spark是粗粒度资源申请，而MapReduce是细粒度资源申请**

  粗粒度申请资源指的是在提交资源时，spark会提前向资源管理器（yarn，mess）将资源申请完毕，如果申请不到资源就等待，如果申请到就运行task任务，而不需要task再去申请资源。 MapReduce是细粒度申请资源，提交任务，task自己申请资源自己运行程序，自己释放资源，虽然资源能够充分利用，但是这样任务运行的很慢

 

## Spark 为什么比MapReduce 快？ ★★★★★

1. **Spark 是基于内存计算，MapReduce 是基于磁盘运算**；MapReduce是将中间结果保存到磁盘中，减少了内存占用，牺牲了计算性能。Spark是将计算的中间结果保存到内存中，提高了处理数据的性能
2. **Spark 拥有高效的调度算法，是基于 DAG有向无环图的** , 多个任务之间的通信基于内存，且在计算过程中**减少了shuffle以及落地磁盘的次数**，而多个MR只能串联，多个任务之间基于磁盘交互，效率低下。（Main）
3. **Spark 是通过 RDD 算子来运算的**，拥有缓存功能，可以将先运算的结果cache在内存中，之后可进行复用
4. Spark RDD还拥 Linage血缘机制，数据丢失或出错可基于Linage血缘关系重算数据；另外在RDD 计算时可以通过 CheckPoint 来实现容错

 

## spark 和hadoop的区别 ★★★★★

1） 数据存储和处理的区别
        Hadoop是一个综合性质的大数据处理框架，包含HDFS(分布式存储)将巨大的数据集分派到一个由普通计算机组成的集群中的多个节点进行存储，降低硬件的成本，包含MapReduce计算引擎可进行数据计算，只能进行离线批处理，此外还有Yarn资源管理功能

Spark 是一个专门用来对那些分布式存储的大数据进行处理的工具，可以进行离线和实时处理，**但是没有提供文件管理系统，自身不会进行数据的存储**。它必须和其他的分布式文件系统进行集成才能运作。可以选择Hadoop的HDFS , 也可以选择其他平台。

2）**计算模型不同**与**处理速度**不同

spark可以通过DAG有向无环图，轻松实现复杂迭代计算，而Hadoop中的MapReduce任务只包含Map和Reduce阶段，多任务之间只能串联，不够灵活；

Spark 任务的数据是基于内存的，而Hadoop中MapReduce 任务是基于磁盘的

> hadoop的MapReduce是分步对数据进行处理的，从磁盘中读取数据，进行一次处理，将结果写到磁盘，然后在从磁盘中读取更新后的数据，再次进行的处理，最后再将结果存入磁盘，这存取磁盘的过程会影响处理速度。spark从磁盘中读取数据，把中间数据放到内存中，完成所有必须的分析处理，将结果写回集群，所以spark更快。

3）灾难恢复

Hadoop将每次处理后的数据都写入到磁盘上，对应对系统错误具有天生优势。Spark的数据对象存储在弹性分布式数据集 RDD，RDD是分布在一组节点中的只读对象集合，如果数据集一部分丢失，则可以根据于血缘机制对它们进行重建。而且RDD 计算时可以通过 CheckPoint 来实现容错。

 

## **是不是用了Spark就不需要Hadoop了？**

不是，Spark和Hadoop各有其长处。

- Hadoop和Spark两者都是大数据框架，但是各自应用场景是不同的。Hadoop可以作为一个分布式数据存储架构，它将巨大的数据集分派到一个由普通计算机组成的集群中的多个节点进行存储，降低了硬件的成本。Spark是那么一个专门用来对那些分布式存储的大数据进行处理的工具，可以借助hdfs做数据存储。两者完全可以结合在一起，Hadoop提供分布式集群和分布式文件系统，Spark依附在Hadoop的 HDFS，代替MapReduce弥补MapReduce计算能力不足的问题。
- 此外hadoop的yarn资源管理引擎同样出色，其他大数据框架经常以yarn作为他的资源管理引擎；
- 低成本，对处理速度没什么要求的场景，hadoop还是会被优先考虑的

 

## **Spark和Hive的区别**

> 字节

**1、Hive**

Hive是基于Hadoop的数据仓库工具，同时又是查询引擎，Spark SQL只是取代的Hive的查询引擎这一部分，企业可以使用Hive+Spark SQL进行开发。

Hive的主要工作如下：

把HQL翻译长map-reduce的代码，并且有可能产生很多mapreduce的job

把生产的Mapreduce代码及相关资源打包成jar并发布到Hadoop的集群当中并进行运行

Hive默认情况下用derby存储元数据，所以在生产环境下一般会采用多用户的数据库进行元数据的存储，并可以读写分离和备份，一般使用主节点写，从节点读，一般使用mysql

**2、Spark**

Spark SQL处理一切存储介质和各种格式的数据(可以扩展sparksql来读取更多类型的数据)；

Spark SQL把数据仓库的计算速度推向了新的高度（Tungsten成熟之后会更厉害）；

Spark SQL 推出的Dataframe可以让数据仓库直接使用机器学习，图计算等复杂算法；

**Hive+Spark SQL+DataFrame使用**：

Hive：负责廉价的数据仓库存储

Spark Sql：负责高速的计算

DataFrame：负责复杂的数据挖掘

**3、Hive on Spark与Spark Sql的区别**

Hive on Spark大体与Spark SQL结构类似，只是SQL解析器不同，但是计算引擎都是spark。

**4、Hive on Mapreduce和Spark SQL使用场景**

**Hive on Mapreduce场景**

Hive的出现可以让那些精通SQL技能、但是不熟悉MapReduce 、编程能力较弱与不擅长**Java**语言的用户能够在HDFS大规模数据集上很方便地利用SQL 语言查询、汇总、分析数据，毕竟精通SQL语言的人要比精通Java语言的多得多。

Hive适合处理离线非实时数据。

**Spark SQL场景**

Spark既可以运行本地local模式，也可以以Standalone、cluster等多种模式运行在Yarn、Mesos上，还可以运行在云端例如EC2。此外，Spark的数据来源非常广泛，可以处理来自HDFS、HBase、 Hive（Cassandra、Tachyon）上的各种类型的数据。

实时性要求或者速度要求较高的场所。

**5、Hive on Mapreduce和Spark SQL性能对比**

Spark SQL和Hive on Spark时间差不多，但都比Hive on mapreduce快很多，官方数据认为Spark会被传统mapreduce快10-100倍。

 

## **Spark的架构**

![image-20220326143853585](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326143853585.png)

**Cluster Manager**：在standalone模式中即为Master主节点，控制整个集群，监控worker。在YARN模式中为资源管理器

**Worker节点**：从节点，负责控制计算节点，启动Executor或者Driver。

**Driver**驱动器： Spark 驱动器节点，用于执行 Spark 任务中的 main 方法，负责实际代码的执行工作

**Executor**：执行器，是为某个Application运行在worker node上的一个进程，负责在 Spark 作业中运行具体任务（Task），任务彼此之间相互独立。

 

 

## **Spark** **的提交方式有哪些？** ★★★★★

1. Local 本地模式(单机)。分为 Local 单线程和 Local-Cluster 多线程。

2. Standalone 独立集群模式。 包含 Standalone 模式和 Standalone-HA 高可用模式。Standalone-HA 使用 Zookeeper 搭建高可用，避免单点故障问题。

3. Spark On Yarn 集群模式。运行在 Yarn 集群之上，由 Yarn 负责资源管理，Spark 负责任务调度和计算。Spark on YARN 模式根据 Driver 在集群中的位置分为两种模式：一种是 YARN Client 模式，另一种是 YARN-Cluster (或称为 YARN-Standalone 模式)。

   Yarn-Client模式中，Driver在客户端本地运行，这种模式可以使得Spark Application和客户端进行交互，适用于交互、调试，希望立即看到app的输出

   Yarn-Cluster模式中，Driver运行在ApplicationMaster中；适用于生产环境

好处：计算资源按需伸缩，集群利用率高，共享底层存储，避免数据跨集群迁移。

 

### **YARN-Client** **与** **YARN-Cluster** **区别**

> 理解YARN-Client和YARN-Cluster深层次的区别之前先清楚一个概念：Application Master。在YARN中，每个Application实例都有一个ApplicationMaster进程。它负责和ResourceManager打交道并请求资源，获取资源之后告诉NodeManager为其启动Container。从深层次的含义讲YARN-Cluster和YARN-Client模式的区别其实就是ApplicationMaster进程的区别。
>

YARN-Cluster模式下，Driver运行在AM(Application Master)中，它负责向YARN申请资源，并监督作业的运行状况。当用户提交了作业之后，就可以关掉Client，作业会继续在YARN上运行，因而YARN-Cluster模式不适合运行交互类型的作业；

YARN-Client模式下，Driver在客户端本地运行，Application Master仅仅向YARN请求Container(Executor运行在其中)，Client会和请求的Container通信来调度他们工作，也就是说Client不能离开。

 

>  **Spark的任务执行流程 **★★★★★
>
> 1）构建Application的运行环境，Driver创建一个SparkContext
>
> 2）SparkContext向资源管理器（Standalone、Mesos、Yarn）申请Executor资源，资源管理器启动 Executor(StandaloneExecutorbackend)
>
> 3）Executor向SparkContext申请Task
>
> 4）SparkContext将应用程序分发给Executor
>
> 5）SparkContext构建成DAG图，DAGScheduler将DAG图解析成Stage，每个Stage有多个task，形成taskset发送给task Scheduler，由task Scheduler将Task发送给Executor运行
>
> 6）Task在Executor上运行，运行完释放所有资源

 

## Spark提交一个任务的具体流程  ★★★★★★

![image-20220616100529931](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220616100529931.png)

> 上图为Spark通用运行流程图，体现了基本的Spark应用程序在部署中的基本提交流程。

1、任务在client提交后，会先向Master申请启动Driver

2）Master找一台满足资源的Worker节点，启动Driver

3）driver 执行main()方法， 初始化程序的入口：SparkContext；在SparkContext中初始化两个对象：DAG Scheduler，Task Scheduler

4）SparkContext向资源管理器申请Executor资源，资源管理器在一个worker节点中启动 Executor，excutor会向Driver反向注册，这样Driver就知道哪些Executor为他进行服务了

5）SparkContext将Applicaiton代码发送给Executor；并且SparkContext解析Applicaiton代码，构建DAG图，它以**懒执行**策略，遇到一个action算子触发job执行，形成一个完整的DAG，并提交给DAG Scheduler 根据**宽依赖**分解成Stage，每个Stage有多个task，形成taskset发送给task Scheduler，由task Scheduler遍历解析taskset将每一个Task发送给Executor运行

6）Task在Executor上运行，运行完释放所有资源

[Spark任务提交全流程（简述+全流程）_一个不会写代码的小黑的博客-CSDN博客_spark的任务提交流程](https://blog.csdn.net/qq_37332702/article/details/88687251)

 

> ##  standalone模式下的任务执行与调度流程
>
> 1)   我们提交一个任务，任务就叫Application；
>
> 2）初始化程序的入口SparkContext；
>
> - 初始化DAG Scheduler
> - 初始化Task Scheduler
>
> 3）Task Scheduler向master去进行注册并申请资源（CPU Core和Memory）；
>
> 4）Master根据SparkContext的资源申请要求和Worker心跳周期内报告的信息决定在哪个Worker上分配资源，然后在该Worker上获取资源，然后启动StandaloneExecutorBackend；顺便初始化好了一个线程池；
>
> 5）StandaloneExecutorBackend向Driver(SparkContext)注册，这样Driver就知道哪些Executor为他进行服务了。到这个时候其实我们的初始化过程基本完成了。
>
> 6）SparkContext将Applicaiton代码发送给StandaloneExecutorBackend；并且SparkContext解析Applicaiton代码，构建DAG图，并提交给DAG Scheduler分解成Stage（当碰到Action操作时，就会催生Job；每个Job中含有1个或多个Stage，Stage一般在获取外部数据和shuffle之前产生）；
>
> 7）将Stage（或者称为TaskSet）提交给Task Scheduler。Task Scheduler负责将Task分配到相应的Worker，最后提交给StandaloneExecutorBackend执行；
>
> > 8）对task进行序列化，并根据task的分配算法，分配task；
> >
> > 9）executor对接收过来的task进行反序列化，把task封装成一个线程；
>
> 10）开始执行Task，并向SparkContext报告，直至Task完成；
>
> 11）资源注销
>

 

## **YARN Cluster 模式下的执行流程**

- 在 YARN Cluster 模式下，任务提交后会和 ResourceManager 通讯申请启动ApplicationMaster，
- 随后 ResourceManager 分配 container，在合适的 NodeManager 上启动 ApplicationMaster，此时的 ApplicationMaster 就是 Driver。
- Driver 启动后 初始化程序的入口：SparkContext；在SparkContext中初始化两个对象：DAG Scheduler，Task Scheduler，然后向 ResourceManager 申请 Executor 内存，ResourceManager 接到ApplicationMaster 的资源申请后会分配 container，然后在合适的 NodeManager 上启动Executor 进程
- Executor 进程启动后会向 Driver 反向注册
- 之后执行到 Action 算子时，触发一个 Job，并根据宽依赖开始划分 stage，每个 stage 生成对应的 TaskSet，之后将 task 分发到各个 Executor 上执行。

>  和前面的具体流程只是 master不同；这里是ResourceManager ；
>

 

## **什么是** **RDD ? ** ★★★★★

RDD（Resilient Distributed Dataset）叫做弹性分布式数据集，是 Spark 中最基本的数据处理模型。代码中是一个抽象类，它代表一个弹性的、不可变、可分区、可并行计算的集合。RDD中并不装载真正要计算的数据，而装的是描述信息，描述以后从哪读取数据，调用了什么方法，传入了什么函数，以及依赖关系等。RDD是只读的，是不可以改变的，想要改变，只能产生新的 RDD

**弹性**

- 存储的弹性：内存与磁盘的自动切换；
- 容错的弹性：数据丢失可以自动恢复；
- 计算的弹性：计算出错重试机制；
- 分片的弹性：可根据需要重新分片。

> 分布式：数据存储在大数据集群不同节点上
>
> 数据集：RDD 封装了计算逻辑，并不保存数据
>
>  数据抽象：RDD 是一个抽象类，需要子类具体实现
>
> 不可变：RDD 封装了计算逻辑，是不可以改变的，想要改变，只能产生新的 RDD，在新的 RDD 里面封装计算逻辑
>
> 可分区、并行计算
>

 

### RDD的特性

一个RDD对象，包含如下5个核心属性

![image-20220326145750633](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326145750633.png)

​     1）一组分区，每个分区里是RDD的部分数据（或称数据块）。

  2）一个依赖列表：存储RDD之间的依赖关系；
  3）一个名为compute的计算函数，Spark在计算时，是使用分区函数对每一个分区进行计算
  4）分区器（可选），用于键/值类型的RDD，比如某个RDD是按散列来分区（自定义）。
  5）计算各分区时优先的位置列表（可选），比如从HDFS上的文件生成RDD时，RDD分区的位置优先选择数据所在的节点，这样可以避免数据移动带来的开销。

 

**RDD缓存和血缘机制**

如果在应用程序中多次使用同一个RDD，可以将该RDD缓存起来，该RDD只有在第一次计算的时候会根据血缘关系得到分区的数据，在后续其他地方用到该RDD的时候，会直接从缓存处取而不用再根据血缘关系计算，这样就加速后期的重用。

**RDD的CheckPoint**

虽然RDD的血缘关系天然地可以实现容错，当RDD的某个分区数据失败或丢失，可以通过血缘关系重建。但是对于长时间迭代型应用来说，随着迭代的进行，RDDs之间的血缘关系会越来越长，一旦在后续迭代过程中出错，则需要通过非常长的血缘关系去重建，势必影响性能。为此，RDD支持checkpoint将数据保存到持久化的存储中，这样就可以切断之前的血缘关系，因为checkpoint后的RDD不需要知道它的父RDDs了，它可以从checkpoint处拿到数据。

 

### RDD算子分类

 transformation  转换算子：调用转换算子会生成一个新的RDD，Transformation是**lazy**的，不会触发job执行。

action 动作算子，调用行动算子会触发job执行，行成一个完整的DAG

> 本质上是调用了sc.runjob方法；（生成DAG后就划分stage）该方法从最后一个RDD，根据其依赖关系，从后往前，划分stage，生成Task;

 

**(1)transformation** **操作常用算子如下：**

Map、MapPartitions、FlatMap、Filter、distinct、sortBy、union、reduceByKey、groupByKey、sortByKey、join

**(2)action** **操作常用算子如下：**

reduce、collect、count、save、take、aggregate、countByKey 等。

 

### **RDD底层原理**

> 问过的一些公司：携程
>

参考答案：

RDD是一个分布式数据集，顾名思义，其数据应该分部存储于多台机器上。事实上，每个RDD的数据都以Block的形式存储于多台机器上，下图是Spark的RDD存储架构图，其中每个Executor会启动一个 BlockManagerSlave，并管理一部分Block；而Block的元数据由Driver节点的BlockManagerMaster保存。BlockManagerSlave生成Block后向BlockManagerMaster注册该Block，BlockManagerMaster管理RDD与Block的关系，当RDD不再需要存储的时候，将向BlockManagerSlave发送指令删除相应的Block。

![image-20220326152927423](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326152927423.png)

 

### **RDD** **有哪些缺点？**

1. 不支持细粒度的写和更新操作（如网络爬虫）， spark 写数据是粗粒度的所谓粗粒度，就是批量写入数据，为了提高效率。但是读数据是细粒度的也就是说可以一条条的读。

2. 不支持增量迭代计算， Flink 支持

 

## 为什么要分transformation 算子和action算子  ★★★★★

Spark算子主要划分为两类：transformation和action，并且只有action算子触发的时候才会真正执行任务；这样有利于减少内存消耗，提高了执行效率。比如sc.textfile读数据时，并不会立刻将数据拉到内存；而是action时再拉取；

spark如果一遇到算子就触发任务的执行，那么DAG有向无环图将变得无意义

**多个任务的时候，变的和MR一样会有非常多的作业之间的通信**；

MapReduce的计算模型，涉及多个任务时，会有非常多的作业间通信，并且中间结果需要落地，导致性能相对Spark较低下，这也是MapReduce广为诟病的原因之一。所以Spark采用只有调用action算子时才会真正执行任务，这是相对于MapReduce的优化点之一； spark 将算子操作通过DAG有向无环图相连，**减小作业间的交互与通信，**提高效率；

> Spark会将多个map算子pipeline起来应用到RDD分区的每个数据元素上

举个例子 ：

1+1+1

MR：1+1=2（磁盘）  -->2+1=3;

spark :  1+1+1=3;  如果一遇到算子就触发任务的执行：1+1=2 （内存） 2+1=3

 

## **你知道** **reduceByKey** **和** **groupByKey** **有啥区别吗？**★★★

reduceByKey()会在 shuffle 之前对数据进行合并。有点类似于在 MapReduce 中的combiner。这样做的好处在于，在转换操作时就已经对数据进行了一次聚合操作，从而减小数据传输。并且 merge 操作可以通过函数自定义。

![image-20220326152427386](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326152427386.png)

groupByKey 算子操作发生在动作操作端，即 Shuffle 之后，所以势必会将所有的数据通过网络进行传输，造成不必要的浪费。同时如果数据量十分大，可能还会造成OutOfMemoryError。

![image-20220326152441402](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326152441402.png)

应用场景：reducebykey有一个聚合操作，groupbykey 分组而已，从功能上来说，groupbykey是reducebykey的一部分。

 

## **RDD** **的宽窄依赖了解吗？ **★★★★★

![image-20220326153633993](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220326153633993.png)

一个作业从开始到结束的计算过程中产生了多个 RDD，RDD 之间是彼此相互依赖的，这种父子依赖的关系称之为“血统”。

• 如果父 RDD 的每个分区最多只能被子 RDD 的一个分区使用，称之为**窄依赖（一对一）**。意味着父RDD的一个分区的数据是不能被分割的，子

RDD的任务可以和父RDD的任务在同一个Eexcutor一起执行，不需要经过shuffle阶段重组数据。

比如map，filter，union属于窄依赖

• 若一个父 RDD 的每个分区可以被子 RDD 的多个分区使用，称之为**宽依赖（一对多）**。意味着父RDD的一个分区的数据会被分割的，发送给子RDD的多个分区，因此宽依赖也意味着父RDD与子RDD之间存在着shuffle过程。

比如sort，reduceByKey，groupByKey，join，和调用rePartition函数的任何操作

 

## **RDD** **任务划分**  ★★★★★

RDD 任务切分中间分为：Application、Job、Stage 和 Task

- Application：初始化一个 SparkContext 即生成一个 Application；

- Job：Driver解析代码，触发一次Acition形成一 个完整的DAG, 一个DAG对应一 个Job；

- Stage：Job的子集，**以RDD宽依赖(即Shuffle)为界进行划分**，Stage 等于宽依赖(ShuffleDependency)的个数加 1；

  > 对于宽依赖，由于有Shuffle的存在，只能在parent RDD处理完成后，才能开始接下来的计算，因此宽依赖是划分Stage的依据。

- Task：Stage的子集，一个 Stage 阶段中，**最后一个 RDD 的分区个数就是 Task 的个数**。

 

## Spark任务划分过程+任务/作业调度+Stage划分与提交+Task调度与执行(源码)

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621153353334.png" alt="image-20220621153353334" style="zoom:80%;" />

Driver初始化SparkContext过程中，会分别初始化DAGScheduler、TaskScheduler、SchedulerBackend以及HeartbeatReceiver，并启动SchedulerBackend以及HeartbeatReceiver。SchedulerBackend通过ApplicationMaster申请资源，并不断从TaskScheduler中拿到合适的Task分发到Executor执行。HeartbeatReceiver负责接收Executor的心跳信息，监控Executor的存活状况，并通知到TaskScheduler。Spark的调度首先是Stage级的调度，然后是Task级的调度。

![image-20220621220735893](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621220735893.png)

* 当遇到一个Action操作后就会触发一个Job的计算，并交给DAGScheduler来提交。DAGScheduler负责Stage级的调度。Stage划分与提交过程如下：

  ![image-20220621171754045](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621171754045.png)

  它会根据RDD的血缘关系构成的DAG进行切分，将一个Job划分为若干Stages，具体划分策略是，由**最终的RDD**不断通过血缘依赖回溯(通过getShuffleDependencies方法)判断父依赖是否是宽依赖，是就创建一个stage；即以Shuffle为界，划分Stage，窄依赖的RDD都被划分到同一个Stage中，此类Stage称为ShuffleMapStage，可以进行pipeline数据管道式的计算。是中间的stage，为Shuffle生产数据。还有一类ResultStage，为DAG最后的Stage，应用action得出结果。
  一个Stage是否被提交，需要判断它的父Stage是否执行，只有在父Stage执行完毕才能提交当前Stage，如果一个Stage没有父Stage，那么从该Stage开始提交（getmissParentStage方法）。Stage提交时会将Task信息（主要是**分区信息**）序列化并被打包成TaskSet交给TaskScheduler，**一个Partition对应一个Task**。

  ![image-20220621213028458](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621213028458.png)

* TaskScheduler负责Task级的调度，将DAGScheduler给过来的TaskSet，封装为 TaskSetManager 加入到调度队列中。TaskSetManager 负责监控管理同一个 Stage 中的 Tasks， TaskScheduler 就是以 TaskSetManager 为单元来调度任务。TaskScheduler 支持两种调度策略，一种是 FIFO，也是默认的调度策略，另一种是 FAIR(公平调度策略：让实际运行 task 比例较少的TaskSetManager先执行)。

  ![image-20220621222831959](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621222831959.png)

  >     SchedulerBackend 是管资源的，同时它在启动后会定期地去询问 TaskScheduler 有没有任务要运行。当有任务需要运行时，TaskScheduler 会从调度队列中按照指定的调度策略选择 TaskSetManager 去调度运行。
  >

  ![image-20220621223217215](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621223217215.png)

  默认的FIFO策略将TaskSetManager加入rootPool调度池中之后，调用SchedulerBackend的riviveOffers方法给driverEndpoint发送ReviveOffer消息（就是取出任务的消息）；driverEndpoint收到取出任务的消息后调用makeOffers方法，将过滤出活跃状态的Executor的信息集合与调度池中的Tasks封装成WokerOffers对象传给了 scheduler.resourceoffers()方法；执行具体的任务取出逻辑；getSortedTaskSetQueue方法确定哪个TaskSetmanager先执行（两种队列有两种不同的调度算法） ，以及通过任务的本地级别判断将任务发送到哪个excutor等；

  ![image-20220922101920588](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220922101920588.png)

  > 本地化级别
  >
  > - 进程本地化：数据和计算在同一个进程
  >- 节点本地化
  > - 机架本地化
>- no_pref
  > - any

  然后调用launchTasks方法启动任务。launchTasks方法将遍历Tasks集合,对每个Task任务序列化，然后发送启动Task执行消息给 **指定的**（找到对应excutor的终端）Executor的onReceive方法。Executor收到后，将收到的Task序列化信息反序列化, 调用 Executor 的 launchTask 方法执行任务。launchTask内将Task提交到线程池去运行，TaskRunner是Runnable对象，里面的run方法执行了我们真正的运行逻辑；

 

## **为什么要划分Stage** ★★★★★

由于一个job任务中可能有大量的宽窄依赖，窄依赖不会产生shuffle，宽依赖会产生shuffle。

依据宽依赖后期划分完stage之后，在同一个stage中只有窄依赖，并没有宽依赖，这些窄依赖对应的task就可以相互独立的去运行而且可以在同一个excutor运行。也就是说划分完stage之后，它内部是有很多可以**并行运行**task，**且数据不落地到磁盘效率极高**。

 

## Spark中的一些重要概念

**Master**:  是一个Jave进程，接收Worker的注册信息和心跳、移除异常超时的Worker,接收客户端提交的任务、负责资源调度、命令Worker启动Executor
**Worker**: 是一个Java进程，负责管理当前节点的资源管理，向Master注册并定期发送心跳，负责启动Executor、并监控Executor的状态。
**Driver:** 是很多类的统称，可以认为SparkContext就是Driver,client模式Driver运行在SparkSubmit进程中，cluster模式单独运行在一个进程中，负责将用户编写的代码转成Tasks,然后调度到ExRecutor中执行，并监控Task的状态和执行进度。
**Executor:** 是一个Java进程， 负责执行Driver端生成的Task, 将Task放入线程中运行。
**Appliation** 使用SarkSubmit提交的个计算应用，一个Appication中可以触发多次Action, 触发一次Action产生一个Job,一个Application中可以有一 到多个Job
**Job:** Driver向Executor提交的作业，触发一次Acition形成一 个完整的DAG, 一个DAG对应一 个Job, 一个Job中有一 到多个Stage,一个Stage中有一到多个Task
**DAG:** 有向无环图，是对多个RDD转换过程和依赖关系的描述，触发Action就会形成一个完整的DAG，一个DAG对应一个Job
**Stage**: 任务执行阶段，Stage执行是有先后顺序的，先执行前的，在执行后面的，一个Stage对应一个TaskSet, 一个TaskSet中的Task的数量取决于Stage中最后一个RDD分区的数量；
**Task**: Spark中任务最小的执行单元， Task分 类两种，即ShuffleMapTask和ResultTask,Task其实就是类的实例， 有属性(从哪里读取数据)，有方法(如何计算)，Task的数量决定并行度， 同时也要考虑可用的cores
**TaskSet:**保存同一种计算逻辑多个Task的集合，一个TaskSet中的Task计算逻辑都一样，计算的数据不一样

 

##  Lineage 机制

相比其他系统的细颗粒度的内存数据更新级别的备份或者 LOG 机制， RDD 的 Lineage 记**录的是粗颗粒度的特定数据 Transformation 操作**（如 filter 、 map 、 join 等）行为。当这个 RDD 的部分分区数据丢失时，**它可以通过 Lineage 获取足够的信息来重新运算和恢复丢失的数据分区**。因为这种粗颗粒的数据模型，限制了 Spark 的运用场合，所以 Spark 并不适用于所有高性能要求的场景，但同时相比细颗粒度的数据模型，也带来了性能的提升。

 

##  RDD的缓存和checkpiont?  ★★★★★

- RDD 通过 **Cache 或者 Persist 方法将前面的计算结果缓存**，该 RDD 将会被缓存在计算节点的内存或磁盘中，并供后面重用但是并不是这两个方法被调用时立即缓存，而是**触发后面的 action 算子时**。


- 所谓的checkpiont检查点其实就是通过将 RDD 中间结果持久化，  血缘依赖过长会造成容错成本过高，这样就不如切断血缘依赖在中间阶段做检查点容错，如果检查点之后有节点出现问题，可以从检查点开始重做血缘，减少了开销。对 RDD 进行 checkpoint 操作并不会马上被执行，必须执行 **Action 操作才能触发**。


**持久化和检查点区别**

1）持久化只是将数据保存起来，**不切断血缘依赖**。Checkpoint **检查点切断血缘依赖**。

2）持久化 数据通常存储在磁盘、内存等地方，可靠性低。Checkpoint 的数据通常存储在 HDFS 等容错、高可用的文件系统，可靠性高。

cache和persist区别：

```
def cache(): this.type = persist()
```

cache()调用了persist()，再看一下persist函数：

```
def persist(): this.type = persist(StorageLevel.MEMORY_ONLY)
```

**cache只有一个默认的缓存级别MEMORY_ONLY** **，而persist可以根据情况设置其它的缓存级别**。

> **RDD持久化策略有哪些**
>
> MEMORY_ONLY            以非序列化的方式持久化在JVM内存中
> MEMORY_AND_DISK        同上，但是当某些partition无法存储在内存中时，会持久化到磁盘中
> MEMORY_ONLY_SER        同MEMORY_ONLY，但是会序列化
> MEMORY_AND_DISK_SER    同MEMORY_AND_DSK，但是会序列化
> DISK_ONLY            以非序列化的方式完全存储到磁盘上
> MEMORY_ONLY_2、MEMORY_AND_DISK_2等    尾部加了2的持久化级别，表示会将持久化数据复制一份，保存到其他节点
>
> 补充说明：
> MEMORY_ONLY：以非序列化的Java对象的方式持久化在JVM内存中。如果内存无法完全存储RDD所有的partition，那么那些没有持久化的partition就会在下一次需要使用它的时候，重新被计算。
>
> MEMORY_AND_DISK：当某些partition无法存储在内存中时，会持久化到磁盘中。下次需要使用这些partition时，需要从磁盘上读取，不需要重新计算
>
> MEMORY_ONLY_SER：同MEMORY_ONLY，但是会使用Java的序列化方式，将Java对象序列化后进行持久化。可以减少内存开销，但是在使用的时候需要进行反序列化，因此会增加CPU开销。
>
> MEMORY_AND_DISK_SER：同MEMORY_AND_DSK。但是会使用序列化方式持久化Java对象。
>
> DISK_ONLY：使用非序列化Java对象的方式持久化，完全存储到磁盘上。
>
> MEMORY_ONLY_2、MEMORY_AND_DISK_2等：如果是尾部加了2的持久化级别，表示会将持久化数据复制一份，保存到其它节点，从而在数据丢失时，不需要重新计算，只需要使用备份数据即可。
>

 

### 对需要checkpoint的RDD，先执行cache/persist，为什么呢？ ★★★★★

因为默认情况下，如果某个RDD没有持久化，但是设置了checkpoint，那么这个时候，遇到action算子触发checkpoint；**为保证数据的安全**，checkpoint会独立执行作业，就是说checkpoint会将这个RDD**前面的流程全部走一遍**，然后将得到的RDD写入外部存储，这样跟业务job互不影响，独立运行；

如果对需要checkpoint的rdd进行了缓存，那么后面进行checkpoint操作时，就会直接从内存/磁盘上读取rdd的数据了，就不需要重新再计算一次了，这样效率就高了。

 

## **Spark的哪些算子会有shuffle过程？**★★★★★

> 字节x2，作业帮，海康，触宝(2021.07)

**spark中会导致shuffle操作的有以下几种算子：**

**1、重分区类操作**

比如repartition、repartitionAndSortWithinPartitions、coalesce(shuffle=true)等。重分区一般会shuffle，因为需要在整个集群中，对之前所有的分区的数据进行随机，均匀的打乱，然后把数据放入下游新的指定数量的分区内。

**2、聚合、bykey类操作**

比如reduceByKey、groupByKey、sortByKey等。byKey类的操作要对一个key，进行聚合操作，那么肯定要保证集群中，所有节点上的相同的key，移动到同一个节点上进行处理。

**3、集合/表间交互操作**

比如join、cogroup等。两个rdd进行join，就必须将相同join key的数据，shuffle到同一个节点上，然后进行相同key的两个rdd数据的笛卡尔乘积。

**4、去重类操作**

如distinct。

> **5、排序类操作**
>
> 如sortByKey。

> **无shuffle操作的一些算子：**
>
> 如map，filter，union等。
>

 

## spark的shuffle过程  ★★★★★

**Shuffle 过程本质上都是将 Map 端获得的数据使用分区器进行划分，并将数据发送给对应的 Reducer 的过程。**

在spark中可以认为 **Shuffle Write 阶段 指的就是 Map Task  ，Shuffle Read 阶段 指的就是 Reduce Task 。**

Spark Shuffle 分为两种：一种是基于 Hash 的 Shuffle；另一种是基于 Sort 的 Shuffle。

> spark1.2以前默认是基于 hash的shuffle；之后是基于sort 的shuffle

**1、Hash Shuffle**

**1）未优化的HashShuffle**

在 Map Task 过程按照 Hash 的方式重组 Partition 的数据，不进行排序。每个 Map Task 为每个 Reduce Task 生成一个文件，通常会产生大量的文件（即对应为 M*R 个中间文件，其中 M 表示 Map Task 个数，R 表示 Reduce Task 个数），伴随大量的随机磁盘 I/O 操作与大量的内存开销。

![image-20220416110712456](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220416110712456.png)

**2) 优化后的HashShuffle**

优化的 HashShuffle 过程就是**启用合并机制**，合并机制就是复用 buffer，开启合并机制 的配置是 spark.shuffle.**consolidateFiles=true**，将 Mapper 端生成的中间文件进行合并，减少中间生成的文件数量。在同一个进程中，无论是有多少个Task，都会把同样的Key放在同一个Buffer里，然后把Buffer中的数据写入以**Core核心数量**为单位的本地文件中，通过文件合并，可以将中间文件的生成方式修改为**每个执行单位**（核数）为每个 Reduce 阶段的 Task 生成一个文件，那么总共文件数就是 核数*Reduce个数。

![image-20220416110816385](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220416110816385.png)

 

**2、sort Shuffle**

1）普通的sort Shuffle

在该模式下，数据会先写入一个数据结构，此时根据不同的shuffle算子，可以选用不同的数据结构。如果是有聚合操作的shuffle算子如reduceByKey ，就是用map的数据结构，边聚合边写入内存；如果是非聚合类 算子如join，就使用array的数据结构直接写入内存中。然后需要判断是否达到阈值，如果达到就会将内存数据结构的数据写入到磁盘，清空内存数据结构。

在溢写磁盘前，**先根据 key 进行排序**，排序过后的数据，会分批写入到磁盘文件中。默认批次为 10000 条，数据会以每批一万条写入到磁盘文件。写入磁盘文件通过缓冲区溢写的 方式，每次溢写都会产生一个磁盘文件，也就是说一个 Task 过程会产生多个临时文件。

最后在每个 Task 中，将所有的临时文件合并，**这就是 merge 过程**，此过程将所有临时文件读取出来，一次写入到最终文件。意味着一个(maptask) Task 的所有数据都在这一个文件中。同时单独写一份索引文件，标识下游各个Task的数据在文件中的索引，start offset和end offset

![image-20220416110438583](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220416110438583.png)

 

**2）bypass SortShuffle**

当（满足以下两个条件）

1) shuffle reduce task 数量小于等于 spark.shuffle.sort.bypassMergeThreshold 参数的值，默认 为 200。

2) 不是聚合类的 shuffle 算子（比如 reduceByKey） **就会触发bypass 运行机制**

> 不符合这两个条件就会排序（还是普通的sort Shuffle）

此时 task 会为每个 reduce 端的 task 都创建一个临时磁盘文件，并将数据按 key 进行 hash 然后根据 key 的 hash 值，将 key 写入对应的磁盘文件之中。当然，写入磁盘文件时也是先写入内存缓冲，缓冲写满之后再溢写到磁盘文件的。最后，同样会将所有临时磁盘文件 都合并成一个磁盘文件，并创建一个单独的索引文件。

该过程的磁盘写机制其实跟未经优化的 HashShuffleManager 是一模一样的，因为都要 创建数量惊人的磁盘文件，**只是在最后会做一个磁盘文件的合并而已**。因此少量的最终磁盘文件，也让该机制相对未经优化的 HashShuffleManager 来说，shuffle read 的性能会更好。

而该机制与普通 SortShuffleManager 运行机制的不同在于：**不会进行排序**。也就是说， 启用该机制的最大好处在于，shuffle write 过程中，不需要进行数据的排序操作，也就节省 掉了这部分的性能开销。

![image-20220416110603380](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220416110603380.png)

>  上面两种sorted都是一个maptask生成一个磁盘文件
>

 

## MR的shuffle和spark的shuffle的区别  ★★★

1. 功能上，MR的shuffle和Spark的shuffle是没啥区别的，都是对Map端的数据进行分区，要么聚合排序，要么不聚合排序，然后Reduce端或者下一个调度阶段进行获取数据，完成map端到reduce端的数据传输功能。
2. 方案上，有很大的区别，MR的shuffle是基于合并排序的思想，在数据进入reduce端之前，都会进行sort，为了方便后续的reduce端的全局排序，而Spark的shuffle是可选择的聚合，特别是1.2之后，**需要通过调用特定的算子才会触发排序聚合的功能**。
3. 流程上，MR的Map端和Reduce区分非常明显，两块涉及到操作也是各司其职，在 Spark 中，没有这样功能明确的阶段，只有不同的 stage 和一系列的 transformation，所以 spill, merge, aggregate 等阶段操作需要蕴含在 transformation中；
4. 数据拉取，MR的reduce是直接拉去Map端的分区数据，而Spark是根据索引读取，而且是在action触发的时候才会去读。

 

## **Spark** **广播变量和累加器介绍一下？** ★★★

在默认情况下，当 Spark 在集群的多个不同节点的多个任务上并行运行一个函数时，它会把函数中涉及到的每个变量，在每个任务上都生成一个副本。但是，**有时候需要在多个任务之间共享变量，或者在任务(Task)和任务控制节点(Driver Program)之间共享变量**。

为了满足这种需求，Spark 提供了两种类型的变量：

**累加器** **accumulators**：只写变量；累加器支持在所有不同节点之间进行累加计算(比如计数或者求和)。在driver端定义，在Excutor端更新，更新后传回driver端进行合并。

**广播变量** **broadcast variables**：只读变量；广播变量用来把变量在所有节点的内存之间进行共享，**在每个机器上缓存一个只读的变量**，而不是为机器上的每个任务都生成一个副本。适用于高效分发较大的对象。

 

## RDD、**DataFrame**、**DataSet**及其区别   ★★★

> 海康

**RDD**

RDD（Resilient Distributed Dataset）叫做**弹性分布式数据集**，是Spark中最基本的数据抽象。代码中是一个抽象类，它代表一个不可变、可分区、里面的元素可并行计算的集合。

**DataFrame**

- DataFrame是一种**以RDD为基础的分布式数据集，类似于传统数据库中的二维表格**。DataFrame与RDD的主要区别在于，**前者带有schema元信息，即DataFrame所表示的二维表数据集的每一列都带有名称和类型。**
- DataFrame每一行的类型固定为Row, 但是每一列的值没法直接访问，只有通过解析才能获取各个字段的值。

- **性能上比 RDD 要高**，主要原因是会对执行计划进行优化

**DataSet**

是Dataframe API的一个扩展，是Spark最新的数据抽象。它结合了RDD和DataFrame的优势

> 它提供了RDD的优势（强类型，使用强大的lambda函数的能力）以及Spark SQL优化执行引擎的优点。

- Dataset支持编解码器，当需要访问非堆上的数据时可以避免反序列化整个对象，提高了效率

- DataSet 和 DataFrame拥有完全相同的成员函数，区别只是每一行的数据类型不同。

- DataFrame其实就是DataSet的一个特例，DataFrame也可以叫DataSet[Row]，每一行类型是Row,每一行究竟有哪些字段，各个字段又是什么类型都无从得知，只能通过解析（用getAs方法或者模式匹配）拿出特定字段，而DataSet中，每一行是什么类型是不一定的，在自定义case class之后可以很自由的获取每一行的信息。

![image-20220616210435782](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220616210435782.png)

 

**共性**：

- RDD、DataFrame、DataSet 全都是 spark 平台下的分布式弹性数据集，为处理超大型数据提供便利;
- 三者都有惰性机制，在进行创建、转换，如 map 方法时，不会立即执行，只有在遇到Action 如 foreach 时，三者才会开始遍历运算;
- 三者有许多共同的函数，如 filter，排序等;
- 在对 DataFrame 和 Dataset 进行操作许多操作都需要这个包:import spark.implicits._（在创建好 SparkSession 对象后尽量直接导入）
- 三者都会根据 Spark 的内存情况自动缓存运算，这样即使数据量很大，也不用担心会内存溢出
- 三者都有 partition 的概念
- DataFrame 和 DataSet 均可使用模式匹配获取各个字段的值和类型

 

## Spark的map和flatmap的区别？

- Spark 中 map函数会对每一条输入进行指定的操作，**然后为每一条输入返回一个对象**；


- 而flatMap函数则是将处理的数据进行扁平化后再进行映射处理，所以算子也称之为**扁平映射**

  每个输入的元素可以被映射为1个或者多个输出的元素，原RDD与新RDD的**元素**是一对多的关系；

> 比如一行元素经过map只输出一行，而经过flatmap可能输出多行；只是最后将这多行的数据以一个可迭代的集合形式返回
>

 

## **你知道** **map** **和** **mapPartitions** **有啥区别吗？**

1. map：每次对 RDD 中的每一个元素进行操作；

2. mapPartitions：每次对 RDD 中的每一个分区的迭代器进行操作；

**mapPartitions** **优点：**

如果是普通的 map，比如一个 **Partition** 中有 1 万条数据。ok，那么你的 Function 要执行和计算 1 万次。

对于 mapPartitions 来说，一个 task 仅仅会执行一次 function，function 一次接收所有的 Partition 数据。只要执行一次就可以了，性能比较高。

如果在 map 过程中需要频繁创建额外的对象(例如将 rdd 中的数据通过 jdbc 写入数据库,map 需要为每个元素创建一个链接而 mapPartitions 为每个 partition 创建一个链接),则 mapPartitions 效率比 Map 高的多。SparkSql 或 DataFrame 默认会对程序进行 mapPartitions 的优化。

**mapPartitions** **的缺点：**

会造成内存溢出。

举例，对于 100 万数据，一次传入一个 function 以后，可能一下子内存不够，但是又没有办法腾出内存空间来，可能就 OOM，内存溢出。

 

## **你知道** **reduceByKey、foldByKey、aggregateByKey、combineByKey** 区别吗？

- reduceByKey  没有初始值  分区内和分区间逻辑相同

- foldByKey  有初始值  分区内和分区间逻辑相同

- aggregateByKey  有初始值  分区内和分区间逻辑可以不同

- combineByKey  初始值可以变化结构（发现数据结构不满足要求时，可以让第一个数据转换结构）  分区内和分区间逻辑不同

 

## **Spark数据倾斜问题，如何定位，解决方案**  ★★★★★

**1、数据倾斜**

Spark中的数据倾斜问题主要指shuffle过程中出现的数据倾斜问题，是由于不同的key对应的数据量不同导致的不同task所处理的数据量不同的问题

**数据倾斜俩大直接致命后果**

1）数据倾斜直接会导致一种情况：Out Of Memory

2）运行速度慢

**数据倾斜的表现：**

1）Spark作业的大部分task都执行迅速，只有有限的几个task执行的非常慢，此时可能出现了数据倾斜，作业可以运行，但是运行得非常慢

2）Spark作业的大部分task都执行迅速，但是有的task在运行过程中会突然报出OOM，反复执行几次都在某一个task报出OOM错误，此时可能出现了数据倾斜，作业无法正常运行

**定位数据倾斜问题：**

1）查阅代码中的shuffle算子，例如reduceByKey、sortbykey、groupByKey、join等算子，根据代码逻辑判断此处是否会出现数据倾斜

2）查看Spark作业的log文件，log文件对于错误的记录会精确到代码的某一行，可以根据异常定位到的代码位置来明确错误发生在第几个stage，对应的shuffle算子是哪一个；

 

### 解决方案

**一、聚合源数据**

**1）避免shuffle过程**

如果数据源是hive表；可通过Hive来进行数据预处理（即通过Hive ETL预先对数据按照key进行聚合，或者是预先和其他表进行join），然后在Spark作业中针对的数据源就不是原来的Hive表了，而是预处理后的Hive表。此时由于数据已经预先进行过聚合或join操作了，那么在Spark作业中也就不需要使用原先的shuffle类算子执行这类操作了。

**2）增大key粒度（减小数据倾斜可能性，增大每个task的数据量）**

**二：过滤导致倾斜的key**

如果我们判断那少数几个数据量特别多的key，对作业的执行和计算结果不是特别重要的话，那么干脆就直接过滤掉那少数几个key。

**三：提高shuffle操作的并行度**

增加shuffle read task的数量，可以让原本分配给一个task的多个key分配给多个task，从而让每个task处理比原来更少的数据。

**四：使用随机key实现双重聚合**

当**使用了类似于groupByKey、reduceByKey**这样的算子时，可以考虑使用随机key实现双重聚合

第一次是局部聚合，先给每个key都打上一个随机数。

第二次然后将各个key的前缀给去掉，再次进行全局聚合操作。

**五：将reduce join转换为map join**

正常情况下，join操作都会执行shuffle 过程，并且执行的是reduce join，也就是先将所有相同的key和对应的value汇聚到一个reduce task中，然后再进行join。

如果**join操作中的一个RDD或表的数据量比较小**，则可以使用Broadcast数据与map类算子达到与join同样的效果，也就是map join，进而完全规避掉shuffle类的操作，彻底避免数据倾斜的发生。

**六：sample采样对倾斜key单独进行join**

在Spark中，如果某个RDD只有一个key，那么在shuffle 过程中会默认将此key对应的数据打散，由不同的reduce端task进行处理，当由**单个key导致数据倾斜时**，可将发生数据倾斜的key单独提取出来，组成一个RDD，然后用这个原本会导致倾斜的key组成的RDD根其他RDD单独join，此时，根据Spark的运行机制，此RDD中的数据会在shuffle 阶段被分散到多个task中去进行join操作。

> 当数据量非常大时，可以考虑使用sample采样获取10%的数据，然后分析这10%的数据中哪个key可能会导致数据倾斜，然后将这个key对应的数据单独提取出来; **---如何知道哪个key倾斜**

 

**七：使用随机数以及扩容进行join**

RDD/Hive表中有**大量**key导致倾斜时；那么进行分拆key也没什么意义，此时就只能使用最后一种方案来解决问题了；查看RDD/Hive表中的数据分布情况，找到那个造成数据倾斜的RDD/Hive表。然后将该RDD的每条数据都打上一个n以内的随机前缀。同时对另外一个正常的RDD使用falt map进行扩容，将每条数据都扩容成n条数据，扩容出来的每条数据都依次打上一个n以内的随机数前缀；然后jion。

**使用扩容的方式只能缓解数据倾斜，不能彻底解决数据倾斜问题**

附：

- 当RDD中有几个key导致数据倾斜时，方案六不再适用，而方案七又非常消耗资源，此时可以引入方案七的思想完善方案六

![image-20220621215644750](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220621215644750.png)

 

## spark sql jion 分类/ 原理  ★★★

Hash join 和 sort-merge join ，其中，Hash join 又分为 Broadcast Hash join 和 Shuffle Hash join

    1 Hash join （适用于有小表的情况）
     
        确定Build Table（小表映射成hashtable） 以及 Probe Table（大表作为探测）
        Build table 根据join key构建hashtable，probe Table使用join key进行探测，探测成功就join在一起
        因为映射表要放入内存，经常访问到，所以采用小表映射
     
        1.1 Broadcast Hash Join（当有一个表很小时使用，一般小于10M）
     
            broadcast 阶段：把小表广播到大表的各个分区上，放在各个大表的的分区的内存中
            hash join阶段：小表映射成hashtable，大表作为probetable，然后根据key的hashcode进行join
     
        1.2 shuffle hash join（当小表也挺大的时候使用）
            小表比较大时，广播就不大合适了
            shuffle阶段：    将两个表按照join key进行分区，将相同join key的记录重分布到同一节点，这样两张表的数据就分布到各个节点
            hash join阶段：小表映射成hashtable，大表作为probetable，然后根据key的hashcode进行join
     
    2 sort-merge join （适用于两个表都很大的情况）
     
        分三步
        1：shuffle阶段：将两张大表根据join key进行重新分区，两张表数据会分布到整个集群，以便分布式并行处理
        2：sort阶段：    对单个分区节点的两表数据，分别进行排序
        3：merge阶段：    对排好序的两张分区表数据执行join操作。join操作很简单，分别遍历两个有序序列，碰到相同join key就merge输出，否则继续取更小一边的key
     
    优化，避免大表join，更多实现broadcast join
> 排序，这样去做等值比较的时候就不需要将某一方的全部数据都加载到内存进行计算了，只需要取一部分就能知道是否有相等的（比如按升序排列，某个值明显比它大了，后面肯定就不会有相等的，就不用继续比较了，节省了时间和内存），也就是在进行等值比较的时候即用即丢的。这个方法在前面进行排序的时候可能会消耗点时间，但相对于后面的时间来说，总体是大大节省了时间。

[Spark难点解析：Join实现原理 - 简书 (jianshu.com)](https://www.jianshu.com/p/97e76dddcbfb)

 

## Spark 性能调优  ★★★★★★

### **1、常规性能调优**

#### **1）最优资源配置**

Spark性能调优的第一步，就是为任务分配更多的资源，在一定范围内，增加资源的分配与性能的提升是成正比的，实现了最优的资源配置后，在此基础上再考虑进行后面论述的性能调优策略。

![image-20220625194634510](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220625194634510.png)

参数配置参考值：

- --num-executors：50~100
- --driver-memory：1G~5G
- --executor-memory：6G~10G
- --executor-cores：3
- --master：实际生产环境一定使用yarn

#### 2）RDD调优

**（1）RDD持久化**

在Spark中，当多次对同一个RDD执行算子操作时，每一次都会对这个RDD以之前的父RDD重新计算一次，这种情况是必须要避免的，对同一个RDD的重复计算是对资源的极大浪费，因此，必须对多次使用的RDD进行持久化，通过持久化将公共RDD的数据缓存到内存/磁盘中，之后对于公共RDD的计算都会从内存/磁盘中直接获取RDD数据。

**（2）RDD尽可能早的filter操作**

获取到初始RDD后，应该考虑尽早地过滤掉不需要的数据，进而减少对内存的占用，从而提升Spark作业的运行效率。

#### 3）并行度调节

Spark作业中的并行度指各个stage的task的数量。如果并行度设置不合理而导致并行度过低，会导致资源的极大浪费

**Spark官方推荐，task数量（也就是并行度）应该设置为Spark作业总CPU core数量的2~3倍**

#### 4）广播大变量

默认情况下，task中的算子中如果使用了外部的变量，每个task都会获取一份变量的复本，这就造成了内存的极大消耗；

广播变量在每个Executor保存一个副本，此Executor的所有task共用此广播变量，这让变量产生的副本数量大大减少。

#### 5）Kryo序列化

默认情况下，Spark使用Java的序列化机制。Java的序列化机制使用方便，不需要额外的配置，在算子中使用的变量实现Serializable接口即可，但是，Java序列化机制的效率不高，序列化速度慢并且序列化后的数据所占用的空间依然较大。

Kryo序列化机制比Java序列化机制性能提高10倍左右，Spark之所以没有默认使用Kryo作为序列化类库，是因为它不支持所有对象的序列化，同时Kryo需要用户在使用前注册需要序列化的类型，不够方便，但

从Spark 2.0.0版本开始，**简单类型、简单类型数组、字符串类型的Shuffling RDDs已经默认使用Kryo序列化方式了**。

 

### 2、算子调优

1）**mapPartitions**

mapPartition算子，由于一个task处理一个RDD的partition，那么一个task只会执行一次function， function一次接收所有的partition数据，效率比较高；

mapPartitions算子适用于数据量不是特别大的时候，此时使用mapPartitions算子对性能的提升效果还是不错的。（当数据量很大的时候，一旦使用mapPartitions算子，就会直接OOM）

2）**foreachPartition优化数据库操作**

通常使用foreachPartition算子来完成数据库的写入，通过foreachPartition算子的特性，可以优化写数据库的性能。如果使用foreach算子完成数据库的操作，由于foreach算子是遍历RDD的每条数据，因此，每条数据都会建立一个数据库连接，这是对资源的极大浪费，因此，对于写数据库操作，我们应当使用

foreachPartition算子。与mapPartitions算子非常相似，foreachPartition是将RDD的每个分区作为遍历对象，一次处理一个分区

的数据，也就是说，如果涉及数据库的相关操作，一个分区的数据只需要创建一次数据库连接；（同样数据量大是不适合）

> 3）**算子调优三：filter与coalesce、repartitionn的配合使用**
>
> 在Spark任务中我们经常会使用filter算子完成RDD中数据的过滤，在任务初始阶段，从各个分区中加载到的数据量是相近的，但是一旦进过filter过滤后，每个分区的数据量有可能会存在较大差异；
>
> - 每个partition的数据量变小了，如果还按照之前与partition相等的task个数去处理当前数据，有点浪费task的计算资源；
> - 每个partition的数据量不一样，会导致后面的每个task处理每个partition数据的时候，每个task要处理的数据量不同，这很有可能导致数据倾斜问题。
>
> 我们可以使用coalesce算子或者repatition算子重新规划分区；
>
> [(1条消息) repartition和coalesce的区别_敲代码的羊的博客-CSDN博客_coalesce repartition](https://blog.csdn.net/iyak78/article/details/122144214)

4）**reduceByKey预聚合**

reduceByKey相较于普通的shuffle操作一个显著的特点就是会进行map端的本地聚合，map端会先对本地的数据进行combine操作；

groupbykey则不会，因此在**某些场景下可将groupbykey替换成 reduceByKey**；

> 5）**repartion重分区解决SparkSQL低并行度问题**
>
> 并行度的设置对于Spark SQL是不生效的；

 

### 3、shuffle调优

**1）调节map端缓冲区大小**

在Spark任务运行过程中，如果shuffle的map端处理的数据量比较大，但是map端缓冲的大小是固定的，可能会出现map端缓冲数据频繁spill溢写到磁盘文件中的情况，使得性能非常低下，通过调节map端缓冲的大小，可以避免频繁的磁盘IO操作，进而提升Spark任务的整体性能。

**2）调节reduce端拉取数据缓冲区大小**

Spark shuffle过程中，shuffle reduce task的buffer缓冲区大小决定了reduce task每次能够缓冲的数据量，也就是每次能够拉取的数据量，如果内存资源较为充足，适当增加拉取数据缓冲区的大小，可以减少拉取数据的次数，也就可以减少网络传输的次数，进而提升性能。

**3）调节reduce端拉取数据重试次数**

Spark shuffle过程中，reduce task拉取属于自己的数据时，如果因为网络异常等原因导致失败会自动进行重试。对于那些包含了特别耗时的shuffle操作的作业，建议增加重试最大次数（比如60次），以避免由于JVM的full gc或者网络不稳定等因素导致的数据拉取失败。在实践中发现，对于针对超大数据量（数十亿~上百亿）的shuffle过程，调节该参数可以大幅度提升稳定性。

**4）调节reduce端拉取数据等待间隔**

Spark Shuffle过程中，reduce task拉取属于自己的数据时，如果因为网络异常等原因导致失败会自动进行重试，在一次失败后，会等待一定的时间间隔再进行重试，可以通过加大间隔时长（比如60s），以增加shuffle操作的稳定性。

**5）调节Sort-Shuffle排序操作阈值**

对于SortShuffleManager，如果Shuffle reduce task的数量小于某一阈值并且是非聚合类算子则Shuffle write过程中不会进行排序操作，而是直接按照未经优化的HashShuffleManager的方式去写数据，但是最后会将每个task产生的所有临时磁盘文件都合并成一个文件，并会创建单独的索引文件。当你使用SortShuffleManager时，如果的确不需要排序操作，那么建议将这个参数调大一些，大于Shuffle read task的数量，那么此时map-side就不会进行排序了，减少了排序的性能开销，但是这种方式下，依然会产生大量的磁盘文件，因此Shuffle write性能有待提高

 

### 4、jvm调优

 

## **Spark Streaming是什么？**

Spark Streaming 用于流式数据的处理；Spark Streaming 支持的数据输入源很多，例如：Kafka、Flume等等。数据输入后可以用 Spark 的高度抽象原语如：map、reduce、join、window 等进行运算。而结果也能保存在很多地方，如 HDFS，数据库等。

Spark Streaming 使用离散化流(discretized stream)作为抽象表示，叫作 DStream。DStream 是随时间推移而收到的数据的序列。在内部，每个时间区间收到的数据都作为 RDD 存在，而 DStream 是由这些 RDD 所组成的序列(因此得名“离散化”)。所以简单来将，DStream 就是对 RDD 在实时数据处理场景的一种封装。

**所以：**

Spark Streaming 中的流式计算其实并不是真正的流计算，而是微批计算。Spark Streaming 把流式计算当做一系列连续的小规模批处理(batch)来对待（RDD）。Spark Streaming 接收输入数据流，并在内部将数据流按均匀的时间间隔分为多个较小的batch。然后再将这部分数据交由Spark引擎进行处理，处理完成后将结果输出到外部文件。------**Spark Streaming** **如何执行流式计算的?**

> # DStream
>
> DStream：Discretized Stream，离散流，Spark Streaming提供的一种高级抽象，**代表了一个持续不断的数据流**；
> DStream可以通过输入数据源来创建，比如Kafka、Flume，也可以通过对其他DStream应用高阶函数来创建，比如map、reduce、join、window；
>
> DStream的内部，其实是一系列持续不断产生的RDD，RDD是Spark Core的核心抽象，即，不可变的，分布式的数据集；所以简单来讲，DStream就是对RDD在实时数据处理场景的一种封装。
> **DStream中的每个RDD都包含了一个时间段内的数据；**

 

## **Saprk Streaming从Kafka中读取数据两种方式？**★

**一、基于** **Receiver** **的方式**

使用 Receiver 来获取数据。Receiver 是使用 Kafka 的高层次 Consumer API 来实现的，需要消费者连接Zookeeper来读取数据。是由Zookeeper来维护偏移量，不用我们来手动维护。receiver 从 Kafka 中获取的数据都是存储在 Spark Executor 的内存中的（如果突然数据暴增，大量 batch 堆积，很容易出现内存溢出的问题），然后 Spark Streaming 启动的 job 会去处理那些数据。 然而，在默认的配置下，这种方式可能会因为底层的失败而丢失数据。**如果要启用高可靠机制，让数据零丢失，就必须启用** **Spark Streaming** **的预写日志机制**（Write Ahead Log，WAL）。该机制会同步地将接收到的 Kafka 数据写入分布式文件系统（比如 HDFS）上的预写日志中。所以，当意外出现时，可以使用预写日志中的数据进行恢复。

**二、基于** **Direct** **的方式**

这种方式是在 Spark 1.3 中引入的，它会周期性地查询Kafka，来获得每个 topic+partition 的最新的 offset，从而定义每个 batch 的 offset 的范围。当处理数据的 job 启动时，就会使用 Kafka 的简单 consumer api 来获取Kafka 指定 offset 范围的数据。

**优点如下**：

- 简化并行读取：如果要读取多个 partition，不需要创建多个输入 DStream 然后对它们进行合并（ union 操作）。Spark 会创建跟 Kafka partition 一样多的 RDD partition，并且会并行从 Kafka 中读取数据。所以在 Kafka partition 和 RDD partition 之间，有一个一对一的映射关系。

- 高性能：如果要保证零数据丢失，在基于 receiver 的方式中，需要开启 WAL机制。这种方式其实效率低下，因为数据实际上被复制了两份，Kafka 自己本身就有高可靠的机制，会对数据复制一份，而这里又会复制一份到 WAL 中。而基于 direct 的方式不需要开启 WAL 机制，通过 Kafka 的副本进行恢复。 一次且仅一次的事务机制。

**三、对比：**

• 基于 receiver 的方式，是使用 Kafka 的高阶 API 来在 ZooKeeper 中保存消费过的 offset 的。这是消费 Kafka 数据的传统方式。这种方式配合着 WAL 机制可以保证数据零丢失的高可靠性，但是却无法保证数据被处理一次且仅一次，可能会处理两次。因为 Spark 和 ZooKeeper 之间可能是不同步的。

• 基于 direct 的方式，使用 kafka 的简单 api，Spark Streaming **自己就负责追踪消费的 offset**，并保存在 checkpoint 中。Spark 自己一定是同步的，因此可以保证数据是消费一次且仅消费一次。

**在实际生产环境中大都用** **Direct** **方式**

 

**spark streaming实现一致性语义**

[(1条消息) Kafka与Spark Streaming集成，如何保证exactly once语义_ylqdh的博客-CSDN博客](https://blog.csdn.net/weixin_43802014/article/details/103490116)

kafka derect API +中间计算过程基于RDD天然满足+幂等写入或者事务性写入

## SparkStreaming窗口函数的原理

窗口函数就是在原来的SparkStreaming计算批次大小的基础上再次进行封装，每次计算（就是一个窗口）多个批次的数据，同时还需要传递一个滑动步长的参数，用来设置当次计算任完成后下一次从什么地方开始计算。需要注意的是，滑动步长必须是采集周期（批处理时间间隔）大小的整数倍。

 

## Spark Streaming **背压机制了解吗？**

**问题：**

在默认情况下，Spark Streaming 通过 receivers (或者是 Direct 方式) 以生产者生产数据的速率接收数据。当 batch processing time > batch interval 的时候，也就是每个批次数据处理的时间要比 Spark Streaming 批处理间隔时间长；越来越多的数据被接收，但是数据的处理速度没有跟上，导致系统开始出现数据堆积，可能进一步导致 Executor 端出现 OOM 问题而出现失败的情况。

**解决办法：**

设置 spark.streaming.backpressure.enabled：ture；开启背压机制后 Spark Streaming 会根据延迟动态去 kafka 消费数据；

上限由 spark.streaming.kafka.maxRatePerPartition 参数控制，所以两个参数一般会一起使用

 

# Flink

## Flink基础

### **什么是** **Flink？描述一下**  ★★★

Flink 是一个以 **流** 为核心的高可用的分布式计算引擎。具备 **流批一体，**高吞吐、低延迟，高性能、容错能力，大规模复杂计算等特点；在 Flink 的世界观中，一切都是由流组成的，离线数据是有界的流；实时数据是一个没有界限的流。

是唯一一个同时支持高吞吐、低延迟，高性能的流式数据处理框架

**流批一体：**

之前的版本中，流处理和批处理其实是两个API; 流处理对应dataStream,批处理对应dataSet; 在创建 Flink 作业时，并**不能通过将两者混合**在一起来同时 利用 Flink 的所有功能。 现在Flink 支持两种关系型的 API，Table API 和 SQL。这两个 API 都是批处理和流处理统一的 API，这意味着在无边界的实时数据流和有边界的历史记录数据流上，关系型 API 会以相同的语义执行查询，并产生相同的结果，但是在底层还是会有Stream和set  API的选择；从长远来看，DataStream API应该通过*有界数据流*完全包含DataSet API。

**容错能力：**

在分布式系统中，硬件故障、进程异常、应用异常、网络故障等异常无处不在，Flink 引擎必须保证故障发生后 不仅可以 **重启** 应用程序，还要 **确保** 其内部状态保持一致，从最后一次正确的时间点重新出发

Flink 提供 **集群级容错** 和 **应用级容错** 能力

**集群级容错：** Flink 与 集群管理器紧密连接，如 YARN、Kubernetes（集群管理工具），当进程挂掉后，自动重启新进程接管之前的工作。同时具备 **高可用性 ，**可消除所有单点故障

**应用级容错：**Flink 使用 轻量级分布式快照，设计检查点（**checkpoint**）实现可靠容错。Flink 利用检查点特性，在框架层面 提供 **Exactly-once** 语义，即端到端的一致性，确保数据仅处理一次，不会重复也不会丢失，即使出现故障，也能保证数据只写一次。

 

### 组成架构（任务调度原理）--关于架构问题回答这一个 ★★★

**Client**：Flink 客户端是 Flink 提供的 CLI 命令行工具，用来提交 Flink 作业到 Flink 集群，在客户端中负责 StreamGraph (流图)和 JobGraph (作业图)的构建。

**JobManager**：JobManager 根据并行度将 Flink 客户端提交的 Flink 应用生成“执行图”（ExecutionGraph），分解为子任务，从资源管理器 ResourceManager 申请所需的计算资源，资源具备之后，开始分发任务到TaskManager 执行 Task，并负责应用容错，跟踪作业的执行状态，发现异常则恢复作业等。

**TaskManager**：TaskManager 接收 JobManage 分发的子任务，根据自身的资源情况管理子任务的启动、 停止、销毁、异常恢复等生命周期阶段。Flink 程序中必须有一个TaskManager。在 TaskManager 中资源调度的最小单位是 task slot。任务在具体的slot上执行；

> 一个TaskManager可以跟其它运行同一应用程序的TaskManager交换数据。

**资源管理器ResourceManager**

ResourceManager 负责 Flink 集群中的资源提供、回收、分配并管理 task slots。

**分发器Dispatcher**

Dispatcher 提供了一个 REST 接口，用来提交 Flink 应用程序执行，当一个应用被提交执行时，分发器就会启动并将应用移交给一个JobManager。它还运行 一个Flink WebUI 用来提供作业执行信息。

 

### **Flink**运行时的架构组件（client不属于运行时组件）

![image-20220524161536490](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220524161536490.png)

 

 

### **Flink 相比 Spark Streaming 有什么区别**

我认为最重要的区别：**Flink 是标准的实时处理引擎，基于事件驱动。而 Spark Streaming 是微批（Micro-Batch）的模型。**

**1. 架构模型**

Spark Streaming 在运行时的主要角色包括：Master、Worker、Driver（调度器）、Executor（执行器），

Flink 在运行时主要包含：Jobmanager、Taskmanager 、ResourceManager和Dispatcher。

**2. 任务调度**

Spark Streaming 连续不断的生成微小的数据批次，构建有向无环图 DAG，Spark Streaming 会依次创建 DStreamGraph、JobGenerator、JobScheduler。

Flink 根据用户提交的代码生成 StreamGraph，经过优化生成 JobGraph，然后 提交给 JobManager 进行处理，JobManager 会根据 JobGraph 生成 ExecutionGraph执行图，ExecutionGraph（执行图，物理层面） 是 Flink 调度最核心的数据结构， JobManager 根据 ExecutionGraph 对 Job 进行调度。

**3. 时间机制**

Spark Streaming 支持的时间机制有限，只支持 ’‘处理时间’‘。

Flink 支持了流处理程序在时间上的三个定义：事件时间、注入时间、处理时间。同时也支持 watermark 机制来处理滞后数据。

**4. 容错机制**

对于 Spark Streaming 任务，我们可以设置 checkpoint，然后假如发生故障并重启，我们可以从上次 checkpoint 之处恢复，但是这个行为只能使得数据不丢失，可能会重复处理，不能做到恰一次处理语义。 Flink 则使用了两阶段提交协议来解决这个问题。

什么是两阶段提交协议?

 

### flink的并行度？

一个特定算子的 子任务（subtask）的个数被称之为其并行度（parallelism）。

一般情况下，一个 stream 的并行度，可以认为就是其所有算子中最大的并行度

并行子任务的分配：

![image-20220310170521746](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220310170521746.png)

（上图并行度是4）

 

### **如何确定Flink任务的合理并行度？**

社招

task的parallelism可以在Flink的不同级别上指定。

四种级别是：**算子级别、执行环境（ExecutionEnvironment）级别、客户端（命令行）级别、配置文件（flink-conf.yaml）级别。**

- 每个operator、data source或者data sink都可以通过调用setParallelism()方法来指定并行度
- 运行环境的默认并发数可以通过调用setParallelism()方法来指定。env.setParallelism(3);运行环境的并发数可以被每个算子确切的并发数配置所覆盖。
- 对于客户端，并发参数可以通过-p来指定
- 影响所有运行环境的系统级别的默认并发度可以在./conf/flink-conf.yaml的parallelism.defaul项中指定。不建议。

当然，也可以设置最大的并行度，通过调用setMaxParallelism()方法来设置最大并发度。

Flink如何确定TaskManager个数：Job的最大并行度除以每个TaskManager分配的任务槽数。

Flink on YARN时，TaskManager的数量就是：max(parallelism) / yarnslots（向上取整）。

例如，一个最大并行度为10，每个TaskManager有两个任务槽的作业，就会启动5个TaskManager

 

### Flink的编程模型

Flink 应用程序主要由三部分组成，**源** Source、**转换** transformation、**目的地**sink。，Flink上运行的程序会被映射成“逻辑数据流”（dataflows），这些流式 dataflows 形成了有向图，以一个或多个源（source）开始，并以一个或多个目的地（sink）结束。

![image-20220310161546766](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220310161546766.png)

dataflows：“逻辑数据流”，**每一个dataflow以一个或多个sources开始以一个或多个sinks结束**。dataflow类似于任意的有向无环图（DAG）

 

### 分区策略?

说几个就行

StreamPartitioner是 Flink 中的数据流分区抽象接口，决定了在实际运行中的数据流分发模式， 将数据切分交给 Task 计算，每个Task 负责计算一部分数据流。所有的数据分区器都实现了ChannelSelector 接口，该接口中定义了**负载均衡选择行为**。

**（1）GlobalPartitioner**

数据会被分发到下游算子的第一个实例中进行处理。

**（2）ForwardPartitioner**

在 API 层面上 ForwardPartitioner 应用在 DataStream 上，生成一个新的DataStream。 该 Partitioner 比较特殊，用于在同一个 OperatorChain 中上下游算子之间的数据转发，实际上数据是直接传递给下游的，要求上下游并行度一样。

**（3）ShufflePartitioner**

随机的将元素进行分区，可以确保下游的 Task 能够均匀地获得数据，使用代码如下：dataStream.shuffle();

**（4）RebalancePartitioner**

以 Round-robin（轮询）的方式为每个元素分配分区，确保下游的 Task 可以均匀地获得数据，避免数据倾斜。使用代码如下：dataStream.rebalance();

**(5)RescalePartitioner**

根据上下游 Task 的数量进行分区， 使用 **Round-robin** 选择下游的一个 Task 进行数据分区，如上游有 2 个 Source.，下游有 6 个 Map，那么每个 Source 会分配3 个固定的下游 Map，不会向未分配给自己的分区写人数据。这一点与ShufflePartitioner 和 RebalancePartitioner 不同， 后两者会写入下游所有的分区。

运行代码如下：dataStream.rescale();

**(6)BroadcastPartitioner**

将该记录广播给所有分区，即有 N 个分区，就把数据复制 N 份，每个分区 1 份，

其使用代码如下：dataStream.broadcast();

**（7）KeyGroupStreamPartitioner**

在 API 层面上，KeyGroupStreamPartitioner 应用在 KeyedStream 上，生成一个新的 KeyedStream。KeyedStream 根据 keyGroup 索引编号进行分区，会将数据按 Key 的 Hash 值输出到下游算子实例中。该分区器不是提供给用户来用的。

KeyedStream 在构造 Transformation 的时候默认使用 KeyedGroup 分区形式，从而在底层上支持作业 Rescale 功能。

**（8）CustomPartitionerWrapper**

用户自定义分区器。需要用户自己实现 Partitioner 接口，来定义自己的分区逻辑。

 

### **描述一下** **Flink wordcount** **执行包含的步骤有哪些？**

主要包含以下几步：

（1）获取运行环境 StreamExecutionEnvironment

（2）接入 source 源

（3）执行转换操作，如 map()、flatmap()、keyby（）、sum()

（4）输出 sink 源  如 print()

（5） 执行 execute

 

### **Flink** **常用的算子有哪些？**

分两部分：

1. **数据读取的算子**，这是 Flink 流计算应用的起点，常用算子有：

- 从内存读：fromElements
- 从文件读：readTextFile
- Socket 接入 ：socketTextStream
- 自定义读取：createInput

2. **处理数据的算子**，常用的算子包括：Map（单输入单输出）、FlatMap（单 输入、多输出）、Filter（过滤）、KeyBy（分组）、Reduce（聚合）、 Window（窗口）、Connect（连接）、Split（分割）等。

 

### Flink中的数据传输形式（算子之间的数据传输形式）？

一个程序中，不同的算子可能具有不同的并行度

算子之间传输数据的形式可以是 one-to-one (forwarding) 的模式也可以是redistributing 的模式，具体是哪一种形式，取决于算子的种类

➢ One-to-one：stream维护着分区以及元素的顺序（比如source和map之间）。 这意味着map 算子的子任务看到的元素的个数以及顺序跟 source 算子的子任务生产的元素的个数、顺序相同。map、fliter、flatMap等算子都是one-to-one的对应关系。

➢ Redistributing：stream的分区会发生改变。每一个算子的子任务依据所选择的transformation发送数据到不同的目标任务。例如，keyBy 基于 hashCode 重分区、而 broadcast 和 rebalance 会随机重新分区，这些算子都会引起redistribute过程，而 redistribute 过程就类似于 Spark 中的 shuffle 过程。

 

## Flink核心

### Flink四大基石

Flink之所以能这么流行，离不开它最重要的四个基石：**Checkpoint**、**State**、**Time**、**Window**。

 

### **Flink的窗口了解哪些，都有什么区别，有哪几种？如何定义？**

窗口（window）就是将无限流切割为有限流的一种方式，flink的window可分为时间窗口和计数窗口。

**时间窗口（Time Window）** **：按照时间标准生成的Window。**

- 滚动时间窗口
- 滑动时间窗口

**计数窗口（Count Window）： 按照指定的数据条数生成一个Window，与时间无关。**

-  滚动计数窗口

-  滑动计数窗口

**滚动窗口（Tumbling Window）：**

如果是滚动时间窗口的话就是以固定的时间创建窗口；如果是滚动计数窗口的话就是以固定的数据量创建窗口         **特点：窗口长度固定，没有重叠。**

**滑动窗口（Sliding Window）：**

滑动窗口由**固定的窗口长度**（size）和 **滑动间隔**(inteval)组成。size和inteval单位如果是时间那就是滑动时间窗口，如果是数据量那就是滑动计数窗口       **特点：窗口长度固定，可以有重叠(当inteval<size时)。**

**会话窗口** **SessionWindows**:

session 窗口分配器通过 session 活动来对元素进行分组，一个 session 窗口通过一个 session 间隔来配置，这个 session 间隔定义了非活跃周期的长度，在这个间隔内没有数据到来，就会关闭这个窗口。后续数据进入新的窗口。session 窗口跟滚动窗口和滑动窗口相比，不会有重叠和固定的开始时间和结束时间的情况（没有固定的长度）。

 

**Window API**

- DataStream.window(); 可以传入基于时间的window，和会话窗口（需要给一个间隔）
- DataStream.countwindow(); 定义计数窗口

**窗口函数**

window function 定义了要对窗口中收集的数据做的计算操作，主要可以分为两类：

- **增量聚合函数**（incremental aggregation functions）

  每条数据到来就进行计算，保持一个简单的状态。典型的增量聚合函数有ReduceFunction， AggregateFunction。

- **全窗口函数**（full window functions）

  先把窗口所有数据收集起来，等到计算的时候会遍历所有数据。ProcessWindowFunction 就是一个全窗口函数。

**其它可选API**

trigger() —— 触发器

- 定义 window 什么时候关闭，触发计算并输出结果

evitor() —— 移除器

- 定义移除某些数据的逻辑

allowedLateness() —— 允许处理迟到的数据

sideOutputLateData() —— 将迟到的数据放入侧输出流

getSideOutput() —— 获取侧输出流

 

### **介绍下Flink的窗口机制以及各组件之间是如何相互工作的**？

1. Flink 中定义一个窗口主要需要的三个组件。

   **Window Assigner**：用来决定某个元素被分配到哪个/哪些窗口中去。

   **Trigger：触发器**。决定了一个窗口何时能够被计算或清除，每个窗口都会拥有一个自己的Trigger。

   **Evictor**：可以译为“驱逐者”。在Trigger触发之后，在窗口被处理之前，Evictor（如果有Evictor的话）会用来剔除窗口中不需要的元素，相当于一个filter。

   ![image-20220311153648797](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220311153648797.png)

   1. 首先上面中的组件都位于一个算子（window operator）中，数据流源源不断地进入算子，每一个到达的元素都会被交给 WindowAssigner。**WindowAssigner 会决定元素被放到哪个或哪些窗口**（window），可能会创建新窗口。因为一个元素可以被放入多个窗口中，所以同时存在多个窗口是可能的。注意，Window 本身只是一个ID标识符，其内部可能存储了一些元数据，如 TimeWindow 中有开始和结束时间，但是并不会存储窗口中的元素。窗口中的元素实际存储在 Key/Value State 中，key为 Window ， value为元素集合（或聚合值）。为了保证窗口的容错性，该实现依赖了 Flink 的 State 机制。

   2. 每一个窗口都拥有一个属于自己的 Trigger，Trigger上会有定时器，用来决定一个窗口何时能够被计算或清除。每当有元素加入到该窗口，或者之前注册的定时器超时了，那么Trigger都会被调用。**Trigger的返回结果可以是  continue（不做任何操作），fire（处理窗口数据），purge（移除窗口和窗口中的数据），或者 fire + purge（触发计算+清理，处理数据并移除窗口和窗口中的数据）**。一个Trigger的调用结果只是fire的话，那么会计算窗口并保留窗口原样，也就是说窗口中的数据仍然保留不变，等待下次Trigger fire的时候再次执行计算。一个窗口可以被重复计算多次直到它被 purge 了。在purge之前，窗口会一直占用着内存。
   3. 当Trigger fire了，窗口中的元素集合就会交给 Evictor （如果指定了的话）。Evictor 主要用来遍历窗口中的元素列表，并决定最先进入窗口的多少个元素需要被移除。剩余的元素会交给用户指定的函数进行窗口的计算。如果没有 Evictor 的话，窗口中的所有元素会一起交给函数进行计算。

      > 4. Flink 对于一些聚合类的窗口计算（如sum,min）做了优化，因为聚合类的计算不需要将窗口中的所有数据都保存下来，只需要保存一个result值就可以了。**每个进入窗口的元素都会执行一次聚合函数并修改result值。这样可以大大降低内存的消耗并提升性能。但是如果用户定义了 Evictor，则不会启用对聚合窗口的优化，因为 Evictor 需要遍历窗口中的所有元素，必须要将窗口中所有元素都存下来。**

 

 

### 讲一下Flink中Time概念（时间语义）

flink中定义了三个时间语义：

**Event Time**：是事件创建的时间。它通常由事件中的时间戳描述，例如采集的日志数据中，每一条日志都会记录自己的生成时间，Flink通过时间戳分配器访问事件时间戳。

**Ingestion Time**：是数据进入Flink的时间。

**Processing Time**：某个 Flink 节点执行某个 operation 的时间，例如：timeWindow 处理数据时的系统时间，默认的时间属性就是 Processing Time

使用：

![image-20220311152202381](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220311152202381.png)

**先获取流式执行环境，然后设置使用什么时间**。在 Flink 的流式处理中，绝大部分的业务都会使用 EventTime，EventTime无法使用时才会使用其他的。

### **介绍下Flink的watermark（水位线），watermark需要实现哪个实现类，在** **何处定义？有什么作用？ **★ ☆★☆★

Watermark是flink中一种应对乱序和延迟数据的机制。所谓乱序，就是指Flink接收到的事件的先后顺序不是严格按照事件的Event Time顺序排列的（网络，分布式等原因 ）。那么此时出现一个问题，一旦出现乱序，如果只根据eventTime决定window的运行，我们不能明确数据是否全部到位，但又不能无限期的等下去，此时必须要有个机制来保证一个特定的时间后，必须触发window去进行计算了，这个特别的机制，就是Watermark。

Watermark水印就是一个时间戳（timestamp），可以理解成一个延迟触发机制，假设允许的延迟时间为t； 那么**`Watermark=eventtime-t`**；Flink 可以给数据流添加水印

- 水印并不会影响原有 Eventtime 事件时间
- 当数据流添加水印后，会按照水印时间来触发窗口计算,也就是说**watermark 水印是用来触发窗口计算的**

例如一个5秒时刻结束的时间窗口，可允许的延迟时间为2秒；那么此时以Watermark=5触发窗口计算（即Eventtime =7时）；也就是说等待了2秒让窗口内的数到齐。**综上Watermark用于处理乱序和延迟数据。**

 

**watermark的使用**

- DataStream API指定，常用的是调用assignTimestampsAndWatermarks方法（dataStram.assignTimestampsAndWatermarks）传入一个

BoundedOutOfOrdernessTimestampExtractor为乱序的数据设置时间戳和Watermark，传入一个AscendingTimestampExtractor为升序数据定义时间戳；

 项目中 flink 1.12 是  assignTimestampsAndWatermarks、watermakerstratergy() ...传入需要的watermaker

 

- Source Function中生成Watermark， Source Function可以直接为数据元素分配时间戳，同时也会向下游发送Watermark。在Source Function中为数据分配了时间戳和Watermark就不必在DataStream API中使用了。

  > 需要注意的是:如果一个timestamp分配器被使用的话，由源提供的任何Timestamp和Watermark都会被重写。

为了通过SourceFunction直接为一个元素分配一个时间戳，SourceFunction需要调用SourceContext中的collectWithTimestamp（...）方法。为了生成Watermark，源需要调用emitWatermark（Watermark）方法。

 

- 在 DataStream API 中使用 TimestampAssigner 接口定义时间戳的提取和生成Watermark行为，它包含两个子接口 **AssignerWithPeriodicWatermarks** 接口和 **AssignerWithPunctuatedWaterMarks** 接口

**AssignerWithPeriodicWatermarks**

-  周期性的生成 watermark：系统会周期性的将 watermark 插入到流中
-  默认周期是200毫秒，可以使用ExecutionConfig.setAutoWatermarkInterval() 方法进行设置
-  升序AscendingTimestampExtractor和乱序的处理 BoundedOutOfOrdernessTimestampExtractor，都是基于周期性 watermark 的。

**AssignerWithPunctuatedWatermarks**

- 没有时间周期规律，可打断的生成 watermark

 

### **如果数据延迟非常严重呢？只使用** **WaterMark可以处理吗？那应该怎么解决？**

在某些情况下，数据延迟会非常严重，即使通过 Watermark + EventTimeWindow 也无法等到数据全部进入窗口再进行处理，因为窗口触发计算后，**对于延迟到达的本属于该窗口的数据，Flink默认会将这些延迟严重的数据进行丢弃**

此时使用 **WaterMark + EventTimeWindow + AllowedLateness** **方案**（将严重迟到的数据通过侧输出流输出），可以做到数据不丢失。

 

**侧输出流这种方法只针对于基于 event-time 的窗口**

```java
allowedLateness(lateness:Time)---设置允许延迟的时间
 
sideOutputLateData(outputTag:OutputTag[T])--保存延迟数据
 
DataStream.getSideOutput(tag:OutputTag[X])--获取延迟数据
```

 

### 说一下什么是state? ★ ☆★☆★

Flink在做计算的过程中经常需要存储中间状态，来避免数据丢失并进行状态恢复（ Flink拥有丰富的状态访问和高效的容错机制 ）。 即可以将中间的计算结果进行保存，并提供给后续的计算使用；

 

（Flink 会进行状态管理，包括状态一致性、故障处理以及高效存储和访问，以便开发人员可以专注于应用程序的逻辑。）

根据状态是否需要保存中间结果，分为 **无状态计算** 和 **有状态计算。**

对于流计算而言，事件持续产生，如果每次计算**相互独立**，不依赖上下游的事件，则相同输入，可以得到相同输出，**是无状态计算**。如果计算需要**依赖**于之前或者后续事件，则被称**为有状态计算**。

 

### **Flink** **状态包括哪些？**

**（1）** 按照由 Flink 管理 还是 用户管理，状态可以分为  **托管状态（ManagedState）和 原始状态（Raw State）**

**托管状态（ManagedState）**:由 Flink 自行进行管理的 State。

**原始状态（Raw State）**：由用户自行进行管理。

两者区别：

1. 从状态管理方式的方式来说，Managed State 由 Flink Runtime 管理，自动存储，自动恢复，在内存管理上有优化；而 Raw State 需要用户自己管理，需要自己序列化，Flink 不知道 State 中存入的数据是什么结构，只有用户自己知道，需要最终序列化为可存储的数据结构。

2. 从状态数据结构来说，Managed State 支持已知的数据结构，如Value、List、Map 等。而 Raw State **只支持** **字节** 数组，所有状态都要转换为二进制字节数组才可以。

3. 从推荐使用场景来说，Managed State 大多数情况下均可使用，而 Raw State 是当 Managed State 不够用时，比如需要自定义 Operator 时，才会使用 Raw State。**在实际生产过程中，只推荐使用** **Managed State** **。**

 

**（2）State 按照是否有 key 划分为 KeyedState （键控状态）和 OperatorState（算子状态） 两种**。

**keyedState** **特点：**

1. **只能用在 keyedStream 上的算子中，状态跟特定的 key 绑定。**

2. **keyStream 流上的每一个 key 对应一个 state 对象。**

3. keyedState 保存在 StateBackend (状态后端)中

4. 实现 Rich Function 接口，通过 里面的RuntimeContext 访问。

5. **支持多种数据结构：ValueState、ListState、ReducingState、AggregatingState、MapState.**

**OperatorState** **特点：**

1. **可以用于所有算子，但整个算子只对应一个 state**，这意味着由同一并行任务所处理的所有数据都可以访问到相同的状态，状态对于同一任务而言是共享的

   > 并发改变时有多种重新分配的方式可选：均匀分配等；
   >
   > 实现 CheckpointedFunction 或者 ListCheckpointed 接口。
   >
   > **目前支持 ListState、联合列表状态和广播状态 数据结构。**

 

### **Flink** **广播状态了解吗？** ★ ☆★☆★

Flink 中，广播状态中叫作 BroadcastState。**所谓广播状态模式， 就是来自一个流的数据需要被广播到下游算子的所有子任务**，**在下游算子本地存储，在处理另一个流的时候依赖于广播的数据**。所以广播状态可以用于通过一个特定的方式来组**合并共同处理两个事件流**。

ps: 广播状态（State）必须是 MapState 类型，广播状态模式需要使用广播函数进行处理（广播函数提供了处理广播数据流和普通数据流的接口。）

k-v 看需求；谈一下项目中的

**广播状态模式的应用**

一般来说广播状态的主要应用场景如下：

**动态规则**：动态规则是一条事件流，要求吞吐量不能太高。例如，当一个报警规则时触发报警信息等。我们将这个规则广播到计算的算子的所有并发实例中。

**数据丰富**：例如，将用户的详细信息作业广播状态进行广播，对包含用户ID的交易数据流进行数据丰富

 

### **Flink** **状态接口包括哪些？**

在 Flink 中使用状态，包含两种状态接口：

（1）**状态操作接口：**使用状态对象本身存储，写入、更新数据。

（2）**状态访问接口：**从 StateBackend 获取状态对象本身。

[6万字、110个知识点Flink面试大全.pdf](file:///D:/BaiduNetdiskDownload/6万字、110个知识点Flink面试大全.pdf)

 

### **Flink** **状态如何存储（状态后端概念） **★ ☆★☆★

在 Flink 中，状态的存储、访问以及维护，由一个组件决定，这个组件就叫做**状态后端**（state backend）

状态后端主要负责两件事：本地的状态管理，以及将检查点（checkpoint）状态管理

有三种状态后端

**MemoryStateBackend**(默认)

- 内存级的状态后端，会将运行时所需的状态作为内存中的对象进行管理，将它们存储在TaskManager 的 JVM 堆上，而将 checkpoint时的状态快照 存储在 JobManager 的内存中 ；（每个 State 默认 5MB,可通过 MemoryStateBackend 构造函数调整）
- 特点：快速、低延迟，但不稳定

**FsStateBackend**

- 将 checkpoint时的状态快照存到配置的持久化文件系统（FileSystem）上，而对于运行时所需的状态，跟 MemoryStateBackend 一样，也会存在 TaskManager 的 JVM 堆上
- 同时拥有内存级的本地访问速度，和更好的容错保证

**RocksDBStateBackend**

-  将所有状态序列化后，存入本地的 key-value 型 RocksDB数据库（磁盘），不会受限于 TaskManager 的内存大小，在执行检查点的时候，再将整个 RocksDB 中保存的 State 数据全量或者增量持久化到配置的文件系统中（在 JobManager 内存中会存储少量的检查点元数据）。RocksDB 克服了 State 受内存限制的问题，同时又能够持久化到远端文件系统中，比较适合在生产中使用。
-  RocksDBStateBackend 是**目前唯一支持增量检查点的后端。** 增量检查点非常适用于超 大状态的场景。
-  缺点是访问成本高，可能导致数据流的吞吐量剧烈下降

![image-20220317155656515](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220317155656515.png)

> ps:在运行时，**MemoryStateBackend** 和 **FSStateBackend** 本地的 State 都保存在TaskManager 的内存中，所以其底层都依赖于 HeapKeyedStateBackend。HeapKeyedStateBackend 面向 Flink 引擎内部，使用者无须感知。
>

 

### flink状态如何持久化？ ★ ☆★☆★

首先，Flink 的状态最终都要持久化到第三方存储中，确保集群故障或者作业挂掉后能够恢复。

内存型和文件型的状态后端都只支持**全量持久化策略** RocksFullSnapshotStrategy

RocksDBStateBackend 持久化策略有两种：

**全量持久化策略** RocksFullSnapshotStrategy

- 每次将全量的 State 写入到状态存储中（如HDFS）。
- 在执行持久化策略的时候，使用异步机制，每个算子启动 1 个独立的线程，将自身的状态写入分布式可靠存储中。在做持久化的过程中，状态可能会被持续修改，**基于内存的状态后端**使用 CopyOnWriteStateTable 来保证线程安全

**增量持久化策略** RocksIncementalSnapshotStrategy    ★ ☆★☆★

- 增量持久化就是每次持久化增量的 State，**只有** **RocksDBStateBackend** **支持增量持久化。**

Flink 增量式的检查点以 RocksDB 为基础， RocksDB 是一个基于 LSM-Tree 的 KV 存储。新的数据保存在内存中， 称为 memtable。如果 Key 相同，后到的数据将覆盖之前的数据，一旦 memtable 写满了，RocksDB 就会将数据压缩并写入 磁盘。memtable 的数据持久化到磁盘后，就变成了不可变的 sstable。RocksDB 会将多个sstable 合并成新的sstable，然后删除旧的sstable；

在 Flink 执行检查点时，会将新的 sstable 持久化到HDFS 中，同时保留引用。

> **因为 sstable 是不可变的，Flink 对比前一个检查点创建和删除的 RocksDB sstable 文件就可以计算出状态有哪些发生改变。**RocksDB 会在后台合并 sstable 并删除其中重复的数据。然后在 RocksDB 删除 原来的 sstable，替换成新合成的 sstable。新的 sstable 包含了被删除的 sstable 中的信息，这样可以减少检查点的历史文件，避免大量小文件的产生

 

[6万字、110个知识点Flink面试大全.pdf](file:///D:/BaiduNetdiskDownload/6万字、110个知识点Flink面试大全.pdf)

 

### **Flink** **状态过期后如何清理？**

**1、DataStream** **中状态过期**

可以对 DataStream 中的每一个状态设置 **清理策略** **StateTtlConfig**，可以设置的内容如下：

- 过期时间：超过多长时间未访问，视为 State 过期，类似于缓存。
- 过期时间更新策略：创建和写时更新、读取和写时更新。
- State 可见性：未清理可用，超时则不可用。

**2、Flink SQL** **中状态过期**

Flink SQL 一般在 Join、聚合类场景使用 State，如果 State 不定时清理，则导致 State 过多，内存溢出。清理策略配置如下：

```java
//设置过期时间为 min = 12 小时 ，max = 24 小时
StreamQueryConfig qConfig = qConfig.withIdleStateRetentionTime(Time.hours(12),Time.hours(24));
```

 

### checkpiont检查点机制★★★★★

Flink 使用 轻量级分布式快照，也就是检查点（**checkpoint**）实现可靠容错。**Checkpoint** 是 Flink 实现容错机制最核心的功能，是 Flink 可靠性的基石。

Checkpoint 是某一时刻，Flink中所有的Operator的当前State的全局快照。Flink会在输入的数据集上间隔性地生成checkpoint barrier，通过栅栏（barrier）将间隔时间段内的数据划分到相应的checkpoint中，将这些数据定期持久化存储下来。当应用出现异常时，Operator就能够从上一次快照中恢复所有算子之前的状态，实现容错从而保证数据的一致性。

> checkpoint过程中状态数据一般被保存在一个可配置的环境中，通常是在JobManager节点或HDFS上。
>
> 默认情况下Flink不开启检查点的，用户需要在程序中通过调用enable-Checkpointing(n)方法配置和开启检查点
>
> 参数：开启和时间间隔指定、exactly-ance和at-least-once语义选择、Checkpoint超时时间、检查点之间最小时间间隔、最大并行执行的检查点数量等；

**区分** **State** **和** **Checkpoint**

**1.State:**

- 一般指一个具体的 Task/Operator 的状态(operator 的状态表示一些算子在运行的过程中会产生的一些中间结果)
- State 数据默认保存在 Java 的堆内存中/TaskManage 节点的内存中

- State 可以被记录，在失败的情况下数据还可以恢复。

**2.Checkpoint:**

- 表示了一个 FlinkJob 在一个特定时刻的一份全局状态快照，即包含了所有Task/Operator 的状态
- 可以理解为 Checkpoint 是把 State 数据定时持久化存储了
- 比如 KafkaConsumer 算子(source算子)中维护的 Offset 状态,当任务重新恢复的时候可以从Checkpoint 中获取。

 

### 什么是保存点（Savepoints）★ ☆★☆★

- 是**基于 Flink 检查点机制**的应用**完整快照备份机制**，原则上，创建保存点使用的算法与检查点完全相同，因此保存点可以认为就是具有一些额外元数据的检查点。(Savepoint 由两部分组成：稳定存储（如HDFS) 上包含二进制文件的目录（通常很大），和元数据文件（相对较小）)
- 保存点是一个强大的功能。除了故障恢复外，保存点可以用于：有计划的手动备份，更新应用程序，版本迁移，暂停和重启应用，等等
- Flink不会自动创建保存点，因此用户（或者外部调度程序）必须明确地触发创建操作；用户在恢复时需要提供用于恢复作业状态的保存点路径。

 

### **什么是** **CheckpointCoordinator** **检查点协调器？**

**CheckpointCoordinator**，负责协调 制作Flink 算子的State 的分布式快照。当触发快照的时候，CheckpointCoordinator 向 Source 算子

中注入 **Barrier** 消息 ，然后等待所有的 Task 通知检查点确认完成，同时持有所有 Task 在确认完成消息中上报的 State 句柄。

 

### checkpiont检查点的流程 ★★★★★

Checkpoint由Jobmanager的Checkpoint Coordinator发起

1. CheckpointCoordinator(检查点协调器) 周期性的向该流应用的所有 source 算子发送 barrier(屏障)。
2. 当某个 source 算子收到一个 barrier 时，便暂停数据处理过程，然后将 自己的当前状态制作成快照，并保存到指定的持久化存储中，最后向 CheckpointCoordinator 报告自己快照制作情况，同时向自身所有下游算子广播该 barrier，恢复数据处理
3. 下游算子收到 barrier 之后，会暂停自己的数据处理过程，然后将自身的 相关状态制作成快照，并保存到指定的持久化存储中，最后向 CheckpointCoordinator 报告自身快照情况，同时向自身所有下游算子广 播该 barrier，恢复数据处理。
4. 每个算子按照步骤 3 不断制作快照并向下游广播barrier ，直到最后 barrier 传递 到 sink 算子， 当 Sink 算子已经收到了所有上游的Barrie 时， Sink 算子对自己的 State 进行快照，然后通知检查点协调器( CheckpointCoordinator) 。当所有 的算子都向检查点协调器汇报成功之后，检查点协调器向所有的算子确认本次Checkpoint完成

 

> 我认为此时可以分两种情况：
>
> **如果是flink引擎内部严格一次处理保证，**当 Sink 算子已经收到了所有上游的Barrie 时， Sink 算子对自己的 State 进行快照，然后通知检查点协调器( CheckpointCoordinator) 。当所有 的算子都向检查点协调器汇报成功之后，检查点协调器向所有的算子确认本次快照完成。这时将数据写到外部系统，遇到故障进行恢复时，可能会出现重复消费。
>
> > （例：我程序中Flink的CheckPoint语义设置了 Exactly Once，但是我的mysql中看到数据重复了？程序中设置了1分钟1次CheckPoint，但是5秒向mysql写一次数据，并commit（mysql  innodb支持事务，myasim引擎不支持事务）
>
> >    答：Flink要求end to end的精确一次都必须实现TwoPhaseCommitSinkFunction。如果你的chk-100成功了，过了30秒，由于5秒commit一次，所以实际上已经写入了6批数据进入mysql，但是突然程序挂了，从chk100处恢复，这样的话，之前提交的6批数据就会重复写入，所以出现了重复消费。）--**项目中遇到了这个问题**
>
>
>    **如果是端到端严格一次处理保证（涉及外部系统，如Kafka），**当 Sink 算子已经收到了所有上游的Barrie n 时， Sink 算子对自己的 State 进行快照，**并预提交外部事务（Kafka事务），再通知检查点协调器( CheckpointCoordinator) ，检查点协调器向所有的算子确认本次快照完成，Sink 算子正式提交数据**，提交成功后本次事务完成（kafka关闭事务）。这里就涉及了两阶段提交协议。

 

**Exactly Once 和 At Least Once 语义由Barrier 是否对齐控制**

### **什么是** **Barrier** **对齐？**

对有两个以上输入管道Operator 来说；一旦 Operator 从输入流接收到 CheckPoint barrier n，它就不能处理来自该流的任何数据记录，直到它从其他所有输入接收到 barrier n 为止。

### **什么是** **Barrier** **不对齐？**

**barrier** **不对齐：就是指当还有其他流的 **barrier **还没到达时，为了不影响性能，不用理会，直接处理**当前流barrier **之后的数据。等到所有流的** **barrier** **的都到达后，就可以对该** **Operator** **做** **CheckPoint** **了；**

 

### **为什么要进行** **barrier** **对齐？不对齐到底行不行？**

**Exactly Once（精确一次） 时必须 barrier 对齐，如果 barrier 不对齐就变成了 At Least Once（至少一次）；**

**CheckPoint** **的目的就是为了保存快照**，如果不对齐，那么在某次快照之前，已经处理了一些**这次快照 对应的 offset 之后的数据**，那么当程序从 这个检查点 恢复任务时，此检查点对应的 offset 之后的数据还会被处理一次，所以就出现了重复消费。

 

### **Flink checkpoint 与 Spark Streaming 的有什么区别或优势吗** ★★★

spark streaming 的 checkpoint是针对RDD的checkpoint，并在 driver 的故障恢复做了数据和元数据的 checkpoint。而 flink 的 checkpoint 机制 要复杂了很多，它采用 的是轻量级的分布式快照，实现了每个算子的快照，及流动中的数据的快照。

- flink 的checkpoint更加轻量，flink针对算子的快照，且支持增量快照 ；spark每个批次全量保存；
- 在Flink中的Checkpoint中有仅一次语义概念和用法 , 而spark checkpoint没有仅一次的概念

 

### **Flink** **支持** **Exactly-Once** **语义，那什么是** **Exactly **Once？

Exactly-Once 语义 : 指**端到端**的一致性，从**数据读取**、**引擎计算**、**写入外部存储的**整个过程中，**即使机器或软件出现故障，**每个数据仅会影响最终结果一次，不会重复、也不会丢失。

 

### **要实现** **Exactly-Once,**需具备什么条件？（flink如何保证 Exactly-Once？/如何保证端到端的一致性？）★ ☆★☆★

最核心的是**两阶段提交协议（和状态保存）**，但流系统要实现 Exactly-Once，需要保证上游 Source 层、中间计算层和下游 Sink 层三部分同时满足Exactly-Once

**Source** **端：**数据从上游进入 Flink，必须保证消息严格一次消费。同时 Source 端必须满足可重放（replay）。否则 Flink 计算层收到消息后未计算，却发生failure 而重启，消息就会丢失。

**Flink** **计算层：**利用 Checkpoint 机制，把状态数据定期持久化存储下来，Flink程序一旦发生故障的时候，可以选择检查点恢复，避免数据的丢失、重复。

**Sink** **端（端到端一致性，所以这里一般指的是外部sink，如kafka sink）：**Flink 将处理完的数据发送到 Sink 端时，通过 **两阶段提交协议（**即 TwoPhaseCommitSinkFunction 函数。该 SinkFunction 提取并封装了两阶段提交协议中的公共逻辑**） 实现Sink 端精确一次语义。 **同时：**Sink 端必须支持**事务机制**，能够进行数据**回滚。

sink端不支持事务：**需要满足幂等性**

> **回滚机制：**即当作业失败后，能够将部分写入的结果回滚到之前写入的状态。
>
> **幂等性：**就是一个相同的操作，无论重复多少次，造成的结果和只操作一次相等。即当作业失败后，写入部分结果，但是当重新写入全部结果时，不会带来负面结果，重复写入不会带来错误结果。
>
> **ps : sink端若是不支持事务可以用采用幂等写入的方式，但此时不是严格的Exactly-Once（故障恢复时会出现暂时不一致，指恢复前和恢复后不一致，故障之前的数据是可见的，这次故障和最近检查点之间的数据会导致写入不一致，因为不仅仅有重复的数据还有不重复的新数据）；**
>
> **Exactly-Once不是说数据只被处理一次，它们实际上是在说，它们可以保证引擎管理的状态更新只提交一次到持久的后端存储（对结果只产生一次影响）。**

 

到这可以谈一下两阶段提交协议，下面我以Kafka为例介绍下两阶段提交协议的具体流程。

 

### flink的两阶段提交协议流程？端到端一致性案列★ ☆★☆★

**两阶段提交协议（Two -Phase Commit，2PC）是解决分布式事务问题最常用的方法，它可以保证在分布式事务中，要么所有参与进程都提交事务，要么都取消**，即满足原子性

一般流程：

1）开始事务（beginTransaction）创建一个临时文件夹，用于把数据写入到这个文件夹里面

2）预提交（preCommit）将内存中缓存的数据写入文件并关闭

3）正式提交（commit）将之前写完的临时文件放入目标目录下。这代表着最终的数据会有一些延迟

4）丢弃（abort）丢弃临时文件

flink的两阶段提交协议要涉及外部支持事务的系统，所以下面我以kafka-flink-kafka为例进行说明

**以kafaka为例：**

1、Checkpoint **启动**，向source算子注入barrier，开启kafka事务，进入Pre-commit(预提交阶段)。

2、所有的Operator执行各自的Pre-commit，（保存消费Kafka的偏移量）对状态做快照并保存，向下游发送barrier等

3、如果有任一个Pre-commit失败，所有其他的Pre-commit必须停止，并且flink会回滚到最近成功的checkpoint。

4、当sink端收到了checkpoint barrier(检查点分界线)，sink对当前状态做快照并保存，同时 **预提交外部事物（Kafka事务）**，然后通知jobmanager。

5、jobmanager收到所有任务完成的通知，发出确认信息，向所有的算子确认本次Checkpoint完成，**此时预提交接段完成**；sink收到jobmanager的确认信息，**正式提交（commit）**这段时间的数据和**外部事物**。

6、外部系统kafka关闭事务，提交的数据可以被正常消费。

从上过程我们可以发现：

- 一旦所有的operator完成预提交，就提交一个commit。
- 如果至少有一个预提交失败，其他的都会失败，这时回滚到上一个checkpoint保存的位置。
- **预提交成功后，提交的commit也需要保障最终成功----  operator和外部系统需要提供这个保障**。如果commit失败了（比如网络中断引起的故障），整个flink程序也因此失败，它会根据用户的重启策略重启，可能还会有一个尝试性的提交。这个过程非常严苛，因为如果提交没有最终生效，会导致数据丢失。
- 所以，所有的operator都必须对checkpoint达成共识：即所有的operator都必须认定数据要么成功执行，要么被终止然后回滚。

 

### **当作业失败后，检查点如何恢复作业？（恢复作业的策略/机制）**

Flink 提供了 **应用自动恢复机制** 和 **手动作业恢复机制**。

**应用自动恢复机制：**

Flink 设置有作业失败重启策略，包含四种：

**1、定期恢复策略：fixed-delay**

作业失败后，延迟一定时间重启。但是有最大重启次数限制，超过这个限制后作业失败，不再重启。默认 Integer.MAX_VALUE 次。（不设置默认这种）

**2、失败比率策略：failure-rate**

作业失败后，延迟一定时间重启。但是有最大失败率限制。如果一定时间内作业失败次数超过配置值，则标记为真的失败，不再重启。

**3、exponential-delay：**作业失败后重启延迟时间随着失败次数指数递增。没有最大重启次数限制，无限尝试重启作业。

**4、直接失败策略：None** **失败不重启**

 

**手动作业恢复机制：**

Flink 提供了在启动之时通过设置 **-s** 参数指定检查点目录的功能，让新的 jobld 读取该检查点元文件信息和状态信息，从而达到指定时间节点启动作业的目的。

 

### Flink广播机制了解吗

可以理解 **广播** 就是一个**公共的共享变量，**广播变量是发往**TaskManager** **的内存中，**所以广播变量不应该太大，将一个数据集广播后，不同的 **Task** 都可以在节点上获取到，每个节点只存一份。 如果不使用广播，每一个Task 都会拷贝一份数据集，造成内存资源浪费 。

![image-20220315132642923](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220315132642923.png)

 

### Flink的反压了解吗？反压会带来哪些问题？ ★ ☆★☆★

反压概念：流系统中数据的**处理速度跟不上数据的发送速度**，导致数据的堆积，这造成了反压。

 

反压会影响到两项指标: **checkpoint** **时长**和 **state** **大小**

- 因为 checkpoint barrier 是不会越过普通数据的，**数据处理被阻塞**也会**导致** checkpoint barrier 流经**整个数据管道的时长变长**，因而checkpoint 总体时间（End to End Duration）变长。


- 为保证Exactly-Once语义，对于有两个以上输入管道的 Operator，checkpoint barrier 需要对齐，接受到较快的输入管道的 barrier 后，它后面数据会被缓存起来但不处理，直到较慢的输入管道的 barrier 也到达，这些被缓存的数据会被放到 state 里面，反压的话缓存的数据变多，导致**state** 变大。

**这两个影响对于生产环境的作业来说是十分危险的**，因为 checkpoint 是保证数据一致性的关键，checkpoint 时间变长有可能导致 checkpoint 超时失败，而 state 大小同样可能拖慢 checkpoint流程 甚至导致 OOM （使用 Heap-based StateBackend）或者物理内存使用超出容器资源（使用 RocksDBStateBackend）的稳定性问题

 

### Flink是如何处理反压的？以及在生产环境中如何排查？ ★ ☆★☆★

**flink对反压的处理：**

> Flink 没有使用任何复杂的机制来解决背压问题，**它利用自身作为纯数据流引擎的优势来优雅地响应背压问题**。 对于 Flink 的数据传输机制一种形象的**类比**是，Flink 使用了**高效有界的分布式阻塞队列**，就像 Java 通用的阻塞队列（BlockingQueue）一样。使用 BlockingQueue 的话，一个较慢的接受者会降低发送者的发送速率，因为一旦队列满了（有界队列）发送者会被阻塞。Flink 解决背压的方案就是这种感觉。**在 Flink 中，这些分布式阻塞队列就是这些逻辑流，而队列容量是通过缓冲池来（LocalBufferPool）实现的**。每个被生产和被消费的流都会被分配一个缓冲池。缓冲池管理着一组缓冲(Buffer)，缓冲在被消费后可以被回收循环利用。
>

在Flink 1.5之后，引入了（Credit-based Flow Control）基于信用点的流量控制来解决背压问题。这种方法，首先把每个子任务的本地缓存分为两个部分，独占缓存（Exclusive Buffers）和浮动缓存（Floating Buffers）；然后，独占缓存的大小作为信用点发给数据发送方，发送方会按照不同的子任务分别记录信用点，并发送尽可能多数据给接收方，发送后则降低对方应信用点的大小；**当信用点为0时，则不再发送，起到背压的作用**。在发送数据的同时，发送方还会把队列中暂存排队的数据量发给接收方，接收方收到后，根据本地缓存的大小，决定是否去浮动缓存里请求更多的缓存来加速队列的处理，起到动态控制流量的作用。  这个设计实现了任务级别的背压：任意一个任务产生背压，只会影响这个任务，并不会对TaskManger上的其它任务造成影响（远程传输情况下）。

[Flink内核原理学习（四）内存模型_oahaijgnahz的博客-CSDN博客](https://blog.csdn.net/weixin_38836273/article/details/116976493)

**生产环境的排查：**

要解决反压首先要做的是定位到造成反压的节点

1. **通过 Flink Web UI 发现反压问题**。

   Flink 的 TaskManager 会每隔 50 ms 触发一次反压状态监测，共监测 100 次， 并将结果反馈给 JobManager，最后由 JobManager 进行计算反压的比例， 然后进行展示。默认配置下，这个频率在 0.1 以下则为 OK，0.1 至 0.5 为 LOW，而超过 0.5 则为 HIGH，表示要处理了。

2. **Task Metrics**

   Flink 提供的 Task Metrics 是更好的反压监控手段

   如果一个 Subtask 的发送端 Buffer 占用率很高，则表明它被下游反压限速了；

   如果一个 Subtask 的接受端 Buffer 占用率很高，则表明它将反压传导至上游。

**问题定位及处理：**

- **数据倾斜**：可以在 Flink 的后台管理页面看到每个 Task 处理数据的大小。当数据倾斜出现时，通常是简单地使用类似 KeyBy 等分组聚合函数导致的，需要 用户将热点 Key 进行预处理，降低或者消除热点 Key 的影响。
- **GC**：不合理的设置 TaskManager 的垃圾回收参数会导致严重的 GC 问题，我们 可以通过 -XX:+PrintGCDetails 参数查看 GC 的日志。
- **户代码的执行效率问题（频繁被阻塞或者性能问题）**：我们可以通过查看运行机器节点的 CPU 和内存情况定位问题。

 

 

**Flink** **支持的数据类型有哪些？**

Flink 类型可以分为基础类型（Basic）、数组（Arrays）、复合类型（Composite）、辅助类型（Auxiliary）、泛型和其它类型（Generic）。

Flink 支持任意的 Java 或是 Scala 类型。

![image-20220315142927782](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220315142927782.png)

 

### **Flink** **如何进行序列和反序列化的？**

**序列化：**就是将一个内存对象转换成二进制串，形成网络传输或者持久化的数据流。

**反序列化：**将二进制串转换为内存对象。

flink中**TypeInformation 是所有类型描述符的基类**。它揭示了该类型的一些基本属性， 并且可以生成序列化器，TypeInformation 会提供一个 createSerialize() 方法，通过这个方法就可以得到序列化器 TypeSerializer。TypeSerializer 提供了序列化和反序列化能力。

![image-20220315152410117](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220315152410117.png)

**对于大多数数据类型** **Flink** **可以自动生成对应的序列化器，能非常高效地对数据集进行序列化和反序列化**---------回答到这里即可

- BasicTypeInfo: 任意 Java 基本类型或 String 类型
- BasicArrayTypeInfo: 任意 Java 基本类型数组或 String 数组
- WritableTypeInfo: 任意 Hadoop Writable 接口的实现类
- TupleTypeInfo: 任意的 Flink Tuple 类型(支持 Tuple1 to Tuple25)。
- Flink tuples 是固定长度固定类型的 Java Tuple 实现
- CaseClassTypeInfo: 任意的 Scala CaseClass(包括 Scala tuples)
- PojoTypeInfo: 任意的 POJO (Java or Scala)，例如，Java 对象的所有 成员变量，要么是 public 修饰符定义，要么有 getter/setter 方法
- **GenericTypeInfo: 任意无法匹配之前几种类型的类**，**Flink** **会使用** **Kyro** **进行序列化和反序列化**

![image-20220315152339656](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220315152339656.png)

**Tuple、Pojo **和**CaseClass** **类型是复合类型，它们可能嵌套一个或者多个数据类型。在这种情况下，它们的序列化器同样是复合的。它们会将内嵌类型的序列化委托给对应类型的序列化器。**

![image-20220315221323410](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220315221323410.png)

 

**MemorySegment** **具有什么作用呢？**

**MemorySegment** 在 Flink 中会将对象序列化到预分配的内存块上，它代表 1 个固定长度的内存，默认大小为 32 kb。MemorySegment 代表 Flink 中的一个最小的内存分配单元，相当于是 Java 的一个 byte 数组。每条记录都会以序列化的形式存储在一个或多个 MemorySegment 中。

 

 

### **为什么** **Flink** **使用自主内存管理而不用** **JVM** **内存管理？** ★ ☆★☆★

1）Java 对象存储密度低。Java 的对象在内存中存储包含 3 个主要部分：对象头、实例数据、对齐填充部分。例如，一个只包含 boolean 属性的对象占 16byte：对象头占 8byte，boolean 属性占 1byte，为了对齐达到 8 的倍数额外占 7byte。实际boolean 属性只需要1bit。

2）Full GC 会极大地影响性能。尤其是为了处理更大数据而开了很大内存空间的 JVM来说，GC 会达到秒级甚至分钟级。

3）OOM 问题影响稳定性。OutOfMemoryError 是分布式计算框架经常会遇到的问题，当JVM中所有对象大小超过分配给JVM的内存大小时，就会发生OutOfMemoryError错误，导致 JVM 崩溃，分布式框架的健壮性和性能都会受到影响。

4）缓存未命中问题。Java 对象在堆上存储的时候并不是连续的，所以从内存中读取 Java 对象时，缓存的邻近的内存区域的数据往往不是 CPU 下一步计算所需要的，这就是缓存未命中。此时 CPU 需要空转等待从内存中重新读取数据。

 

### **那** **Flink** **自主内存是如何管理对象的？**（**Flink 的内存管理是如何做的**？） ★ ☆★☆★

Flink 并不是将大量对象存在堆内存上，而是将对象**都序列化到**一个预分配的内存块上， 这个内存块叫做 **MemorySegment**，它代表了一段固定长度的内存（默认大小为 32KB），也是 **Flink** **中最小的内存分配单元**，并且提供了非常高效的读写方法，很多运算可以直接操作 二进制数据，不需要反序列化即可执行。每条记录都会以序列化的形式存储在一个或多个 MemorySegment 中。如果需要处理的数据多于可以保存在内存中的数据，Flink (的运算符)会将部分数据溢出到磁盘，避免OOM。

这块内存既可以是堆上内存，也可以是堆外内存；它是常驻型数据，如果在堆上，这些MemorySegment一直待在老年代而不会被minor GC回收

[Flink 原理与实现：内存管理 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/27241485)

### flink内存模型

[6万字、110个知识点Flink面试大全.pdf](file:///D:/BaiduNetdiskDownload/6万字、110个知识点Flink面试大全.pdf)

flink总体内存类：

![image-20220316143333435](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220316143333435.png)

主要包含 **JobManager** **内存模型**和 **TaskManager** **内存模型**

**JobManager** **内存模型**

![image-20220316143558520](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220316143558520.png)

分为堆外内存和堆上内存，**Flink 内存模型主要指 TaskManager 运行时提供的内存资源**

**TaskManager** **内存模型**  （1.1.0版本）

![image-20220316144415367](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220316144415367.png)

 

 

|           组件            | 配置项                                                       | 描述                                                         |
| :-----------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
|   Framework Heap Memory   | taskmanager.memory.framework.heap.size                       | （高级参数，一般不需要用户配置）分配给 Flink 框架的 JVM 堆内存（默认128MB）,不计入 Slot 资源。 |
|     Task Heap Memory      | taskmanager.memory.task.heap.size                            | Task 执行用户代码时所使用的堆上内存。                        |
|      managed memory       | taskmanager.memory.managed.size(默认none) taskmanager.memory.managed.fraction(默认0.4) | 被 flink 管理的本地内存(堆外内存)，用于排序、哈希表、缓存中间结果及 RocksDB State Backend 的本地内存。 |
| Framework Off-heap Memory | taskmanager.memory.framework.off-heap.size(默认128 mb)       | （高级参数）分配给 Flink 框架的 堆外内存（TaskManager 本身所占用的堆外内存）,不计入 Slot 资源。 |
|   Task Off-heap Memory    | taskmanager.memory.task.off-heap.size                        | Task 执行用户代码时所使用的堆外内存。                        |
|      Network Memory       | taskmanager.memory.network.min(默认64 mb) taskmanager.memory.network.max(默认1 gb) taskmanager.memory.network.fraction(默认0.1) | 网络数据交换所使用的堆外内存大小，如网络数据交换缓冲区，是flink total memory的一个有上下限的细分组件。 |
|       JVM metaspace       | taskmanager.memory.jvm-metaspace.size(默认96 mb) flink-1.10.0 为 96 mb flink-1.10.1及flink-1.11为256 mb 更改原因见 [FLINK-16406](https://issues.apache.org/jira/browse/FLINK-16406) | Flink JVM 进程的元数据空间大小，为本地内存                   |
|       JVM Overhead        | taskmanager.memory.jvm-overhead.min(默认192 mb) taskmanager.memory.jvm-overhead.max(默认1 gb) taskmanager.memory.jvm-overhead.fraction(默认0.1) | JVM 执行时自身所需要的内容，包括线程堆栈、IO 、编译缓存等所使用的内存。是flink total memory的一个有上下限的细分组件。 |

**总进程内存：**Flink Java 应用程序（包括用户代码）和 JVM 运行整个进程所消 耗的总内存。

总进程内存 = Flink 使用内存 + JVM 元空间 + JVM 执行开销

配置项：taskmanager.memory.process.size: 1728m

**Flink** **总内存：**仅 Flink Java 应用程序消耗的内存，包括用户代码，但不包括JVM 为其运行而分配的内存。

Flink 使用内存：框架堆内外 + task 堆内外 + network + manage

 

## Flink源码篇

 

### Flink的作业提交分为几种方式？

**Flink** **的作业提交分为两种方式**

**1.Local** **方式：**即本地提交模式，直接在 IDEA 运行代码。

**2.远程提交方式：**分为 Standalone 方式、yarn 方式、K8s 方式

**Yarn** **方式分为三种提交模式：**Yarn-perJob 模式、Yarn-Session模式、Yarn Application 模式

 

### **那在** **jobGraph** **提交集群之前都经历哪些过程？**

（1）用户通过启动 Flink 集群，使用命令行提交作业，比如运行 flink run - c WordCount xxx.jar （standalone模式提交任务）

（2）运行命令行后，会通过 run 脚本调用 CliFrontend 入口，CliFrontend 会触发用户提交的 jar 文件中的 main 方法，然后交给 PipelineExecuteor 的 execute 方法，最终根据提交的模式选择触发一个具体的 PipelineExecutor 执行。

（3）根据具体的 PipelineExecutor 执行，将对用户的代码进行编译生成streamGraph，经过优化后生成 jobgraph。

![image-20220316213544174](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220316213544174.png)

 

### **看你提到** **PipeExecutor，它有哪些实现类？**

PipeExecutor 在 Flink 中被叫做 流水线执行器，它是一个接口，是 Flink Client 生成 JobGraph 之后，将作业提交给集群的重要环节，前面说过，作业提交到集群有好几种方式，最常用的是 yarn 方式，yarn 方式包含 3 种提交模式，主要使用 session 模式，perjob 模式。Application 模式 jaobGraph 是在集群中生成。

![image-20220316214046858](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220316214046858.png)

PipeExecutor 的实现类有：

``AbstractJobClusterExcutor``

有子类：``YarnJobClusterExcutor``；为yarn perJob提交模式所使用

``AbstractSessionClusterExcutor``

有子类：

``KubernetesSessionClusterExcutor``；为K8s 提交模式所使用

``AbstractSessionClusterExcutor``；为yarn session 提交模式所使用

``RemoteExcutor``  standalone  模式提交时使用

`embeddedExecutor`  嵌入模式

此外 在 IDEA 环境中运行 提交时，使用 LocalExecutor。

[Flink 1.11.0 job提交流程源码解析（精髓)_乾坤瞬间的博客-CSDN博客](https://blog.csdn.net/u012491646/article/details/109245608)

 

### **Local** **提交模式有啥特点，怎么实现的？**

1. Local 是在本地 IDEA 环境中运行的提交方式。不上集群。主要用于调试

   ![image-20220317090612537](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220317090612537.png)

   1. Flink 程序由 JobClient 进行提交

   2. JobClient 将作业提交给 JobManager

   3. JobManager 负责协调资源分配和作业执行。资源分配完成后，任务将提交给相应的 TaskManager

   4. TaskManager 启动一个线程开始执行，TaskManager 会向 JobManager 报告状态更改，如开始执 行，正在进行或者已完成。

   5. 作业执行完成后，结果将发送回客户端。

**源码分析：通过 Flink1.12.2 源码进行分析的**

**（1）创建获取对应的** **StreamExecutionEnvironment** **对象**：LocalStreamEnvironment

 

### **yarn - session** **模式特点？**

Session-Cluster 模式需要先启动集群，然后再提交作业，接着会向 yarn 申请一块空间后，资源永远保持不变。如果资源满了，下一个作业就无法提交，只能等到yarn 中的其中一个作业执行完成后，释放了资源，下个作业才会正常提交。所有**作业共享集群资源**，隔离性差，JM 负载瓶颈，main 方法在客户端执行。所有作业共享 Dispatcher 和 ResourceManager；**只有一个** **JobManager**，另外，**Job** **被随机分配给** **TaskManager**；它共享资源；适合规模小执行时间短的作业。

**在 yarn 中初始化一个 flink 集群，开辟指定的资源，以后提交任务都向这里提交。这个 flink 集群会常驻在 yarn 集群中，除非手工停止。**

 

 

### **yarn - perJob** **模式特点？**

**一个任务会对应一个** **Job**，**每提交一个作业**会根据自身的情况，**都会单独向** **yarn**申请资源**，直到作业执行完成，一个作业的失败与否并不会影响下一个作业的正常提交和运行。就是**每个作业单独启动集群**，这样隔离性好，JM 负载均衡。在 per-job 模式下，每个 Job 都有一个 JobManager，每个TaskManager 只有单个 Job，且独享 Dispatcher 和 ResourceManager，按需接受资源申请；**适合规模大长时间运行的作业。

 

### **yarn - application** **模式特点？**

每个作业单独启动集群，隔离性好，JM 负载均衡，**main** **方法在** **JobManager** **上执行**

原本需要客户端做的**三件事**被转移到了 JobManager 里，也就是说 main()方法在集群中执行(入口点位于 ApplicationClusterEntryPoint )，客 户端只需要负责发起部署请求了

在 yarn-per-job 和 yarn-session 模式下，客户端都需要执行以下三步，即：

1、获取作业所需的依赖项并创建StreamGraph流图；

2、通过执行环境分析并取得逻辑计划，即 StreamGraph→JobGraph；

3、将依赖项和 JobGraph 上传到集群中

**如果所有用户都在同一个客户端上提交作业**，**较大的依赖会消耗更多的带宽**，而较复杂的作业逻辑翻译成 JobGraph 也需要吃掉更多的 CPU 和内存，**客户端的资源反而会成为瓶颈**。

 

# HBase

## 介绍下HBase / Hbase的原理

HBase是一种**高可靠、面向列、可伸缩、支持海量数据存储的非关系型分布式数据库**，运行于HDFS文件系统之上；

HBase的**目标是存储和处理非常庞大的表**，可以通过水平扩展的方式，利用廉价计算机集群处理极大的（超过10亿行数据和数百万列元素组成的）数据表。

广泛应用于：交通、金融、电商、电信等场景；

原理：回答下面的架构

 

## hbase的架构  ★★★★★

![image-20220515103347740](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220515103347740.png)

 

- **Region**  HBase自动把表水平划分成多个区域(region)，每个region会保存一个表里面某段连续的数据；每个表一开始只有一个region，随着数据不断插入表，region不断增大，当增大到一个阀值的时候，region就会等分成两个新的region（裂变），随着region越多，一个表的region会被保存在多个Region Server上

- **Region Server**   Region Server 为 Region 的管理者，其实现类为 HRegionServer，主要作用如下: （对于数据的操作：get, put, delete）； 对于 Region 的操作：Region server维护region，处理对这些region的IO请求，并负责切分与合并region  （splitRegion、compactRegion）。

- **Master**  Master 是所有 Region Server 的管理者，其实现类为 HMaster，主要作用如下： 对于表的操作：create, delete, alter

  对于 RegionServer的操作：分配 regions到每个RegionServer，监控每个 RegionServer 的状态，负载均衡和故障转移。


- **Zookeeper**  HBase 通过 Zookeeper 来做 Master 的高可用、RegionServer 的监控、元数据的入口以及 集群配置的维护等工作。
- **HDFS**  HDFS 为 HBase 提供最终的底层数据存储服务，同时为 HBase 提供高可用的支持。
- **StoreFile（HFile）**  保存实际数据的物理文件。每个 Store 会有 一个或多个 StoreFile（HFile），数据在每个 StoreFile 中都是有序的。
- **MemStore**  写缓存，由于 HFile 中的数据要求是有序的，所以数据是先存储在 MemStore 中，**排好序后**，等到达刷写时机才会刷写到 HFile，每次刷写都会形成一个新的 HFile。
- **WAL（Hlog）**  由于数据要经 MemStore 排序后才能刷写到 HFile，但把数据保存在内存中会有很高的 概率导致数据丢失，为了解决这个问题，数据会先写在一个叫做 Write-Ahead logfile 的文件中，这个文件在HDFS中，然后再写入 MemStore 中。所以在系统出现故障的时候，数据可以通过这个日志文件重建。
- **BlockCache** 读缓存，每次查询出的数据会缓存在BlockCache中，方便下次查询。

[Hbase架构与原理 - 简书 (jianshu.com)](https://www.jianshu.com/p/3832ae37fac4)

 

##  **HBase的memstore冲刷条件**

> 问过的一些公司：小米

主要有以下几种情况会触发 Memstore Flush：

- Region 中所有 MemStore 占用的内存超过相关阈值
- 整个 RegionServer 的 MemStore 占用内存总和大于相关阈值
- WAL数量大于相关阈值
- 数据更新超过一定阈值
- 定期自动刷写
- 手动触发刷写

 

> **Hbase master 高可用**
>
> 在 HBase 中 HMaster 负责监控 HRegionServer 的生命周期，均衡 RegionServer 的负载，如果 HMaster 挂掉了，那么整个 HBase 集群将陷入不健康的状态，并且此时的工作状态并不会维持太久。所以 HBase 支持对 HMaster 的高可用配置。
>
> 基于zookeeper 和 hdfs（Hlog）

 

 

## **StoreFile Compaction**

由于memstore每次刷写都会生成一个新的HFile，且同一个字段的不同版本（timestamp）和不同类型（Put/Delete）有可能会分布在不同的 HFile 中，因此查询时需要遍历所有的 HFile。

为了减少 HFile 的个数，以及清理掉过期和删除的数据，会进行 StoreFile Compaction。

Compaction 分为两种，分别是 Minor Compaction 和 Major Compaction。

- Minor Compaction会将临近的若干个较小的 HFile 合并成一个较大的 HFile，但**不会**清理过期和删除的数据。
- Major Compaction 会将一个 Store 下的所有的 HFile 合并成一个大 HFile，并且**会**清理掉过期和删除的数据。

> **HBase合并：**删除一条记录，就会在该记录上打上标记，被打上标记的记录就成了墓碑记录，该记录使用get和scan查询不到，但还是在HFile中。**只有进行大合并的时候才会删除HFile中的墓碑记录**。
>
> **大合并：**指定region的一个列族的所有HFile。合并完成后，这个列族的所有HFile文件合并成一个HFile文件，可以在shell中手动触发，但该动作相当耗资源。
>
> **小合并：**将多个小的HFile文件内容读取出来合并生成一个大的HFile,把新文件设置成激活状态，然后删除小的HFile。

 

## hbase优缺点

**优点**

1、海量存储

Hbase适合存储PB级别的海量数据，在PB级别的数据，能在几十到几百毫秒内返回数据。这与Hbase的极易扩展性息息相关。正是因为

Hbase良好的扩展性，才为海量数据的存储提供了便利。

2、列式存储

这里的列式存储其实说的是列族存储，Hbase是根据列族来存储数据的。HBase中的每个列都由Column Family(列族)和Column Qualifier（列限定符）进行限定，例如info：name，info：age。

3、极易扩展

Hbase的扩展性主要体现在两个方面，一个是基于上层处理能力（RegionServer）的扩展，一个是基于存储的扩展（HDFS）。通过横向添加RegionSever的机器，进行水平扩展，提升Hbase上层的处理能力，提升Hbsae服务更多Region的能力。

4、 数据多版本

数据多版本：每个单元中的数据可以有多个版本，默认情况下，版本号自动分配，版本号就是单元格插入时的时间戳

5、稀疏

稀疏主要是针对Hbase列的灵活性，在列族中，你可以指定任意多的列，在列数据为空的情况下，是不会占用存储空间的。

**缺点**

1）原生不支持SQL

SQL查询也是HBase的一个弱项，虽然HBase是一个非关系型数据库但是它不支持SQL语句，不过这块可以通过引入Phoenix解决，Phoenix是专为HBase设计的SQL层。

2）原生不支持二级索引

单一RowKey固有的局限性决定了它不可能有效地支持多条件查询，只支持按照Row key来查询，因此正常情况下对非Rowkey列做查询比较慢。所以，我们一般会选择一个HBase二级索引解决方案，目前比较成熟的解决方案是Phoenix，此外还可以选择Elasticsearch/Solr等搜索引擎自己设计实现。

3）数据分析能力弱

数据分析是HBase的弱项，比如聚合运算、多维度复杂查询、多表关联查询等。所以，我们一般在HBase之上架设Phoenix或Spark等组件，增强HBase数据分析处理的能力。

 

##  Hbase的数据模型★★★★★

> 问过的一些公司：顺丰，科大讯飞，海康威视
>

**1）Name Space**

命名空间，类似于关系型数据库的 DatabBase 概念，每个命名空间下有多个表。HBase有两个自带的命名空间，分别是 hbase 和 default，hbase 中存放的是 HBase 内置的表，default 表是用户默认使用的命名空间。

**2）Region**

类似于关系型数据库的表概念。不同的是，HBase 定义表时只需要声明列族即可，不需要声明具体的列。这意味着，**往 HBase 写入数据时，字段可以动态、按需指定**。因此，和关系型数据库相比，HBase 能够轻松应对字段变更的场景。

**3）Row**

HBase 表中的每行数据都由一个 **RowKey** 和多个 **Column**（列）组成，数据是按照 RowKey的字典顺序存储的，并且查询数据时需要根据 RowKey 进行检索，所以 RowKey 的设计十分重要。

**4）Column**

HBase 中的每个列都由 Column Family(列族)和 Column Qualifier（列限定符）进行限定，例如 info：name，info：age。**建表时**，只需指明列族，而列限定符无需预先定义。

**5）Time Stamp**

用于标识数据的不同版本（version），每条数据写入时，如果不指定时间戳，系统会自动为其加上该字段，其值为写入 HBase 的时间。

**6）Cell**

一个列中可以存储多个版本的数据。而每个版本就称为一个单元格（Cell）。cell 中的数据是没有类型的，全部是字节码形式存贮 由{rowkey, column Family：column Qualifier, time Stamp} 唯一确定的单元。

[我终于看懂了HBase，太不容易了... - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/145551967)

 

## 多版本数据过期-和-删除命令

HBase 的删除操作并不会立即将数据从磁盘上删除，删除操作主要是对要被删除的数据打上标记。---删除命令

> 当执行删除操作时，HBase 新插入一条相同的 KeyValue 数据，但是使 keytype=Delete，这便意味着数据被删除了，直到发生 Major compaction 操作时，数据才会被真正的从磁盘上删除，删除标记也会从StoreFile删除。
>
> hbase删除数据一般有两个时机，一是flush的时候，如果**数据都还在同一个memstore里面**，那flush不会刷写**覆盖掉的数据**和**delete标记的数据**，**但是delete标记会保留**？？？？？？。二是

major compact的时候。多个hfile文件中相同cell只会把最新的一个版本的数据放到新的hfile中，并且**会**清理掉过期和删除的数据。

 

## **HBase的rowkey设计原则 ** ★★★★★

**1、rowkey长度原则**

Rowkey是一个二进制码流，Rowkey的长度被很多开发者建议说设计在10~100个字节，不过建议是越短越好，不要超过16个字节。

原因如下：

1）数据的持久化文件HFile中是按照**Key Value** 存储的，**如果Rowkey过长**比如100个字节，1000万列数据光Rowkey就要占用100*1000 万=10亿个字节，将近1G数据，**这会极大影响 HFile的存储效率**；

2）MemStore将缓存部分数据到内存，如果 Rowkey字段过长内存的有效利用率会降低，系统将无法缓存更多的数据，这会降低检索效率。

**2、rowkey散列原则**

**散列将会提高数据均衡分布在每个Regionserver实现负载均衡的几率**。如果没有散列字段，首字段直接是时间信息将产生所有新数据都在一个RegionServer上堆积的热点现象，这样在做数据检索的时候负载将会集中在个别 RegionServer，降低查询效率。

**3、rowkey唯一原则**

必须在设计上保证其唯一性。因为数据会按照rowkey排序

> rowkey是按照字典顺序排序存储的，因此，设计rowkey的时候，要充分利用这个排序的特点，将经常读取的数据存储到一块，将最近可能会被访问的数据放到一块。（MemStore中的数据按RowKey字典顺序排序、HFile中的数据按RowKey字典顺序排序）

**如何设计**

（1）生成随机数、hash、散列值

（2）字符串反转

> Phoenix表的主键，对应到Hbase的row key

 

## hbase的读写流程  ★★★★★

**写流程**

![image-20220514213018835](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220514213018835.png)

1）Client 先访问 zookeeper，获取 hbase:meta 表（元数据）位于哪个 Region Server。

2）访问对应的 Region Server，获取 hbase:meta 表，根据写请求的 namespace:table/rowkey， 查询出目标数据要插入哪个 Region Server 中的哪个 Region 中。并将该 table 的 region 信息以 及 meta 表的位置信息缓存在客户端的 meta cache，方便下次访问。（客户端缓存）

3）与目标 Region Server 进行通讯；

4）将数据顺序写入（追加）到 WAL；

5）将数据写入对应的 MemStore（写缓存），数据会在 MemStore 进行排序；

6）向客户端发送 ack；

7）等达到 MemStore 的刷写时机后，将数据刷写到 HFile。

[聊一聊 HBase 是如何写入数据的？ - Data跳动 - 博客园 (cnblogs.com)](https://www.cnblogs.com/datadance/p/16284653.html)

**读流程**

![image-20220514213240077](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220514213240077.png)

1）Client 先访问 zookeeper，获取 hbase:meta 表位于哪个 Region Server。

2）访问对应的 Region Server，获取 hbase:meta 表，根据读请求的 namespace:table/rowkey，查询出目标数据位于哪个 Region Server 中的哪个 Region 中。并将该 table 的 region 信息以及 meta 表的位置信息缓存在客户端的 meta cache，方便下次访问。

3）与目标 Region Server 进行通讯；

4）分别在 MemStore，Block Cache（读缓存）， 和 Store File（HFile）中查询目标数据，并将查到的所有数据进行合并。此处所有数据是指同一条数据的不同版本（time stamp）或者不同的类型（Put/Delete）。

5） 将从文件中查询到的数据块（Block，HFile 数据存储单元，默认大小为 64KB）缓存到Block Cache。

6）将合并后的**最终结果**返回给客户端。（合并后会有一个筛选）

 

[一个HBase查询问题引发的思考，作为HBase使用者这个问题你知道答案吗?_梦回从前的博客-CSDN博客_hbase 查询问题](https://blog.csdn.net/microGP/article/details/124348673)

## **Phoenix二级索引**

在Hbase中，按字典顺序排序的rowkey是一级索引。不通过rowkey来查询数据时需要过滤器来扫描整张表。通过二级索引，这样的场景也可以轻松定位到数据。

二级索引的原理通常是（在写入时）针对某个字段和rowkey进行绑定，查询时先根据这个字段查询到rowkey，然后根据rowkey查询数据，二级索引也可以理解为查询数据时多次使用索引的情况。

 

```
create index USERS_TEST_IDX0 on "users_test ("info".USER_NAME)
```

 

> ![image-20220624100421979](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220624100421979.png)

[Phoenix创建二级索引 - 简书 (jianshu.com)](https://www.jianshu.com/p/8155bf732b82)

 

## **HBase和Phoenix的区别**

**Phoenix 是专门为Hbase设计的SOL层**

在Phoenix中建的表，在HBase里是可以查到的，而在HBase里建的表，Phoenix中是查看不到的。

Phoenix支持Join操作，而HBase不支持Join操作，所以可以通过Phoenix来操作HBase。

 

## **HBase的RegionServer宕机以后怎么恢复的？**

> 问过的一些公司：海康
>

参考答案：

**1、HBase常见故障**

导致RegionServer故障的原因：

- FullGc引起长时间停顿


- HBase对Jvm堆内存管理不善，未合理使用堆外内存


- Jvm启动参数配置不合理


- 业务写入或吞吐量太大


- 写入读取字段太大


- HDFS异常 : 读取写入数据都是直接操作hdfs的，若hdfs发生异常，会导致region server直接宕机


- 机器宕机
  - 物理节点直接宕机
  - 虚拟云主机不稳定，包括网络环境等

**2、HBase常见故障**

**Master恢复：**

- Master主要负责实现集群的负载均衡和读写调度，没有直接参与用户的请求，所以整体负载并不高

- 热备方式实现Master高可用，zookeeper上进行注册

- active master会接管整个系统的元数据管理任务，zk以及meta表中的元数据，相应用户的管理指令，创建、删除、修改，merge region等

**RegionServer恢复：**

- RegionServer宕机，HBase会检测到（master通过zk）

- **Master将宕机RegionServer上所有region重新分配到集群中其它正常的RegionServer上**

- **根据HLog进行丢失数据恢复，恢复之后对外提供服务**

**大致流程：**

1）master通过zk实现对RegionServer的宕机检测。RegionServer会周期性的向zk发送心跳，超过一定时间，zk会认为RegionServer离线，发送消息给master

2）切分为持久化的日志，所有region的数据都混合存储在同一个hlog文件里（一个RegionServer一个hlog），为了使这些数据能够按照region进行组织回放，需要将hlog日志进行切分再合并，同一个region的数据合并在一起，方便后续按照region进行数据恢复。

3）master重新分配宕机regionserver上的所有region,regionserver宕机后，所有region处于不可用状态，所有路由到这些region上的请求都会返回异常。异常情况比较短暂，master会将这些region分配到其它regionserver上。

4）回放HLog日志补救数据

5）恢复完成，对外提供读写服务

**HBase故障恢复流程总结如下：**

故障检测

数据切分

region上线

数据回放

 

## **HBase的预分区**

问过的一些公司：美团

预分区是指**每一个region**维护着startRowKey与endRowKey，如果加入的数据符合某个region维护的rowKey范围，则该数据交给这个region维护。那么依照这个原则，我们可以将数据所要投放的分区提前大致的规划好，以提高HBase性能。

 

## hbase为什么读很快   ★★★★★

> 其实hbase的读性能不如写性能，但是hbase做了一些读性能的优化，使得hbase读性能也不俗；
>

根据读取的rowkey可以直接定位到Region server和Region；HBase读取首先会先从内存中的MemStore中查找，然后在读缓存（BlockCache）中查找，它采用了LRU（最近最少使用算法），在这两个地方读取都是很快的；最后，加载HFile中的内容，定位到具体Hfile时，读取HFile速度也不俗，因为它使用了LSM树型结构（而不是B或B+树），这使得hbase可以使用磁盘顺序读取的方式来读数据；并且HFile磁盘文件是会进行合并的  这又节省了寻道开销。

 

> 写很快：写预写日志HLOG **顺序写**（追加）、写HFile相当于写内存

## LSM 树

LSM树的设计思想非常朴素：**将对数据的修改增量保持在内存中，达到指定的大小限制后再使用归并排序的方式将内存内的数据合并追加到磁盘**，所以写入性能是比较高的，读取时可能需要先看是否命中内存，否则需要访问较多的磁盘文件，牺牲了部分读性能。但是好在磁盘文件会进行合并，来降低寻找文件次数 且读磁盘是顺序读；此外还可以开始布隆过滤器优化；

 

**LSM树原理把一棵大树拆分成N棵小树，它首先写入内存中，随着小树越来越大，内存中的小树会flush到磁盘中，磁盘中的小树定期可以做merge操作（归并排序过程），合并成一棵大树。**

 

**关键读写流程**

[LSM树 - 简书 (jianshu.com)](https://www.jianshu.com/p/6043aaaccd8a)

 

# Mysql

## 非关系型数据库（NOSQL）和关系型数据库（SQL）区别 ★★★★★

1、**关系型数据库** 就是由二维表及其之间的关系组成的一个数据组织。存储的是结构化的数据；**Oracle、mysql...**

**优点：**

1）易于维护：都是使用表结构，格式一致；

2）使用方便：SQL语言通用，可用于复杂查询（多表查询）；

**缺点：**

1）读写性能比较差，尤其是海量数据的高效率读写；

2）固定的表结构，灵活度稍欠；

3）高并发读写需求下，传统关系型数据库来说，硬盘I/O是一个很大的瓶颈。

 

2、**非关系型数据库**又被称为 NoSQL（Not Only SQL )，意为不仅仅是 SQL。通常指数据以对象的形式存储在数据库中，而对象之间的关系通过对象自身的属性来决定，常用于存储非结构化的数据。 **hbase、redis...**

**优点：**

1）格式灵活：存储数据的格式可以是key,value形式、文档形式、图片形式等等，使用灵活，应用场景广泛，而关系型数据库则只支持基础类型。

2）速度快：nosql可以使用硬盘或者随机存储器作为载体，而关系型数据库只能使用硬盘；

3）高扩展性；

4）成本低：nosql数据库部署简单，基本都是开源软件。

**缺点**：

1）不提供sql支持，学习和使用成本较高；

2）无事务处理；

3）数据结构相对复杂，复杂查询方面稍欠。

 

 

## 1.请说下你对 MySQL 架构的了解？

基本架构图

![image-20211212104409534](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211212104409534.png)

MySQL 可以分为 Server 层和存储引擎两部分。

Server 层包括：
连接器、查询缓存、分析器、优化器、执行器等，涵盖了 MySQL 的大多数核心服务功能，以及所有的内置函数（如：日期、时间、数学和加密函数等），
所有跨存储引擎的功能都在这一层实现，比如：存储过程、触发器（用来保证数据完整性）、视图等等，
还有一个通用的日志模块 binglog 。

存储引擎层负责：
数据的存储和提取。
其架构是插件式的，支持 InnoDB、MyISAM 等多个存储引擎。从 MySQL5.5.5 版本开始默认的是InnoDB，但是在建表时可以通过 engine = MyISAM 来指定存储引擎。
不同存储引擎的表数据存取方式不同，功能也不同，但是共用一个 Server 层。

 

## 2.一条 SQL 语句在数据库框架中的执行流程？★★★★★

### **查询语句**

1. 先检查该语句是否有权限，如果没有权限，直接返回错误信息，如果有权限，在 MySQL8.0 版本以前，会先查询缓存，缓存中有数据直接返回（以这条 sql 语句为 key 在内存中查询是否有结果），没有则执行以下步骤：
2. 分析器进行词法分析（关键字等）和语法分析
3. 优化器进行优化（按照mysql认为的最优化语法进行优化）
4. 执行器调用数据库引擎接口，返回引擎的执行结果

> 查询缓存缺点（8.0以后不走查询缓存的原因）
>
> 对于更新比较频繁的表，查询缓存的命中率很低，因为只要一个表有更新操作，那么这个表的查询缓存就会被清空。如果刚缓存了一个查询结果很大的数据，还没被使用的时候，刚好这个表有更新操作，查询缓冲就被清空了，相当于缓存了个寂寞

 

### 更新语句--两阶段提交 ★★★

更新语句先要查询，也就是上面的查询过程

查询到需要修改的语句后，更改字段值，然后调用引擎 API 接口写入这一行数据，InnoDB 引擎把数据保存在内存中，同时记录 redo log（重做日志），将 redo log 对应的事务状态设置为 prepare，然后将 redo log 刷新到磁盘；通知执行器；

执行器收到通知后记录 binlog（归档日志），然后将 binlog 刷新到磁盘，最后调用引擎接口，提交 redo log 为提交状态（还会有一次刷盘）。

> redo log  在更新数据之前写入磁盘；数据在后面的某个时刻由后台线程写入磁盘；
>
> 这里还需要说明一点，因为MySQL的innodb存储引擎时需要支持崩溃恢复的，依赖prepare阶段的redo log ，所以，如果innodb_flush_logs_at_trx_commit的值是1，MySQL会在redo log的prepare阶段就进行一次持久化redo log的fsync操作

 

## 为什么要两阶段提交 ★★★★★

- **先写 redo log 直接提交，然后写 binlog**，假设写完 redo log 后，机器挂了，binlog 日志没有被写入，那么机器重启后，这台机器会通过 redo log 恢复数据，但是这个时候 bingog 并没有记录该数据，后续进行机器备份的时候，就会丢失这一条数据，同时主从同步也会丢失这一条数据。

- **先写 binlog，然后写 redo log**，假设写完了 binlog，机器异常重启了，由于没有 redo log，本机是无法恢复这一条记录的，但是 binlog 又有记录，那么和上面同样的道理，就会产生数据不一致的情况。

如果采用 redo log 两阶段提交的方式就不一样了，写完 binglog 后，然后再提交 redo log 就会防止出现上述的问题，从而保证了数据的一致性。那么问题来了，有没有一个极端的情况呢？假设 redo log 处于预提交状态，binglog 也已经写完了，这个时候发生了异常重启会怎么样呢？ 这个就要依赖于 MySQL 的处理机制了，MySQL 的处理过程如下：

- 如果 redo log 里面的事务是完整的，也就是已经有了 commit 标识，则直接提交；
- 如果 redo log 里面的事务只有完整的 prepare，则判断对应的事务 binlog 是否**存在并完整**：
  a. 如果是，则提交事务；
  b. 否则，回滚事务

> ### MySQL 怎么知道 binlog 是完整的?
>
> 回答：一个事务的 binlog 是有完整格式的：
>
> - statement 格式的 binlog，最后会有 COMMIT；
> - row 格式的 binlog，最后会有一个 XID event。
>
> 另外，在 MySQL 5.6.2 版本以后，还引入了 binlog-checksum 参数，用来验证 binlog 内容的正确性。对于 binlog 日志由于磁盘原因，可能会在日志中间出错的情况，MySQL 可以通过校验 checksum 的结果来发现。所以，MySQL 还是有办法验证事务 binlog 的完整性的。
>
> ### redo log 和 binlog 是怎么关联起来的?
>
> 回答：它们有一个共同的数据字段，叫 **XID**。
> 崩溃恢复的时候，会按顺序扫描 redo log：
>
> - 如果碰到既有 prepare、又有 commit 的 redo log，就直接提交；（已经标识为commit 但是提交失败了？）
> - 如果碰到只有 parepare、而没有 commit 的 redo log，就拿着 XID 去 binlog 找对应的事务。

 

## 3.MyISAM 和 InnoDB 存储引擎的区别 ★★★★★

1. 事务：MyISAM不支持事务，InnoDB支持事务；
2. > 全文索引：MyISAM 支持全文索引，InnoDB 5.6 之前不支持全文索引；
3. 关于 count()：MyISAM会直接存储总行数，InnoDB 则不会，需要按行扫描。意思就是对于 select count() from table; 如果数据量大，MyISAM 会瞬间返回，而 InnoDB 则会一行行扫描；
4. 外键：MyISAM 不支持外键，InnoDB 支持外键；
5. 锁：MyISAM 只支持表锁，InnoDB 可以支持行锁。
6. **MVCC**（Multi-Version Concurrency Control （多版本并发控制））。MyISAM 不支持，而 InnoDB 支持。

 

## 4.谈谈你对MVCC的了解？★★★★★

多版本并发控制（MVCC）是一种用来解决读-写冲突的无锁并发控制，也就是为事务分配单向增长的事务版本号，在某个事务对一条记录进行操作的时候，需要查看这一条记录的隐藏列中的事务版本id，比对事务id并根据事物隔离级别去判断读取哪个版本的数据。

**事务版本号：**事务每次开启前，都会从数据库获得一个**自增**长的事务ID，可以从事务ID判断事务的执行先后顺序。这就是事务版本号。

**隐式字段**： 对于InnoDB存储引擎，每一行记录都有两个隐藏列**trx_id**、**roll_pointer**，如果表中没有主键和非NULL唯一键时，则还会有第三个隐藏的主键列**row_id**。

![image-20211217201556296](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211217201556296.png)

**undo log回滚日志**，用于记录数据被修改前的信息。在表记录修改之前，会先把数据拷贝到undo log里，如果事务回滚，即可以通过undo log来还原数据；（undo log用途：1. 事务回滚时，保证原子性和一致性；2. 用于MVCC快照读）

**版本链**：多个事务并行操作某一行数据时，不同事务对该行数据的修改会产生多个版本，然后通过回滚指针（roll_pointer），连成一个链表，这个链表就称为**版本链**，先前版本的数据再undo日志中；

![image-20211217204500825](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211217204500825.png)

 

**快照读和当前读**

**快照读：** 读取的是记录数据的可见版本（有旧的版本）。不加锁,普通的select语句都是快照读,如：

```
select * from core_user where id > 2;
```

**当前读**：读取的是已经完成提交的最新的版本数据，update类型、显式加锁的都是当前读

```
select * from core_user where id > 2 for update;
select * from account where id>2 lock in share mode;
```

 

基于MVCC的读是快照读，会创建一个读视图来讲进行可见性判断

**Read View（读视图）**：**进行可见性判断**

几个重要的属性：

- m_ids:当前系统中那些活跃(**未提交**)的读写事务ID, 它数据结构为一个List。
- min_limit_id:表示在生成ReadView时，当前系统中活跃的读写事务中最小的事务id，即m_ids中的最小值。
- max_limit_id:表示生成ReadView时，系统中应该分配给下一个事务的id值。
- creator_trx_id: 创建当前read view的事务ID

**Read view 匹配条件规则**如下：

1. 如果数据事务ID `trx_id < min_limit_id`，表明生成该版本的事务在生成Read View前，已经提交(因为事务ID是递增的)，所以该版本可以被当前事务访问。
2. 如果`trx_id>= max_limit_id`，表明生成该版本的事务在生成ReadView后才生成，所以该版本不可以被当前事务访问。
3. 如果 `min_limit_id =<trx_id< max_limit_id`,需要分2种情况讨论：在数组内（只有自己可读）

> - （1）.如果`m_ids`包含`trx_id`,则代表Read View生成时刻，这个事务还未提交，但是如果数据的`trx_id`等于`creator_trx_id`的话，表明数据是自己生成的，因此是**可见**的。
> - （2）如果`m_ids`包含`trx_id`，并且`trx_id`不等于`creator_trx_id`，则Read   View生成时，事务未提交，并且不是自己生产的，所以当前事务也是**看不见**的；

故：InnoDB 实现MVCC，是通过` Read View+ Undo Log` 实现的，Undo Log 保存了历史快照，Read View可见性规则帮助判断当前版本的数据是否可见。

 

**查询一条记录，基于MVCC，是怎样的流程**

1. 获取事务自己的版本号，即事务ID
2. 获取Read View
3. 查询目标数据，然后与Read View中的事务版本号进行比较。
4. 如果不符合Read View的可见性规则， 即就需要Undo log中历史数据 ;
5. 最后返回符合规则的数据

[看一遍就理解：MVCC原理详解 - 掘金 (juejin.cn)](https://juejin.cn/post/7016165148020703246)

 

## 5.MySQL锁机制与 InnoDB 锁种类（1）

### 表级锁与行级锁

- **表级锁：** MySQL 中锁定 **粒度最大** 的一种锁，对当前操作的整张表加锁，实现简单，资源消耗也比较少，加锁快，不会出现死锁。其锁定粒度最大，触发锁冲突的概率最高，并发度最低，MyISAM 和 InnoDB 引擎都支持表级锁
- **行级锁：** MySQL 中锁定 **粒度最小** 的一种锁，只针对当前操作的行进行加锁。 行级锁能大大减少数据库操作的冲突。其加锁粒度最小，并发度高，但加锁的开销也最大，加锁慢，会出现死锁。

 

**死锁场景：**[MySQL 死锁了，怎么办？ | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/mysql/lock/deadlock.html#死锁的发生)

[字节面试：加了什么锁，导致死锁的？ | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/mysql/lock/show_lock.html#准备工作)

###  **InnoDB 存储引擎的锁种类有三种**

- Record lock：记录锁，单个行记录上的锁
- Gap lock：间隙锁，锁定一个范围，不包括记录本身
- Next-key lock：record+gap  临键锁，锁定一个范围，包含记录本身；左开右闭

>  间隙锁在本质上是不区分共享间隙锁或互斥间隙锁的，而且间隙锁是不互斥的，即两个事务可以同时持有包含共同间隙的间隙锁。
>
> 这里的共同间隙包括两种场景：
>
> 其一是两个间隙锁的间隙区间完全一样；
> 其二是一个间隙锁包含的间隙区间是另一个间隙锁包含间隙区间的子集。

 

## 6.介绍一下事务的特性？ （1）★★★★★

**原子性**（`Atomicity`） ： 事务是最小的执行单位，不允许分割。事务的原子性确保动作要么全部完成，要么完全不起作用；

**一致性**（`Consistency`）： 执行事务前后，数据库保持一致性状态；

**隔离性**（`Isolation`）： 并发访问数据库时，一个用户的事务不被其他事务所干扰，各并发事务之间数据库是独立的；

**持久性**（`Durability`）： 一个事务被提交之后。它对数据库中数据的改变是持久的，即使数据库发生故障也不应该对其有任何影响。

 

实现原理（方式）：

以 MySQL 的 InnoDB 引擎为例

MySQL InnoDB 引擎使用 **redo log(重做日志)** 保证事务的**持久性**，使用 **undo log(回滚日志)** 来保证事务的**原子性**。

MySQL InnoDB 引擎通过 **锁机制**、**MVCC** 等手段来保证事务的隔离性（ 默认支持的隔离级别是 **`REPEATABLE-READ`** ）。

保证了事务的持久性、原子性、隔离性之后，一致性才能得到保障

 

## 如何实现事务的持久性  ★

**WAL 预写日志机制；这个日志就是redo log** ; 日志先到磁盘；然后实际数据到磁盘；实际数据到磁盘之前崩溃的话可以通过redo log恢复；保证持久性

看下上面的更新语句的执行流程；

 

## 7.并发事务带来哪些问题？（1）★★★★★

脏读、丢失修改、不可重复读、幻读

**脏读（Dirty read）**：一个事务正在访问数据，并进行了修改，但未提交到数据库，这时另外一个事务，读取到这个未提交的数据，这就是脏读。

**丢失修改（Lost to modify）**：指在一个事务修改一个数据时，另外一个事务也访问了该数据，那么如果在第一个事务中修改了这个数据后，第二个事务也修改了这个数据。这样第一个事务内的修改结果就被丢失，因此称为丢失修改

**不可重复读（Unrepeatable read）**：指在一个事务内多次读同一数据不一致。在这个事务还没有结束时，另一个事务也访问该数据并做了修改。那么，在第一个事务中的两次读数据之间，读取的数据可能不太一样，出现了在一个事务中两次读取到的数据不一致的情况，因此称为不可重复读。

**幻读（Phantom read）:** 幻读与不可重复读类似。它发生在一个事务（T1）读取了几行数据，接着另一个并发事务（T2）插入了一些数据时。在随后的查询中，第一个事务（T1）就会发现多了一些原本不存在的记录，就好像发生了幻觉一样，所以称为幻读。

 

## 8. 事务的隔离级别有哪些?（1）★★★★★

**READ-UNCOMMITTED(读取未提交)：** 最低的隔离级别，允许读取尚未提交的数据变更，**可能会导致脏读、幻读或不可重复读**。

**READ-COMMITTED(读取已提交)：** 允许读取并发事务已经提交的数据，**可以阻止脏读，但是幻读或不可重复读仍有可能发生**。

**REPEATABLE-READ(可重复读)：** 对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修改，**可以阻止脏读和不可重复读，但幻读仍有可能发生**。是MySQL的默认隔离级别。

**SERIALIZABLE(可串行化)：** 最高的隔离级别，完全服从 ACID(原子性、隔离性、一致性、持久性) 的隔离级别。所有的事务依次逐个执行，这样事务之间就完全不可能产生干扰，也就是说，**该级别可以防止脏读、不可重复读以及幻读**。但是这将严重影响程序的性能。通常情况下也不会用到该级别。

 

## REPEATABLE-READ(可重复读)不能完美解决幻读

select 类型（快照读）的幻读是可以解决的；通过mvcc机制避免了这种幻读现象；当前读不行；

快照读: 我们读到的数据可能是历史数据，不是数据库最新的数据。这种读取历史数据的方式，我们叫它快照读 (snapshot read)，而读取数据库最新版本数据的方式，叫当前读 (current read)。

**select 快照读**

当执行select操作是innodb默认会执行快照读，会记录下这次select后的结果（多次select共用一个视图），**之后select 的时候就会返回这次快照的数据**，即使其他事务提交了不会影响当前select的数据，这就实现了可重复读了。也解决了幻读

 

> ![image-20220627103906455](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220627103906455.png)

 

![image-20220613102623063](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220613102623063.png)

 

**这种不会发生**；

 

**update的幻读还是会发生**

**update当前读**（select 创建 read view的事务id 执行了**update更新了要查询的数据，并修改了事务Id为当前事务ID**）

![image-20220627143604743](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220627143604743.png)

对于会对数据修改的操作(update、insert、delete)都是采用当前读的模式。在执行这几个操作时会读取最新的版本号记录，写操作后把版本号改为了当前事务的版本号，所以**即使是别的事务提交的数据也可以查询到**。

![image-20220613103207739](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220613103207739.png)

**快照读依靠MVCC控制，当前读通过间隙锁解决**；

间隙锁可以解决这个问题

间隙锁：只有在Read Repeatable、Serializable隔离级别才有，就是锁定那些范围空间内的数据，假设锁定id>3的数据，id有3,4,5，那么4，5和后面的数字都会被锁定，像6,7...，为什么要这样？因为如果我们不锁定没有的数据，当加入了新的数据id=6，就会出现幻读，间隙锁避免了幻读。

 

 

## 9.数据库的三范式？（1）

- 1NF：强调的是列的原子性，即数据库表的每一列都是不可分割的原子数据项；

- 2NF：1NF 的基础之上，消除了非主键字段对于主键的部分函数依赖。

  > 部分函数依赖：通过AB能得出C，通过A也能得出C，或者通过B也能得出C，那么说C部分依赖于AB。

- 3NF：3NF 在 2NF 的基础之上，消除了非主键字段对于主键的传递函数依赖 。

  > 通过A得到B，通过B得到C，但是C得不到A，那么说C传递依赖于A。

 

 

## 10.drop、delete 与 truncate 区别？ （1）

drop(丢弃数据): `drop table 表名` ，直接将表都删除掉，在删除表的时候使用。

truncate (清空数据) : `truncate table 表名` ，只删除表中的数据，再插入数据的时候自增长 id 又从 1 开始，在清空表中数据的时候使用。

delete（删除数据） : `delete from 表名 where 列名=值`，删除某一行的数据，如果不加 where 子句和`truncate table 表名`作用类似。

**drop和truncate是DDL（Data Definition Language）语言，不可回滚，delete 是DML（Data Manipulation Language）语言，可回滚**

（DML只对表中的数据增删改查；DDL涉及表的定义和结构等的修改）

drop删除速度最快，delete删除速度慢，需要逐行删除，truncate删除速度快

 

DML 数据库操纵语言、 DDL 数据库定义语言、DQL 数据库查询语言、DCL 数据库控制语言

 

## 11.数据库的设计步骤？ （1）

**需求分析** : 分析用户的需求，包括数据、功能和性能需求。

**概念结构设计** : 主要采用 E-R 模型进行设计，包括画 E-R 图。

**逻辑结构设计** : 通过将 E-R 图转换成表，实现从 E-R 模型到关系模型的转换。

**物理结构设计** : 主要是为所设计的数据库选择合适的存储结构和存取路径。

**数据库实施** : 包括编程、测试和试运行

**数据库的运行和维护** : 系统的运行与数据库的日常维护

 

## 12.char和varchar的区别？ （1）

1. **char(n) ：**固定长度类型，比如：订阅 char(10)，当你输入”abc”三个字符的时候，它们占的空间还是 10 个字符，其他 7 个是空字符。char 优点：效率高；缺点：占用空间；适用场景：固定长度的数据字段，使用 char 非常合适。

2. **varchar(n) ：**可变长度，需要的字节数是每个值占用的字节再加上一个用来记录其长度的字节。

   （varchar(n)需要1到2个额外字节记录长度n的值当n<=255的时候，只需要1个字节记录即可（数据表示范围：0 ~ (2^8-1)，即0~255）；当n>255的时候，则需要2个字节存储n的值（（2^8）~ (2^16)-1，即256~65535）。

   varchar字段报错的实际值得长度保存在第一个或者前两个字节中。
    所以：
    如果varchar(255)，实际是需要1+255个字节的存储空间;
    如果varchar(256)，实际是需要2+256个字节的存储空间;）

3. **CHAR**的存储方式是，一个英文字符（ASCII）占用1个字节，一个汉字占用两个字节；而**VARCHAR**的存储方式是，一个英文字符占用2个字节，一个汉字也占用2个字节。

4. char最多可以存放255个字符

　 varchar的最大长度为65535个字节，varchar可存放的字符数跟编码有关

　（ 字符类型若为gbk，每个字符最多占2个字节，最大长度不能超过32766个字符

　 字符类型若为utf8，每个字符最多占3个字节，最大长度不能超过21845个字符）

所以，从空间上考虑 varcahr 比较合适；从效率上考虑 char 比较合适，二者使用需要权衡

 

## 13. varchar(10) 和 varchar(20) 的区别？

varchar(10) 中 10 的涵义最多存放 10 个字符，varchar(10) 和 varchar(20) 存储小于等于10个字符所占**磁盘**空间一样；但是对于**内存**来说，就是使用定义的长度，即20个字符空间。显然，这对于排序或者临时表(这些内容都需要通过内存来实现)作业会消耗更多的内存。

 

## 14.谈谈你对索引的理解 ？ ★★★

**目的**：索引的出现是为了提高数据的查询效率，就如同书的目录一样。

**优点** ：

- 使用索引可以大大加快 数据的检索速度（大大减少检索的数据量）。
- 通过创建唯一性索引，可以保证数据库表中每一行数据的唯一性。

**缺点** ：

- 创建和维护索引需要耗费许多时间。当对表中的数据进行增删改的时候，那么索引也需要动态的修改，会降低 SQL 执行效率。
- 索引需要使用物理文件存储，也会耗费一定空间。

**建立索引的原则：**

1. 在最频繁使用的、用以缩小查询范围或用于需要排序的字段上建立索引；

**不适合建立索引的情况**：

* 对于查询中**很少涉及**的列或者**重复值比较多的列**，不宜建立索引；
* 表数据太少的时候，不需要创建索引
* 对于一些特殊的数据类型，不宜建立索引，比如：文本字段（text），这是因为，这些列的数据量要么相当大，要么取值很少。
* 频繁更新的字段不适合创建索引，因为每次更新不单单是更新记录，还会更新索引，保存索引文件；

[索引常见面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/mysql/index/index_interview.html#什么时候需要-不需要创建索引)

 

## 15.索引的底层使用的是什么数据结构？（1）

索引的数据结构和具体存储引擎的实现有关，在MySQL中使用较多的索引有 Hash 索引、B+树索引等。**而我们经常使用的 InnoDB 存储引擎的默认索引实现为 B+ 树索引**。

> MyISAM也是B+树

 

## 索引为什么能加快查询速度 ★★★

**DB在执行一条Sql语句的时候，默认的方式是根据搜索条件进行全表扫描，遇到匹配条件的就加入搜索结果集合。 如果我们对某一字段增加索引， 查询时就会先去索引列表中查询，大大减少遍历匹配的行数**，所以能明显增加查询的速度 。 我们的索引列表是B类树的数据结构，查询的时间复杂度为O(log2N)，定位到特定值得行就会非常快，所以其查询速度就会非常快。**原来O(n)；现在O(logn)**

 

## 16.为什么 InnoDB 存储引擎的默认索引实现为 B+ 树索引，而不用哈希索引？★★★★★

1. 哈希索引有哈希冲突

2. **Hash 索引不支持顺序和范围查询(Hash 索引不支持顺序和范围查询是它最大的缺点**）

```sql
SELECT * FROM tb1 WHERE id < 500;
```

**B+ 树索引直接遍历比 500 小的叶子节点就够了, 哈希索引的话需要哈希计算，性能太低。**

 

## 17.B树和B+树  ★★★★★

### B树

B树（B-树），是一种多路搜索树（并非二叉的），每个节点可存储**多个关键字和多个指针**：

对于M阶B树：

- **定义任意非叶子节点最多可以有M（且M>2）个儿子节点**；则根节点的儿子数为：[2，M]；
- 除根节点外的非叶子节点的儿子数为[M/2，M]；
- **每个结点存放至少M/2 - 1 且至多M -1 个关键字**；（至少为2）；
- **非叶子结点的关键字个数 = 指向子节点的指针数 -1**；
- 非叶子节点的关键字：K[1],K[2],K[3],…,K[M-1];且K[i] < K[i +1]; 关键字有序
- 非叶子结点的指针：P[1], P[2], …, P[M]；p[i]指向关键字值属于**（**K[i-1], K[i]**)**  的子树
- **所有节点关键字都是有序的、任何一个关键字出现且只出现在一个结点中，所有叶子结点位于同一层**；
  如(M = 3)


![image-20211214205814021](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211214205814021.png)

**B-树的搜索**，从根结点开始，对结点内的关键字（有序）序列进行二分查找，如果命中则结束，否则进入查询关键字所属范围的儿子结点；重复，直到所对应的儿子指针为空，或已经是叶子结点；

B-树的特性：

1. 关键字集合分布在整颗树中；
2. 任何一个关键字出现且只出现在一个结点中；
3. 搜索有可能在非叶子结点结束；
4. 其搜索性能等价于在关键字全集内做一次二分查找；

**B树的高度**

一棵含有N个总关键字数的m阶的B树的最大高度是多少？

　　log（m/2）(N+1)/2 + 1 ，log以（m/2）为低，(N+1)/2的对数再加1

**磁盘读取的I/O次数为：最大高度（h）：h-1；因为根节点常驻内存，剩下h-1层在磁盘，一层一次I/O次数；**

 

### B+树


B+树是B树的变体，**B+ 树是基于 B 树和叶子节点顺序访问指针进行实现，它具有 B 树的平衡性，并且通过顺序访问指针来提高区间查询的性能。**也是一种多路搜索树：其定义基本与B-树同，除了：

1.**非叶子结点的子树指针与关键字个数相同**；

2.非叶子结点的子树指针P[i]，指向关键字值属于**[**K[i], K[i+1]**)**的子树（B-树是开区间）；

3.**为所有叶子结点增加一个链指针**；

4.**所有关键字都在叶子结点出现**；

M=3时：

![image-20211214211606671](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211214211606671.png)

 

**B+的搜索**与B-树也基本相同，区别是B+树只有达到叶子结点才命中（B-树可以在非叶子结点命中），其性能也等价于在关键字全集做一次二分查找；（首先在根节点进行二分查找，找到一个 key 所在的指针，然后递归地在指针所指向的节点进行查找。直到查找到叶子节点，然后在叶子节点上进行二分查找，找出 key 所对应的 data。）

**B+树的特性：**

1.**所有关键字都出现在叶子结点的链表中，且链表中的关键字恰好是有序的**；

2.**不可能在非叶子结点命中**；

3.非叶子结点相当于是叶子结点的索引，**叶子结点相当于是存储（关键字）数据的数据层**；

对于B树和B+树：插入、删除操作会破坏平衡树的平衡性，因此在插入删除操作之后，需要对树进行一个分裂、合并、旋转等操作来维护平衡性。

 

## 18. 为什么 InnoDB 存储引擎选用 B+ 树而不是 B 树呢？★★★★★

1. **用 B+ 树不用 B 树考虑的是 IO 对性能的影响**，B 树的每个节点都存储数据，而 B+ 树只有叶子节点才存储数据，所以查找相同数据量的情况下，**B 树的高度更高，IO 更频繁。**

2. 因为 B+ 树索引的所有数据均存储在叶子节点，数据是按照顺序排列的，并且可以通过顺序访问指针来**提高区间查询的性能**

**那么 B+ 树使得范围查找，排序查找，分组查找以及去重查找变得异常简单**。而 B 树因为数据分散在各个节点，要实现这一点是很不容易的。

> (ps:B+ 树中各个页之间是通过双向链表连接的，叶子节点中的数据是通过单向链表连接的。MyISAM 中的 B+ 树索引实现与 InnoDB 中的略有不同。在 MyISAM 中，B+ 树索引的叶子节点并不存储数据，而是存储数据的文件地址)
>

（MySQL底层采用数据页存储数据，一页16k）

 

## 19.谈谈有哪些索引？

**从数据结构角度**

1. 树索引 (O(log(n)))
2. Hash 索引

**从物理存储角度**

1. 聚集索引（clustered index）
2. 非聚集索引（non-clustered index）

**逻辑角度**

主键索引

二级索引（辅助索引）

二级索引又分为：唯一索引，普通索引，前缀索引，联合索引，全文索引

**二级索引又称为辅助索引（属于非聚集索引），是因为二级索引的叶子节点存储的数据是主键。也就是说，通过二级索引，可以定位主键的位置。**

 

## 20.谈谈你对聚簇索引和非聚簇索引的理解？★★★★★

**聚簇索引**是对磁盘上实际数据重新组织以按指定的一个或多个列的值排序的一种索引机制。特点是存储数据的顺序和索引顺序一致。一般情况下主键会默认创建聚簇索引，且一张表只允许存在一个聚簇索引。

![image-20220614101326205](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614101326205.png)

**非聚簇索引**是索引顺序和磁盘上实际数据的顺序不一致的一种索引。（**二级索引属于非聚集索引**）

![image-20220614101350123](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614101350123.png)

**区别：**

- 聚集索引存储数据的顺序和索引顺序一致，非聚集索引不一致

- 聚集索引一个表只能有一个，而非聚集索引一个表可以存在多个

- 聚簇索引的叶节点就是数据节点。而非聚簇索引的叶节点仍然是索引节点，只不过有一个指针指向对应的数据块。

- 聚集索引查询数据比非聚集索引的速度快

  **非聚集索引可能会二次查询(回表)** :这应该是非聚集索引最大的缺点了。 当查到索引对应的**指针或主键**后（非聚集索引的叶子节点并不一定存放数据的指针， 因为二级索引的叶子节点就存放的是主键，根据主键再回表查数据），**可能**还需要根据指针或主键再到数据文件或表中查询；（覆盖索引的话，查询的字段正好是索引的字段不用回表查询。）

 

> **非聚集索引插入数据快于聚集索引的原因：**（有待商榷，了解即可）
>
> 在有主键的表中插入数据行，由于有主键唯一性的约束，所以需要保证插入的数据没有重复。聚集索引由于索引叶节点就是数据页，所以如果想检查主键的唯一性，需要遍历所有数据节点才行，但非聚集索引不同，由于非聚集索引上已经包含了主键值，所以查找主键唯一性，只需要遍历所有的索引页就行（索引的存储空间比实际数据要少），这比遍历所有数据行减少了不少IO消耗。这就是为什么主键上创建非聚集索引比主键上创建聚集索引在插入数据时要快的真正原因。
>

 

## 21.谈谈你对覆盖索引的理解？（1）

如果一个索引包含（或者说覆盖）所有需要查询的字段的值，我们就称之为“覆盖索引”。**覆盖索引即需要查询的字段正好是索引的字段，那么直接根据该索引，就可以查到数据了， 而无需回表查询。**

 

## 22.谈谈你对哈希索引的理解？ （1）

哈希表是键值对的集合，通过键(key)即可快速取出对应的值(value)，因此哈希索引可以快速检索数据（接近 O（1）），但是失去了有序性。无法用于排序与分组、只支持精确查找，无法用于部分查找和范围查找。

 

## 23.谈谈对最左前缀原则的理解？

MySQL 使用联合索引时，需要满足最左前缀原则

```java
1. 一个 2 列的索引 (name, age)，对 (name)、(name, age) 上建立了索引；
2. 一个 3 列的索引 (name, age, sex)，对 (name)、(name, age)、(name, age, sex) 上建立了索引。
```

**匹配的时候严格从左到右匹配。**

1. 最左前缀匹配原则会一直向右匹配直到遇到**范围查询（>、<、between、like）就停止匹配**，比如：a = 1 and b = 2 and c > 3 and d = 4 如果建立 (a, b, c, d) 顺序的索引，d 是用不到索引的。如果建立 (a, b, d, c) 的索引则都可以用到，a、b、d 的顺序可以任意调整。
2. = 和 in 可以乱序，比如：a = 1 and b = 2 and c = 3 , 建立 (a, b ,c) 索引可以任意顺序，MySQL 的**优化器会优化成索引可以识别的形式**。

>  select * from t where a=1 and b >1 and c=1;  #如果是建立(a,c,b)联合索引，则a,b,c都可以使用索引
>
> #优化器改写为 select * from t where a=1 and c=1 and b >1;

 

## 24.怎么知道创建的索引有没有被使用到？或者说怎么才可以知道这条语句运行很慢的原因?

使用 **Explain 命令来查看语句的执行计划**，MySQL 在执行某个语句之前，会将该语句过一遍查询优化器，之后会拿到对语句的分析，也就是执行计划，其中包含了许多信息。可以通过其中和索引有关的信息来分析是否命中了索引，例如：possilbe_key、key、key_len 等字段，分别说明了此语句可能会使用的索引、实际使用的索引以及使用的索引长度；根据查询执行计划也可以分析语句执行慢的原因。

 

## 25.什么情况下索引会失效？即查询不走索引？ ★★★

- 索引列参与表达式的计算、函数、类型转换
- %词语，like 模糊查询（%在前）
- 在 WHERE 子句中，如果在 OR 前的条件列是索引列，而在 OR 后的条件列不是索引列，那么索引会失效
- 正则表达式不使用索引
- MySQL 内部优化器会对 SQL 语句进行优化，如果优化器估计使用全表扫描要比使用索引快，则不使用索引。

 

## 索引如何优化 ★★★★★

- 在合适的字段上创建索引

- 前缀索引优化；

- 覆盖索引优化；

- 多个条件经常同时出现，可以考虑多个字段建立联合索引

- 主键索引最好是自增的；

- 索引最好设置为 NOT NULL

- 防止索引失效；

  [索引常见面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/mysql/index/index_interview.html#有什么优化索引的方法)

 

## 26.InnoDB引擎中的索引策略，了解过吗？

- 覆盖索引
- 最左前缀原则
- **索引下推**

索引下推优化是 MySQL 5.6 引入的， 可以在**索引遍历过程中，对索引中包含的字段先做判断，直接过滤掉不满足条件的记录，减少回表次数。**

 

## 27.查询性能的优化方法？

1. 优化查询语句，不规范或不合理的查询语句可能会及其影响性能

2. 缓存重复查询的数据：使用缓存可以避免在数据库中进行查询，特别在要查询的数据经常被重复查询时，缓存带来的查询性能提升将会是非常明显的。

3. 建立合适的索引，快得多的速度检索特定的行，尤其是在查询语句当中包含有MAX(),MIN()和ORDERBY这些命令的时候，性能提高更为明显。

 

## 28.如果一天SQL语句查询太慢，你会怎么做？★★★★★

1. 先根据经验调优，比如查看是否子查询过多（join替换）以及笛卡尔积是否存在，是不是selelct * 了，优化Sql结构，如去除冗余字段
2. 没有索引可以尝试创建索引；有索引的话检查索引是否被用到（索引失效），或者尝试索引结构是否可以优化
3. 之后   再用explain分析sql语句，查看执行计划，看看哪里还能优化改进；
4.  最后可开启慢查询日志，查看慢查询的 SQL。如果锁等待时间过长：检查锁粒度以及是否发生死锁；如果是数据量过大的话，可以分库分表

![image-20220614154047161](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614154047161.png)

 

## SQL调优问题总结（抛开硬件原因）★★★★★

1. **优化查询语句**，不规范或不合理的查询语句可能会及其影响性能

   -     选择合适的查询字段，尽量避免select *
-     避免笛卡尔积
   -     使用联合(UNION)来代替手动创建的临时表
-     where条件后不要再添加表达式计算等

2. 判断所作的操作是否涉及事务性，准确及时的使用事务也是一种调优手段

3. **使用合理的索引**，可以更快速度检索特定的行，尤其是在查询语句当中包含有MAX(),MIN()和ORDERBY这些命令的时候。

4. 使用 **Explain 命令**查询 SQL 语句执行计划  ★★★★★

   当`Explain` 与 `SQL`语句一起使用时，`MySQL` 会显示来自优化器关于SQL执行的信息。也就是说，`MySQL`解释了它将如何处理该语句

   > 包括如何连接表以及什么顺序连接表等
   >
   > - 表的加载顺序
   > - `sql` 的查询类型
   > - 可能用到哪些索引，哪些索引又被实际使用
   > - 表与表之间的引用关系

   `Explain` 执行计划包含字段信息如下：分别是 `id`、`select_type`、`table`、`partitions`、`type`、`possible_keys`、`key`、`key_len`、`ref`、`rows`、`filtered`、`Extra` **12**个字段。

   挑几个重点字段：

   -  `select_type`：表示 `select` 查询的类型，主要是用于区分各种复杂的查询，例如：`普通查询`、`联合查询`、`子查询`等，如果发现子查询过多就可以做调优；

   -  `key`：区别于`possible_keys`，key是查询中实际使用到的索引，若没有使用索引，显示为`NULL`

   -  `key_len`：表示查询用到的索引长度（字节数），原则上长度**越短越好** (调优点)。（while中使用的索引才会key_len）
   -  `ref`：哪些列或常量被用于查找索引列上的值；常见的有：`const`，`func`，`null`，字段名。如果查询条件使用了`表达式`、`函数`，或者条件列发生内部隐式转换，可能显示为`func`（调优点，查询条件中不应有过多表达式或函数计算）
   -  `rows`：以表的统计信息和索引使用情况，估算要找到我们所需的记录，需要读取的行数（行数过多可以limit）

 

## 29. MySQL 问题排查都有哪些手段？

1. 使用 show processlist 命令查看当前所有线程的连接信息；
2. 使用 Explain 命令查询 SQL 语句执行计划；
3. 开启慢查询日志，查看慢查询的 SQL。

 

## 30.MySQL 数据库 CPU 飙升到 500% 的话怎么处理？

1. 当 CPU 飙升到 500% 时，先用操作系统命令 top 命令观察是不是 mysqld 占用导致的，如果不是，找出占用高的进程，并进行相关处理。
2. 如果是 mysqld 造成的，通过 SHOW PROCESSLIST 查看正在运行的线程，是不是有消耗资源的 SQL 在运行，找出其中消耗高的 SQL，看看执行计划是否准确， index 是否缺失，或者是数据量太大造成。
3. 然后 kill 掉这些线程（同时观察 CPU 使用率是否下降），等进行相应的调整（比如说加索引、改 SQL、改内存参数）之后，再重新跑这些 SQL。
4. 若每个 SQL 消耗资源都不多，只是同一时间大量的 session 连进来导致 CPU 飙升，这种情况就需要分析为何连接数会激增，再做出相应的调整，比如说限制连接数等

 

## 31.什么是数据库的主从复制，为什么要主从复制？ ★★★★★

**MySQL 主从复制是指数据可以从一个MySQL数据库服务器主节点复制到一个或多个从节点**。（MySQL 默认采用**异步复制**方式，这样从节点不用一直访问主服务器来更新自己的数据，数据的更新可以在远程连接上进行，从节点可以复制主数据库节点中的所有数据库或者特定的数据库，或者特定的表）
主从复制是MySQL最重要的功能之一。对于多级复制，数据库服务器即可充当主机，也可充当从机。**MySQL主从复制的基础是主服务器对数据库修改记录二进制日志，从服务器通过主服务器的二进制日志自动执行更新。**

 

**为什么要主从复制/优点**

- 随着系统中业务访问量的增大，如果是单机部署数据库，就会导致I/O访问频率过高。有了主从复制，增加多个数据存储节点，将负载分布在多个从节点上，降低单机磁盘I/O访问的频率，提高单个机器的I/O性能；
- 一般会让主库负责写，从库负责读，这样**读写分离**，即使主库出现了锁表的情景，通过读从库也可以保证业务的正常运作；
- 从库可以实时从主库进行复制，这样就可以做数据的热备；

 


## 32.主从复制涉及到哪三个线程？★★★★★

主要涉及三个线程：binlog 线程、I/O 线程和 SQL 线程。

1. binlog 线程（log dump线程） ：负责将主服务器上的数据更改写入二进制日志（Bin log）中。
2. I/O 线程 ：负责从主服务器上读取二进制日志，并写入从服务器的重放日志（Relay log）中。
3. SQL 线程 ：负责读取relay log中的内容，解析成具体的操作并执行，最终保证主从数据的一致性。

![image-20211215153611116](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211215153611116.png)

 

[(1条消息) mysql主从复制（一主一从）配置，uuid重复，数据库主从复制失败_brother~海的博客-CSDN博客_mysql 主从uuid](https://blog.csdn.net/qq_53270893/article/details/124808544)

## 33.主从同步的延迟原因及解决办法？

**主从同步的延迟的原因：**

假如一个服务器开放 Ｎ 个连接给客户端，这样有会有大并发的更新操作, 但是从服务器的里面读取 binlog 的线程仅有一个， 当某个 SQL 在从服务器上执行的时间稍长或者由于某个 SQL 要进行锁表就会导致主服务器的 SQL 大量积压，未被同步到从服务器里。这就导致了主从不一致， 也就是主从延迟。

解决办法：

1. 采用更好的硬件设备
2. 增加从服务器，降低读的压力

3. 同步参数调整：主库是写，对数据安全性较高，比如sync_binlog=1，innodb_flush_log_at_trx_commit = 1 之类的设置是需要的。而slave则不需要这么高的数据安全，完全可以讲sync_binlog设置为0或者关闭binlog，innodb_flush_log_at_trx_commit 也可以设置为0来提高 SQL 的执行效率。

（sync_binlog=1，表示每次事务提交，MySQL都会把binlog刷写到磁盘，性能消耗大）；

（innodb_flush_log_at_trx_commit 默认值1的意思是每一次事务提交或事务外的指令都需要把日志写入（flush）硬盘，这是很费时的）

 

## 34.谈谈你对数据库读写分离的理解？

读写分离**常用代理方式**来实现，代理服务器接收应用层（用户）传来的读写请求，然后决定转发到哪个服务器。主服务器**处理写操作以及实时性要求比较高的读操作**，而从服务器处理读操作。

（ps: 读写分离常见方案？

- 应用程序根据业务逻辑来判断，增删改等写操作命令发给主库，查询命令发给备库。

- 利用中间件来做代理，负责对数据库的请求识别出读还是写，并分发到不同的数据库中。（如：amoeba，mysql-proxy））

 

**读写分离能提高性能的原因在于：**

1. 物理服务器增加，负荷增加
2. 主从服务器负责各自的读和写，极大程度缓解了锁的争用；
3. 增加冗余，提高可用性，当一台数据库服务器宕机后能通过调整另外一台从库来以最快的速度恢复服务

 

[(1条消息) mysql读写分离，以及保证保持数据一致性实现方案_JeekMrc的博客-CSDN博客_mysql读写分离如何保证数据同步](https://blog.csdn.net/JeekMrc/article/details/118887359)

![image-20220721203730764](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220721203730764.png)

 

## 35.MySQL的redo log，undo log，bin log都是干什么的？★★★★★★

**`redo log`（重做日志）**是`InnoDB`存储引擎独有的，用于记录事务操作的变化，**记录的是数据页的物理修改**，是两阶段提交的(不是某一行或某几行修改成怎样怎样，不管事务是否提交都会记录下来) 。它让`MySQL`拥有了崩溃恢复能力。

> 崩溃恢复时由 redo log和binlog 一起完成；写入binlog后再提交redo log

**`binlog` （归档日志）**是逻辑日志，记录内容是语句的原始逻辑，类似于“给 ID=2 这一行的 c 字段加 1”(记录SQL修改语句)，属于`MySQL Server` 层。不管用什么存储引擎，只要发生了表数据更新，都会产生 `binlog` 日志；`MySQL`数据库的**数据备份、主从复制等**都离不开`binlog`，需要依靠`binlog`来同步数据，保证数据一致性。

> MySQL 5.7.7 之前，binlog 的默认格式都是 STATEMENT，在 5.7.7 及更高版本中，binlog_format 的默认值才是 ROW

**undo log(回滚日志)** 来保证事务的**原子性**。在事务没提交之前，MySQL会先记录更新前的数据到 undo log日志文件里面，然后再执行相关的操作。如果执行过程中遇到异常的话，我们直接利用 **回滚日志** 中的信息将数据回滚到修改之前的样子。

[一条SQL语句在MySQL中如何执行的 (qq.com)](https://mp.weixin.qq.com/s?__biz=Mzg2OTA0Njk0OA==&mid=2247485097&idx=1&sn=84c89da477b1338bdf3e9fcd65514ac1&chksm=cea24962f9d5c074d8d3ff1ab04ee8f0d6486e3d015cfd783503685986485c11738ccb542ba7&token=79317275&lang=zh_CN%23rd)

![image-20220627095427981](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220627095427981.png)

[MySQL崩溃恢复功臣—Redo Log - 腾讯云开发者社区-腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1417482)

## 36.为什么要分库分表？

随着数据量增加，**增删改查的开销** 也会越来越大；另外，若不进行分布式部署，而一台服务器的 **资源** （CPU、磁盘、内存、IO 等）是有限的，最终数据库所能承载的数据量、数据处理能力都将遭遇瓶颈。所以，从 **性能** 和 **可用性** 角度考虑，会进行数据库拆分处理，具体地说，把原本存储于一个库的数据分块存储到多个库上，把原本存储于一个表的数据分块存储到多个表上，即 分库分表。

 

# Linux

## VM 和 Linux 的安装

学习 Linux 需要一个环境，我们需要创建一个虚拟机，然后在虚拟机上安装一个 Centos 系统来学习
1) 先安装 virtual machine ,vm12
2) 再安装 Linux (CentOS )
CentOS 安装技术难点-网络配置三种方式理解：
关于 桥连，nat 模式和主机模式的含义和区别：
![image-20220220143826851](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220220143826851.png)

使用Xshell连接Linux时，需要需要Linux开启sshd服务的22号端口监听。远程上传或者下载文件使用Xftp5（win -- linux）

## linux 的层级式目录结构

在 Linux 世界里，一切皆文件（即使是一个硬件设备，也是使用文本来标志）
与windows不同 Linux只有一个根，不像windows中的有C盘 D盘
![image-20220220145442439](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220220145442439.png)

* /root: 系统管理员（超级权限者用户的主目录）
* /bin: 存放一些常用命令（如拷贝、删除）
* /boot：启动Linux时用的一些核心文件、引导文件
* /dev: 类似于Windows的设备管理器，把所有硬件用文件的形式存储
* /etc: 系统管理所需要的配置文件和子目录
* /home：存放普通用户的主目录
* /var：存放经常被修改的变化的目录
* /lib ：系统开机需要的最基本的动态链接共享库
* /usr：用户应用程序的安装与文件的存放
* /media：Linux把自动识别出来的U盘、光驱等等设备挂载到这个目录下
* /mnt : 让用户临时挂载别的文件系统 比如Windows的D盘

## 常用命令

* Vi vim 命令 ： 文本编辑  Vim比Vi多了个具有程序编辑的能力
  wq:写入保存退出
  q:没写入退出
  q!:强制退出

* su- 用户名 ： 用来切换系统管理员与普通用户的登陆 logout 注销用户

* useradd userdel 添加和删除用户。    id：查询用户信息

  groupadd  groupdel 新增/删除组   usermod  修改用户的组

* help 指令 ：获得命令的帮助

* pwd: 显示当前工作目录的绝对路径

* ls -la : 显示当前路径所有文件

* mkdir 创建目录

* cp 拷贝目录

* rm - r 递归删除整个文件夹

* mv 移动文件

* cat 查看文件内容

* echo 输出内容到控制台

* tail 输出文件的尾部

* history 指令 ：查看执行过的命令

* date  : 显示当前日期

* find 搜索查找 文件或目录

* grep 过滤查找 ， 管道符，表示将前一个命令的处理结果输出传递给后面的命令处理

* tar -zxvf ：解压到当前目录

* chown：修改文件所有者

* chmod：修改文件或者目录的权限

* crontab 进行 定时任务的设置

* kill -9 进程号 ：  强制杀掉进程

* yum install : 下载 安装命令

* 较为高级的指令：

  top : 查看内存运行的所有进程

  top -p 2913  查看进程ID号2913的进程情况（cpu、内存）

  ps -aux：显示所有的进程

  ps -ef | grep hdfs  查看进程ID

  ps -aux | grep hdfs//查看 hdfs进程(内存等)

  cat/proc/**cpuinfo**  查看**cpu基本信息**

  df -h: 查看磁盘存储情况

  iotop : 查看磁盘 IO 读写

  iotop -o: 直接查看比较高的磁盘读写程序

  netstat -tunlp | grep 端口号 查看端口占用情况

![image-20220902191502285](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220902191502285.png)

## linux 系统权限

权限简介

- Linux系统上对文件的权限有着严格的控制，如果想对某个文件执行某种操作，必须具有对应的权限方可执行成功。

- Linux下文件的权限类型一般包括读，写，执行。对应字母为 r、w、x。我们规定 数字 4 、2 和 1表示读、写、执行权限

- Linux下权限的粒度有 **拥有者 、群组(用户组) 、其它组** 三种。每个文件都可以针对三个粒度，设置不同的rwx(读写执行)权限。通常情况下，一个文件只能归属于一个用户和组， 如果其它的用户想有这个文件的权限，则可以将该用户加入具备权限的群组，一个用户可以同时归属于多个组。 用三个8进制数字分别表示 拥有者 、群组 、其它组( **u、 g 、o**)

  Linux上通常使用chmod命令对文件的权限进行设置和更改。

```shell
chmod 777 file  (等价于  chmod u=rwx,g=rwx,o=rwx file 或  chmod a=rwx file)
```

设置所有人可以读写及执行;

 

#  计算机网络

## 各层及其作用

OSI七层模型

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220712085645589.png" alt="image-20220712085645589" style="zoom:200%;" />

学习计算机⽹络时我们⼀般采⽤折中的办法，也就是中和 OSI 和 TCP/IP 的优点，采⽤⼀种只有五层协议的体系结构，这样既简洁⼜能将概念阐述清楚。

![image-20220701214950417](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220701214950417.png)

结合互联⽹的情况，⾃上⽽下地，⾮常简要的介绍⼀下各层的作⽤。

● **应⽤层**(application-layer）的任务是通过应⽤进程间的交互来完成特定⽹络应⽤。

> 应⽤层协议定义的是应⽤进程（进程：主机中正在运⾏的程序）间的通信和交互的规则。对于不同的⽹络应⽤需要不同的应⽤层协议。在互联⽹中应⽤层协议很多，如**域名系统DNS**，⽀持万维⽹应⽤的**HTTP协议**，⽀持电⼦邮件的 **SMTP协议、pop3协议**等等。我们把应⽤层交互的数据单元称为报⽂。

● **运输层**(transport layer)的主要任务就是负责向两台主机进程之间的通信提供通⽤的数据传输服务。应⽤进程利⽤该服务传送应⽤层报⽂

运输层主要有TCP和UDP两种协议

> 所谓（传输层）套接字，实际上是一个通信端点，每个套接字都有一个套接字序号，包括主机的IP地址与一个16位的主机端口号，即形如（主机IP地址：端口号）。例如，如果IP地址是210.37.145.1，而端口号是23，那么得到套接字就是（210.37.145.1：23）。
>
> [TCP第三次握手能携带数据吗？做个实验就知道！ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/373422503)

●  **网络层**  在计算机⽹络中进⾏通信的两个计算机之间可能会经过很多个数据链路，也可能还要经过很多通信⼦⽹。⽹络层的任务就是选择合适的⽹间路由和交换结点， 确保数据及时传送。 在发送数据时，⽹络层把运输层产⽣的报⽂段或⽤户数据报封装成 分组（ip数据报）和包进⾏传送。（ICMP : 因特⽹控制报⽂协议，⽤于在IP主机、路由器之间传递控制消息）

● **数据链路层**(data link layer)通常简称为链路层。两台主机之间的数据传输，总是在⼀段⼀段的链路上传送的，这就需要使⽤专⻔的链路层的协议。（ARP协议：ip地址和mac 地址的转换）

● **物理层**(physical layer)的作⽤是实现相邻计算机节点之间⽐特流的透明传送，尽可能屏蔽掉具体传输介质和物理设备的差异。 使其上⾯的数据链路层不必考虑⽹络的具体传输介质是什么。

![image-20220701085150008](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220701085150008.png)

 

> 应用层http:超⽂本传输协议（HTTP，HyperText Transfer Protocol)是互联⽹上应⽤最为⼴泛的⼀种⽹络协议。所有的 WWW（万维⽹） ⽂件都必须遵守这个标准。设计 HTTP 最初的⽬的是为了提供⼀种发布和接收 HTML ⻚⾯的⽅法。（百度百科）

 

**简述ARP地址解析协议⼯作原理**

⾸先， 每个主机会在⾃⼰的ARP缓冲区建立⼀个ARP列表，以表示IP地址和MAC地址之间的对应关系。

当源主机要发送数据时，⾸先检查⾃⼰的ARP列表中是否有对应的⽬的主机的MAC地址，如果有就直接发送数据，如果没有，就 向本⽹段的所有的主机发送ARP数据包， 该数据包括的内容由：源主机IP地址，源主机的MAC地址，⽬的主机的IP地址； 当本⽹络的所有主机收到ARP数据包时，⾸先检查数据包中的IP地址是否是⾃⼰的IP地址，如果不是，则忽略该数据包，如果是， 则⾸先从数据包中取出源主机的IP和MAC地址写⼊到ARP列表中，如果已经存在，则覆盖，然后将⾃⼰的MAC地址中放⼊到ARP 响应包中，告诉源主机⾃⼰是它想找的MAC地址。

源主机接收到ARP响应包后，将⽬的主机的IP和MAC地址写⼊到ARP列表，并利⽤此消息发送数据。如果源主机⼀直没有收到 ARP响应数据包，表示ARP查询失败

![image-20220718145711068](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220718145711068.png)

> （填入的MAC地址是路由器，这里的MAC是目标mac地址，其实应该是网关MAC，只不过现在局域网都是用路由器接入；所以网关就是路由器IP）

[ARP协议，同一网段，不同网段的详细通信流程_MKWH的博客-CSDN博客](https://blog.csdn.net/xayddxjsjxywuhui/article/details/72796646)

 

## 请简述TCP\UDP的区别

TCP和UDP是OSI模型中的运输层中的协议。

> TCP提供可靠的通信传输，⽽UDP则常被⽤于让⼴播和细节控制交给应⽤的通信传输。

两者的区别⼤致如下：

● TCP⾯向连接，UDP⾯向⾮连接即发送数据前不需要建⽴链接

● TCP提供可靠的服务（数据传输），UDP⽆法保证（对差错恢复无能为力）

● TCP⾯向字节流，UDP⾯向报⽂

● TCP数据传输慢，UDP数据传输快

 

udp不可靠传输

![image-20220720092246464](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220720092246464.png)

 

 

## **TCP** **协议如何保证可靠传输**

一句话：通过`校验和`、`序列号`、`确认应答`、`超时重传`、`连接管理`、`流量控制`、`拥塞控制`等机制来保证可靠性。

**（1）校验和**

TCP 将保持它⾸部和数据的检验和。这是⼀个端到端的检验和，⽬的是检测数据在传输过程中的任何变化。如果收到端的检验和有差错，TCP 将丢弃这个报⽂段和不确认收到此报⽂段。

**（2）序列号**

TCP 传输时将每个字节的数据都进行了编号，这就是序列号。序列号的作用不仅仅是应答作用，有了序列号能够将接收到的数据根据序列号进行排序，并且去掉重复的数据。

**（3）确认应答**

TCP 传输过程中，每次接收方接收到数据后，都会对传输方进行确认应答，也就是发送 ACK 报文，这个 ACK 报文中带有对应的确认序列号，告诉发送方，接收了哪些数据，下一次数据从哪里传。

**（4）超时重传**

在进行 TCP 传输时，由于存在确认应答与序列号机制，也就是说发送方发送**一部分**数据后，都会等待接收方发送的 ACK 报文，并解析 ACK 报文，判断数据是否传输成功。如果发送方发送完数据后，迟迟都没有接收到接收方传来的 ACK 报文，那么就对刚刚发送的数据进行重发。

**（5）连接管理**

就是指三次握手、四次挥手的过程。

**（6）流量控制**

如果发送方的发送速度太快，会导致接收方的接收缓冲区填充满了，这时候继续传输数据，就会造成大量丢包，进而引起丢包重传等等一系列问题。TCP 支持根据接收端的处理能力来决定发送端的发送速度，这就是流量控制机制。

> **TCP** **利⽤滑动窗⼝实现流量控制**。接收⽅发送的确认报⽂中的窗⼝字段可以⽤来控制发送⽅窗⼝⼤⼩，从⽽影响发送⽅的发送速率。具体实现方式：接收端将自己的接收缓冲区大小放入 TCP 首部的『窗口大小』字段中，通过 ACK 通知发送端。将窗⼝字段设置为 0，则发送⽅不能发送数据。

**（7）拥塞控制**

当⽹络拥塞时，减少数据的发送。TCP的拥塞控制采⽤了四种算法，即 **慢开始** 、 **拥塞避免** 、**快重传** 和 **快恢复**。

 

## 拥塞控制

在某段时间，若对⽹络中某⼀资源的需求超过了该资源所能提供的可⽤部分，⽹络的性能就要变坏。这种情况就叫拥塞。拥塞控制就是为了防⽌过多的数据注⼊到⽹络中，这样就可以使⽹络中的路由器或链路不致过载。拥塞控制所要做的都有⼀个前提，就是⽹络能够承受现有的⽹络负荷。拥塞控制是⼀个全局性的过程，涉及到所有的主机，所有的路由器，以及与降低⽹络传输性能有关的所有因素。

> 相反，流量控制往往是点对点通信量的控制，是个端到端的问题。流量控制所要做到的就是抑制发送端发送数据的速率，以便使接收端来得及接收。

为了进⾏拥塞控制，TCP 发送⽅要维持⼀个 **拥塞窗⼝(cwnd)** 的状态变量。拥塞控制窗⼝的⼤⼩取决于⽹络的拥塞程度，并且动态变化。发送⽅让⾃⼰的发送窗⼝取为拥塞窗⼝和接收⽅的接受窗⼝中较⼩的⼀个。

TCP的拥塞控制采⽤了四种算法，即 **慢开始** 、 **拥塞避免** 、**快重传** 和 **快恢复**。在⽹络层也可以使路由器采⽤适当的分组丢弃策略（如主动队列管理 AQM），以减少⽹络拥塞的发⽣。

**慢开始：** 慢开始算法的思路是当主机开始发送数据时，如果⽴即把⼤量数据字节注⼊到⽹络，那么可能会引起⽹络阻塞，因为现在还不知道⽹络的负荷情况。经验表明，较好的⽅法是先探测⼀下，即由⼩到⼤逐渐增⼤发送窗⼝，也就是由⼩到⼤逐渐增⼤拥塞窗⼝数值。cwnd初始值为1，每经过⼀个传播轮次，cwnd加倍。

**拥塞避免：** 拥塞避免算法的思路是让拥塞窗⼝cwnd缓慢增⼤，即每经过⼀个往返时间RTT就把发送放的cwnd加1；注意到慢开始每个轮次都将 cwnd 加倍，这样会让 cwnd 增⻓速度⾮常快，从⽽使得发送⽅发送的速度增⻓速度过快，⽹络拥塞 的可能性也就更⾼。所以设置⼀个慢开始⻔限 ssthresh，当 cwnd >= ssthresh 时，进⼊拥塞避免，每个轮次只将 cwnd 加 1。 如果出现了超时，则令 ssthresh = cwnd / 2，然后重新执⾏慢开始。

**快速重传和恢复：**

**快重传**：快重传要求接收⽅在收到⼀个 失序的报⽂段 后就⽴即发出 重复确认（为的是使发送⽅及早知道有报⽂段没有到达对⽅）⽽不要等到⾃⼰发送数据时捎带确认。快重传算法规定，发送⽅只要⼀连收到三个重复确认就应当⽴即重传对⽅尚未收到的报⽂段，⽽不必继续等待设置的重传计时器时间到期。

**快恢复**：快重传配合使⽤的还有快恢复算法，当发送⽅连续收到三个重复确认时，就执⾏把ssthresh⻔限减半，但是接下去并不执⾏慢开始算法：因为如果⽹络出现拥塞的话就不会收到好⼏个重复的确认，所以发送⽅现在认为⽹络可能没有出现拥塞。所以此时不执⾏慢开始算法，⽽是将cwnd设置为ssthresh的⼤⼩，然后执⾏拥塞避免算法。

 

## TCP了解吗，说⼀下滑动窗⼝

窗⼝是缓存的⼀部分，⽤来暂时存放字节流。发送⽅和接收⽅各有⼀个窗⼝，接收⽅通过 TCP 报⽂段中的窗⼝字段告诉发送⽅⾃ ⼰的窗⼝⼤⼩，发送⽅根据这个值和其它信息设置⾃⼰的窗⼝⼤⼩。 发送窗⼝内的字节都允许被发送，接收窗⼝内的字节都允许被接收。如果发送窗⼝左部的字节已经发送并且收到了确认，那么就 将发送窗⼝向右滑动⼀定距离，直到左部第⼀个字节不是已发送并且已确认的状态；接收窗⼝的滑动类似，接收窗⼝左部字节已 经发送确认并交付主机，就向右滑动接收窗⼝。 接收窗⼝只会对窗⼝内最后⼀个按序到达的字节进⾏确认，例如接收窗⼝已经收到的字节为 {31, 34, 35}，其中 {31} 按序到达， ⽽ {34, 35} 就不是，因此只对字节 31 进⾏确认。发送⽅得到⼀个字节的确认之后，就知道这个字节之前的所有字节都已经被接 收

![image-20220702072734939](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220702072734939.png)

 

## TCP三次握手和四次挥手

### **三次握手**

![image-20220701100013784](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220701100013784.png)

 

- SYN：同步SYN(SYNchronization),在连接建⽴时⽤来同步序号。SYN置1表示这是⼀个连接请求或连接接受请求。
- ACK：确认ACK(ACKnowledgment),仅当ACK=1时确认号字段才有效。TCP规定，在连接建⽴后所有的报⽂段都必须把 ACK置1。

- seq: 序号。

- ack: 确认号。


**主要过程**

● 最初两端的TCP进程都处于CLOSE(关闭)状态。 上图中A主动打开连接，B被动打开连接。

● B打开连接后处于LISTEN(监听状态)，等待客户的连接请求。

● A向B发送请求报⽂，SYN=1,（ACK=0）选择⼀个初始序号seq=x。

● B 收到连接请求报⽂，如果同意建⽴连接，则向 A 发送连接确认报⽂，SYN=1，ACK=1，确认号为ack= x+1，同时也选择 ⼀个初始的序号 seq=y。

● A 收到 B 的连接确认报⽂后，还要向 B 发出确认，ACK=1, 确认号为ack= y+1，序号为 seq=x+1。

● B 收到 A 的确认后，连接建⽴

 

#### **为什么要三次握⼿**

- 三次握手才可以**阻止重复历史连接的初始化**（主要原因）

  > 三次握手可以解决
  >
  > - 一个「旧 SYN 报文」比「最新的 SYN 」 报文早到达了服务端；
  > - 那么此时服务端就会回一个 `SYN + ACK` 报文给客户端；
  > - 客户端收到后可以根据自身的上下文，判断这是一个历史连接（序列号过期或超时），那么客户端就会发送 `RST` 报文给服务端，表示中止这一次连接
  >
  > 两次则不行
  >
  > 两次握手的情况下，「被动发起方」在收到 SYN 报文后，就进入 ESTABLISHED 状态，意味着这时可以给对方发送数据；
  >
  > 「被动发起方」在向「主动发起方」发送数据前，并没有阻止掉历史连接，导致「被动发起方」建立了一个历史连接，又白白发送了数据，妥妥地浪费了「被动发起方」的资源

- 三次握手才能**保证双方具有接收和发送的能力**

  > **三次握⼿的⽬的是建⽴可靠的通信信道，说到通讯，简单来说就是数据的发送与接收，⽽三次握⼿最主要的⽬的就是双⽅确认⾃⼰与对⽅的发送与接收是正常的。**
  >
  > - 第⼀次握⼿：Client 什么都不能确认；Server 确认了对⽅发送正常，⾃⼰接收正常
  > - 第⼆次握⼿：Client 确认了：⾃⼰发送、接收正常，对⽅发送、接收正常；Server 确认了：对⽅发送正常，⾃⼰接收正常
  > - 第三次握⼿：Client 确认了：⾃⼰发送、接收正常，对⽅发送、接收正常；Server 确认了：⾃⼰发送、接收正常，对⽅发送、接收正常
  >
  > 所以三次握⼿就能确认双发收发功能都正常，缺⼀不可。

- 三次握手才可以避免资源浪费

 

**为什么要传回** **SYN**

接收端传回发送端所发送的 SYN 是为了告诉发送端，我接收到的信息确实就是你所发送的信号了。

 

**传了** **SYN,为啥还要传** **ACK**

双⽅通信⽆误必须是两者互相发送信息都⽆误。传了 SYN，证明**发送⽅到接收⽅**的通道没有问题，但是**接收⽅到发送⽅**的通道还需要 ACK 信号来进⾏验证。

 

### 四次挥手

![image-20220701100653375](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220701100653375.png)

● FIN: 终⽌FINs,⽤来释放⼀个连接。当FIN等于1时，表明此报⽂段的发送⽅的数据已发送完毕，并要求释放运输连接。

● ACK: 确认ACK(ACKnowledgment),仅当ACK=1时确认号字段才有效。TCP规定，在连接建⽴后所有的报⽂段都必须把ACK 置1。

● seq: 序号。

● ack: 确认号。

**主要过程：**

- 客户端-发送⼀个 FIN，选择⼀个初始序号seq=u，⽤来关闭客户端到服务器的数据传送，客户端进入FIN_WAIT1Z状态；
- 服务器-收到这个 FIN，它发回⼀ 个 ACK，确认序号为收到的序号u+1,同时也选择 ⼀个初始的序号 seq=v 。此时服务器进入close_wait状态，客户端收到ACK消息，进入FIN_WAIT2状态；
- 服务器-关闭与客户端的连接，发送⼀个FIN给客户端, ack还是u+1, 重新选择 ⼀个初始的序号 seq=w；
- 客户端-发回 ACK 报⽂确认，并将确认序号设置为收到序号w加1，序列号为u+1，进入TIME_WAIT状态；服务端收到ACK后连接正式关闭。

 

### 为什么建⽴连接协议是三次握⼿，⽽关闭连接却是四次握⼿

这是因为服务端的LISTEN状态下的SOCKET当收到SYN报⽂的连接请求后，它可以把ACK和SYN(ACK起应答作⽤，⽽SYN起同 步作⽤)放在⼀个报⽂⾥来发送。但关闭连接时，当收到对⽅的FIN报⽂通知时，**它仅仅表示对⽅没有数据发送给你了；但未必你 所有的数据都全部发送给对⽅了，所以你可能未必会⻢上会关闭SOCKET,也即你可能还需要发送⼀些数据给对⽅之后，再发送 FIN报⽂给对⽅来表示你同意现在可以关闭连接了，**所以它这⾥的ACK报⽂和FIN报⽂多数情况下都是分开发送的。

 

**需要 TIME-WAIT 状态，主要是两个原因：**

- 防止历史连接中的数据，被后面相同四元组的连接错误的接收；
- 保证「被动关闭连接」的一方，能被正确的关闭；客户端必须等待足够长的时间确保对端收到 ACK，如果对端没有收到 ACK，那么就会触发 TCP 重传机制，**服务端**会重新发送一个 FIN，这样一去一来刚好两个 MSL 的时间。

[4.1 TCP 三次握手与四次挥手面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/3_tcp/tcp_interview.html#tcp-连接断开)

![image-20220814091402728](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220814091402728.png)

**原因1** 如上图：

- 服务端在关闭连接之前（Fin发送之前）发送的 `SEQ = 301` 报文，被网络延迟了。
- 接着，服务端以相同的四元组重新打开了新连接，前面被延迟的 `SEQ = 301` 这时抵达了客户端，而且该数据报文的序列号刚好在客户端接收窗口内，因此客户端会正常接收这个数据报文，但是这个数据报文是上一个连接残留下来的，这样就产生数据错乱等严重的问题。

为了防止历史连接中的数据，被后面相同四元组的连接错误的接收，因此 TCP 设计了 TIME_WAIT 状态，状态会持续 `2MSL` 时长，这个时间**足以让两个方向上的数据包都被丢弃，使得原来连接的数据包在网络中都自然消失，再出现的数据包一定都是新建立连接所产生的。**

 

[4.6 如何理解是 TCP 面向字节流协议？ | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/3_tcp/tcp_stream.html#如何理解字节流)

以及粘包问题

 

## **在浏览器中输⼊url地址** **->>** **显示主页的过程(⾯试常客)**

解析URL、生成http请求消息 ->DNS域名解析 -> 建立TCP连接（三次握手）-> 发起http请求 -> 服务器响应http请求，浏览器得到html代码 -> 浏览器解析html代码，并请求html代码中的资源（如 js、css、图片等）-> 浏览器对页面进行渲染呈献给用户。

[2.2 键入网址到网页显示，期间发生了什么？ | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/1_base/what_happen_url.html#孤单小弟-http)

 

[【计算机网络】HTTP 协议详解_吞吞吐吐大魔王的博客-CSDN博客_http协议详解](https://blog.csdn.net/weixin_51367845/article/details/123313047)

## **HTTP** **和** **HTTPS** **的区别？**

1、**端⼝** ：HTTP的URL由“http://”起始且默认使⽤端⼝80，⽽HTTPS的URL由“https://”起始且默认使⽤端⼝443

2、**安全性和资源消耗：** HTTP协议运⾏在TCP之上，所有传输的内容都是**明⽂**，客户端和服务器端都⽆法验证对⽅的身份。HTTPS是运⾏在SSL/TLS之上的HTTP协议，SSL/TLS 运⾏在TCP之上。所有传输的内容都经过加密，**加密采⽤对称加密，但对称加密的密钥⽤服务器⽅的证书进⾏了⾮对称加密**。所以说，HTTP 安全性没有 HTTPS⾼，但是 HTTPS ⽐HTTP耗费更多服务器资源。

> - 对称加密：密钥只有⼀个，加密解密为同⼀个密码，且加解密速度快，典型的对称加密算法有DES、AES等；
> - ⾮对称加密：密钥成对出现（且根据公钥⽆法推知私钥，根据私钥也⽆法推知公钥），加密解密使⽤不同密钥（公钥加密需要私钥解密，私钥加密需要公钥解密），相对对称加密速度慢，典型的⾮对称加密算法有RSA、DSA等。

 

## 对称加密和非对称加密的区别和原理吗？

对称密钥加密是指加密和解密使用同一个密钥的方式，密钥较短，加密速度快、加密效率高；但这种方式存在的最大问题就是密钥发送问题，即`如何安全地将密钥发给对方`;

而非对称加密是指使用一对非对称密钥，即`公钥`和`私钥`，公钥可以随意发布（可根据私钥和加密算法推导出来），但私钥只有自己知道。发送密文的一方使用对方的公钥进行加密处理，对方接收到加密信息后，使用自己的私钥进行解密。

由于非对称加密的方式不需要发送用来解密的私钥，所以可以`保证安全性`；但是和对称加密比起来，它比较`慢`，所以我们还是要用对称加密来传送消息，但对称加密所使用的密钥我们可以通过非对称加密的方式发送出去。

所以区别有下：

1、加密和解密过程不同

2、加密解密速度不同

3、传输的安全性不同

 

## HTTPS传输过程

- 浏览器发起 HTTPS 请求
- 服务端返回证书(包含服务器公钥S_PuKey)、对称加密算法（用于生成对称密钥）种类及其他相关信息
- 客户端验证证书是否合法，是否有效，如果不合法则提示告警
- 校验通过后客户端会随机生成一个对称密钥（randomkey+密钥生成算法），通过服务端返回的公钥加密，并传输到服务端
- 服务端接收报文后，使用私钥，对加密的内容的进行解密，然后得到一个对称密钥
- 这时，服务端会将请求域名的响应结果，使用对称密钥进行加密，返回客户端
- 客户端对 服务端的加密报文使用对称密钥 解密，然后就可以展示在浏览器上（数据传输采用了对称加密）

 

## Session、Cookie 的区别

Cookie 和 Session都是⽤来跟踪浏览器⽤户身份的会话⽅式，但是两者的应⽤场景不太⼀样。

- session 在服务器端，cookie 在客户端（浏览器）
- **Cookie** **⼀般⽤来保存⽤户信息** ⽐如①我们在 Cookie 中保存已经登录过得⽤户信息，下次访问⽹站的时候⻚⾯可以⾃动帮你登录的⼀些基本信息给填了；
- **Session** **的主要作⽤就是通过服务端记录⽤户的状态。** 典型的场景是购物⻋，当你要添加商品到购物⻋的时候，系统不知道是哪个⽤户操作的，因为 HTTP 协议是⽆状态的。服务端给特定的⽤户创建特定的 Session 之后就可以标识这个⽤户并且跟踪这个⽤户了
- session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果浏览器禁用了 cookie ，同时 session 也会失效（但是可以通过其它方式实现，比如在 url 中传递 session_id）

> session 可以放在 文件、数据库、或内存中都可以（但默认是文件）
>
> **HTTP是不保存状态的协议，用Session保存用户状态**

 

## GET 和 POST 的区别

GET 和 POST 其实没有本质区别，使用 GET 的场景完全可以使用 POST 代替，使用 POST 的场景一样可以使用 GET 代替。但是在具体的使用上，还是存在一些细节的区别

- GET 习惯上会把客户端的数据通过 URL中的query string 来传输（body 部分是空的）；POST 习惯上会把客户端的数据通过传输报文中的body 来传输（query string 部分是空的）
- GET 请求的长度受限于浏览器或服务器对URL长度的限制，允许发送的数据量比较小，而POST请求则是没有大小限制的。
- GET 习惯上用于从服务器获取数据；POST 习惯上是客户端给服务器提交数据
- 一般情况，程序员会把 GET 请求的处理，实现成“幂等”的；对于 POST 请求的处理，不要求实现成“幂等”
- GET 请求可以被缓存，可以被浏览器保存到收藏夹中；POST 请求不能被缓存

> **其他方法**
>
> PUT： 与 POST 相似，但是具有幂等特性，一般用于更新
> DELETE： 删除服务器指定资源
> OPTIONS： 返回服务器所支持的请求方法
> HEAD： 与 GET 类似，只不过响应体不返回，只返回响应头
> TRACE： 能显示服务器端收到的请求，测试的时候会用到
> CONNECT： 预留，暂无使用

 

## http中常见的header字段有哪些

![image-20220704133903425](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220704133903425.png)

 

![image-20220704134448491](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220704134448491.png)

 

-  HOST  表示服务器主机的地址和端口（地址可以是域名，也可以是 IP；端口号可以省略或者手动指定）


- connection，管理持久连接，keep-alive , close

- Cache-Control，控制浏览器的强缓存

- Content-Length 表示 body 的数据长度，长度单位是字节

- Content-Type  表示 body 的数据格式

  > 请求header：表单、jason
  >
  > 响应header：html、txt/css、JS、jason

- User-Agent 表示浏览器或者操作系统的属性

- Referer 表示这个页面是从哪个页面跳转过来的

- cookie，请求时传递给服务端的cookie信息

- set-cookie ：**响应报文**中，设置cookie信息

 

## 常见状态码

1×× : 请求处理中，请求已被接受，正在处理

2×× : 请求成功，请求被成功处理   200 OK

3×× : 重定向，要完成请求必须进行进一步处理   301 : 永久性转移   302 ：暂时性转移   304 ：已缓存；也称缓存重定向，也就是告诉客户端可以继续使用缓存资源

4×× : 客户端错误，请求不合法   400：Bad Request , 请求有语法问题    403：拒绝请求   404：客户端所访问的页面不存在

5×× : 服务器端错误，服务器不能处理合法请求   500 ：服务器内部错误  503 ：服务不可用，稍等；**502** 表示作为网关或者代理工作的服务器返回的错误码，表示服务器自身工作正常，访问后端（上游）服务器发生了错误。

[3.1 HTTP 常见面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/2_http/http_interview.html#http-常见的状态码有哪些)

 

## HTTP/1.1 相比 HTTP/1.0 性能上的改进

- 使用长连接的方式改善了 HTTP/1.0 短连接造成的性能开销。

- 支持管道（pipeline）网络传输，只要第一个请求发出去了，不必等其回来，就可以发第二个请求出去，可以减少整体的响应时间。但是**服务器必须按照接收请求的顺序发送对这些管道化请求的响应**

- **带宽优化及⽹络连接的使⽤** :HTTP1.0中，存在⼀些浪费带宽的现象，例如客户端只是需要某个对象的⼀部分，⽽服务器却将整个对象送过来了，并且不⽀持断点续传功能，HTTP1.1则在请求头引⼊了range头域，它允许只请求资源的某个部分，即返回码是206（Partial

  Content），这样就⽅便了开发者⾃由的选择以便于充分利⽤带宽和连接。

下面两点了解即可

> **错误状态响应码** :在HTTP1.1中新增了24个错误状态响应码，如409（Conflict）表示请求的资源与资源的当前状态发⽣冲突；410（Gone）表示服务器上的某个资源被永久性的删除。
>
> **缓存处理** : 在HTTP1.0中主要使⽤header⾥的 If-Modified-Since , Last-Modified；Cache-Control、expire 等 来做为缓存判断的标准，HTTP1.1则引⼊了更多的缓存控制策略例如Entity tag（唯一标识响应资源）， If-None-Match等更多可供选择的缓存头来控制缓存策略。
>
> [3.1 HTTP 常见面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/2_http/http_interview.html#什么是协商缓存)

 

 

## 简述http2.0的改进

HTTP/2 协议是基于 HTTPS 的，所以 HTTP/2 的安全性也是有保障的。

**头部压缩**  HTTP/2 会**压缩头**（Header）如果你同时发出多个请求，他们的头是一样的或是相似的，那么，协议会帮你**消除重复的部分**。

**多路复用**  多路复用前，文件是串行传输的，请求a文件，b文件只能等待，并且连接数过多。引入多路复用，a文件b文件可以同时传输。**一个连接中并发多个请求或回应，而不用按照顺序一一对应**

![image-20220814110914045](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220814110914045.png)

**引入了二进制数据帧**。增加了传输效率；因为计算机底层就是二进制；

**数据流**  HTTP/2 的数据包不是按顺序发送的，同一个连接里面连续的数据包，可能属于不同的回应。因此，必须要对数据包做标记，指出它属于哪个回应。

在 HTTP/2 中每个请求或响应的所有数据包，称为一个数据流（`Stream`）。每个数据流都标记着一个独一无二的编号（Stream ID），**不同 Stream 的帧是可以乱序发送的，因此可以并发不同的 Stream **，因为每个帧的头部会携带 Stream ID 信息，所以接收端可以通过 Stream ID 有序组装成 HTTP 消息

[3.1 HTTP 常见面试题 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/2_http/http_interview.html#http-2-做了什么优化)

 

## DNS是什么

DNS是⼀种⽤于TCP/IP应⽤程序的分布式数据库，它提供域名到IP地址的转换。

> 当DNS客户机需要在程序中使⽤名称时，它会查询DNS服务器来解析该名称。客户机发送的每条查询信息包括三条信息：指定的 DNS域名，指定的查询类型，DNS域名的指定类别。基于UDP服务，端⼝53。该应⽤⼀般不直接为⽤户使⽤，⽽是为其他应⽤服 务，如HTTP，SMTP等在其中需要完成主机名到IP地址的转换。

1. 客户机向其本地域名服务器发出DNS请求报⽂

2. 本地域名服务器收到请求后，查询本地缓存，假设没有该记录，则以DNS客户的身份向根域名服务器发出解析请求

3. 根域名服务器收到请求后，判断该域名所属域，将对应的顶级域名服务器的IP地址返回给本地域名服务器

4. 本地域名服务器向顶级域名服务器发出解析请求报⽂

5. 顶级域名服务器收到请求后，将所对应的授权域名服务器的IP地址返回给本地域名服务器

6. 本地域名服务器向授权域名服务器发起解析请求报⽂

7. 授权域名服务器收到请求后，将查询结果返回给本地域名服务器

8. 本地域名服务器将查询结果保存到本地缓存，同时返回给客户机

 

# 操作系统

 

## 什么是操作系统

- **操作系统（Operating System，简称 OS）本质上是是管理计算机硬件与软件资源的程序，是计算机的基⽯。**
-  **操作系统存在屏蔽了硬件层的复杂性。** 操作系统就像是硬件使⽤的负责⼈，统筹着各种相关事项。
- **操作系统的内核（Kernel）是操作系统的核⼼部分，它负责系统的内存管理，硬件设备的管理，⽂件系统的管理以及应⽤程序的管理**。 内核是连接应⽤程序和硬件的桥梁，决定着系统的性能和稳定性。

 

## 什么是系统调用

首先得介绍**用户空间和内核空间** 以及 **用户态和内核态**

内核具有很高的权限，可以控制 cpu、内存、硬盘等硬件，而应用程序具有的权限很小，因此大多数操作系统，把内存分成了两个区域：

- 内核空间，这个内存空间只有内核程序可以访问；
- 用户空间，这个内存空间专门给应用程序使用；

用户空间的代码只能访问一个局部的内存空间，而内核空间的代码可以访问所有内存空间。因此，当程序使用用户空间时，我们常说该程序在**用户态**执行，而当程序使内核空间时，程序则在**内核态**执行。

 

应用程序如果需要进入内核空间，就需要通过系统调用，下面来看看系统调用的过程

![image-20220715213050595](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220715213050595.png)

当应用程序使用系统调用时，会产生一个中断。发生中断后， CPU 会中断当前在执行的用户程序，转而跳转到中断处理程序，也就是开始执行内核程序。内核处理完后，主动触发中断，把 CPU 执行权限交回给用户程序，回到用户态继续工作；

 

## 进程和线程的区别？

- **进程：**是程序运行和资源分配的基本单位，一个程序至少有一个进程，一个进程至少有一个线程。进程在执行过程中拥有独立的内存单元。

- **线程：**是进程的一个实体，是` cpu `调度和分派的基本单位，是比程序更小的能独立运行的基本单位。同一进程中的多个线程之间可以并发执行并**共享内存资源**。

- 线程执行开销小，时间效率和空间效率线程比进程都要高；但不利于资源的管理和保护。

 

## 进程有哪几种状态

**创建状态(new)** ：进程正在被创建，尚未到就绪状态。

**就绪状态(ready)** ：进程已处于准备运⾏状态，即进程获得了除了处理器之外的⼀切所需资源，⼀旦得到处理器资源(处理器分配的时间⽚)即可运⾏。

**运⾏状态(running)** ：进程正在处理器上运⾏(单核 CPU 下任意时刻只有⼀个进程处于运⾏状态)。

**阻塞状态(waiting)** ：⼜称为等待状态，进程正在等待某⼀事件⽽暂停运⾏如等待某资源为可⽤或等待 IO 操作完成。即使处理器空闲，该进程也不能运⾏。

**结束状态(terminated)** ：进程正在从系统中消失。可能是进程正常结束或其他原因中断退出运⾏。

 

## 进程间的通信方式

- **管道/匿名管道(Pipes)** ：⽤于具有亲缘关系的⽗⼦进程间或者兄弟进程之间的通信。

- **有名管道(Names Pipes)** : 匿名管道由于没有名字，只能⽤于亲缘关系的进程间通信。为了克服这个缺点，提出了有名管道。有名管道提前创建了一个类型为管道的设备文件（磁盘），在进程里只要使用这个设备文件，就可以相互通信。

  > 不管是匿名管道还是命名管道，通信数据都遵循**先进先出**原则

-  **消息队列(Message Queuing)** ：**消息队列**克服了管道通信的数据是无格式的字节流的问题，**消息队列是保存在内核中的消息链表**，在发送数据时，会分成一个一个独立的数据单元，也就是消息体（数据块），消息体是用户自定义的数据类型，消息的发送方和接收方要约定好消息体的数据类型，所以每个消息体都是固定大小的存储块，不像管道是无格式的字节流数据。如果进程从消息队列中读取了消息体，内核就会把这个消息体删除。消息队列生命周期随内核，如果没有释放消息队列或者没有关闭操作系统，消息队列会一直存在，而前面提到的匿名管道的生命周期，是随进程的创建而建立，随进程的结束而销毁。消息队列可以实现消息的**随机查询**,消息不⼀定要以先进先出的次序读取,也可以按消息的类型读取，⽐ FIFO 更有优势。

- **信号量(Semaphores)** ：信号量是⼀个计数器，⽤于多进程对共享数据的访问，信号量的意图在于进程间同步。这种通信⽅式主要⽤于解决与同步相关的问题并避免竞争条件。
- **信号(Signal)** ：信号是⼀种⽐较复杂的通信⽅式，通过一些信号；通知和接收进程某个事件已经发⽣；kill -9 等

- **共享内存Shared memory)** ：使得多个进程可以访问同⼀块内存空间，不同进程可以及时看到对⽅进程中对共享内存中数据的更新。这种⽅式需要依靠某种同步操作，如互斥锁和信号量等。可以说这是最有⽤的进程间通信⽅式。

-  **套接字(Sockets)** : 此⽅法主要⽤于在客户端和服务器之间通过⽹络进⾏通信。套接字是⽀持 TCP/IP 的⽹络通信的基本操作单元，可以看做是不同主机之间的进程进⾏双向通信的端点，简单的说就是通信的两⽅的⼀种约定，⽤套接字中的相关函数来完成通信过程。

 

## 线程间的同步方式

**互斥量(Mutex)**：采⽤互斥对象机制，只有拥有互斥对象的线程才有访问公共资源的权限。因为互斥对象只有⼀个，所以可以保证公共资源不会被多个线程同时访问。⽐如 Java 中的synchronized 关键词和各种 Lock 都是这种机制。

**信号量(Semphares)** ：它允许同⼀时刻多个线程访问同⼀资源，但是需要控制同⼀时刻访问此资源的最⼤线程数量

**事件(Event)** :Wait/Notify：通过通知操作的⽅式来保持多线程同步，还可以⽅便的实现多线程优先级的比较

 

## 进程的调度算法

**先到先服务(FCFS)调度算法** : 从就绪队列中选择⼀个最先进⼊该队列的进程为之分配资源，使它⽴即执⾏并⼀直执⾏到完成或发⽣某事件⽽被阻塞放弃占⽤ CPU 时再重新调度。

**短作业优先(SJF)的调度算法** : 从就绪队列中选出⼀个估计运⾏时间最短的进程为之分配资源，使它⽴即执⾏并⼀直执⾏到完成或发⽣某事件⽽被阻塞放弃占⽤ CPU 时再重新调度。

**时间⽚轮转调度算法** : 时间⽚轮转调度是⼀种最古⽼，最简单，最公平且使⽤最⼴的算法，⼜称 RR(Round robin)调度。每个进程被分配⼀个时间段，称作它的时间⽚，即该进程允许运⾏的时间。时间片长度是关键

**优先级调度** ： 为每个进程分配优先级，⾸先执⾏具有最⾼优先级的进程，依此类推。具有相同优先级的进程以 FCFS ⽅式执⾏。此外可以根据内存要求，时间要求或任何其他资源要求来确定优先级

**多级反馈队列调度算法** ：前⾯介绍的⼏种进程调度的算法都有⼀定的局限性。如**短进程优先**的调度算法，仅照顾了短进程⽽忽略了⻓进程 。多级反馈队列调度算法是「时间片轮转算法」和「最高优先级算法」的综合和发展；随着队列优先级的降低而cpu的运行时间片的增大的；新的进程会被放入到第一级队列的末尾，按先来先服务的原则排队等待被调度，如果在第一级队列规定的时间片没运行完成，则将其转入到第二级队列的末尾，以此类推，直至完成；多级反馈队列调度算法既能使⾼优先级的作业得到响应⼜能使短作业（进程）迅速完成。因⽽它是⽬前**被公认的⼀种较好的进程调度算法**，UNIX 操作系统采取的便是这种调度算法。

 

## 内存管理主要是做什么的

操作系统的内存管理主要负责内存的分配与回收（malloc 函数：申请内存，free 函数：释放内存），另外地址转换也就是将逻辑地址转换成相应的物理地址等功能也是操作系统内存管理做的事情。

[4.2 malloc 是如何分配内存的？ | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/os/3_memory/malloc.html#malloc-是如何分配内存的)

 

## 内存管理机制

简单分为**连续分配管理⽅式**和**⾮连续分配管理⽅式**这两种。连续分配管理⽅式是指为⼀个⽤户程序分配⼀个连续的内存空间，常⻅的如 **块式管理** 。同样地，⾮连续分配管理⽅式允许⼀个程序使⽤的内存分布在离散或者说不相邻的内存中，常⻅的如**⻚式管理** 和 **段式管理**。

- **块式管理** ： 远古时代的计算机操系统的内存管理⽅式。将内存分为⼏个固定⼤⼩的块，每个块中只包含⼀个进程。如果程序运⾏需要内存的话，操作系统就分配给它⼀块，如果程序运⾏只需要很⼩的空间的话，分配的这块内存很⼤⼀部分⼏乎被浪费了。这些在每个块中未被利⽤的空间，我们称之为碎⽚。

- **⻚式管理** ：把主存分为⼤⼩相等且固定的⼀⻚⼀⻚的形式，⻚较⼩，相对相⽐于块式管理的划分⼒度更⼤，提⾼了内存利⽤率，减少了碎⽚。⻚式管理通过⻚表对应逻辑地址和物理地址。

- **分段式管理**

  内存分段是根据程序的逻辑角度，将主存分成了栈段、堆段、数据段、代码段等，这样可以分离出不同属性的段；同时段内是一块连续的空间；每个段的大小都不是统一的；段式管理通过段表对应逻辑地址和物理地址。

- **段页式内存管理**

  段⻚式管理机制结合了段式管理和⻚式管理的优点。简单来说段⻚式管理机制就是把主存先分成若⼲段，每个段⼜分成若⼲⻚

 

## 内存分页中的 多级页表 和 快表（TLB）

- **多级页表**

  为了解决简单分页产生的页表过大的问题，特别是那些根本就不需要的⻚表就不需要保留在内存中，就有了**多级页表**

  对于单页表的实现方式，在 32 位系统（4GB虚拟内存）和页大小 `4KB` 的环境下，一个进程的页表需要装下 100 多万个「页表项」，并且每个页表项是占用 4 字节大小的，于是相当于每个页表需占用 4MB 大小的空间。

  我们把这个 100 多万个「页表项」的单级页表再分页，将页表（一级页表）分为 `1024` 个页表（二级页表），每个表（二级页表）中包含 `1024` 个「页表项」，形成**二级分页**

  看似使用的内存更多了；但是由于**局部性原理**的存在，他的内存使用的降低的；

  每个进程都有 4GB 的虚拟地址空间，而显然对于大多数程序来说，其使用到的空间远未达到 4GB；

  如果使用了二级分页，一级页表就可以覆盖整个 4GB 虚拟地址空间，但**如果某个一级页表的页表项没有被用到，也就不需要创建这个页表项对应的二级页表了，即可以在需要时才创建二级页表**。做个简单的计算，假设只有 20% 的一级页表项被用到了，那么页表占用的内存空间就只有 4KB（一级页表） + 20% * 4MB（二级页表）= `0.804MB`，这对比单级页表的 `4MB` 就是巨大的节约；

- **快表  TLB**

  多级页表虽然解决了空间上的问题，但是虚拟地址到物理地址的转换就多了几道转换的工序，这显然就降低了这俩地址转换的速度，也就是带来了时间上的开销。

  程序是有局部性的，即在一段时间内，整个程序的执行仅限于程序中的某一部分。相应地，执行所访问的存储空间也局限于某个内存区域

  我们就可以利用这一特性，把最常访问的几个页表项存储到访问速度更快的硬件，于是计算机科学家们，就在 CPU 芯片中，加入了一个专门存放程序最常访问的页表项的 Cache，这个 Cache 就是 TLB

  有了 TLB 后，那么 CPU 在寻址时，会先查 TLB，如果没找到，才会继续查常规的页表

 

局部性原理见下面

 

## **CPU** **寻址了解吗?为什么需要虚拟地址空间?**

现代处理器使⽤的是⼀种称为 **虚拟寻址(Virtual Addressing)** 的寻址⽅式。**使⽤虚拟寻址，CPU需要将虚拟地址翻译成物理地址，这样才能访问到真实的物理内存**。实际上完成虚拟地址转换为物理地址转换的硬件是 CPU 中含有⼀个被称为 **内存管理单元（Memory Management Unit,MMU）** 的硬件;

![image-20220715200843261](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220715200843261.png)

 

## **为什么要有虚拟地址空间呢？**

先从没有虚拟地址空间的时候说起吧！没有虚拟地址空间的时候，**程序都是直接访问和操作的都是物理内存** 。但是这样有什么问题呢？

1. ⽤户程序可以访问任意内存，寻址内存的每个字节，这样就很容易（有意或者⽆意）破坏操作系统，造成操作系统崩溃。

2. 想要同时运⾏多个程序特别困难，⽐如你想同时运⾏⼀个微信和⼀个 QQ ⾳乐都不⾏。为什么呢？举个简单的例⼦：微信在运⾏的时候给内存地址 1xxx 赋值后，QQ ⾳乐也同样给内存地址 1xxx 赋值，那么 QQ ⾳乐对内存的赋值就会覆盖微信之前所赋的值，这就造成了微信这个程序就会崩溃。

**总结来说：如果直接把物理地址暴露出来的话会带来严重问题，⽐如可能对操作系统造成伤害以及给同时运⾏多个程序造成困难**

通过虚拟地址访问内存有以下优势：

- 不同进程使⽤的虚拟地址**彼此隔离**，它让每个进程产⽣了⼀种⾃⼰在独享主存的错觉；⼀个进程中的代码⽆法更改正在由另⼀进程或操作系统使⽤的物理内存。
- **它为每个进程定义了⼀个连续的虚拟地址空间**，并且**把内存扩展到硬盘空间**，使得程序可以拥有超过物理内存的空间大小；

 

## **什么是虚拟内存(Virtual Memory)**

**虚拟内存**是计算机系统内存管理的⼀种技术; 这个在我们平时使⽤电脑特别是 Windows 系统的时候太常⻅了。很多时候我们使⽤点开了很多占内存的软件，这些软件占⽤的内存可能已经远远超出了我们电脑本身具有的物理内存。**为什么可以这样呢？** 正是因为 **虚拟内存** 的存在，通过 **虚拟内存** 可以让程序可以拥有超过系统物理内存⼤⼩的可⽤内存空间。虚拟内存 就是当内存不够用，借用额外存储空间进行主存的扩展，是一种逻辑内存空间。

> 基于局部性原理实现的 ；再讲一下下面的虚拟存储器

另外，**虚拟内存为每个进程提供了⼀个连续的、私有的地址空间，它让每个进程产⽣了⼀种⾃⼰在独享主存的错觉**。这样会更加有效地管理内存并减少出错。

所以：**虚拟内存的重要意义是它为每个进程定义了⼀个连续的虚拟地址空间**，并且 **把内存扩展到硬盘空间**，使得程序可以拥有超过物理内存的空间大小；

[深入理解计算机系统 - 虚拟内存 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/368032279)

 

## 局部性原理

局部性原理是虚拟内存技术的基础，正是因为程序运⾏具有局部性原理，才可以只装⼊部分程序到内存就开始运行

局部性原理表现在以下两个方面：

- 时间局部性 ：如果程序中的某条指令⼀旦执⾏，不久以后该指令可能再次执⾏；如果某数据被访问过，不久以后该数据可能再次被访问。产⽣时间局部性的典型原因，是由于在程序中存在着⼤量的循环操作。

- 空间局部性 ：⼀旦程序访问了某个存储单元，在不久之后，其附近的存储单元也将被访问，即程序在⼀段时间内所访问的地址，可能集中在⼀定的范围之内，这是因为指令通常是顺序存放、顺序执⾏的，数据也⼀般是以向量、数组、表等形式簇聚存储的。

 


## 虚拟存储器

基于局部性原理，在程序装入时，可以将程序的一部分装入内存，而将其他部分留在外存，就可以启动程序执行。由于外存往往比内存大很多，所以我们运行的软件的内存大小实际上是可以比计算机系统实际的内存大小大的。在程序执行过程中，当所访问的信息不在内存时，由操作系统将所需要的部分调入内存，然后继续执行程序。另一方面，操作系统将内存中暂时不使用的内容换到外存上，从而腾出空间存放将要调入内存的信息。这样，**计算机好像为用户提供了一个比实际内存大的多的存储器----虚拟存储器。**

实际上，我觉得虚拟内存同样是**一种时间换空间的策略**，你用CPU 的计算时间，页的调入调出花费的时间，换来了一个虚拟的更大的空间来支持程序的运行。

 

## 虚拟内存的技术实现/虚拟内存管理

**虚拟内存的实现需要建立在离散分配的内存管理方式的基础上，虚拟内存的实现有以下三种方式**:

- **请求分页存储管理**:建立在分页管理之上，为了支持虚拟存储器功能而增加了**请求调页功能和页面置换功能**。请求分页是目前最常用的一种实现虚拟存储器的方法。请求分页存储管理系统中，在作业开始运行之前，仅装入当前要执行的部分页即可运行。假如在作业运行的过程中发现要访问的页面不在内存，则由处理器通知操作系统按照对应的页面置换算法将相应的页面调入到主存，同时操作系统也可以将暂时不用的页面置换到外存中。
- **请求分段存储管理**:建立在分段存储管理之上，增加了**请求调段功能、分段置换功能**。请求分段储存管理方式就如同请求分页储存管理方式一样，在作业开始运行之前，仅装入当前要执行的部分段即可运行; 在执行过程中，可（使用请求调入中断）动态装入要访问但又不在内存的程序段 ; 当内存空间已满，而又需要装入新的段时，根据置换功能适当调出某个段，以便腾出空间而装入新的段。
- **请求段页式存储管理**

 


## 请求分页与分页存储管理的不同？

根本区别在于，**是否要求将程序所需全部的地址空间都装入内存**，分页存储是这样要求的，所以无法提供虚拟内存

 

## 常见的页面置换算法有哪些？

在程序运行过程中，如果要访问的页面不在内存中，就发生缺页中断从而将该页调入内存中。此时如果内存已无空闲空间，系统必须从内存中调出一个页面到磁盘对换区中来腾出空间。这就是页面置换

页面置换算法的主要目标是使页面置换频率最低（也可以说缺页率最低）

- 最佳置换算法（OPT）：理论上最好的算法，每次置换选择的将是未来最久不会被访问的页面


- 最近最久未使用（LRU）: 记录的是页面上次的访问时间，每次置换掉访问时间离现在最晚的页面


- 最少使用（LFU）：该置换算法选择在之前时期使⽤最少的⻚⾯作为淘汰页，记录的是一段时间内的使用频率。


- 先进先出（FIFO）：每次置换的将是最先进来的页面

 

# 常见场景题

## 1、数据量大内存不够的排序问题（10G数据1G内存）- 分治思想(分多个小文件)

方案：将数据切分成n段，保证每段数据的大小在内存中放得下；对各段数据进行堆排序；产生n个有序的小文件；然后多路归并排序即可（每个文件取最小，n个较小值中，再取最小的写入最终文件）；

类似问题：[原创 | 一张图秒杀滴滴大数据场景题(已拿offer)_无精疯的博客-CSDN博客](https://blog.csdn.net/a934079371/article/details/114362209?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-114362209-blog-85269982.t0_layer_searchtargeting_s&spm=1001.2101.3001.4242.1&utm_relevant_index=3)

##  2、数据量大内存不够找出不重复的数（2.5亿个整数中找出不重复的整数）-2 bitmap

方案1：采用**2-Bitmap**（每个数分配2bit，00表示不存在，01表示出现一次，10表示多次，11无意义）进行，共需内存2^32 * 2 bit=1 GB内存，还可以接受。然后扫描这2.5亿个整数，查看Bitmap中相对应位，如果是00变01，01变10，10保持不变。扫描完事后，查看bitmap，把对应位是01的整数输出即可。

方案2：同上面的划分小文件方法。

## 3、数据量大内存不够，判断数据是否存在--bitmap

如题：给40亿个不重复的unsigned int的整数，没排过序的，然后再给一个数，如何快速判断这个数是否在那40亿个数当中

方案：申请一个2^32长度大小的bitmap，2^29个字节，2^10 x 2^10 x 2^10byte=1GB,所以只需512M内存；一个bit位代表一个unsigned int值。读入40亿个数，设置相应的bit位，读入要查询的数，查看相应bit位是否为1，为1表示存在，为0表示不存在。

[十道海量数据处理面试题 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzU3MzgwNTU2Mg==&mid=2247495750&idx=1&sn=125e5a1800beeeb9faddd5c614136fec&scene=21#wechat_redirect)

[面试系列：十个海量数据处理方法大总结 (qq.com)](https://mp.weixin.qq.com/s?__biz=MzU3MzgwNTU2Mg==&mid=2247485151&idx=1&sn=665e5e284934aecd2fcf3d69e26e3b52&scene=21#wechat_redirect)

 

# 机器学习

## 1、svm

支持向量机（Support Vector Machine, SVM）是一类按[监督学习](https://baike.baidu.com/item/监督学习/9820109)（supervised learning）方式对数据进行[二元分类](https://baike.baidu.com/item/二元分类/15635322)的广义线性分类器（generalized linear classifier），其[决策边界](https://baike.baidu.com/item/决策边界/22778546)是对学习样本求解的最大边距超平面；样本到决策边界的最小距离称为硬间隔，间隔边界线称为支持向量，所以被叫做支持向量机；

SVM使用铰链损失函数（hinge loss）计算经验风险（empirical risk）并在求解系统中加入了正则化项以优化结构风险（structural risk），是一个具有稀疏性和稳健性的分类器 （风险的大小可理解为分类的准确率）。SVM可以通过[核方法](https://baike.baidu.com/item/核方法/1683712)（kernel method）进行非线性分类，是常见的核学习（kernel learning）方法之一。

## 2、Logistics回归

logistic回归又称logistic[回归分析](https://baike.baidu.com/item/回归分析)，是一种广义的线性回归分析模型；

> 以胃癌病情分析为例，选择两组人群，一组是胃癌组，一组是非胃癌组，两组人群必定具有不同的体征与生活方式等。因此[因变量](https://baike.baidu.com/item/因变量)就为是否胃癌，值为“是”或“否”，自变量就可以包括很多了，如年龄、性别、饮食习惯、[幽门螺杆菌](https://baike.baidu.com/item/幽门螺杆菌)感染等。自变量既可以是连续的，也可以是分类的。然后通过logistic回归分析，可以得到自变量的权重，从而可以大致了解到底哪些因素是胃癌的危险因素。同时根据该权值可以根据危险因素预测一个人患癌症的可能性。

logistic回归模型是wx+b,然后通过logistic函数L将w‘x+b对应一个隐状态p，p =L(w‘x+b),然后根据p 与1-p的大小决定因变量的值。

## 3、K均值聚类

常用的无监督学习的聚类算法；算法流程是：

先随机选取K个对象作为初始的聚类中心（K个）。然后计算每个对象与各个种子聚类中心之间的**距离**，把每个对象分配给距离它最近的聚类中心。聚类中心以及分配给它们的对象就代表一个聚类。一旦全部对象都被分配了，每个聚类的聚类中心会根据聚类中现有的对象被重新计算（一个类的数据求平均）。这个过程将不断重复直到满足某个终止条件。终止条件可以是以下任何一个：

1)没有（或最小数目）对象被重新分配给不同的聚类。

2)没有（或最小数目）聚类中心再发生变化。

3)误差平方和局部最小。

## 4、神经网络

神经网络是通过对人脑的基本单元——神经元的建模和联接，探索模拟人脑神经系统功能的模型，并研制一种具有**学习、联想、记忆和模式识别等智能信息处理功能的人工系统**。神经网络的一个重要特性是**它能够从环境中学习，并把学习的结果分布存储于网络的突触连接中**。神经网络的学习是一个过程，在其所处环境的激励下，相继给网络输入一些样本模式，并按照一定的规则（学习算法）调整网络各层的权值矩阵，待网络各层权值都收敛到一定值，学习过程结束。然后我们就可以用生成的神经网络来对真实数据做分类。

![image-20220824232252453](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220824232252453.png)

## 5、决策树

决策树(Decision Tree）是在已知各种情况发生概率的[基础](https://baike.baidu.com/item/基础/32794)上，通过构成决策树来求取**净现值的[期望](https://baike.baidu.com/item/期望/35704)值**大于等于零的概率，评价项目风险，判断其可行性的决策分析方法，是直观运用概率分析的一种图解法。由于这种决策分支画成图形很像一棵树的枝干，故称决策树。

决策树是一种树形结构，其中每个内部节点表示一个属性上的测试，每个分支代表一个测试输出，每个叶节点代表一种类别。也一种监督学习。

 

# 数仓项目

 

## 数据采集与传输流程

数据分为用户行为数据和业务数据；

对于用户行为数据，通过埋点得到，并传输到日志服务器，避免单层flume采集数据在高峰期阶段容易出现数据积压导致宕机的情况; 采用双层flume进行数据传输；第一层数据传输：flume将数据发送到kafka消息队列做一个缓冲；第二层：flume消费kafka将数据导入HDFS；（数据类型为json类型）

> 第一层：flume 采用 TailDir Source：断点续传、多目录、采用 Kafka Channel，省去了 Sink，提高了效率。KafkaChannel 数据存储在 Kafka 里面， 所以数据是存储在磁盘中
>
> 第二层：Kafka source、file channel、hdfs sink;
>
> > FileChannel 传输速度相对于 Memory 慢，但数据安全保障高，Agent 进程挂掉也可以从 失败中恢复数据。
>
> 配置三个参数从源头预防大量小文件的产生
>
> 官方默认的配置会产生小文件
>
> ![image-20220628135303181](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220628135303181.png)
>
> 基于以上hdfs.rollInterval=3600，hdfs.rollSize=134217728，hdfs.rollCount =0几个参数综合作用，效果如下：
>
> ①文件在达到128M时会滚动生成新文件
>
> ②文件创建超3600秒时会滚动生成新文件

 

对于业务数据，同样是通过埋点然后将数据传输到业务服务器，之后传入MySQL数据库（在数据库中提前建好了表）并使用sqoop将数据以增量或者全量等同步策略导入HDFS；

> 由于条件限制，本数仓使用的数据均为通过脚本模拟生成；  最终存储在hdfs上，且数据采用 LZO 压缩，减少磁盘存储空间；
>
> 因为hdfs 本身不支持lzo压缩，所以需要编译配置hdfs 支持lzo , 此外 为了使LZO压缩文件可切片，手动为lzo文件建索引；

 

**同步策略**

数据同步策略的类型包括：全量同步、增量同步、新增及变化同步、特殊情况

- 全量表：每天存储一份完整的数据。
- 增量表：存储新增加的数据。
- 新增及变化表：存储新增加的数据和变化的数据。**(订单表为例，create_time改变则是新增，operate_time改变则是变化)**
- 特殊表：只需要存储一次

![image-20220719152712413](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220719152712413.png)

## **数仓搭建与数据计算**

#### 1、数仓分层

![image-20220406094904759](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220406094904759.png)

> **DIM公共维度层**
>
> **公共**维度汇总层DIM（Dimension）基于**维度建模理念**，建立整个企业的一致性维度。
>
> 公共维度汇总层（DIM）主要由维度表（维表）构成。维度是逻辑概念，是衡量和观察业务的角度。维表是根据维度及其属性在数据平台上构建的物理化的表，采用宽表设计的原则。因此，公共维度汇总层（DIM）首先需要定义维度。

 

#### 2、数仓理论

**关系建模与维度模型：**

关系模型严格遵循第三范式（3NF），数据冗余程度低，数据的一致性容易得到保证。由于数据分布于众多的表中，查询会相对复杂，在大数据的场景下，查询效率相对较低。

维度模型以**数据分析**作为出发点，不遵循三范式，故数据存在一定的冗余。维度模型面向业务，将业务用事实表和维度表呈现出来。表结构简单，故查询简单，查询效率较高。

维度模型分为：星型模型、雪花模型、星座模型；本数仓全部采用星型模型；

**DWD采用维度建模，使用的模型为星型模型；**

数仓中的表分为事实表和维度表：

**维度表**：一般是对事实的**描述信息**。每一张维表对应现实世界中的一个对象或者概念。  例如：用户、商品、日期、地区等

**事实表：**事实表中的每行数据代表一个业务事件（下单、支付、退款、评价等）

> **1）事务型事实表**
>
> 以**每个事务或事件为单位**，例如一个销售订单记录，一笔支付记录等，作为事实表里的一行数据。一旦事务被提交，事实表数据被插入，数据就不再进行更改，其更新方式为增量更新。
>
> **2）周期型快照事实表**
>
> 周期型快照事实表中**不会保留所有数据**，**只保留固定时间间隔的数据**，例如每天或者每月的销售额，或每月的账户余额等。
>
> 例如购物车，有加减商品，随时都有可能变化，但是我们更关心每天结束时这里面有多少商品，方便我们后期统计分析。全量同步策略
>
> **3）累积型快照事实表**
>
> **累计快照事实表用于跟踪业务事实的变化。**例如，数据仓库中可能需要累积或者存储订单从下订单开始，到订单商品被打包、运输、和签收的各个业务阶段的时间点数据来跟踪订单声明周期的进展情况。当这个业务过程进行时，事实表的记录也要不断更新；新增及变化

**维度建模流程：选择业务过程→声明粒度→确认维度→确认事实**

**DWS层和DWT层统称宽表层**

**ADS层  对系统各大主题指标分别进行分析**，不涉及建模；

#### 3、数仓搭建

数仓搭建基于hive，所有的数据由hive进行管理

**ods层：**在hive中以天为分区创建对应的表；包括日志表和业务数据表；将数据从hdfs导入至hive表中；（日志表每一行都是一个字符串，以字符串的格式进行存储，json字符串）

原始数据层，存放原始数据，直接加载日志、业务数据；保持原貌不做处理；创建各个日志表和业务数据表（按照日期分区，指定分隔符，指定parquet列式存储+LZO压缩，设置在HDFS上的存储位置）从HDFS中将 日志数据和业务数据加载进 ods 层中。

**DIM层：**公共维度层；五张维度表：商品维度表、优惠券维度表、地区维度表、时间维度表、用户维度表；

用户维度表以拉链表的方式制作；

拉链表，记录每条信息的生命周期；一旦一条信息的生命周期结束，就重新开始一条新的记录，并把当前日期放入生效开始日期；

拉链表适合于：数据会发生变化，但是变化频率并不高的维度；比如用户维度表。

**DWD层：**明细数据层，1）对用户行为数据解析。 2）对核心数据进行判空过滤。 3）对业务数据采用维度模型重新建模。

**DWS层和DWT层统称为宽表层**：以需求为驱动，构建各个主题表，DWS层按天进行轻量汇总，DWT在DWS基础上进行累积汇总；

**ADS层**：数据应用层，各种指标统计表格（用户留存率等）；

 

 

## 全流程调度与可视化

**全流程调度**

**报表数据要先写入mysql：在MySQL中创建ADS对应的表格，并将数据导入；**

1、在集群中部署Azkabna

2、编写Azkaban项目文件，流文件（添加依赖信息），并将 azkaban.project、gmall.flow文件压缩到一个zip文件，文件名称必须是英文

3、在Azkaban Web界面新建项目，上传文件并配置参数即可进行全流程调度；

> Azkaban 是由 Linkedin 公司推出的一个批量工作流任务调度器，主要用于在一个工作流 内以一个特定的顺序运行一组工作和流程，它的配置是通过简单的 key:value 对的方式，通 过配置中的 Dependencies 来设置依赖关系。Azkaban 使用 job 配置文件建立任务之间的依赖 关系，并提供一个易于使用的 web 用户界面维护和跟踪你的工作流。
>
> ![image-20220406165841252](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220406165841252.png)

**可视化**

部署Superset，并对接MySQL数据源，添加dataset; 将所有数据表格都导入为 dataset；创建仪表盘；选择数据 创建图表保存到仪表盘，然后进行可视化展示；

> Apache Superset 是一个开源的、现代的、轻量级 BI 分析工具，能够对接多种数据源、 拥有丰富的图标展示形式、支持自定义仪表盘，且拥有友好的用户界面，十分易用；

 

## Kylin 即席查询

Kylin 是一个开源的分布式分析引擎 底层会依赖于hadoop/spark（最新版已经支持flink）
能对PB级别以上的数据做到亚秒查询 做到交互式的效果

支持标准 SQL 接口

可伸缩性（可以搭建kylin集群）和高吞吐率：单节点 Kylin 可实现每秒 70 个查询

可以与BI 工具集成，将查询好的数据可视化（比如Kylin 自己开发的Zepplin）

### Kylin术语

<img src="https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211030152909674.png" alt="image-20211030152909674" style="zoom:150%;" />

![image-20211030153545901](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211030153545901.png)

![image-20211030154540505](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211030154540505.png)
Cuboid：每个角度对应的数据集，所有的Cuboid加在一起组成一个cube
比如此例中就7个Cuboid 一个cube
麒麟对接的就是我们的维度模型 能对接星型模型也能对接雪花模型。
一个cube对应星型或者雪花模型
一个星型或雪花模型里有一张事实表 多张维度表
一个事实表对应一个业务线 比如下单事实表对应下单

预计算过程：

首先，计算最高维度的多维数据集。多维分析就是对维度字段进行分组，对度量字段进行聚合。计算多维数据集是按照角度去分组聚合的。
然后后续需要分析计算cuboid的时候对最高维度的cube进行降维，三维到二维，二维到一维。

### Kylin架构

![image-20211030155644350](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211030155644350.png)

1.数据源

RDBMS（关系型数据库）

2.REST Server

访问这个暴露的接口，进入这个接口后给相应的请求（查询、构建刷新合并cube、获取元数据、用户权限等等）

然后给我们响应json数据

3.查询引擎（Query Engine）

当 cube 准备就绪后，查询引擎就能够获取并解析用户查询。把SQL解析成HBase查询语言

4.路由器（Routing）

因为预计算只能做分组聚合类的查询，一些复杂查询麒麟无法预计算

所以从Hbase中查不到结果就路由到Hive中。因为查询速度的差异，后面就不路由去Hive了。

现在去HBase中查不到结果就返回空所以尽量查询聚合数据

5.元数据管理工具（Metadata）

OLAP cube的元数据以及其他元数据

比如哪些维度字段

度量值是什么

聚合函数是啥

6.任务引擎（Cube Build Engine）
计算搭建多维数据集cube，处理所有离线任务（比如shell java MR）
这个模块是所有模块的基础，它负责预计算创建cube，创建的过程是通过hive读取原始数据然后通过一些==mapreduce计算==生成Htable然后load到hbase中。
cube是通过预计算缓存在hbase中

### **Kylin** **安装**

上传Kylin 安装包 tar.gz -> 解压 -> 启动
Kylin 依赖 hive hbase hadoop ZK
所以启动 Kylin 之前，需先启动 Hadoop、Zookeeper、Hbase
在 http://hadoop102:7070/kylin 查看 Web 页面

### Kylin 使用

创建项目工程 - 获取数据源（导入 Hive 表） -
创建 model : -
指定事实表 - 选择维度表，并指定事实表和维度表的关联条件 -

> 指定维度字段 (因为维度退化，所以选维度字段时可以来自事实表也可以来自维度表)   现在只是在给字段分类，没有涉及计算 计算的时候用哪些维度我们还得重新指明<

指定度量字段 -

>指定事实表分区字段（仅支持时间分区）根据此字段识别,进行此计算是哪一天的

构建 cube:
选择 cube 所依赖的 mode - 选择所需的维度 -

> 选择四个维度的话 Cuboid就有15个 2的四次方-1个 维度数量太多计算就爆炸

选择所需度量值 还有聚合函数

- cube 自动合并设置

>   为提高查询效率，需将每日计算出来的 cube 进行合并，此处可设置合并周期
>   7天小合并、28天大合并

Kylin 相关属性配置覆盖

>在这配的参数只对当前cube有效,全局则需要到kylin的conf目录

-选择要构建的时间区间构建 Cube（计算）

>默认是MR做计算 实际上任务已经提交到yarn上了

-点击 Monitor 查看构建进度

1.如何给kylin配置计算规则
定义好预计算的规则：维度、度量值、聚合函数
2.如何使用kylin查询数据

 

## 数据安全模块

### `Kerberos`**用户认证**

`Kerberos`**用户认证** 用于验证自己的身份；比如Hadoop设计之初，默认集群内所有的节点都是可靠的。由于用户与HDFS或M/R进行交互时不需要验证，恶意用户可以伪装成真正的用户或者服务器入侵到hadoop集群上，导致：恶意的提交作业，篡改HDFS上的数据，造成及其严重的后果。所以进行`Kerberos`用户认证时十分有必要的；

> **Kerberos 是一种计算机网络认证协议，用来在非安全网络中，对个人通信以安全的手段 进行身份认证，软件设计上采 用客户端/服务器结构**，**并且能够进行相互认证**，即客户端和服务器端均可对对方进行身份 认证。可以用于防止窃听、防止重放攻击、保护数据完整性等场合，**是一种应用对称密钥体 制进行密钥管理的系统**。

`Kerberos`有以下四个核心概念：

1）`KDC（Key Distribute Center）`：密钥分发中心，负责存储用户信息，管理发放票据。

2）`Realm`：`Kerberos`所管理的一个领域或范围，称之为一个Realm。

3）`Principal`：`Kerberos`所管理的一个用户或者一个服务，可以理解为`Kerberos`中保存的一个账号，其格式通常如下：`primary/instance@realm`

4）`keytab`：`Kerberos`中的用户认证，可通过密码或者密钥文件证明身份，`keytab`指密钥文件。

**流程**：

选择一台服务器作为Kerbers服务端，安装KDC（包括初始化、修改配置文件等），所有主机都需 要部署 Kerberos 客户端；

安装配置并启动Kerbers服务后，**首先要做的就是创建管理员用户**；用于**后续登录KDC数据库创建主体**（kinit admin/admin）

**为hadoop配置`Kerberos`用户认证**

1、**创建 Hadoop 系统用户**

为 Hadoop 开启 Kerberos，需为不同服务准备不同的用户，启动服务时需要使用相应的用户。比如hdfs、yarn、mapreduce用户，并且配置他们**都属于Hadoop用户组**。

2、**Hadoop Kerberos 配置**

- 为各个服务（进程）创建Kerberos主体（NN、2NN等），配置以密钥文件的方式进行认证，因为服务不能提供一个交互界面 ; 并配置Hadoop用户组下面用户有权限访问密钥路径（不配置的话只有root可以，hadoop下的hdfs就不可以，因为启动nn等服务是hdfs用户）；

- 修改 Hadoop 配置文件(keberos用户和系统用户的映射关系，配置各服务的访问需要认证等)

  > kerberos中有一套用户体系；hadoop有自己的一套用户体系；访问hadoop要自己的用户体系，所以要配置映射关系（kerberos映射到hadoop）；nn主体（用户）映射到HDFS 用户，所以启动nn...只能用hdfs用户；

- 配置`HDFS`使用`HTTPS`安全传输协议  (**用keytool配置**，修改文件名ssl-server.xml.example为 ssl-server.xml；配置keystore路径和密码、配置turststore路径和密码、配置密钥对密码)

  > Keytool 是 java 数据证书的管理工具，使用户能够管理自己的公/私钥对及相关证书。

-     配置`Yarn`使用`LinuxContainerExecutor` 哪个用户提交的MR，container所属用户（启动container的用户）就是他，不配置默认时，是启动namenode的用户。

3、**启动hadoop**

    在启动之前需要修改特定的路径访问权限，因为现在是每个服务一个用户了，之前统一一个用户，所以现在可能对一些路径没有访问权限，需要进行修改。

现在hadoop的**`Kerberos`用户认证**配置已完成，那么现在对于普通用户来说，如果它要能访问集群有三个条件

- 集群中的每个节点都需要创建该用户
- 该用户需要属于 hadoop 用户组，因为只有属于hadoop用户组才能拥有对Hadoop各个服务的访问权限（拿到钥匙 然后访问）
- 需要创建该用户对应的 Kerberos 主体

那么完成用户的认证之后，即可访问集群；

 

(对于普通用户只能访问hdfs，hdfs超级用户才能修改hdfs相关内容)

![image-20220629080403158](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220629080403158.png)

hdfs自己能读写和执行；别人只能读和执行；

 

> 之后为hive、hive的客户端datagrip配置了Kerberos用户认证；

**接下来配置了 数仓全流程 用户认证**；**此处统一将数仓的全部数据资源的所有者设为 hive 用户**，全流程的每步操作均认证为 hive 用户，这样方便访问所有的数据；

那么首先就是创建hive用户，并创建其主体生成密钥文件，并分发密钥文件（主要是为了azkaban, azkaban自选节点为excutor进行执行）；

其次是数据采集通道的修改：

- flume提供了参数用于配置Kerberos用户认证；只需增加参数即可；
- sqoop并未提供参数进行配置，所以修改数据脚本，在脚本的第一行增加认证语句，认证为hive；

修改HDFS 特定路径所有者为hive；（ 数据路径、hive的家目录）

最后在各节点创建azkaban用户，加入hadoop 组，启动azkaban，让azkaban拥有各脚本的访问权限，即可在安全环境下进行全流程调度。

 

### Ranger权限管理

Apache Ranger是一个Hadoop平台上的全方位数据安全管理框架，它可以为整个Hadoop 生态系统提供全面的安全管理；允许用户使用一个管理工具对操作 Hadoop 体系中的组件和工具的行为进行**细粒度** 的授权；

> 允许用户**使用 UI** 或 REST API 对所有和安全相关的任务进行集中化的管理
>
> **允许用户使用一个管理工具对操作 Hadoop 体系中的组件和工具的行为进行细粒度 的授权**
>
> 支持 Hadoop 体系中各个组件的授权认证标准
>
> 增强了对不同业务场景需求的授权方法支持，例如基于角色的授权或基于属性的授 权
>
> 支持对 Hadoop 组件所有涉及安全的审计行为的集中化管理

 

**Ranger** **的工作原理**

Ranager 的核心是 Web 应用程序，也称为 RangerAdmin 模块，此模块由管理策略，审计日志和报告等三部分组成。

管理员角色的用户可以通过 RangerAdmin 提供的 web 界面或 REST APIS 来定制安全策略。这些策略会由 Ranger 提供的轻量级的针对不同 Hadoop 体系中组件的插件来执行。插件会在 Hadoop 的不同组件的核心进程启动后，启动对应的插件进程来进行安全管理！

> **为某组件配置管理策略需要安装一个对应的插件，如Ranger Hive-plug。**

 

**Ranger权限管理基于开启 Kerberos 安全认证的 Hadoop 和 Hive 环境**

首先创建系统用户和 Kerberos 主体

Ranger 的启动和运行需使用特定的用户，故须在 Ranger 所在节点创建所需系统用户并 在 Kerberos 中创建所需主体。

- 创建ranger用户，加入hadoop用户组

- HTTP 主体（该主体在 Hadoop 开启 Kerberos 时已创建） 用于web ui界面的认证
- rangeradmin 主体      包含管理策略，审计日志和报告等。
- rangerlookup 主体    同步hadoop组件的元数据信息，比如hive同步库、表、字段等
- rangerusersync 主体   同步系统的用户信息

**安装RangerAdmin**

- 使用mysql作为ranger 存储数据的数据库；
- 首先在mysql中创建ranger存储数据的数据库ranger，创建Mysql的ranger用户，并把数据库ranger下的所有表的所有权限授予ranger用户
- 解压软件并配置安装文件（需要的数据库名和用户信息，各组件主体用户密码，还有一些Kerberos 用户认证的配置信息：包括lookup主体和密钥文件，启动时就能拿到去做认证）
- 即可启动RangerAdmin，并通过6080端口访问web 页面

**安装RangerUsersync**

解压并配置启动文件（因为系统中的用户和数据资源会发生变化，所以需要配置同步时间间隔，RangerUsersync的用户密码，Kerberos 用户认证的配置信息），之后即可启动RangerUsersync

**安装 Ranger Hive-plugin**，是 Ranger 对 hive 进行权限管理的插件，Ranger Hive-plugin 只能对使用 jdbc 方式访问 hive 的请求进行权限管理，hive-cli 并不受限制

- 同样解压并配置启动文件（install.properties）（策略管理器的 url 地址，组件名称：hive、hive组件的启动用户、hive的安装目录、hive组件的启动用户等）；

- 在 ranger admin  web页面 上配置 hive 插件

  - 授予hive用户在Ranger 中的 Admin 角色

  - 配置hive插件：点击 Access Manager，添加 Hive Manager并进行相关配置

  ![image-20220617211134040](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220617211134040.png)

配置完之后即可进行具体的策略管理；

对普通用户来说：

首先需要进行用户认证，**然后赋予其对数据仓库中数据（gmall数据库）的操作权限**；之后点击web页面的add policy按钮，按需求配置具体的管理策略（比如用户张三对数据中的某张表有访问权限）。

> Ranger 授权模型 Ranger 所采用的权限管理模型可归类为 RBAC（Role-Based Access Control ）基于角色 的访问控制。基础的 RBAC 模型共包含三个实体，分别是用户（user）、角色（role）和权 限（permission）。用户需划分为某个角色，权限的授予对象也是角色，例如用户张三为管 理角色，那他就拥有了管理员角色的所有权限。

![image-20220404110540038](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220404110540038.png)

 

 

![image-20220404204218681](C:\Users\FangWu\Documents\My Knowledge\temp\634103890\upload\image-20220404204218681.png)

 

## 数据管理模块

### Atlas元数据管理

元数据：数据的描述信息，在数据仓库中指的是库、表、字段等；

元数据管理的意义：让开发人员和业务人员快速的了解数据的关系以及数据本身的含义；精准的定位需要查找的数据，从而减少数据的研究成本，提高效率，减少熟悉业务的时间减少

Atlas提供 **元数据分类、元数据检索、构建血缘**关系的功能。

![image-20220617212911029](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220617212911029.png)

 

**Atlas安装需要集成 Kafka和HBase和 Solr，Kafka用于将元数据导入Atlas；Atlas采用HBase存储元数据；采用Solr来建立索引 方便的访问元数据；**

> Atlas自带一些组件（hive-hooks等，相当于一个监控hive功能，元数据只要产生变动即可将其发送到Kafka，然后发送到Atlas）
>
> solr是将整个索引操作功能封装好了的搜索引擎系统(企业级搜索引擎产品)

所以要安装Atlas前，先需要安装准备好Kafka、HBase和Solr，然后配置Atlas集成kafka，HBase和Solr

**集成HBas**

- 在Atlas的配置文件（atlas-application.properties）中添加zoookeeper集群地址，hbase需要基于zookeeper进行交互访问
- 在atlas环境变量配置文件（atlas/conf/atlas-env.sh）中添加HBase的配置文件路径（/opt/module/hbase/conf），atlas需要拿到hbase的配置文件

**集成Solr**

- 在Atlas的配置文件（atlas-application.properties）中修改参数：使用solr创建索引、solr工作模式为cloud模式、zookeeper集群地址。
- 创建 Solr 索引容器：顶点索引、边索引、全文索引；并配置三个分区


**集成kafka**

- 在Atlas的配置文件（atlas-application.properties）中配置kafka的数据目录、zookeeper集群地址、Kafka集群地址

 

最后配置 Atlas自己服务的一些参数（/atlas-application.properties 配置文件中）：web ui地址、zookeeper集群地址等；

 

但现在Atlas还不能与hadoop集群交互，因为hadoop开启了用户认证；所以需要先创建Atlas主体进行认证。

**最后集成hive，为hive做元数据管理**：这里最重要的是安装并配置hive-hook ；

> Hive无法自己把变动信息发至kafka，所以需要hive暴露的一个（钩子）接口 hook，每一条语句都会触发hook，Atlas自定义hook后把类/jar包加载进classpath下面，后续的每次查询都会触发逻辑（每条SQL语句都发送到kafka 然后atlas就会拿到信息然后就能解析元数据的变动）

1、在Atlas安装路径下安装hive-hook ；

2、在hive环境变量文件/hive/conf/hive-env.sh中添加额外jar包信息路径，就是刚安装的hive-hook 相关jar包；

3、修改 Hive 配置文件，在/opt/module/hive/conf/hive-site.xml 文件中增加参数依赖，配置 Hive Hook；

4、atlas/conf/atlas-application.properties 配置文件中配置参数：**hook向Kafka异步发送**、失败重试次数等、

5、将 Atlas 配置文件atlas/conf/atlas-application.properties 拷贝到/hive/conf 目录下，因为hive中的hook程序需要atlas的一些相关参数；

现在可以启动Atlas了，需要将**元数据初次导入**，Atlas 提供了一个 Hive 元数据导入的脚本，直接执行该脚本，即可完成 Hive 元数据的 初次全量导入；现在登录Atlas WEB页面就可以看到相关元数据信息了；但是现在并不能看到具体的血缘关系，原因是 Atlas 是根据 Hive 所执行的 SQL 语句获取 表与表之间以及字段与字段之间的依赖关系的，下次执行SQL 语句之后就能看到血缘关系了

 

### 数据质量管理

数据质量管理（Data Quality Management），是指对数据从计划、获取、存储、共享、 维护、应用、消亡生命周期的每个阶段里可能引发的各类**数据质量问题，进行识别、度量、 监控、预警等一系列管理活动，并通过改善和提高组织的管理水平使得数据质量获得进一步 提高**。

![image-20220629094558122](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220629094558122.png)

**准确性：**准确性是指数据中记录的信息和数据是否准确、是否存在异常或者错误的信息。例如，成绩单中分数出现负数或订单中出现错误的买家信息等，这些数据都是问题数据。

 

在本数仓中进行了

- ODS 层数据量，每日环比和每周同比变化不能超过一定范围

- DIM 层id 不能有空值，重复值；  （完整性、唯一性）

- DWD 层id 不能有空值，重复值 ；（完整性、唯一性）

  的指标监控

本数仓使用了 **Python 和 Shell 脚本**实现数据质量监控的各项功能；包括四个模块：检测存储模块、告警模块、调度模块、可视化模块；

先初始化MySQL 环境；MySQL 主要用于存储数据质量监控的结果值，这里需要提前建库建表：创建 data_supervisor 库，五个结果表

- 空值指标表：字段有日期、表名、列名、空id个数、上下限值、告警级别

- 重复值指标表

- 值域指标表: 字段有日期、表名、列名、超出预定值域(value值)个数、值域上下限、结果值上下限值、告警级别

  > 订单金额规定0-10万，就是值域上下限，超过0-10个数的个数不大于100，就是结果值上下限

- 环比增长指标表；字段有日期、表名、环比增长百分比(统计数据量行数)、上下限值、告警级别

  > 环比：（今天-昨天）/ 昨天

- 同比增长指标表。

  > 同比：（本周-上周）/  上周

**检测模块**

**单一指标检测脚本**：检测规则脚本分为五个shell脚本：分别是

- 空 id 检查脚本
- 重复 id 检查脚本
- 值域检查脚本
- 数据量环比检查脚本
- 数据量同比检查脚本

> 如果日期和告警级别没有设置的话，日期默认为昨天，告警级别为0 ; 因为hive开启了Kerberos 认证，所以在脚本中还需认证语句认证为hive用户

**数仓各层检测脚本**： 为数仓各层创建单独脚本，在各层脚本中调用单一指标检测脚本，并将结果插入MySQL 对应的表中；

**ods层**：check_ods.sh

![image-20220618090158982](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220618090158982.png)

调用  数据量同比检查脚本 、数据量环比检查脚本、值域检查脚本；

**DWD层**：check_dwd.sh ：订单表

**DIM层**：check_dim.sh ：用户表

 

**告警集成模块**

该模块主要用于检查 MySQL 中的检测结果的异常，若有异常出现就发送警告。警告方式可选择邮件或者集成第三方告警平台睿象云。

> 使用电子邮件发送告警信息可能会出现接收不及时的现象

该部分的脚本用python实现；安装python的MySQL驱动

新建 python 脚本（check_notification.py）用于查询数据监控结果表格并发送告警，脚本中主要包含三个函数

- read_table 用于读取指标有问题的数据
- one_alert 函数用于向睿象云发送告警
- mail_alert 函数用于发送邮件告警（使用smtp协议配置发送邮件）

one_alert 函数中集成了第三方告警平台睿象云；集成睿象云需要使用的 rest 接口 和 APP KEY，须在睿象云平台获取；并根据睿象云的 rest api 要求，传入必要的参数（事件类型、事件ID等）

 

**调度模块**

该模块的主要功能为调度数据质量监控流程。数据质量监控工作流也采用 Azkaban 进行 调度。**数据质量监控工作流必定依赖数据仓库工作流，此处为了解耦，利用 Azkaban API 主动监视数据仓库工作流的执行状态，进而触发数据质量监控工作流**

比如一分钟检测一次数仓某一节点是否计算完成，完成后  再把监测结果写入MySQL,然后进行数据质量检查和告警；

编写 Azkaban REST API 封装脚本azclient.py ，该脚本主要是对 Azkaban API 的封装，主要有三个方法：

- login 函数可以登录 Azkanban 并返回 **session_id** （使用`Authenticate`API进行azkaban身份认证，获取session ID）
- get_exec_id 函数（ get_exec_id(session_id ) ）可以获取正在执行的工作流程的 **Execution ID** （使用`Fetch Running Executions of a Flow`API获取正在执行的Flow的Exec Id）
- **wait_node 可以等待指定 Flow 中某一结点执行完毕并判断其是否执行完成**（循环使用`Fetch a Flow Execution`API获取指定Flow中的某个节点(job)的执行状态，直到其执行完成）**在某一结点执行完毕后，才触发数据质量监控**

 

**编写各层调度脚本**：调用Azkaban REST API 封装脚本传入节点参数进行判断，继而进行各层的数据质量监察；

如：check_ods.py：

调用 Azkaban REST API 封装脚本azclient.py 导入三个函数：login 、get_exec_id 、wait_node ；判断**hdfs_to_ods_db**节点是否执行完成，**执行完成就调用ods层的检测脚本进行检测**，否则就等待；

编写azkaban工作流配置文件, 一个 .project项目文件，一个 .flow流文件；   最后将所有的文件打包成zip包，在 Azkaban 框架中新建项目并上传该文件，即可进行数据质量管理；

> 启动数仓工作流时需要加一个useExecutor参数因为此时脚本都只位于hadoop102这一台节点去Azkaban数据库看到102节点的执行id为1
>
> 因为只有102节点有hive的客户端或者MySQL的客户端所以启动质量监控工作流的时候也需要加一个useExecutor参数

 

**可视化模块**

该模块的主要作用是对数据质量监控结果进行可视化展示。 检测结果可以采用 Superset 进行可视化展示，新建连接到MySQL数据库；添加dataset; 将所有数据表格都导入为 dataset；创建仪表盘；选择数据 创建图表保存到仪表盘，然后进行可视化展示

 

[最新数仓面试题_知行教育数仓项目 - 云+社区 - 腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1811111)

## 项目中的面试题

集群规模：一台4核6GB，两台2核4GB阿里云服务器(学生机)

数据规模：一天大概1.5~2GB , 用到了两天的数据；（最多2x2x3副本=12G）

 

### 为什么使用flume

Flume是**一个高可靠的，分布式的海量日志采集、聚合和传输的系统**；Flume当初的设计初衷就是将数据传送到HDFS中，它更加地注重数据的传输，此外他具有高可靠特性，在Flume中传输的数据会持久化在channel中，除非已确认数据被传输到了下一位置，即sink端，否则不会删除，这个过程是通过事务来控制的，这样的设计使得可靠性非常好。

memory channel 保存在内存，可能会丢数据

file channel 保存在磁盘  不会丢数据

 

> **Flume缺点？**
>
> 可能数据重复。
>
> 例如数据已经成功由Sink发出，但是没有接收到响应，Sink会再次发送数据，此时可能会导致数据的重复。

 

![image-20220806223454272](C:\Users\FangWu\Documents\My Knowledge\temp\634103890\upload\image-20220806223454272.png)

 

flume 相关问题

[Flume采集日志数据_时差N小时的博客-CSDN博客_flume采集日志数据](https://blog.csdn.net/elsechan/article/details/114868126)

 

### 介绍下flume/flume架构

#### **定义**：

Flume是**一个高可靠的，分布式的海量日志采集、聚合和传输的系统**

 

#### **架构**

![image-20220806212248869](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220806212248869.png)

**Agent**

Agent是一个JVM进程，它以事件的形式将数据从源头送至目的。

Agent主要有3个部分组成，Source、Channel、Sink

 

**Sources**：Source负责数据的产生或搜集；从数据发生器接收数据，并将接收的数据以Flume的event格式传递给一个或者多个通道Channel

① Taildir Source：断点续传、多目录
② Exec Source：监测文件中新增内容
③ Spooling directery Source：监测目录下新增的文件
④ Avro Source 用于Flume的级联场景

⑤kafka source 对接kafka数据源

 

**channel**: 是一种短暂的存储容器，负责数据的存储持久化；将从source处接收到的event格式的数据缓存起来，直到它们被sinks消费掉

File Channel：将所有事件写到磁盘，数据存储在磁盘中，宕机数据可以保存

Memory Channel:事件数据写到内存中

Kafka Channel：减少Flume的Sink阶段，提高了传输效率

 

**Sinks**：Sink不断地轮询Channel中的事件且批量地移除它们，并将这些事件批量写入到存储或索引系统、或者被发送到另一个Flume Agent。

① HDFS Sink：推送数据到HDFS，可能产生大量小文件问题
② Avro Sink：用于Flume的级联场景
③ File Roll Sink：存放在外部文件系统中，每隔指定时长生成文件并且保存在这段时间内收集到的日志数据
④ HBase Sink：存储在HBase中
⑤ Logger Sink：用于调试

**Event**

传输单元，Flume数据传输的基本单元，以Event的形式将数据从源头送至目的地。Event由Header和 Body两部分组成，Header用来存放该event的一些属性，为K-V结构，Body用来存放该条数据，形式为字节数组。

![image-20220809161245016](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220809161245016.png)

### 自定义flume拦截器

自定义拦截器的步骤
三步走：
① 实现Interceptor拦截器的接口
② 重写四个方法：
initialize 初始化
public Event intercept(Event event) 处理单个Event
public List<Event>  intercept(Listevents) 处理多个event方法，在这个方法中调用Event intercept(Event event)
close 方法
③静态内部类，实现interceptor.Builder；返回一个拦截器

**TimeStamp时间戳拦截器**：把事件时间加入到header中，**以事件时间而不是系统处理时间分区，解决日志数据的时间跨天的问题。**

**将获取的ts时间写入拦截器header头，header的key必须是timestamp，因为Flume框架会根据这个key的值识别为时间，写入到HDFS**

① 获取数据，数据都存在body中：使用event.getBody()
② 解析Json：JSON.parseObject(json)
获取时间戳：Long ts = obj.getLong(“ts”);
③将时间戳写入header
Map<String, String> headers = event.getHeaders();
// 要求传入字符串，但解析得到的ts为Long类型，故使用+""，即用字符串拼接方法转换成字符串
headers.put(“timestamp”,ts+"");
④ 数据返回
return event;

 

### flume 和kafka区别

它们都是流式数据采集框架

- Flume是**一个高可靠的，分布式的海量日志采集、聚合和传输的系统**；Kafka是一个可持久的**分布式消息队列**、除了消息传递，还有日志缓存，解耦等功能
- Flume追求的是数据和数据源、数据流向的多样性，适合多个生产者的场景；有内置的source 和 sink组件；Kafka追求的是高吞吐，高负载，同一topic下可以有多个partition，由于是pull模式拉取数据，因此适合多个消费者的场景；kafka没有内置的producer和consumer组件，需要自己编写代码
- Flume是用于将数据发送到HDFS的专用工具。Kafka可以支持多个应用程序的数据流，比如应用于spark flink等等实时场景。

 

### **为什么使用Flume+Kafka**

**flume 多数据源 + kafka  缓冲 与 解耦合**

- 生产环境中，往往是读取日志进行分析，而这往往是多数据源的，如果Kafka构建多个生产者使用文件流的方式向主题写入数据再供消费者消费的话，无疑非常的不方便。
- 如果Flume直接对接实时计算框架，当数据采集速度大于数据处理速度，很容易发生数据堆积或者数据丢失，而kafka可以当做一个消息缓存队列；
- Kafka属于中间件，一个明显的优势就是使各层解耦。因此数据从数据源到Flume再到Kafka时，数据一方面可以同步到HDFS做离线计算，另一方面可以做实时计算，可实现数据多分发。

 

### **Spark和Hive对比，谁更好，你觉得为什么（spark sql vs HQL）**

> 要看实际使用场景。
>
> Hive：**数据存储和清洗**，处理海量数据，比如一个月、一个季度、一年的数据量，依然可以处理，虽然很慢。
>
> Spark SQL：**数据清洗和流式计算**，上述情况下Spark SQL不支持，无法处理，因为其基于内存，量级过大承受不住，并且性价比不如Hive高。

综合来看：

Hive的强项在于：1）大数据存储；2）通过sql方式进行MapReduce操作，降低大数据使用门槛，成本低

Spark强项在于：1）基于内存操作，速度快；2）流式计算。

运用上大多两者集合，Hive负责数据仓库存储，Spark sql负责计算，并结合DataFrame进行复杂的数据挖掘（包括机器学习、图计算等复杂算法）。

 

### **Spark和Hive的联系**

* **Hive on Spark**：

  Hive 既作为存储元数据又负责 SQL 的解析优化，语法是 HQL 语法，执行引擎变成了 Spark，Spark 负责采用 RDD 执行。

* Spark on Hive :

  Spark本身只负责数据计算处理，并不负责数据存储。Hive 只存储数据，Spark 负责 SQL 解析优化，语法是 Spark SQL语法，Spark 负责采用 RDD 执行。

 

### Kafka压测

采用官方的脚本进行测试；

#### producer端

kafka-producer-perf-test.sh

创建一个test topic，设置为3个分区2个副本；我此时三台服务器的总带宽在30m/s左右，两个副本 ；所以Kafka的吞吐量预期为 15m/s；

 

如果压测结果显示没达到预期

那么就要Kafka调整参数，Kafka默认异步批量发送，所以可调以下两个参数

- 调整batch.size

batch.size默认值是16k。batch.size较小，会降低吞吐量，测试吞吐量如果小于期望吞吐量比较多，可以调大这个值；但也不能调太大。batch.size过大，会增加消息发送延迟；

- linger.ms

linger.ms为消息发送的时间间隔，可设置为你能接受的延迟时间

同时设置batch.size和 linger.ms，就是哪个条件先满足就都会将消息发送出去

**Kafka需要考虑高吞吐量与延时的平衡**

 

#### comsumer端

kafka-consumer-perf-test.sh

测试的吞吐量小于预期：

- 调整fetch-size

  增加fetch-size值，增大每次拉取的数据量

- 如果这四个指标（IO，CPU，内存，网络）都不能改变，考虑增加分区数来提升性能

 

### kafka 分区数怎么计算确定

（1）创建一个只有1个分区的topic

（2）测试这个topic的producer吞吐量和consumer吞吐量。

（3）假设他们的值分别是Tp和Tc，单位可以是MB/s。

（4）然后假设总的目标吞吐量是Tt，那么分区数 = Tt / min（Tp，Tc）

例如：producer吞吐量 = 20m/s；consumer吞吐量 = 50m/s，期望吞吐量100m/s； 分区数 = 100 / 20 = 5分区

 

> 如果问有没有出现Kafka有没有出现消息积压
>
> 可回答1：没有，因为我的Kafka分区数，是经过**压测**来大致决定的，通过Kafka 的bin目录下提供的kafka-consumer-groups.sh 消费者组管理脚本查看，没有出现消息积压的情况；然后可以谈一下压测！和如果出现消息积压怎么解决。

 

### 数仓为什么要分层？

如果不分层的话：有什么数据就去原始数据查，这样比较麻烦、而且效率低、逻辑多、SQL语句长 、定位改动麻烦。

1.**把复杂问题简单化** ： 将复杂的任务分解成多层来完成，每一层只处理简单的任务。

2.**清晰的数据结构**  每一个数据分层都有它的作用域 , 这样我们在使用表的时候能更方便地定位和理解.

3.**减少重复开发**: 规范数据分层，通过的中间层数据，能够减少极大的重复计算，增加一次计算结果的复用性。

> 比如：某几个需求最开始汇总的几个步骤都是相同的。

4.**隔离原始数据** : 不用关心原始数据的异常还是数据的敏感性，**使真实数据与统计数据解耦开**。

 

### 数仓建模：为什么用维度建模？

  因为关系型建模严格遵循三范式； 表与表之间得关系较为松散 零碎、数据分布于众多的表中。关系模型虽然冗余少，但是在大规模数据，跨表分析统计查询过程中，会造成多表关联，join的表越多，查询的也就越慢，性能也就越差。维度建模是一种以业务为驱动的数仓建模方法，比较贴近人的思维 容易理解 表的关系简单 查询的时候不会join太多层 所以效率较高。维度模型更适合做数据的分析--比如聚合分析等等。

* 维度建模：

  [数仓建设中最常用模型--Kimball维度建模详解 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/343473640)

  * **维度建模分为两种表：事实表和维度表**

    维度表：**一般是对事实的描述信息**。每一张维表对应现实世界中的一个对象或者概念。 例如：用户、商品、日期、地区等。

    **事实表**：**事实表中的**每行数据代表一个业务事件（下单、支付、退款、评价等）**。“事实”这个术语表示的是业务事件的**度量值（可统计次数、个数、金额等）

    本项目涉及到三类事实表：

    > * **事务型事实表**: 一行数据就是一个具体的业务事件。例如一笔支付记录。对应于增量同步策略。
    >
    > * **周期型快照事实表**：周期型快照事实表中**不会保留所有数据**，**只保留固定时间间隔的数据**，例如每天或者每月的销售额。对应于全量同步策略。
    >
    > * **累计快照事实表用于跟踪业务事实的变化。**：比如跟踪订单的生命周期(打包、运输和签收)，对应于新增及变化同步策略。

* **维度模型分类**：

  星型模型和雪花模型：**雪花模型与星型模型的区别主要在于维度的层级**，标准的星型模型**维度只有一层**，而雪花模型可能会涉及多级。星座模型与前两种情况的**区别是事实表的数量，星座模型是基于多个事实表**。星座模型的形成只与数据和需求有关。星座模型不如星型模型和雪花模型。

  模型选择：此处选择维度更少的星型模型，以减少join的层数，提升性能。尤其是Hadoop体系，减少Join就 是减少Shuffle，性能差距很大。

* 维度建模四步走：---- DWD层

  > * 选择业务过程：比如下单业务，一条业务线对应一张事实表。
  >
  > * 声明粒度：声明粒度意味着精确定义事实表中的一行数据表示什么，应该尽可能选择最小粒度，以此来应对各种各样的需求。
  >
  > * 确认维度：维度的主要作用是描述事实表，比如时间维度、地区维度、用户维度。
  >
  > * 确认事实: 此处的“**事实**”一词，指的是**业务中的度量值**（次数、个数、件数、金额，可以进行累加），例如订单金额、下单次数等

 

### OLTP与OLAP

1.定义
OLTP（on-line transaction processing）翻译为联机事务处理， OLAP（On-Line Analytical Processing）翻译为联机分析处理，从字面上来看OLTP是做事务处理，OLAP是做分析处理。从对数据库操作来看，OLTP主要是对数据的增删改，OLAP是对数据的查询。

2.区别
OLTP主要用来记录某类业务事件的发生，如购买行为，当行为产生后，系统会记录是谁在何时何地做了何事，这样的一行（或多行）数据会以增删改的方式在数据库中进行数据的更新处理操作，要求实时性高、稳定性强、确保数据及时更新成功，像公司常见的业务系统如ERP，CRM，OA等系统都属于OLTP。

当数据积累到一定的程度，我们需要对过去发生的事情做一个总结分析时，就需要把过去一段时间内产生的数据拿出来进行统计分析，从中获取我们想要的信息，为公司做决策提供支持，这时候就是在做OLAP了。

因为OLTP所产生的业务数据分散在不同的业务系统中，而OLAP往往需要将不同的业务数据集中到一起进行统一综合的分析，这时候就需要根据业务分析需求做对应的数据清洗后存储在数据仓库中，然后由数据仓库来统一提供OLAP分析。所以我们常说OLTP是数据库的应用，OLAP是数据仓库的应用，下面用一张图来简要对比。

![image-20211022142849135](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20211022142849135.png)

所以OLAP和OLTP之间的关系可以认为OLAP是依赖于OLTP的，因为OLAP分析的数据都是由OLTP所产生的，也可以看作OLAP是OLTP的一种延展，一个让OLTP产生的数据发现价值的过程。

 

### 为什么要采用parquet列式存储 ★★★★★

parquet的定义是：Parquet是为了使Hadoop生态系统中的任何项目都可以使用压缩的，高效的列式数据表示形式

所以第一点：

1、跨平台、可被各种文件系统识别；（兼容 hive 与 spark ; 就是说支持使用hql和spark sql查询）

2、采用parquet 存储格式压缩比率高；**且配合lzo压缩，支持切片**

3、parquet  基于列式存储，可只选择所需要的列，提升性能，因为ADS需要统计指标可能只需要来源于一张宽表的某一两列字段；

 

### 为什么采用lzo压缩 ★★★★★

1、它支持切片，压缩/解压速度比较快，压缩率也还不错

2、文件需要列式存储，**列式存储又要支持切片；所以采用lzo配合parquet **

（主要是**Parquet比orc更通用（olap查询时、如impala）**、使用了Parquet，所以用lzo来支持压缩；不然ORC+snappy也行）

 

> 可切片的压缩：
>
> **Bzip2 压缩**     优点：压缩率高；**支持 Split**； 缺点：压缩/解压速度慢。
>
> **Lzo 压缩**     优点：压缩/解压速度比较快；**支持 Split**； 缺点：压缩率一般；想支持切片需要额外创建索引，Hadoop不自带

列式存储有：**orc、parquet**  ; ORC没有支持切片的压缩格式  （ORC 本身支持切分）

![image-20220614085949255](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220614085949255.png)

![image-20220727160140790](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220727160140790.png)

### 订单业务数仓工作流程 ★★★★★

以订单业务为例：

1、从ODS层的订单表开始；到DWD层首先对订单信息进行清洗和脱敏；与维度表关联进行维度建模；得到订单事实表

2、到达DWS宽表层：与DWD层的其他事实表（如评论事实表）一同构建为用户行为宽表；进行轻量数据汇总

3、到达DWT层同样是宽表层；得到用户主主题宽表，是对数据的累积汇总

4、最后到达ADS层；进行指标分析；可进行用户行为漏斗分析；

> 漏斗分析:浏览首页->浏览商品详情页->加入购物车->下单->支付

 

### 用户维度表-拉链表

拉链表定义：所谓拉链，就是记录历史。记录一个事物从开始，一直到当前状态的所有变化的信息，就是记录每条数据的生命周期（有开始时间和结束时间字段）。

为什么要用拉链表：对本数仓的用户维度表而言；用户信息会发生变化，但是每天变化的比例不高，如果数据量有一定的规模，按照每日全量的方式保存效率很低；每日全量会保存很多不变（重复）的信息，对存储是极大的浪费。

实现：

1、从拉链表中查找出截至今天**前一天**的最新数据

2、从ODS层查询出今天的新增及变化的用户信息（因为ods层的用户表同步策略就是新增及变化，直接查出来就行），这里还有个数据脱敏操作（md5加密），并加上开始时间和结束时间字段；

3、对上面两张子表做**全外连**，选出**最新数据**和**过期数据**并采用动态分区方式写入对应的分区（过期数据和最新数据写入不同的分区）；

> insert overwrite table dim_user_info partition(dt) --动态分区
>
> 重叠部分nvl函数取最新
>
> 过期数据：两个子表的uid同时不等于null，然后选择旧的数据，并将结束日期改成前一天

 

![image-20220611160039938](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220611160039938.png)

**需要使用nvl 函数**，函数的功能是实现空值的转换

例如`NVL(string1,replace_with)`中：
当第一个参数（`string1`）为空时，返回第二个参数（`replace_with`）；
当第一个参数（`string1`)不为空时，则返回第一个参数（`string1`）。

 

### 数仓各层做了哪些事？

#### ODS层

原始数据层

1）创建分区表，按照日期分区，指定分隔符，指定parquet列式存储+LZO压缩；压缩比是 100g 数据压缩完 10g 左右。

2）将数从hdfs导入 创建好的表

3）保持数据原貌，不做任何修改

#### DIM层

维度表：构建企业的一致性维度

创建维度表：商品维度表、优惠券维度表、活动维度表、地区维度表、时间维度表、用户维度表

用户维度表采用拉链表的方式制作；

#### DWD层

1）对用户行为数据解析（因为日志是jason的格式，get_json_object解析每个字段）

2）对核心数据进行清洗及脱敏：判空过滤 、对手机号和身份证号进行加星号处理。

3）对业务数据采用维度模型重新建模（采用的是星型模型）

得到多个事实表

- 事务型事实表：评价事实表、订单明细事实表、退单事实表；增量更新
- 周期型快照事实表（每日快照）：加购事实表、收藏事实表；全量更新
- 累积型快照事实表：优惠券领用事实表、支付事实表、退款事实表、订单事实表；新增及变化

数据压缩LZO

parquet列式存储

#### DWS层  数据服务层 --宽表层

**DWS层存放的所有主题对象当天的汇总行为**，例如每个地区当天的下单次数，下单金额等，

6张宽表：用户主题、访客主题、商品主题、优惠券主题、活动主题、地区主题

最宽的宽表是**用户主题宽表**

本数仓由于资源限制，只有25个字段、现实场景中大概有 60-100 个字段

评论、打赏、收藏、关注--商品、关注--人、点赞、分享、好价爆料、文章发布、活跃、 签到、补签卡、幸运屋、礼品、金币、电商点击

#### DWT层  数据主题层--宽表层

**DWT层存放的是所有主题对象的累积行为**，例如每个地区最近７天（１５天、３０天、６０天）的下单次数、下单金额等。

用户主题、访客主题、商品主题、优惠券主题、活动主题、地区主题；

#### ADS层--数据应用层

日活、月活、周活、留存、留存率、新增（日、周、年）、转化率、流失、回流、七天 内连续 3 天登录、连续 3 周（月）登录、 top n 热门商品、复购率、复购率排行

 

### 为什么要设计宽表

DWS层和DWT层统称宽表层，这两层的设计思想大致相同，通过以下案例进行阐述。

1）问题引出：两个需求，统计每个省份订单的个数、统计每个省份订单的总金额

2）处理办法：都是将省份表和订单表进行join，group by省份，然后计算。同样数据被计算了两次，实际上类似的场景还会更多。

那怎么设计能避免重复计算呢？

针对上述场景，可以设计一张地区宽表，其主键为地区ID，字段包含为：下单次数、下单金额、支付次数、支付金额等。上述所有指标都统一进行计算，并将结果保存在该宽表中，这样就能有效避免数据的重复计算。

3）总结：

（１）需要建哪些宽表：**基本上以维度为基准**。

（２）宽表里面的字段：是站在不同维度的角度去看事实表，重点关注事实表聚合后的度量值。

 


### 分析过最难的指标

**最近** **7** **天连续** **3** **天活跃用户数**

1）查询出最近7天的活跃用户，并对用户活跃日期进行排名

2）计算用户活跃日期及排名之间的差值

3）对同用户及差值分组，统计差值个数

4）将差值相同个数大于等于3的数据取出，然后去重(group by用户；一个用户可能多个三天活跃)，即为连续3天及以上活跃的用户

![image-20220426090015241](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220426090015241.png)

###  Azkaban 是怎么全流程调度的

在集群中部署Azkaban；数仓各层之间有调度脚本，编写Azkaban.flow流文件：添加各个脚本的依赖关系（depends on）；以及 azkaban.project项目文件；这个文件里面就只有一条语句，azkaban的版本；将这两个文件打包成两个ZIP包；在azkaban web页面新建项目，上传这个ZIP包，配置参数（日期、指定Executor运行）即可进行运行进行全流程调度；

 

## 优化、难点、遇到的问题

> ### 双重group by 提前预防数据倾斜；
>
> 第一重将key值加随机数前缀，进行group by 后可以使原来相同key进入到不同的 reduce task ，预防数据倾斜的发生;
>
> 第二重 将随机数去除；再使用一次group by 将数据进行聚合；
>
> **比如统计用户的历史下单次数 使用group by 分组；单重group by分组很可能造成数据倾斜；**

 

> ### 对null 值添加随机key值 预防数据倾斜
>
> 场景：构建用户维度表时；
>
> 表关联时，对null 值添加随机key值，将其分发到不同的reduce中处理；所以对结果无影响。
>
> ```sql
> SELECT *
> FROM log a left join users b
> on case when a.user_id is null then concat('hive',rand()) else a.user_id end = b.user_id;
> ```

 

### 全局排序优化 ★★★★★

场景：ADS商品主题：热门商品销量排名，然后取前100条

使用order by 商品销量进行全局排序，只会产生一个reduce，性能低下；

可以 使用distribute by（按指定字段分发到不同reduce） +  sort by ; 在多个reduce上进行排序；最后汇总到一个reduce进行排序；

 

--从表中获取name长度为TOP10的数据

```sql
select a.id,a.name from
(
 select id,name  from <table_name>
 distribute by length(name)  sort by length(name) desc limit 10
) a
order by length(a.user_name) desc limit 10;
```

 

### Flume 内存优化

问题：启动消费Flume 抛出OOM异常，
解决：在flume-env.sh 的配置文件中 设置JVM相关参数
-Xms 2048m    -Xmx 2048m
XMS表示JVM Heap(堆内存)的最小内存   XMX表示JVM Heap(堆内存)的最大内存
将其 Xms和Xmx 大小设置一致 减少内存抖动带来的性能影响 否则容易在初始化时由于内存不够，频繁触发 fullgc  从而会引发 flume 的暂停。

 

###  FileChannel优化

通过配置dataDirs指向多个路径，每个路径对应不同的硬盘，增大Flume吞吐量。

 

### yarn容量调度器 并发度的问题

Yarn 默认调度器为 Capacity Scheduler（容量调度器）
问题：容量调度器 default 队列中，**同一时间只有一个任务执行，并发度低**。
原因：因为容量调度器中限制了**同时运行**的任务可占用队列的资源的10% 但是因为虚拟机资源少 可能起一个任务就达到了资源的10% 了  所以队列的第二个任务跑不了；
解决：通过参数yarn.scheduler.capacity.maximum-am-resource-percent 调整为队列的50%
还可以配置 Yarn 容量调度器多队列    比如按照业务区分队列 （下单队列、支付队列等等）

 

> - ### spark cluster 模式下的jvm  永久代内存溢出问题
>
> - cluster 模式下，driver运行在集群的某个节点中，使用的是没有经过配置的默认设置永久代大小 ：82M;  sql逻辑会进行语义解析、语法树转换等；
>
> - 调整永久代默认为128M；最大为256M；

 


> ### 配置spark使用kryo序列化
>
> - 默认情况下，Spark内部是使用Java的序列化机制，ObjectOutputStream / ObjectInputStream，对象输入输出流机制，来进行序列化
> - 这种默认序列化机制的好处在于，处理起来比较方便；也不需要我们手动去做什么事情，只是，你在算子里面使用的变量，必须是实现Serializable接口的，可序列化即可。
> - 但是缺点在于，默认的序列化机制的效率不高，序列化的速度比较慢；序列化以后的数据，占用的内存空间相对还是比较大。
>
> 可以手动进行序列化格式的优化
>
> - **Spark支持使用Kryo序列化机制**。Kryo序列化机制，比默认的Java序列化机制，速度要快，序列化后的数据要更小，大概是Java序列化机制的1/10。
>
> > 所以Kryo序列化优化以后，可以让网络传输的数据变少；在集群中耗费的内存资源大大减少。
>
> Kryo序列化机制，一旦启用以后，会生效的几个地方：
>
> 1、算子函数中使用到的外部变量
> 2、持久化RDD时进行序列化，StorageLevel.MEMORY_ONLY_SER
> 3、shuffle
>
> 1、算子函数中使用到的外部变量，使用Kryo以后：优化网络传输的性能，可以优化集群中内存的占用和消耗
> 2、持久化RDD，优化内存的占用和消耗；持久化RDD占用的内存越少，task执行的时候，创建的对象，就不至于频繁的占满内存，频繁发生GC。
> 3、shuffle：可以优化网络传输的性能
>
> **实现**
>
> 1、首先第一步，在SparkConf中设置一个属性，spark.serializer，org.apache.spark.serializer.KryoSerializer类；
>
> SparkConf.set("spark.serializer", "org.apache.spark.serializer.KryoSerializer")
>
> 2、第二步，注册你使用到的，需要通过Kryo序列化的，一些自定义类，SparkConf.registerKryoClasses()
>
> 项目中的使用：
> .set("spark.serializer", "org.apache.spark.serializer.KryoSerializer")
> .registerKryoClasses(new Class[]{CategorySortKey.class})

 

### hive和spark的兼容性问题

官网下载的Hive3.1.2和Spark3.0.0默认是不兼容的。因为Hive3.1.2支持的Spark版本是2.4.5，所以需要我们重新编译Hive3.1.2版本。

编译步骤：

官网下载Hive3.1.2源码，修改pom文件中引用的Spark版本为3.0.0，如果编译通过，直接打包获取jar包。

如果报错，就根据提示，修改相关方法，直到不报错，打包获取jar包。

 

### Sqoop中导入导出Null存储一致性问题

Hive中的 Null 在底层是以 “\N” 来存储，而MySQL中的 Null在底层就是 Null，为了保证数据两端的一致性。

从hive导出数据时采用 --input-null-string 和 --input-null-non-string 两个参数。在导入数据到hive时采用 --null-string 和 --null-non-string。

--input-null-string  '\N' 告诉sqoop 遇到 string类型的字段为  '\N' 导入到mysql中存储为null值

null-string '\N' 含义是 string类型的字段，当Value是NULL，替换成指定的字符'\N'

 

### Sqoop解决数据重复导入到MySQL的问题

解决数据重复的问题就是加参数 ：update-key
指定哪些字段匹配视为同一条数据，进行更新而不增加。也就是指定唯一键
--update-key $2 \    用这个来判断新插入的数据在mysql表中存不存在，所以这里传的参数就是目标表的组合唯一键,保证数据能插入

需要配合参数：

--**update-mode allowinsert**: 若数据在mysql存在，就用新导入的数据对他进行覆盖，不存在的数据进入导入；

> 1) sqoop有两种导出模式：
> 2) 一种是insert，将导出的数据翻译成insert语句；因为sqoop只会导入全量数据，会和里面存在的重复字段出现insert冲突
> 3) 一种是update，将数据翻译成update语句，它又分两种小模式：
>  3.1) allowinsert:若数据在mysql存在，就用新导入的数据对他进行覆盖，不存在的数据进入导入
>     3.2) updateonly(默认):不会新增新数据，只会修改里面的老数据

![image-20220802170727858](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220802170727858.png)

 

### sqoop 导数据到hive发生数据倾斜问题

场景：采用sqoop的多实例并行抽数：导用户表（10来个字段）的时候，发现其中一个任务耗时比其他任务长不少

用户表 百万行数据，4个map , 三个都是10秒左右，最后一个五十来秒

> 每个map大概6m/s；4个并行就是总的 24m/s;传输10秒就是240M；40x6=240m; 共480m

**怎么发现的：跑任务比较慢，打开yarn执行页面查看**

**问题**：

sqoop import 抽数的并行化主要涉及到两个参数：num-mappers：启动N个map来并行导入数据，默认4个；split-by：按照某一列来切分表的工作单元

sqoop是对切分字段做了一个取最大最小值的操作, 然后（最大值-最小值）/  num-mappers 得到各个map获取的数据范围

> 比如select max(split_by),min(split-by) from得到的max(split-by)和min(split-by)分别为1000和1，而num-mappers为2的话，则会分成两个区域(1,500)和(501-100),同时也会分成2个sql给2个map去进行导入操作，分别为select XXX from table where split-by>=1 and split-by<500和select XXX from table where split-by>=501 and split-by<=1000。最后每个map各自获取各自SQL中的数据进行导入工作。

开始split-by直接使用了string类型的主键id作为切分字段，发现sqoop对主键求最大值和最小值，完全不能用（求出来的值远小于id所要表达的值）

**解决**：

1、没有进行类型强转是因为 id的分区也可不均匀，也可能导致数据倾斜

2、**为表创建一个ROWNUM 严格递增字段，用它来作为split-by的参数**

```shell
sqoop import \
--connect jdbc:oracle:thin:@192.168.119.227:1521:odsdb \
--username 123123 \
--password 123123 \
--query 'select draw_id,third_user_id,login_name,user_id,activity_id,participate_times,
is_realized,prize_type_info,useing_detail_id,draw_time,remark,status,is_valid,pk_serial,
created_user,created_date,updated_user,updated_date,task_id,prize_sources,
prize_relation_id,share_string,biz_type,biz_key from
## 添加了一个 ROWNUM
(select ROWNUM AS ETL_ID,ead.* from i_efsdata.efs_activity_draw ead) t1 where $CONDITIONS'\
--fields-terminated-by '\001' \
--hive-drop-import-delims \
--target-dir /ori_warehouse/oylsqooptest/manyMap/ \
--delete-target-dir \
--null-string '\\N' \
--null-non-string '\\N' \
--split-by ETL_ID \
 
## 指定需要求最值的字段
--boundary-query "select 1 as MIN,sum(1) as MAX from i_efsdata.efs_activity_draw" \
-m 32 &> /opt/sqoop_test/logs/oyltest_manyMap_Sqoop.log
```

**参数一：**

```sh
--query 'select draw_id,third_user_id,login_name,user_id,activity_id,participate_times,
is_realized,prize_type_info,useing_detail_id,draw_time,remark,status,is_valid,pk_serial,
created_user,created_date,updated_user,updated_date,task_id,prize_sources,
prize_relation_id,share_string,biz_type,biz_key from
(select ROWNUM AS ETL_ID,ead.* from i_efsdata.efs_activity_draw ead) t1 where $CONDITIONS'\
```

我们看这个查询的sql,是两个SQL拼接上去的，

**第一个SQL**：select ROWNUM AS ETL_ID,ead.* from i_efsdata.efs_activity_draw ead 是为了得到一个均匀分布的字段 ； （oracle的写法）

第二个SQL:就是不想将ROWNUM 字段也导过来所以将字段都写出来了

**参数二**：

--boundary-query "select 1 as MIN,sum(1) as MAX from i_efsdata.efs_activity_draw" \
不加参数二报错

此参数是自己指定怎么来获当前表的max,min，为什么还需要自己指定呢？我们在shell脚本里面的--split-by参数是不是换成了我们临时制造出来的一个字段 ETL_ID，**但是这个字段在表里面是不存在的**，所以如果不指定自定义获取max,min那sqoop在去获取max,min的时候就会使用ETL_ID字段，那就报错了

[(1条消息) Sqoop生产数据倾斜问题验证_NC_NE的博客-CSDN博客_sqoop 数据倾斜](https://blog.csdn.net/NC_NE/article/details/121962916)

 

 

## 简洁介绍

### 1、**数据采集与传输流程**

数据分为用户行为数据和业务数据；

1、对于用户行为数据，通过网页埋点得到，并传输到日志服务器（我这里...），为了避免单层flume采集数据在高峰期阶段容易出现数据积压导致宕机的情况 使用俩层flume进行数据采集；第一层数据传输：flume采集日志服务器的数据发送到kafka消息队列；第二层：flume消费kafka将数据导入HDFS；（数据类型为json类型）

> 每条日志包含了 页面数据、动作数据、曝光数据、错误数据、公共数据等；还有启动日志

- 第二层数据写到hdfs 配置roll.size等参数  从源头预防大量小文件的产生

2、对于业务数据，同样是通过埋点然后将数据传输到业务服务器，之后传入MySQL数据库并使用sqoop将数据增量或者全量的导入HDFS；(本数仓使用的业务数据为通过脚本模拟生成并直接写入MySQL（在数据库中提前建好了表）

- 解决sqoop并行抽取数据时产生的数据倾斜问题

- 且数据最终存储到HDFS采用 LZO 压缩，减少磁盘存储空间

 


### 2、**数仓搭建与数据计算**

**数仓的搭建基于hive，数据计算引擎为spark（hive  on spark）**

对数仓进行分层搭建，各层分别是：

**ODS层**：原始数据层，存放原始数据，创建各个日志表和业务数据表（按照日期分区，指定分隔符，指定parquet列式存储+LZO压缩，设置在HDFS上的存储位置）从HDFS中将 日志数据和业务数据加载进 ods 层中。对数据本身保持原貌不做处理；

**DIM层**：公共维度层，基于**维度建模理念**，保存维度数据，建立整个企业的一致性维度，五张维度表：商品维度表、优惠券维度表、地区维度表、时间维度表、用户维度表

用户维度表以拉链表的方式制作；

> 拉链表，记录每条信息的生命周期；一旦一条周期的生命周期结束，就重新开始一条新的记录，并把当前日期作为生效开始日期；
>
> 拉链表适合于：数据会发生变化，但是变化频率并不高的维度；比如用户维度表。

**DWD层**：明细数据层，1）对用户行为数据解析 （解析出各个日志表）  2）对核心数据进行清洗：判空过滤、敏感数据加密处理  3）对业务数据采用维度模型重新建模（采用的是星型模型）。

**DWS层**：服务数据层，以DWD为基础，按天进行轻量汇总；一行信息代表一个主题对象一天的行为；

**DWT层**：数据主题层，以DWS为基础，对数据进行累计汇总；一行信息代表一个主题对象的累积行为；

**DWS层和DWT层统称为宽表层：以需求为驱动**

**ADS层**：数据应用层，各种指标统计表格（用户留存率、商品销量排名等）；

数仓各层依次有调度脚本进行数据的传输

 

 

### 3、**全流程调度与可视化**

首先在MySQL中创建数据库，并创建ADS层对应的表格，并用sqoop将数据导入；在使用sqoop导数据时要注意**hive和mysql中数据null值存储一致性**的问题；

1、在集群中部署Azkaban

2、编写Azkaban**项目文件，流文件**：添加各个脚本的依赖关系（depends on），并将 azkaban.project、gmall.flow文件压缩到一个zip文件，文件名称必须是英文

3、在Azkaban界面新建项目，上传文件并配置参数即可进行全流程调度；

**可视化**

部署Superset，并对接MySQL数据源，添加dataset; 将所有数据表格都导入为 dataset；创建仪表盘；选择数据 创建图表保存到仪表盘，然后进行可视化展示；

 

### **4、数据安全模块**

`Kerberos`**用户认证** 和Ranger权限管理

`Kerberos`**用户认证**

Hadoop设计之初，默认集群内所有的节点都是可靠的，这显然是不对的，所以需要进行`Kerberos`**用户认证**配置；防止恶意用户伪装成真正的用户或者服务器入侵到hadoop集群上，导致：恶意的提交作业，篡改HDFS上的数据，造成及其严重的后果。

用户只有经过了`Kerberos`认证才能进入集群访问数据，从而保证安全；为数仓需要与数据交互的组件都配置了`Kerberos`**用户认证**

**Kerberos 是一种计算机网络认证协议，用来在非安全网络中，对个人通信以安全的手段 进行身份认证，软件设计上采 用客户端/服务器结构**，**并且能够进行相互认证**，即客户端和服务器端均可对对方进行身份 认证。可以用于防止窃听、防止重放攻击、保护数据完整性等场合，**是一种应用对称密钥体 制进行密钥管理的系统**。

 

**Ranger权限管理**

Ranger是一个Hadoop平台上的全方位数据安全管理框架，它可以为整个Hadoop 生态系统提供全面的安全管理；允许用户使用一个管理工具对操作 Hadoop 体系中的组件和工具的行为进行**细粒度** 的授权（比如某个用户对某个hive表的某个字段拥有访问权限）

Ranager 的核心是 Web 应用程序，也称为 RangerAdmin 模块，此模块由管理策略，审计日志和报告等三部分组成。

管理员角色的用户可以通过 RangerAdmin 提供的 web 界面或 REST APIS 来定制安全策略。这些策略会由 Ranger 提供的轻量级的针对不同 Hadoop 体系中组件的插件来执行。插件会在 Hadoop 的不同组件的核心进程启动后，启动对应的插件进程来进行安全管理！

**Ranger权限管理基于开启 Kerberos 安全认证的 Hadoop 和 Hive 环境**

 

### **5、数据管理模块**

**Atlas元数据管理**

元数据的管理的意义：让开发人员和业务人员快速的了解数据的关系以及数据本省的含义；精准的定位需要查找的数据，从而减少数据的研究成本，提高效率，减少熟悉业务的时间。

Atlas提供 **元数据分类、元数据检索、构建血缘**关系的功能。

**数据质量管理**

数据质量管理（Data Quality Management），是指对数据生命周期的每个阶段里可能引发的各类**数据质量问题，进行识别、度量、 监控、预警等一系列管理活动，并通过改善和提高组织的管理水平使得数据质量获得进一步提高**。

数据质量的评价标准包括：唯一性；完整性；准确性；合法性；时效性；

在本数仓中进行了

- ODS 层数据量，每日环比和每周同比变化不能超过一定范围    （准确性）

- DIM 层id 不能有空值，重复值；  （完整性、唯一性）

- DWD 层id 不能有空值，重复值 ；（完整性、唯一性）

  的指标监控

本数仓使用了 Python 和 Shell 脚本实现数据质量监控的各项功能；包括四个模块：检测存储模块、告警模块、调度模块、可视化模块；

 

 

# 基于flink的电商平台分析系统

## 数据采集与传输

日志数据：mock data  发送到 ----->kafka 生产者（视频教程里经过springboot传输）

业务数据：mock data ---> mysql---->flinkCDC（一开始从头开始消费）----> kafka

Flink CDC读取binlog文件(row格式)，是磁盘文件；不与MySQL服务打交道；不会增加数据库压力

**开启状态后端并设置checkpiont （hdfs，在Hadoop102） 实现断点续传**

flink CDC可以监控到 所有变化的数据，增删改

**自定义反序列化器**：封装数据 （json套json的json字符串）

![image-20220506205054201](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220506205054201.png)

![image-20220506211544860](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220506211544860.png)

type: insert、update、delete

**日志数据**按类型分流 ：Kafka—>flink(ETL、侧输出流完成日志类型分流：页面日志主流（这里把曝光日志和错误日志也放在里面）、启动日志和动作日志侧输出流)--->提取侧输出流-->Kafka不同主题；

**要写入到侧输出流只能用process**

先进行ETL：

转换成Json对象格式；kafkaDS.process()方法，传入ProcessFunction进行处理，发生异常写到侧输出流；

> ![image-20220506151144506](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220506151144506.png)
>
> 如果用 map 则 遇到脏数据会解析不了并停止任务；
>
> map()  传入 RichMapFunction
>
> process　传入ProcessFunction进行　不同日志类型的分流

## 业务数据**动态分流**

**原因（难点）**：由于FlinkCDC是把全部数据统一写入一个Topic中, 这样显然不利于日后的数据处理。所以需要把各个表拆开处理。但是由于每个表有不同的特点，有些表是维度表，有些表是事实表。

目的、功能 ：实现维表 和 事实表的动态分流，维表写入Hbase，事实表写入Kafka的主题  (同时事实表的新增及更新也放到不同的主题，项目中并未实现)

在实时计算中一般把维度数据写入存储容器，一般是方便通过主键查询的数据库比如HBase,Redis,MySQL等。这样的配置不适合写在配置文件中，因为这样的话，业务端随着需求变化每增加一张表，就要修改配置重启计算程序。所以这里**需要一种动态配置方案**，**把这种配置长期保存起来，一旦配置有变化，实时计算可以自动感知**。

原理：**MySQL配置表 +  flink CDC +   广播流 + connect 连接流**

 

```sql
CREATE TABLE `table_process` (
  `source_table` varchar(200) NOT NULL COMMENT '来源表', '--哪张表'
  `operate_type` varchar(200) NOT NULL COMMENT '操作类型 insert,update,delete',
  `sink_type` varchar(200) DEFAULT NULL COMMENT '输出类型 hbase kafka',
  `sink_table` varchar(200) DEFAULT NULL COMMENT '输出表(主题)',
  `sink_columns` varchar(2000) DEFAULT NULL COMMENT '输出字段',
  `sink_pk` varchar(200) DEFAULT NULL COMMENT '主键字段',
  `sink_extend` varchar(200) DEFAULT NULL COMMENT '建表扩展',
PRIMARY KEY (`source_table`,`operate_type`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

**配置表的一行数据表示，mysql原始数据哪张表，执行什么类型的操作，需要输出到哪里，以及要输出哪些字段；**

实现：创建一个配置表（表字段包括：...），存储在MySQL中 使用flink CDC 读取这张配置表，并广播，需要传入一个mapstate，**形成广播流**

key:  String 类型  为配置表的主键（来源表+操作类型）（flink CDC 读取数据会记录下操作类型：c、u、d，通过自定义反序列化器进行封装改写，类型信息定义为: insert、updata、delete）

value : 类型为tableprocess类（根据 配置表自定义的类，可获取配置唯一信息）

**就是mapstate 的 k-v**

之后与 来自**kafka的数据主流** 使用connect() 方法连接；流连接之后调用process方法传入一个BroadcastProcessFunction **进行分流**

> （BroadcastProcessFunction）Type parameters:
>    – The input type of the non-broadcast side.
>    – The input type of the broadcast side.
>    – The output type of the operator.

- processBroadcastElement()方法 处理广播流数据：

  1、获取并解析数据   ：解析出**配置表**“after”:{}中的数据，因为配置表一般不会删除，通常新增和修改，如果有删除做个判断即可

  2、建表-字符串拼接 （如果新增维度表、sinkType是hbase才需要建表）

  3、写入状态并广播，供主流使用

- processElement() 处理主流数据 ：

  1、获取状态数据

  2、过滤字段 -- 现在的数据是主流的数据，同样只需要拿到“after”:{}数据即可（业务数据来自MySQL）；（过滤：只拿需要的字段数据，在MySQL配置表中表达出来的字段）

  3、分流（**将输出表/主题信息字段写入value中**，Kafka数据写入主流  用OUT写、Hbase数据写入侧输出流，用ctx传入outputag来写）

  **注意：需要将输出表和主题信息写入value，不然value不知道往哪写，不知道属于谁**

分流完成之后，提取Kafka流数据和HBase流数据，根据value中输出表/主题信息字段 写入kafka和Hbase

**往hbase中写**不能以问号赋值的方式

![image-20220523171906883](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220523171906883.png)

因为有多个维表，不确定问号的个数；需要自定义sink，继承RichSinkFunction，因为他有生命周期方法和运行时上下文信息，可以在生命周期方法中创建连接;

```java
public class DimSinkFunction extends RichSinkFunction<JSONObject>
```

open方法：创建连接

invoke方法：获取SQL语句（通过value解析-拼接出来，upsert into....），执行插入操作

value格式："sinkTable"   将输出表/主题信息字段是分流的时候加的；不然后期写入对应存储（Kafka、hbase）的时候没有目标

> ```
>    value:{"sinkTable":"dim_base_trademark","database":"gmall-210325-flink","before":{"tm_name":"atguigu","id":12},"after":{"tm_name":"Atguigu","id":12},"type":"update","tableName":"base_trademark"}
> ```

往kafka写：同样面临多个主题不同数据的问题；自定义一个 带泛型的  FlinkKafkaProducer   **通用方法**：getKafkaProducer（这里需要的是Jsobject类型，但是为了通用，采用了泛型），用另外一种重载方法传入参数：需要四个参数，

![image-20220523175717818](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220523175717818.png)

第二个参数KafkaSerializationSchema 是一个接口，里面只有一个方法，**通过这个方法传入主题信息和数据**，**但现在是泛型**，所以需要以参数形式传入，所以在调用者处确定类型并传入需要的数据，这样就可实现写入不同主题不同数据的功能；

![image-20220523181124335](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220523181124335.png)

[实时数仓之Flink维表关联难点解决方案_雾岛与鲸的博客-CSDN博客_flink 维表关联](https://blog.csdn.net/qq_36039236/article/details/111885049)

现在在Kafka中有完整的日志数据和业务数据、且维度数据存放在hbase；为了方面后面进行指标分析；下一步需要创建张宽表；创建宽表需要和维度字段关联；

## 流表与维表的关联-优化（订单宽表）

**订单流表有两个：订单流表、订单明细流表**（订单分两个表是性能方面的考虑）

**订单流表和订单明细流表采用 双流join实现，用的是inteval join**

> 在flink中的流join大体分为两种，一种是基于时间窗口的join（Time Windowed Join），比如join、coGroup等。另一种是基于状态缓存的join（Temporal Table Join），比如intervalJoin。
>
> 这里选用intervalJoin，因为相比较窗口join，intervalJoin使用更简单，而且**避免了应匹配的数据处于不同窗口的问题**。intervalJoin目前只有一个问题，就是还不支持left join。
>
> 但是我们这里是订单主表与订单从表之间的关联不需要left join，所以intervalJoin是较好的选择。
>
> Flink中基于DataStream的join，只能实现在同一个窗口的两个数据流进行join，但是在实际中常常会存在数据乱序或者延时的情况，导致两个流的数据进度不一致，就会出现数据跨窗口的情况，那么数据就无法在同一个窗口内join。Flink基于KeyedStream提供的interval join机制，intervaljoin 连接两个keyedStream, 按照相同的key在一个相对数据时间的时间段内进行连接。

intervel  join 前面join后面  【-5，5】区间是以前面的为基准，后面的流在这个范围内的可以完成join

**两个流join到下一个流，取上游两个流的较小WaterMarker**

### 维度查询的优化--旁路缓存

订单流表、订单明细流表join之后再调用map方法 查询维度信息（查hbase），补充维度字段

![image-20220523202416455](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220523202416455.png)

但是每次查询都会从HBase中查找数据（尽管HBase客户端会有缓存，查询时间还是不理想），外部数据源的查询常常是流式计算的性能瓶颈，所以决定进行一个维度查询的优化；

我们这里首先使用了使用旁路缓存。

**原理：**旁路缓存模式是一种非常常见的按需分配缓存的模式。如下图，任何请求优先访问缓存，缓存命中，直接获得数据返回请求。如果未命中则查询数据库，同时把结果写入缓存以备后续请求使用。

这里缓存使用了redis，开辟一个jedis连接池；

![img](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220507225504197.png)

> 添加一个二级缓存更快
>
> LRU ：最近最少使用（存最常用的数据）
>
> ![image-20220507225527438](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220507225527438.png)

**实现**：

1、缓存设计注意点：

- 缓存要设过期时间，不然冷数据会常驻缓存浪费资源。

  jedis.expire(redisKey, 24 * 60 * 60);

- 要考虑维度数据是否会发生变化，如果发生变化要主动清除缓存。

       就是往HBase 写入数据，如果是更新，先删除 redis中的缓存，再往hbase中写入数据；

> ![image-20220508082029345](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220508082029345.png)
>
> hash 先是 tablename 为redis key， 里面还是k-v 类型
>
> 用hash 一张表只有一个Key，redis是扩展集群，一张表就会存在一台机器，热点数据问题；
>
> 采用string的话不会这样
>
> **过期时间需要通过 redis key 设置**，设置过期的时候整张表都会过期

2、redisk key设计

redis中存储为 json 字符串的格式，redis key 使用字符串类型为：表名+id; 不直接以表名为redis key 提供一种更细粒度的控制，防止整个表的数据全部过期。

下一步就是具体的实现；因为存在多表，不能写死； 所以封装了一个函数：getDimInfo

```java
public static JSONObject getDimInfo(Connection connection, String tableName, String id) throws Exception
```

表名和id从调用者处传入；

3、具体实现。函数内：

- 获取jedis连接，查hbase之前先查Redis, 如果redis 中能查到：先重置过期时间，后归还连接，最后返回结果；
- 如果redis 中不能查到，拼接查询语句，查询Phoenix，在返回结果之前,将数据写入Redis，重置过期时间，归还连接；

4、往 hbase中写数据时，**如果是update的数据，则先删除Redis中的数据**，然后写入hbase

**使用这个优化之后 查询时间 缩短了10多倍。**

即使做了这个优化  还是用了map函数来补充维度字段

### 异步I/O优化

> **为什么要做这个优化**：默认情况下，调用map方法补充维度字段 （即使进行了旁路缓存还是用的是map），传入一个MapFunction，**但是在Flink的MapFunction中，单个并行只能用同步方式去交互: 将请求发送到外部存储，IO阻塞，等待请求返回，然后继续发送下一个请求**。这种同步交互的方式往往在网络等待上就耗费了大量时间。为了提高处理效率，可以增加MapFunction的并行度，但增加并行度就意味着更多的资源，并不是一种非常好的解决方式。
>
> Flink 在1.2中引入了Async I/O，**在异步模式下，将IO操作异步化，单个并行可以连续发送多个请求，哪个请求先返回就先处理，从而在连续的请求间不需要阻塞式等待，大大提高了流处理效率**。
>
> Async I/O 是阿里巴巴贡献给社区的一个呼声非常高的特性，解决与外部系统交互时网络延迟成为了系统瓶颈的问题。

异步 I/O访问数据库：对于单并行度而言，可减小等待时间，增大吞吐量

> （增大吞吐量最有效的是 增大并行度 但是会带来非常大的资源消耗）
>
> 实现异步I/O有客户端（查询的库可提供异步请求的客户端） 和 线程池两种方式进行异步I/O；
>
> 我们要查两个：hbase和redis，用客户端不方便，所以采用线程池的方式
>
> 采用**双重校验的方式初始化一个线程池**，把**维表的查询操作托管给单独的线程池完成**，这样不会因为某一个查询造成阻塞，单个并行可以连续发送多个请求，提高并发效率。

实现：

> 异步方法核心的类是 AsyncDataStream，这个类有两个方法一个是有序等待（orderedWait），一个是无序等待（unorderedWait）。
>
> 无序等待（unorderedWait）
>
> 后来的数据，如果异步查询速度快，可以超过先来的数据，这样性能会更好一些，但是会有乱序出现。
>
> 有序等待（orderedWait）
>
> 严格保留先来后到的顺序，所以后来的数据即使先完成也要等前面的数据。所以性能会差一些。

本项目 使用 unorderedWait ，AsyncDataStream调用unorderedWait需要 传入 数据流（来自kafka的事实表数据流）、**一个继承异步方法类 RichAsyncFunction的实例**、超时时间和超时时间单位 4个参数。

1、自定义一个线程池，用于异步查询

2、**继承异步方法类 RichAsyncFunction**，封装了一个**带泛型**的维度异步查询的函数类DimAsyncFunction（因为还是有**多个维表**的存在）

> RichAsyncFunction这个类要实现两个方法:
>
> open用于初始化异步连接池。
>
> asyncInvoke方法是核心方法，**里面的操作必须是异步的**，如果你查询的数据库有异步api也可以用线程的异步方法。如果没有异步方法，就要自己利用线程池等方式实现异步查询。

 

```java
public void asyncInvoke(T input, ResultFuture<T> resultFuture)
```

asyncInvoke 方法**内部开启线程提交任务**（异步）：1、根据 表名+id  查询维度数据（先从redis中查，查不到再从habse中查，因为配置了旁路缓存优化）2、补充维度信息（将维度字段加入到输入数据中）  3、将数据输出

```java
//获取查询的主键
  String id = getKey(input);
//查询维度信息
JSONObject dimInfo = DimUtil.getDimInfo(connection, tableName, id);
//补充维度信息
if (dimInfo != null) {
    join(input, dimInfo);
}
//将数据输出
resultFuture.complete(Collections.singletonList(input));
```

**因为有不同的维度表，需要补充多种维度字段**，且在函数内部无法通过泛型获取所需字段进行维度关联，所以为了使这个类更通用，自定义一个异步查询接口，接口中定义两个抽象方法：获取查询主键的方法  和  补充维度信息的方法； 然后让这个类实现这个接口，这样就可以从**调用者处传入 主键（表名+id）和 需要的维度字段**；

 

```java
public interface DimAsyncJoinFunction<T> {
    String getKey(T input);
    void join(T input, JSONObject dimInfo) throws ParseException;
}
```

3、在这个类中还会实现一个timeout超时时间方法，标识异步查询最多执行多久。

**使用异步I/O之后查询速度又有不少提升**

==================================================================

进行到这里Kafka中已经创建完成宽表、还有完备的日志数据；下面即可进行指标分析；

 

## 指标分析

### **1、计算PV，UV**

数据源：kafka主题：页面日志表dwd_page_log

**滚动窗口 + 窗口触发器清除窗口数据+ 自定义布隆过滤器实现计算uv的去重 随机key先分组再聚合的数据倾斜优化**

自定义布隆过滤器：一个位图+哈希函数，位图采用redis的位图

实现：读取kafka数据源，将每行数据转换为Json对象，并分配时间戳和Watermaker,设置乱序时间1s

**天级别的PV,UV**，需要按天keyby ，开一个一天的滚窗；同一天的数据进入同一个分区；极易发生数据倾斜；所以**按日期和随机数的拼接字符串为key进行分组keyby**；最后按windowEnd聚合；

一般 聚合只能先keyby    开窗聚合也推荐先keyby

![image-20220524194118801](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220524194118801.png)

map 成二元组 **像wordcount 一样**

**按日期和随机数的拼接字符串为key进行分组keyby**后，开一天的滚动窗口，自定义窗口触发器10秒触发一次窗口计算**并清空窗口数据**，即10秒更新一次结果；然后调用process方法传入一个proesswindowfunction进入窗口中的数据处理逻辑：

在open方法中新建自定义的布隆过滤器和建立redis连接；

在pocess中 设置位图的 key为 windowend的字符串，这样一天之后就会有一个新的位图；**并且可以用redis key 设置过期时间**。将每个窗口的 pv,uv 值以哈希表形式都存在redis中（redis key字符串”uv-count“, 哈希表 key ：windowend为key  **因为状态在redis中所以可以清空窗口的数据**）

因为窗口触发器设置了10秒计算一次，所以对窗口内的10秒数据用**迭代器**进行计算，来一条数据pv值+1，在位图中判断是否存在该userid，不存在uv+1，并把对应位置的位图置为1；更新pv,uv状态

 

最后根据windowend  **keyby** 将每个分区的数据汇总；

**清空窗口数据**将内存使用降到最低，10秒一次窗口计算，窗口也会保留10秒的数据；

> 自定义窗口触发器：
>
> flink 的ContinuousEventTimeTrigger.of(Time.hours(1)) 内部是 fire触发计算，而不是fire_and_purge; 所以他计算之后是会保留数据的，
>
> 仿照ContinuousEventTimeTrigger自定义一个窗口触发器，将fire改成fire_and_purge；
>

 

### **2、flink-CEP 用户恶意登录检测**

五秒内连续三次登录失败的用户

数据源：kafka主题：启动日志：start_log

读取kafka数据源，将每行数据转换为Json对象，并分配时间戳和Watermaker,设置乱序时间3s

- 定义一个循环匹配模式：partterns.begain(...).where......tmie(3).consecutive().within(Time.seconds(5));    consecutive()保证严格近邻模式
- 先以**用户id分组**，然后匹配模式，将匹配模式应用到数据流上，得到一个pattern stream
- 检出符合匹配条件的复杂事件（select方法），进行转换处理，得到报警信息
- ![image-20220524203618341](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220524203618341.png)

### **3、统计最近一小时的下单次数topN的商品，每10秒更新一次**

数据源：kafka主题，订单宽表：order_wide

读取kafka数据源，将每行数据转换为Json对象，并分配时间戳和Watermaker,设置乱序时间1s

keyBy() 按照商品ID分组、timeWindow()开启一个大小为1个小时、滑动间隔为10秒的滑动窗口
然后做聚合计算

```java
.aggregate(new ItemCountAgg(), new WindowItemCountResult());
```

使用aggregate **增量+ 全量**计算

增量：传入一个AggregateFunction 来一条数据做一次聚合，

全量：传入WindowFunction，只需要拿到前面聚合的最后结果；然后结合当前window信息 窗口信息 包装一下输出结果即可

> 增量聚合效率更高 来一个聚合一次  真正的流处理
>   但是全窗口函数能获得当前窗口的信息 时间相关信息 状态 等 全窗口函数更灵活
>   所以此处aggregate() 同时传入自定义的增量聚合函数 和 自定义全窗口函数 俩者配合做聚合计算
>   增量聚合提前聚合掉数据，减少state的存储压力
>   全窗口函数只需要拿到前面聚合的最后结果即可
>   然后结合当前window信息 窗口信息 包装一下输出结果即可

**Flink 的AggregateFunction是一个基于中间计算结果状态进行增量计算的函数。由于是迭代计算方式，所以，在窗口处理过程中，不用缓存整个窗口的数据，所以效率执行比较高**

完成aggregate后，收集同一窗口的所有商品count数据，就是要实现分窗口 TOPN  此处应用**状态编程思想**

首先keyby   以windowEnd 作为 key    按照窗口分组

调用process方法 然后传入自定义 KeyedProcessFunction 类

> 这个类是富函数 可以获取运行环境的上下文，并拥有一些生命周期方法，可以实现更复杂的功能，主要提供了定时器 timer 的功能。
>
> KeyedProcessFunction 类 中 每一个窗口定义一个 ListState列表状态 把当前窗口的数据全部存进来
>
> open : 初始化 ListState列表状态
>
> processElement：每来一条数据，存入ListState中，并**注册定时器** 触发时间为 WindowEnd() + 1 等待窗口数据到齐
>
> onTimer：定时器触发，当前已收集到窗口内的所有数据，从ListState 中拿出所有的数据按count值排序
>
> 排序后遍历列表取 前五热门的商品

![image-20220524162335693](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220524162335693.png)

### **4、每小时各省份累积下单金额 和 TOP3累积下单金额的省份**

Flink SQL实现

- 定义Table流环境

- 把数据源定义为动态表

  ![image-20220529153438228](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220529153438228.png)

  ![image-20220529154051215](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220529154051215.png)

- 通过SQL查询出结果表

- 把结果表转换为数据流

- 把数据流写入目标数据库

 

1、连接kafka使用DDL语句创建表作为数据源；在sql语句中提取时间戳生成WaterMark

2、按省分组 求 订单总金额 排序取topN，因为求的是每小时TOPN；所以还需要开滚动窗口（窗口开始时间和结束时间），开窗语句要放在分组字段里面

3、将动态表转换成流写入 MySql;(因为自定义了MySql两阶段提交的sink)

全局topN

![image-20220606222955779](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220606222955779.png)

**常规优化**

**1、开启MiniBatch 提升吞吐**

MiniBatch是微批处理，原理是缓存一定的数据后再触发处理，以减少对State的访问，从而提升吞吐并减少数据的输出量；

![image-20220625214237417](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220625214237417.png)

微批处理通过增加延迟换取高吞吐，如果有超低延迟的要求，不建议开启微批处理。通常对于聚合的场景，微批处理可以显著的提升系统性能，建议开启

**2、开启LocalGlobal   解决常见数据热点问题**

LocalGlobal优化将原先的Aggregate分成Local+Global两阶段聚合，即MapReduce模型中的Combine+Reduce处理模式。第一阶段在上游节点本地攒一批数据进行聚合（localAgg），并输出这次微批的增量值（Accumulator）。第二阶段再将收到的Accumulator合并（Merge），得到最终的结果（GlobalAgg）。LocalGlobal本质上能够靠LocalAgg的聚合筛除部分倾斜数据，从而降低GlobalAgg的热点，提升性能。

![image-20220625214740949](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220625214740949.png)

## 自定义 mysqlsinkfunction 解决kafka-flink-MySQL重复消费问题；

问题：我程序中Flink的CheckPoint语义设置了 Exactly Once，但是我的mysql中看到数据重复了？程序中设置了1min1次CheckPoint，但是20秒向mysql写一次数据，并commit（mysql  innodb支持事务，myasim引擎不支持事务）

>     答：Flink要求end to end的精确一次都必须实现TwoPhaseCommitSinkFunction。如果你的chk-100成功了，过了40秒，由于20秒commit一次，所以实际上已经写入了2批数据进入mysql，但是突然程序挂了，从chk100处恢复，这样的话，之前提交的2批数据就会重复写入，所以出现了重复消费。）--**项目中遇到了这个问题**

复习端到端一致性的时候觉得可能会有重复消费的问题；就自己做了一个测试；

定时向kafka发数据；保证已经做过一次ck（1min一次）；然后再插入几个数据，随机手动制造异常，让程序异常终止；观察mysql情况；

按道理说后来插入的几条数据不应该出现在MySQL中；但是....

[(2条消息) 解决Flink消费Kafka信息，结果存储在Mysql的重复消费问题_卢子墨的博客-CSDN博客](https://blog.csdn.net/lukabruce/article/details/100737292)

![image-20220528142505801](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220528142505801.png)

实现流程：

**1、**自定义 `MySqlTwoPhaseCommitSink`，首先要实现  `TwoPhaseCommitSinkFunction` ,需要传入三个参数

![img](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220528144104732.png)

\- SinkFunction 的输入类型。
– （存储处理事务所需的所有信息的事务）**就是需要传入一个事务的载体**
– 将在给定的所有调用之间共享的上下文

- 这里我的 IN 就是输入数据类型为 JSONObject

- **难点1**：TXN需要一个事务的载体，这里执行完入库操作后，通过数据库连接connect.commit 来提交这个连接所执行的操作；那么按理说这里传入一个connection.class 就可以了

  但事实上直接传入connetion.class是不可行的，两阶段提交的源码中 会被当作状态保存下来 ，需要序列化， **数据库连接不能被序列化，就会报错**

这里为解决这个问题，自定义一个静态内部类connetionState，这也是仿照了 FlinkKafkaProducer

 

```java
static class ConnectionState {
        private final transient Connection ;
        ConnectionState(Connection connection) {
            this.connection = connection;
        }
    }
```

类中添加一个属性：**finnal 、transient 类型的 Connection**；和一个构造方法；以这个类为参数传入

- CONTEXT 上下文这里没有用到，给了个void

**为防止频繁创建和关闭连接采用连接池的方式提高新能和稳定性；**

**2、然后实现了invoke方法和 四个两阶段提交协议流程的方法**

在invoke方法中  因为同样有多个表要入库，这里也是采取了SQL拼接的方式，执行数据库入库操作    这个方法在task初始化的时候调用

beginTransaction  开启事务，preCommit预提交事务、commit提交事务、abort 事务中断

 

```java
// 获取连接、设置手动提交事务
@Override
    protected ConnectionState beginTransaction() throws Exception {
        Connection connection = DruidConnectionPool.getConnection();
        connection.setAutoCommit(false);
        return new ConnectionState(connection);
    }
    // 啥也不做、invoke中的逻辑
    @Override
    protected void preCommit(ConnectionState transaction) throws Exception {
    }
    @Override
    protected void commit(ConnectionState transaction) {
        Connection connection = transaction.connection;
        try {
            connection.commit();
            connection.close();
        } catch (SQLException e) {
            throw new RuntimeException("提交事物异常");
        }
    }
    @Override
    protected void abort(ConnectionState transaction) {
        Connection connection = transaction.connection;
        try {
            connection.rollback();
            connection.close();
        } catch (SQLException e) {
            throw new RuntimeException("回滚事物异常");
        }
    }
```

**现在的逻辑是**

beginTransaction 方法：从连接池中获取一个连接，创建连接池是为了节省资源与稳定；设置手动提交事务

preCommit 预提交事务：不用做什么；就是invoke中的入库逻辑

commit  提交事务，归还连接

abort : 执行回滚逻辑

**运行一段时间后会报错**

**难点2**：现在的实现逻辑还是有问题的；

- 在beginTransaction中获取连接，这个连接得一直开着才行，**开始检查点 即 进入预提交阶段**；直到检查点完成 commit成功才能归还连接，可能会有连接的时间过长导致连接损坏的问题；

- 且上面的commit方法中只是调用了connect.commit() 提交事务，然后归还连接 ；我们知道程序异常恢复时，会重新提交没有提交的事务；

  但此时commit 方法内部连接已归还，无法再获取连接提交事务；

**代码改进**：

内部类connetionState改为外部类添加属性：一个list类型得集合；用于存放数据

- 在invok中将数据添加到list保存下来
- 在beginTransaction 方法中：不获取连接，返回一个空参的外部类构造实例（作为事务载体）；
- preCommit 预提交事务：同样不用做什么；
- commit方法中：   **获取连接**，设置手动提交；遍历list 拼接SQL 数据入库；提交事务，归还连接

**这样的话，因为前面已经将数据保存到list，且预提交就开始检查点了；最后commit 获取连接只是进行了数据入库操作，应该很快完成，从而这个连接不会持续很长时间而发生损坏问题；且异常恢复时还可以获取连接继续执行提交；**

**外部类：**

```java
public class MyContentTransaction {
    private List storeData=new ArrayList();
    private transient Connection connection;
    // 存储需要insert的事务数据
    private void store(String value){
        storeData.add(value);
    }
    // 提交事务
    private void commit() throws SQLException {
        connection = HikariUtis.getConnection(); // 获取一个MySQL连接
        connection.setAutoCommit(false);
        // 然后遍历 storeData中的数据，拼接成insert的PreparedStatement，最后执行connection.commit()提交事务。（代码就不写了，手敲累死了...）
    }
    // 回滚事务
    private void rollback() throws SQLException {
        connection.rollback();
    }
}
```

 

 

**TwoPhaseCommitSinkFunction 源码**：

**1、**TwoPhaseCommitSinkFunction 首先需要继承 RichSinkFunction，RichSinkFunction又实现SinkFunction接口

> Flink中所有的RichFunction都是普通function的加强版。RichFunction除了支持编写自定义的启动和停止逻辑外，还支持在方法内部获取RuntimeContext。对于RichSinkFunction也不例外

SinkFunction的代码并不是很复杂，只包含一个方法invoke(IN value, Context context)(另一个版本的invoke方法已经被废弃，这里不再介绍)。这个方法的第一个参数为数据流中到达sink算子的元素，第二个参数为context对象。

> 这个context对象包装了元素的附带信息，如下所示：
>
> - currentProcessingTime：返回当前的处理时间。
> - currentWatermark：返回当前watermark的时间戳。
> - timestamp：返回当前元素附带的timestamp（通过timestamp extractor提取或者是通过数据源指定）。如果没有指定为元素指定timestamp，返回null。

invoke是实现sink逻辑的关键。对于任何数据落地（从Flink中输出）的逻辑，我们只需要实现SinkFunction接口，将数据落地逻辑编写在invoke方法中。

**2、**其次 TwoPhaseCommitSinkFunction 实现CheckpointedFunction接口，该接口中有两个方法：initializeState 和 snapshotState

**3、**实现 CheckpointListener  有notifyCheckpointComplete方法和notifyCheckpointAborted 方法

**initializeState**在Flink程序刚启动的时候执行 ：

会先判断是否从上一个检查点恢复，是的话进入下面的逻辑：

- 获取存储了事务数据相关的ListState。
- 提交所有执行了preCommit的事务
- 终止所有尚未preCommit的事务。

最后会调用beginTransactionInternal()，开启一个新的事务，表示新的开始。

**snapshotState和notifyCheckpointComplete**是在Flink做checkpoint时执行

**snapshotState：**

- 先检查确保进行snapshot的时候必须存在事务
- 接着执行preCommit()方法，先进行一些事务前的准备。在未提交事务列表(pendingCommitTransactions)中记录该事务
- 接着执行beginTransactionI()，开启一个新事务，提供给下一次checkpoint使用；
- 最后清空ListState<State> state,  然后记录当前事务和待提交事务

**notifyCheckpointComplete：**里面就是事务commit的处理逻辑 : 获取预提交的事务列表，挨个提交，提交一个就从列表中删除。

**notifyCheckpointAborted ：**检查点失败的逻辑，abort 方法被调用

[Flink二阶段提交方式写入MySQL_淡定一生2333的博客-CSDN博客_flink两阶段提交mysql](https://blog.csdn.net/zc19921215/article/details/117934640)

[Flink 源码之两阶段提交 - 简书 (jianshu.com)](https://www.jianshu.com/p/4d8e3ec9b624)

[[Flink-1.10 源码笔记 两阶段提交 - 简书 (jianshu.com)](https://www.jianshu.com/p/1821208acd3e)](https://www.jianshu.com/p/4d8e3ec9b624)   ★★★

## 可视化展示

该模块的主要作用是对数据质量监控结果进行可视化展示。 检测结果可以采用 Superset 进行可视化展示，新建连接到MySQL数据库；添加dataset; 将所有数据表格都导入为 dataset；创建仪表盘；选择数据 创建图表保存到仪表盘，然后进行可视化展示；

## 项目中涉及的面试题

### **什么是CDC 和 flink CDC？**

CDC是Change Data Capture(变更数据获取)的简称。核心思想是，监测并捕获数据库的变动（包括数据或数据表的插入、更新以及删除等），将这些变更按发生的顺序完整记录下来，写入到消息中间件中以供其他服务进行订阅及消费。

**CDC种类**

1.基于查询的CDC

例如：Sqoop、Kafka 、JDBC source等产品。
特点：基于批处理，不能捕获到所有数据的变化、高延迟、需要查询数据库，会增加数据库压力

2.基于**binlog** 的CDC

例如：Maxwell、Canal、**Debezium**
特点：基于streaming模式、能捕捉所有数据的变化、低延迟、不会增加数据库压力。

**Flink-CDC**

Flink 社区开发了 flink-cdc-connectors 组件，这是一个可以直接从 MySQL(和PostgreSQL)等数据库直接读取全量数据和增量变更数据的 source 组件

flink cdc 原理：

Flink SQL CDC **内置了 Debezium 引擎**，利用其抽取日志获取变更的能力，将change log 转换为 Flink SQL 认识的 RowData 数据。

![image-20220524105809451](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220524105809451.png)

项目中用的是dataSream CDC（因为其可以监控**多库多表**）, 需要自定义反序列化器

![image-20220530203619436](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220530203619436.png)

- **flink CDC的优势可以直接采集数据进行实时处理；其他的组件比如cancel 需要将数据采集到Kafka，然后flink消费Kafka的数据进行处理；**
- **flink 可以依靠checkpoint 和 savepoint 实现断点续传**

flink  实时采集mysql的数据，需要mysql开启binlog，**且其格式为row**

**Debezium 报错：binlog probably contains events generated with statement or mixed based replication format 或 The MySQL server is not configured to use a FULL binlog_row_image**

当前的 Binlog 格式被设置为了 `STATEMENT` 或者 `MIXED`， 这两种都不被 Debezium 支持。为了使用 Flink CDC 功能，需要把 MySQL 的 `binlog-format` 设置为 `ROW`：

 

```
SET GLOBAL binlog_format = 'ROW';
SET GLOBAL binlog_row_image = 'FULL';
```

**MySQL中binlog的三种格式**

**1.Row格式**

此格式不记录sql语句上下文相关信息，保存哪条记录被修改。

优点： binlog中可以不记录执行的sql语句的上下文相关的信息，仅需要记录哪一条记录被修改成什么了。所以Row格式的日志内容会非常清楚的记录下每一行数据修改的细节。

缺点:所有的执行的语句当记录到日志中的时候，都将以每行记录的修改来记录，这样**可能会产生大量的日志内容**,比如一条update语句或者一条alter语句，修改多条记录，则binlog中每一条修改都会有记录，每条记录都发生改变，那么该表每一条记录都会记录到日志中，这样造成binlog日志量会很大。

**2.Statement格式**

    该格式下每一条会修改数据的sql都会记录在binlog中。

**优点：不需要记录每一行的变化，减少了binlog日志量，节约了IO，提高性能**。

> 它相比row模式能节约很多性能与日志量，具体节约的多少取决于应用的SQL情况。正常同一条记录修改或者插入row格式所产生的日志量还小于Statement产生的日志量，考虑到整表删除等一些大量数据操作，ROW格式会产生大量日志，所以总体来讲statement模式会稍微好一些。

缺点：由于记录的只是执行语句，为了这些语句能在slave上正确运行，因此还必须记录每条语句在执行的时候的一些相关信息，以保证所有语句能在slave得到和在master端执行时候相同的结果。

**3.Mixed格式**

    该格式是以上两种level的混合使用，**一般的语句修改使用statment格式保存binlog，当statement无法完成主从复制的操作时(设计一些函数时)，则采用Row格式保存binlog；**

**MySQL会根据执行的每一条具体的sql语句来区分对待记录的日志形式，也就是在Statement和Row之间选择一种**。新版本的MySQL中队Row模式也被做了优化，并不是所有的修改都会以Row模式来记录，像遇到表结构变更的时候就会以statement模式来记录。至于update或者delete等修改数据的语句，还是会记录所有行的变更。

### **为什么要将 维表 分流 到第三方存储（Hbase或者ES）**

> 离线数仓中 **一张维度表是通过主维表和相关维表做关联查询生成**的，与之对应的业务数表数据是通过每日一次全量同步导入到 HDFS 的，只须每日做一次全量数据的关联查询即可。
>
> 而实时数仓中，系统上线后我们采集的是所有表的变化数据，这样就会导致一旦主维表或相关维表中的某张表数据发生了变化，就需要和其它表的历史数据做关联。
>
> 历史数据只能来自MySQL业务数据库
>
> > 实时数仓中的数据是以流的形式存在的，如果不同流中数据进入程序的机器时间差异过大就会出现 join 不上的情况。如何保证导入的历史数据和变化数据可以关联上？势必要尽可能及时地执行历史数据导入命令且在 Flink 程序中设置足够的延迟。而前者难以保证，后者又会影响整个实时数仓的时效性。
>
> **对业务表做 join 的方式并不适合实时数仓**（不进行维表的合并）；
>
> 因此，在实时数仓中，我们**不再对业务数据库中的维度表进行合并**，仅对一些不需要的字段进行过滤，然后将维度数据写入 HBase 的维度表中，**业务数据库的维度表和 HBase 的维度表是一一对应的**。
>
> 写入维度数据使用 HBase 的 Phoenix 客户端提供的 upsert 语法，实现**幂等写入**。当维度数据发生变化时，程序会用变化后的新数据覆盖 Phoenix 维表中相同主键的旧数据。从而保证 Phoenix 表中保存的是一份**全量最新的维度数据**

前面的当作参考

**回答：**事实表的数据来一条处理一条；而维度数据是有历史数据的，**很难和事实表完成join关联**；所以需要以一个表格的形式存放起来；比如地区维度、用户维度数据需要长期存在，就是需要保存一份**全量最新的维度数据**。后期通过查询的方式关联维度

**为什么不对维表进行合并成一个大的维表（离线数仓中是这样的）？**

因为这样的话，当维度数据改变时还需要去改变这个 大 维表，就是这个维表需要 继续进行维护的，还不如全部 存到HBase ，保存全量最新数据，要用到的时候再查寻；

### **维度数据写入Hbase或者ES**

为什么不写入：redis、mysql

不写入redis：redis是基于内存的数据库，而用户维度表数据量巨大，不合适

不写入MySQL：并发压力大；因为MySQL中的表本来就和用户打交道，响应用户请求，增删改查，在本项目中后面还要用它存储分析得到的数据，再用它去查维度数据就不是很合适。

为什么写入Hbase：因为habse支持**海量数据存储**、且**写入和查询速度都比较快，性能强悍**

 

### **如果主流先来 而配置表还没来，那么就会造成丢数据的情况**

两个流连接之后，调用process()方法 传入一个BroadcastProcessFunction进行处理，

processBroadcastElement()方法 处理广播流的数据

processElement() 处理主流数据  处理主流的数据

在这两个方法**之前**一定会先执行的一个方法：open()方法，在这个方法里面先jdbc查询一次MySQL ，并保存到一个map中，之后处理主流数据**先查看map中是否存在相应的数据**；即可解决这个问题

**完全不能接受丢数据：接着查mysql，有对应数据再进行处理**

> 等待一点时间，继续处理；可能会丢

 

### 为什么**订单流表和订单明细流表采用 双流join实现，用的是inteval join**

这里选用intervalJoin，因为相比较窗口join，intervalJoin使用更简单，而且**避免了应匹配的数据处于不同窗口的问题**。

Flink中基于DataStream的join，只能实现在同一个窗口的两个数据流进行join，但是在实际中常常会存在数据乱序或者延时的情况，导致两个流的数据进度不一致，就会出现数据跨窗口的情况，那么数据就无法在同一个窗口内join。Flink基于KeyedStream提供的interval join机制，intervaljoin 连接两个keyedStream, 按照相同的key在一个相对数据时间的时间段内进行连接。

 

### 为什么使用redis 作为 旁路缓存的存储

> 一般两种：堆缓存或者独立缓存服务(redis，memcache)，
>
> 堆缓存，从性能角度看更好，毕竟访问数据路径更短，减少过程消耗。但是管理性差**，其他进程无法维护缓存中的数据**。
>
> 独立缓存服务（redis,memcache）本事性能也不错，不过会有创建连接、网络IO等消耗。但是考虑到数据如果会发生变化，那还是独立缓存服务管理性更强，而且如果数据量特别大，独立缓存更容易扩展。
>
> 因为咱们的维度数据都是可变数据，所以这里还是采用Redis管理缓存。

- redis是使用较为广泛的**非关系型 内存数据库**，**速度快**--最主要原因
- 丰富的特性：可用于消息队列、用于缓存、**用于缓存时可按key设置过期时间，过期后将会自动删除。**
- redis内部是一个key-value存储系统，支持string，list，set，sorted set（有序集合），hash等多种数据类型 ，**可以应对各种redis key的设计**
- 支持事务 ：redis对事务是部分支持的（这里不用说）

 

### 那你的redis key是如何设计的

redis key 使用表名+id的组合字符串，保证唯一的同时，不直接以表名为redis key 提供一种更细粒度的控制，防止整个表的数据全部过期。

 

### **如果先删除了 redis中的数据，但是 hbase 还没写入，此时另外一个进程查一份老数据，又写到redis,那么下一次查询就会查到旧的数据造成数据不一致的现象**

1、加锁/事务：redis是乐观锁，别的进程来了会释放这个锁

2、先写hbase再删除redis： redis 没删掉的时候有问题；

3、先删除 redis ,再写hbase ,再删一次redis; 同样会有挂掉的问题

4、**直接修改 redis为新数据，不做删除操作，再写hbase**

可以解决这个问题：

- 如果进程在没修改redis之前就挂掉了，那么此时重启没有问题，从之前的checkpoint恢复
- 如果进程在修改redis之后 ，没写入hbase之前挂掉，那么可以保证从redis中读到是最新数据，此后进程重启，重新消费 ，没有问题。

### **介绍下flink  CEP**

复杂事件处理（Complex Event Processing，CEP）是一种基于动态环境中事件流的分析技术，事件在这里通常是有意义的状态变化，通过分析事件间的时序关系和聚合关系制定检测规则，持续地从事件流中查询出符合要求的事件序列，最终分析得到更复杂的复合事件。

Flink CEP提供了Pattern API用于对输入流数据进行复杂事件规则定义，用来提取符合规则的事件序列。

模式大致分为三类：

**个体模式（Individual Patterns）**

组成复杂规则的每一个单独的模式定义，就是个体模式。

个体模式包括单例模式和循环模式。单例模式只接收一个事件，而循环模式可以接收多个事件。

（1）量词

可以在一个个体模式后追加量词，也就是指定**循环次数**。times(3)...

![image-20220530213804059](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220530213804059.png)

**组合模式**（Combining Patterns，也叫模式序列）

很多个体模式组合起来，就形成了整个的模式序列。模式序列必须以一个初始模式开始：val start = Pattern.begin(‘start’)

（1）严格近邻

所有事件按照严格的顺序出现，中间没有任何不匹配的事件，由.next()指定。例如对于模式“a next b”，事件序列“a,c,b1,b2”没有匹配。

（2）宽松近邻

允许中间出现不匹配的事件，由.followedBy()指定。例如对于模式“a followedBy b”，事件序列“a,c,b1,b2”匹配为{a,b1}。

（3）非确定性宽松近邻

进一步放宽条件，之前已经匹配过的事件也可以再次使用，由.followedByAny()指定。例如对于模式“a followedByAny b”，事件序列“a,c,b1,b2”匹配为{ab1}，{a,b2}。除了以上模式序列外，还可以定义“不希望出现某种近邻关系”：

.notNext()：不想让某个事件严格紧邻前一个事件发生。

.notFollowedBy()：不想让某个事件在两个事件之间发生。

**模式组**（Group of Pattern）

将一个模式序列作为条件嵌套在个体模式里，成为一组模式。

**CEP流程：**

**模式的检测**

指定要查找的模式序列后，就可以将其应用于输入流以检测潜在匹配。调用CEP.pattern()，给定输入流和模式，就能得到一个PatternStream。

**匹配事件的提取**

创建 PatternStream 之后，就可以应用 select 或者 flatselect 方法，从检测到 的事件序列中提取事件了

• select() 方法需要输入一个 select function 作为参数，每个成功匹配的事件序列都会调用它

• select() 以一个 Map<> 来接收匹配到的事件序列，其中 key  就是每个模式的名称，而 value 就是所有接收到的事件的 List 类型

> **超时事件的提取**
>
> • 当一个模式通过 within 关键字定义了检测窗口时间时，部分事件序列可能因为超过窗 口长度而被丢弃；为了能够处理这些超时的部分匹配，select 和 flatSelect API 调用 允许指定超时处理程序
>
> • 超时处理程序会接收到目前为止由模式匹配到的所有事件，由一个 OutputTag 定义 接收到的超时事件序列

### Flink SQL 用什么解析的

flink sql是用Calcite解析的。Calcite作为一个强大的SQL计算引擎，**在Flink内部的SQL引擎模块就是基于Calcite**。

Apache Calcite是一个动**态数据管理框架**，它具备很多典型数据库管理系统的功能，如SQL解析、SQL校验、SQL查询优化、SQL生成以及数据连接查询等，但是又省略了一些关键的功能，如Calcite并不存储相关的元数据和基本数据，不完全包含相关处理数据的算法等。

### **Calcite的功能**

1）SQL解析

Calcite的SQL解析是通过JavaCC实现的，使用JavaCC编写SQL语法描述文件，将SQL解析成未经校验的AST语法树。

2）SQL效验

校验分两部分：

- 无状态的校验：即验证SQL语句是否符合规范。
- 有状态的校验：即通过与元数据结合验证SQL中的Schema、Field、Function是否存在，输入输出类型是否匹配等。

输出RelNode，逻辑计划树；

3）SQL查询优化

对上个步骤的输出（RelNode，逻辑计划树）进行优化，得到优化后的物理执行计划。

4）SQL生成

将物理执行计划生成为在特定平台/引擎的可执行程序，如生成符合MySQL或Oracle等不同平台规则的SQL查询语句等。

5）数据连接与执行

通过各个执行平台执行查询，得到输出结果。

在Flink或者其他使用Calcite的大数据引擎中，一般到SQL查询优化即结束，由各个平台结合Calcite的SQL代码生成和平台实现的代码生成，将优化后的物理执行计划组合成可执行的代码，然后在内存中编译执行。

### flink sql 是怎么用 Calcite解析的

1）Sql 解析： 将sql语句通过java cc解析成AST（语法树），在calcite中用SqlNode表示AST；

2）Sql 校验： 结合数字字典（catalog）去验证sql语法；

3）生成逻辑计划： 将sqlNode表示的AST转换成LogicalPlan， 用relNode表示;

4）生成 优化后的逻辑计划： 先基于calcite rules 去优化logical Plan，然后基于flink定制的一些优化rules去优化logical Plan；

5）生成Flink PhysicalPlan： 这里也是基于flink里头的rules将optimized LogicalPlan转成Flink的物理执行计划；

6）执行execute操作，然后**编译**成可执行的 JobGraph 提交运行。

> 这里再提一下**SQL的优化**：
>
> **5、SQL查询优化器**
>
> SQL优化的发展，则可以分为两个阶段，即**RBO（基于规则）**，和**CBO（基于代价）**。
>
> 逻辑优化使用Calcite的Hep优化器（基于规则），物理优化阶段使用了Calcite的Hep规则优化器和Volcano优化器（基于代价）。
>
> 1） **RBO（基于规则的优化器）**会将原有表达式裁剪掉，遍历一系列规则（Rule），只要满足条件就转换，生成最终的执行计划。一些常见的规则包括分区裁剪（Partition Prune）、列裁剪、谓词下推（Predicate Pushdown）、投影下推（Projection Pushdown）、聚合下推、limit下推、sort下推、常量折叠（Constant Folding）、子查询内联转join等。
>
> 2） **CBO（基于代价的优化器）**会将原有表达式保留，基于统计信息和代价模型，尝试探索生成等价关系表达式，最终取代价最小的执行计划。CBO的实现有两种模型，Volcano模型，Cascades模型。这两种模型思想很是相似，不同点在于Cascades模型一边遍历SQL逻辑树，一边优化，从而进一步裁剪掉一些执行计划。

### flink SQL 开窗

![image-20220625222657901](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220625222657901.png)

### 为什么使用flink，flink比其他的流式处理框架有何优点

**1、同时支持高吞吐、低延迟、高性能**

**Flink是目前开源社区中唯一一套集高吞吐、低延迟、高性能三者于一身的分布式流式数据处理框架**。Apache Spark也只能兼顾高吞吐和高性能特点，主要是因为Spark Streaming流式计算中无法做到低延迟保障；而流式计算框架Apache Storm只能支持低延迟和高性能特性，但是无法满足高吞吐的要求。而满足高吞吐、低延迟、高性能这三个目标对分布式流式计算框架来说是非常重要的。

flink 以固定的缓存块为单位进行网络数据传输-----高吞吐

**2、支持事件时间（Event Tim）**

在流式计算领域中，窗口计算的地位举足轻重，但目前大多数框架窗口计算采用的都是系统时间（Process Time），也是事件传输到计算框架处理时，系统主机的当前时间。Flink能够支持基于事件时间（Event Time)语义进行窗口计算，也就是使用事件产生的时间，这种基于事件驱动的机制使得事件即使乱序到达，流系统也能够计算出精确的结果，保证了事件原本产生时的时序性。

**3、支持有状态计算**

Flink支持状态管理，所谓状态就是在流式计算过程中将算子的中间结果数据保存在内存或文件系统中，可以让后面的计算进行复用，从而无需每次都基于全部的原始数据来统计结果，这种方式极大地提升了系统的性能，并降低了数据计算过程的资源消耗。对于数据量大且运算逻辑非常复杂的流式计算场景，有状态计算发挥了非常重要的作用。

**4、支持高度灵活的窗口（Window）操作**

Flink将窗口划分为基于Time、Count、Session，用户还可以通过自定义定时器和触发器定制灵活的窗口出发机制来满足不同的需求。

**5、基于轻量级分布式快照（CheckPoint）实现的容错**

在flink执行过程中，会进行周期性的分布式快照Checkpoints操作，一旦发生故障，可以从上一次成功的CheckPoint，将执行过程中的状态信息进行持久化恢复，以确保数据在处理过程中的一致性（Exactly-Once）

**6、基于JVM实现独立的内存管理**

内存管理是所有计算框架需要重点考虑的部分，尤其对于计算量比较大的计算场景，数据在内存中该如何进行管理显得至关重要。针对内存管理，FLink实现了自身管理内存的机制，**尽可能减少JVM GC对系统的影响**。另外，FLink通过序列化将所有的数据对象转换成二进制在内存中存储，降低数据存储的大小的同时，能够更加有效地对内存空间进行利用，**因此Flink较其他分布式处理的框架会显得更加稳定，不会因为JVM GC等问题而影响整个应用的运行**

**7、Savepoints（保存点）**

FLink通过Save Points技术将任务执行的快照保存在存储介质上，相当于给任务按下了暂停键，之后可从Savepoints 处完全恢复运行，Save Points技术可以让用户更好地管理和运维实时流式应用，广泛用于有计划的备份以及重启，应用升级，版本迁移等场景。

回答标题+简单介绍即可；

 

### **Saprk和Flink的区别**

**设计理念&流处理方面**

Spark的技术理念是使用微批来模拟流的计算，基于Micro-batch，数据流以时间为单位被切分为一个个批次，通过分布式数据集RDD进行批量处理，是一种伪实时。

Flink是基于事件驱动的，是面向流的处理框架，Flink基于每个事件一行一行地流式处理，是真正的流式计算。另外它也可以基于流来模拟批进行计算实现批处理。

> **架构方面**
>
> Spark在运行时的主要角色包括：Master、Worker、Driver、Executor。
>
> Flink 在运行时主要包含：Jobmanager、Taskmanager和Slot。

**时间机制和窗口机制**

Spark Streaming 支持的时间机制有限，只支持处理时间。

Flink 支持了流处理程序在时间上的三个定义：处理时间、事件时间、注入时间。同时也支持 watermark机制来处理滞后数据。

Spark只支持基于时间的窗口操作，而Flink支持的窗口操作则非常灵活，不仅支持时间窗口，还支持计数窗口和会话窗口，开发者可以自由定义想要的窗口操作；

**吞吐量和延迟方面**

Spark是基于微批的，吞吐量很大，但是付出了延迟的代价，它的延迟是秒级;

Flink是基于事件的，消息逐条处理，而且他的容错机制很轻量级，所以他能在兼顾高吞吐量的同时又有很低的延迟，它的延迟能够达到毫秒级;

**容错机制**

Spark Streaming的容错机制是基于RDD的容错机制，会对RDD数据做Checkpoint，以及针对 driver 的故障恢复做了数据和 元数据的 checkpoint。

[【容错篇】Spark Streaming的还原药水——Checkpoint - 简书 (jianshu.com)](https://www.jianshu.com/p/00b591c5f623)

flink 是基于全局状态的 轻量分布式快照checkpoint；实现了每个算子的快照，及流动中的数据的快照；

### **为什么你觉得Flink比Spark Streaming好？**

**1、实时方面**

Flink是真正的实时计算，而Spark Streaming是微批处理，是一种伪实时；

**2、延迟方面**

Spark Streaming是秒级别的

Flink是亚秒级别的

**3、时间机制和窗口机制**

Spark Streaming 支持的时间机制有限，只支持处理时间。

Flink 支持了流处理程序在时间上的三个定义：处理时间、事件时间、注入时间。同时也支持 watermark机制来处理滞后数据。

Spark只支持基于时间的窗口操作，而Flink支持的窗口操作则非常灵活，不仅支持时间窗口，还支持计数窗口和会话窗口，开发者可以自由定义想要的窗口操作

**4、反压机制**

Flink 利用了其作为纯数据流的天然优势，在数据传输过程中相当于使用了分布式阻塞队列，队列容量为缓存池的大小，一个阻塞队列中，一个较慢的接受者会降低发送者的发送速率，因为一旦队列满了（有界队列）发送者会被阻塞，这种机制就提供过反压的功能。

Spark Streaming 为了实现反压这个功能，在原来的架构基础上构造了一个“速率控制器”，这个“速率控制器”会根据几个属性，如任务的结束时间、处理时长、处理消息的条数等计算一个速率；

**5、容错机制**

Spark Streaming的容错机制是基于RDD的容错机制，会对RDD数据做Checkpoint，以及针对 driver 的故障恢复做了数据和 元数据的 checkpoint。

flink 是基于全局状态的 **轻量**分布式快照checkpoint；实现了每个算子的快照，及流动中的数据的快照； flink可以增量检查点；

### 那么spark毫无优势？

- Spark中分布式RDD缓存是一个非常强大的功能，在这一点上比Flink好用很多。比如在实时计算过程中需要一些离线大数据与之关联，Spark相比占有比较大的优势。
- Saprk比Flink还有占优的地方就是Spark的executor死了之后不会导致整个job挂掉，而是会创建新的executor再重新执行失败的任务。而Flink的某个task manager死了会导致整个job就失败了，必须设置checkpoint来进行容错。
- Spark 在进行图计算、机器学习等方面也会有优势；
- spark做 批处理  比 fink 强

 

### flink on yarn

1）Client上传Flink的jar包和配置文件到HDFS集群上

2）Client向Yarn的ResourceManager提交任务和申请资源

3）ResourceManager分配Container资源并启动ApplicationMaster

4）ApplicationMaster加载Flink的jar包和配置文件构建环境，启动Flink-JobManager

5）ApplicationMaster向ResourceManager申请任务资源

6）（其他的）NodeManager加载Flink的jar包和配置文件构建环境并启动TaskManager

7）TaskManager启动后会向JobManager发送心跳，并等待JobManager向其分配任务

Flink On Yarn模式的两种方式：**Session模式**和**Per-Job模式**

**1、Session模式（适合小任务使用）**

需要先申请资源，启动JobManager和TaskManager

不需要每次提交任务再去申请资源，而是使用已经申请好的资源，从而提高执行效率

任务提交完  资源不会被释放，因此一直会占用资源

![image-20220530202719174](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220530202719174.png)

**2、Per-Job模式：（适合使用大任务，且资源充足）**

每次提交任务都需要去申请资源，申请资源需要时间，所有影响执行效率（但是在大数据面前都是小事）

每次执行完任务资源就会立刻被释放，不会占用资源

![image-20220530202828386](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220530202828386.png)

![image-20220606212643606](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220606212643606.png)

> 大表开启map join 会变慢：申请资源慢；每个map都会有一个大表的数据，网络I/O

 

# 恒生综合面试准备

## 1、金融大数据

![image-20220927222027530](https://typora-tiger.oss-cn-hangzhou.aliyuncs.com/img/image-20220927222027530.png)

**客户画像**

## 2、金融大数据特点

1、数据量大，数据来源多

2、安全性要求高；

3、数据质量要求高

4、价值高，合理运用大数据技术进行分析，可创造很大价值

## 3、金融知识匮乏咋办

1、第一我认为，不管什么数据，采用的核心技术应是一样的，比如数仓搭建流程，维度建模方法等；但这并不意味着可以完全脱离现实场景，数据含义；

2、所以第二如果我有幸能够加入贵公司，我会在入职前去多补充金融方面的知识，尽量满足企业的需要。

 

## 4、反问环节

1、主要业务，技术栈

2、团队、合作交流过程是啥样的，是每天有总结会议，还是说每周有周会啥的？

3、新人培养体系

4、如果有幸能加入贵公司，您觉得我还有些东西需要去学习，或者说您还有哪些建议可以给到我。

 

## 5、非科班

1、非科班并不是零基础

2、在这个过程中锻炼了自己的自主学习能力和解决问题的能力。

3、该学的东西我都学了，我觉得给我机会，我并不会比科班的差，但是和科班的相比可能某些方面确实还是不足，我愿意慢慢去沉淀，不断提升自己。

 

#  HR 面可能问的问题

## 为什么自学大数据

1、本科接触过编程（单片机 C 语言）、比较有兴趣，就有以后想从事程序员工作的打算

2、研究生来杭电也是原因之一（亲戚朋友有在杭州上班；计算机专业）

3、关于为什么是大数据 不是 Java，这个是 兴趣+前景；双十一滚动大屏深刻吸引到；大数据前景很好，现在可以说是一个大数据时代；大数据方面的志向是我在研一后马上就确立了，所以从研一我就开始了这方面的学习；

 

## 遇到困难怎么解决的

1、检查细节问题（代码敲错，配置出问题等），尽可能去分析问题的原因

2、某些情况下可以 参考已有的实现

3、上网找帖子，看有没有人遇到过类似的问题

4、根据自己的情况做出自己的判断，进行一些尝试（和别人的不一样）

 

## 优缺点

### 优点

- 细心（心思细腻、核对细节）

- 责任心与集体责任感（会把自己份类的事尽量做到最好；在高中运动会，1500和3000没人跑，我包了，并且每天锻炼最后拿了名次）

- 专一（喜欢一个NBA球星快十年了）
- 团队精神（在团队中我可以愉快的和大家共事，但不爱表现，所以不是最瞩目的，却是比较踏实的那一个）

### 缺点

我的短板在于重执行，缺乏大局观 和 深度思考；我认为要成为一个大数据开发工程师，只有执行力是不够的，还要深入思考拥有大局观；

对于这方面能力的欠缺，如果能够加入公司，我肯定会多注意培养这方面能力 虚心向老员工学习

 

## 个人规划

走技术路线：

技术小白 -> 熟悉业务、不断学习、深入理解 -> 独立设计分析的能力 -> 独当一面 -> 项目的管理者

 

 

 

# 面试历程

## 兴业数金

### 8.10一面

1、行式存储和列式存储的区别

2、atlas元数据管理的节点信息

3、数仓分层与维度建模以及三种模型

4、hive分析函数（窗口函数） 计算、排序、取值（LAG 前多少行数据，LEAD后多少行数据）三种

### 9.2二面（HR面）

1、个人规划

2、课外活动

3、哪个项目对自己影响最大

### 9.2晚上内审邮件

 

## 电科28所

### 8.17一面凉经

1、项目中Kafka是怎么使用的

2、MySQL主从复制  以及配置过程中遇到过啥问题（这个没答好） **太急了、语速过快**

3、加班和出差（**不要太啰嗦，在没offer的情况下直接说接受**）！！！！

## 广立微

### 8.22一面

1、hive内外部表区别

2、数仓维度建模

3、介绍atlas元数据管理

4、hive 分析函数

**存在的主要问题还是太紧张、语速过快；语速一定不能过快**

### 8.30二面

1、ppt讲解

2、kerbros用户认证

3、hdfs哪些组件；高可用有没有配置，zkfc, JN

4、zk 的选举机制

5、spark和flink的区别

6、linux 常用命令 ；查看内存top、端口号 netstat、

    查看**cpu基本信息** cat/proc/cpuinfo; **top查看cpu使用率**；ps-aux 显示所有进程

7、hdfs 为什么要配置副本

8、列式存储的优势

9、排序算法；堆排序是怎么实现的

10、left join 、inner join 区别；**inner join 场景举例**

## 江苏苏宁银行

### 9.2一面

1、kafka组成架构

2、kafak的ACK机制

3、**hbase定义，解决的是什么问题**（这个答得很不好）

### 9.4 收到通过邮件

 

## 顺丰

### 9.5 一面

1、flink cdc；为什么要用flink cdc；flink SQL还是Datastream API

2、flink 写到MySQL，重复消费问题，为什么不直接主键覆盖？探讨了一波

3、flink  CK 和 Savepiont 区别

4、垃圾回收机制（分代垃圾回收机制）漏了点没答完全（年龄）

5、离线数仓的分层

### 9.15二面

1、sqoop数据倾斜，怎么解决的

2、后面hive计算时候有没有遇到数据倾斜

3、spark RDD  cache缓存

4、spark 和 MR的区别

5、MySQL 存储引擎，以及使用B+树的优势

 

##  荣耀

### 9.5一面 36min

1、离线数仓增量更新，怎么判断是增量（日期字段; 如订单表有个创建时间字段，根据这个字段即可进行判断）

2、离线数仓的分层

3、**flink 一条数据迟到关联不上，怎么办**

> - 1、直接丢弃
>
> - 2、allowtelateness（设置允许迟到时间）；将之间计算的窗口状态数据保留，迟到数据到达后更新结果
>
> - 3、侧输出流输出，保存到另外一条流，后续我们可以根据业务逻辑的要求，对迟到的数据流进行处理。

4、flink  CK 、Savepiont

5、mysql 三种执行引擎哪三种（innodb和myisam和**MEMORY**）

6、innodb和myisam的区别

7、kafka 节点挂了会数据丢失吗？(不会)

8、ledaer节点挂了数据就会丢失？（ISR列表个数>=2）

9、hive中 select * from A limit 10，会不会走mapreduce(不会，**fetch抓取**)

10、count(*) 呢？ 会走MR（还有sum，group by ）；几个map，几个reduce；默认一个reduce（也会根据数据量而定）；map数量根据数据量大小而定

11、flink的yarn提交模式

12、flink SQL 流批一体

### 9.15 二面

综合面

 

## 烽火星空

### 9.8一面 28min

1、基本数据类型；long多少个字节；一个字节多少位

2、队列（queue、双端队列、优先级队列）

3、queue应用场景

4、Arraylist 应用场景

5、hashmap 底层原理

6、hdfs 组成部分，各组件的作用

7、Yarn

8、hive\spark数据倾斜

**9、hive热点key，负载均衡；两阶段聚合**

**10、两阶段聚合咋实现的（随机数前缀）**

11、linux常用命令 查看所有进程 top

12、**查看后缀为txt的文件**

> find / -name '*.txt'   #在所示目录中查找后缀名为.txt的文件

13、**maven  打包命令package和install的区别**

> **Maven install 安装指令，其做了两件事情：**
>
> 1. 将项目进行打包（jar/war），将打包的最后结果放到项目下的 target 目录下
> 2. 同时将上述打包结果放到maven本地仓库的相应目录中，供其他项目或模块引用
>
> **Maven package 打包指令，其就做了一件事：**
>
> 1. 将项目进行打包（jar/war），将打包结果放到项目下的 target 目录下 （也要先clean）

14、创建线程的几种方式（四种）

15、callable和runable的区别

16、为什么要使用线程池

17、Excutor能创建哪几种线程池（三种）

18、构造方法创建线程池（七个参数）

19、核心线程数已满会怎样（队列未满加入队列；队列已满且最大线程未满，创建新线程；队列已满且最大线程数已满，饱和策略）

### 9.9 二面 20min

1、介绍数仓项目

2、flume->kafka->flume; kafka的作用

3、十亿个数，判断某几个数是否在其中

> 位图法：
>
> 十亿个数如果是INT, 开一个-2^31~2^31-1（20多亿）的数组，每位一个bit，这样的话内存使可接受的（256MB），数据直接作为下标
>
> 如果数很大，做一个哈希运算+位图（其实就是一个布隆过滤器）。位图的大小就是10亿个bit

4、有没有实际用过位图

5、hive 的join

6、flume架构

 

## 同程旅行

### 9.19一面

1、hadoop的各个服务以及作用！！！

2、HDFS读写流程

3、上传的时候，选取三个节点；怎么选取(机架感知？)

4、datanode下线的时候，恢复的时候会做哪些事

5、namenode启动的时候会做哪些事

> 1）首先启动9870端口
> 2）启动完端口之后开始加载镜像文件和编辑日志
> 3）紧接着创建RPC服务
> 4）然后开始对NameNode的资源进行检测
>
> - 检测当前磁盘空间是否能够启动NameNode
> - 要检查镜像文件和编辑日志的路径上能存储多少内容，默认大小是100M，如果当前磁盘空间小于100M，就要进行警告
>
> 5）对DataNode的心跳进行校验
>
> - 心跳检测时如果DateNode超过10分钟30秒没有被检测到，就认为DateNode宕机
>
> 6）判断是否进入安全模式
>
> - 默认block块加载到99.9%之后离开安全模式
>

6、讲一下你了解的几种锁

7、线程池的构造参数

8、A,B,C三类任务，提交到线程池去执行，怎么实现A优先级>B>C（工作队列有个优先级队列）

9、linux内存达到100%，怎么办？

10、hive转换为MR的流程

11、datanode 数据块怎么映射的

 

## 汇量科技

### 9.23一面

### 9.26二面

1、为什么要分订单表和订单详情表

相对来说，订单表相当于主表，把订单的主信息存在这，而订单明细表相当于子表，把订单中具体的产品放在这。他们之间通过订单号相联系着。主表字段少，对应新增和变化同步策略，查询性能高，维护性能也高；子表字段较多内容详细，对应增量更新策略；如修改订单信息对少量的主表做改变，而详情表只要增量

### 9.30三面

业务场景题

 

## 华为

### 9.29一二面