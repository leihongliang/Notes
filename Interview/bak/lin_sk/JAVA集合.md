# 集合

### ArrayList和数组的区别

- 可变长-不可变长
- ArrayList可以指定泛型
- ArrayList提供一系列方法进行操作
- ArrayList只能存对象，无法存基本数据类型
- ArrayList创建时不需要指定长度

### ArrayList 与 LinkedList 区别

- 是都线程不安全的
- 底层结构：ArrayList实际是维护了一个数组，LinkedList是维护一个双向链表
- 插入与删除：根据插入的位置性能也不同，但整体上LinkedList在插入和删除上效率会更高
- 随机访问：ArrayList支持快速随机访问，LinkedList不支持
- 内存占用：ArrayList浪费空间体现在尾部会留有一些空余空间，而LinkedList体现在节点占用的内存会更高

### ArrayList扩容机制

当使用无参构造创建ArrayList时，不会对数组赋值，只有当添加第一个元素，初始容量为10，之后当元素添加导致数组容量不够时会按1.5倍进行扩容

### ArrayList的Fail-Fast机制？

集合具有快速失败机制，即当一个线程读取集合时其他线程进行了修改，会触发快速失败机制，抛出对应的异常。

底层实现：集合内部维护了一个volatile变量modCount用于记录修改次数，在创建迭代器时会添加一个expectedModCount变量，当迭代时发现expectedModCount与modCount不相等了，则说明其他线程做了修改，抛出异常

### Comparable 和 Comparator 的区别

两个都是用于比较的接口。

- 对象实现Comparable并重写compareTo方法，就能实现自定义排序，将比较方法写在对象内部
- 对象实现Comparator并重写compare方法，可以作为一个比较器，传入集合的排序方法中实现自定义排序

###  比较 HashSet、LinkedHashSet 和 TreeSet 三者的异同

- HashSet：底层哈希表，无序且唯一
- LinkedHashSet：底层链表+哈希表，有序，支持先进先出
- TreeSet：底层红黑树，有序，可以自定义排序规则

### 什么是WeakHashMap

使用弱引用来管理元素，在垃圾回收时弱引用不会被看作有效引用，因此其中的元素可能会在垃圾回收时被清除，适用于缓存场景。

### Queue和Dqueue的区别

单端队列—双端队列

Dqueue提供pop和push方法，可以用来当栈用

### ArrayDeque和LinkedList的区别

都实现了Deque，可以作为双端队列使用

ArrayDeque基于可变长数组和双指针来实现

LinkedList基于链表实现

### 什么是 BlockingQueue

阻塞队列，常用于生产者-消费者模型，当没有元素时会一直堵塞

### HashMap和HashTable的区别

- HashMap线程不安全，HashTable线程安全
- HashMap效率高一些
- HashMap可以存null值，HashTable不允许null值
- HashMap初始大小16，之后按2n扩容；HashTable初始大小11，之后按2n+1扩容
- HashMap创建时指定大小会自动扩到2的幂次方，HashTable没有这个机制
- HashMap有树化机制，HashTable没有

### HashMap的底层实现

首先hashMap底层维护一个链表数组；对于一个元素，会计算调用hashcode方法，再经过扰动函数（减小hash碰撞），得到hash值，再通过（n-1）^hash得到索引值。然后会遍历链表与判断元素是否重复，如果重复就覆盖，如果不重复就添加到队尾。单链表长度高于阈值8时，此时如果数组长度大于等于64，会将链表转换为红黑树，否则先进行数组扩容。

### HashMap的长度 为什么是2的幂次方

HashMap中计算出hash值还要取余来求出数组的索引位置，底层采用（n-1）^hash的方式来计算，这种方式求余比用%效率高，不过这种方式的前提是除数是2的幂次方

### ConcurrentHashMap

线程安全的HashMap，适用于并发场景

jdk1.7以前：底层将桶数组分割成多端，使用分段锁来保证并发场景下的线程安全，同时不同段不会互相影响，增加了并发量。最多16段，因此并发量最多16个线程

jdk1.8以后：底层机构与HashMap类似，不过使用优化的同步锁以及CAS操作来保证线程安全，就像优化过且线程安全的HashMap。对链表和红黑树的首节点加锁，因此并发量为node数组的长度