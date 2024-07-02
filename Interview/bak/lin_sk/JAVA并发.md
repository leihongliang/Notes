# 并发编程

## 线程

### 从 JVM 角度说进程和线程之间的关系

线程是进程划分出的更小程序执行单位，最大的区别在于进程是互相独立的，拥有自己的资源空间；但线程之间会互相影响，线程拥有自己程序计数器、虚拟机栈、本地方法栈，而堆和方法去是共享的。

### 何如理解线程安全和不安全

线程安全是指在多线程场景下，不同线程访问同一数据能否保证其正确和一致性的描述

### 如何实现线程安全

- 互斥同步：synchronized和ReentrantLock
- 非阻塞同步：CAS，原子操作类
- 无同步：栈封闭，例如方法中的局部变量；线程本地存储，将数据的可见范围限制在一个线程内部，例如Thread Local

### 线程的生命周期和状态

- NEW：初始状态，线程创建完但没有执行start()方法
- RUNALBE：正在运行或等待时间片运行
- BLOCKING：阻塞状态，获取锁失败而发生阻塞
- WAITING：等待状态，等待直到其他线程进行通知
- TIME_WAITING：超时等待状态，在设置的时间后自动唤醒
- TERMINATED：结束状态，线程运行完或异常退出

### java中线程有哪几种实现方法

- 继承Thread类重写run方法
- 实现Runable接口后传入Thread构造器
- 实现Callable接口c换入Thread构造器

启动方式都是调用Thread对象实例的start方法

### Runable和Callable区别

- Runable没有返回值，Callable有返回值
- Runable不能抛出异常，Callable可以抛出异常

### 线程有哪些协作方法

- 通过调用其他线程的join()方法，将自己挂起等待目标线程执行完成
- 锁的wait()、notify()、notifyAll()来控制线程的等待与唤醒
- Condition对象的await()、signal()、signalAll()来控制线程的等待与唤醒

### 中断线程的几种方式

- 调用interrupt方法，可以中断处于阻塞、无限等待、期限等待状态中的线程，抛出异常从而中断线程
- 调用interruptd可以判断线程是否被中断，从而进行中断逻辑处理
- 调用线程池的shutdown方法，等待所有线程执行完后关闭线程池；调用shutdownNow方法，相当于调用所有线程的interrupt方法

### 什么是上下文切换

线程的运行条件和状态称为上下文，当CPU在线程中切换时，就要保存当前线程的上下文，然后加载下一个线程的上下文，这就是线程的上下文切换

### 可以直接调用Thread的run方法来启动线程吗

不行，调用run只是普通的调用方法，不会开启线程

## 锁

### 如何预防死锁

- 破坏持有并等待条件：一次申请所有资源
- 破坏不可剥夺条件：当无法声情到自己，将自己占有的资源释放
- 破坏环路等待条件：按序申请资源，反序释放资源

### sleep() 方法和 wait() 方法对比

- sleep不会释放锁，wait会释放锁
- sleep一般用于运行暂停运行，wait一般用于线程之间通信
- sleep结束后程序自行恢复，而wait需要其他线程通知才会恢复
- sleep时Thread类的静态方法，而wait是线程对象内置的方法（因为wait需要释放线程占用的对象锁）

### 公平锁和非公平锁的区别

- 公平锁：获取锁时按照申请顺序来，先申请的先获得锁，性能较差
- 非公平锁：获取锁时随机或者按优先级来，性能较好，但有可能出现有的线程永远拿不到锁的情况

### 什么是可重入锁

也称递归锁，指一个线程获取锁后，在内部可以再次获取这个锁，不会发生死锁

### 乐观锁和悲观锁

- 悲观锁：认为访问资源时总是会有其他线程进行修改，会将资源进行加锁，适用于写操作较多的场景，例如synchronized
- 乐观锁：认为访问资源时不会出现问题，在执行结束前进行验证，如果验证通过则修改成功否则失败重试，适用于写操作较少的场景，例如CAS

### 如何实现乐观锁

- 版本号：在修改时会比对版本号是否一致，不一致则失败
- CAS：比较与交换，在修改值判断要更新的值是否等于预期值

### CAS有哪些问题

- ABA问题：当一个线程进行CAS操作时，其他线程进行了一些修改，最后修改过的结果仍是原来的值，此时线程比较预期值则会认为没有其他线程进行了修改
- 失败重试开销大：当多线程并发时，可能会导致线程不断地失败从而导致性能开销较大
- 只能保证一个共享变量的原子操作，

###  Java 内存区域和 JMM 有何区别？

JAVAn内存区域于JVM运行时区域划分有关，决定了内存区域如何划分，例如推中主要存放对象

JMM内存模型于并发编程，它只当了在并发编程环境下java代码转化为CPU指令应该遵守的规范和原则，简化并发编程，提高可移植性

### 什么是happens-before原则

如果一个操作happens-before于另一个操作，那么第一个操作的执行结果对第二个操作是可见的

### happens-before 常见规则有哪些

- 程序顺序原则：书写在前面的代码happens-before书写在后面的代码
- volatile变量原则：volatile修饰的变量写操作happens-before读操作
- 传递原则：A happens-before B，B happens-before C，那么A happens-before C
- 解锁原则：解锁happens-before加锁
- 线程启动规则：start() happens-before 线程内操作

## 并发关键字

### volatile关键字

- 可见性：将变量声明为volatile，在java中表示这个变量是共享且不稳定的

- 禁止指令重排：volatile可以禁止JVM指令重排，在读写变量时会插入特定的内存屏障来实现
- 仅保证单次读写操作的原子性

###  synchronized 是什么？有什么用？

同步锁，被它修饰的方法和代码块在同一时刻只能有一个线程执行

- 修饰实例方法：锁资源为当前对象
- 修饰静态方法：锁对象为当前类对象
- 修饰代码块：括号内指定

构造方法无法被修饰，因为构造方法本身就是线程安全的

### synchronized底层原理

每个对象都会关联一个monitor监视器对象，monitor监视器对象在同一时间只能被一个线程所获取，内部有一个计数器，当计数器为0时表示锁可以被获取；线程获取锁或者重入锁时都会使计数器+1，释放锁时就减1，当减到0就表示这个锁被释放了可以被其他线程获取

### synchronized性能较差有什么优化方法

由于monitor对象实现依赖于操作系统的互斥量，每次竞争锁都要切换到内核态，开销较大。在jdk1.6引入了许多针对synchronized的优化：

- 锁粗化：减少不必要的加锁释放锁，将多个连续的锁拓展为一个大范围的锁
- 锁消除：编译器进行逃逸分析，消除掉一些不必要的锁
- 偏向锁：适用于单线程即没有锁竞争的场景，减少不必要的CAS操作
- 轻量级锁：适用于锁竞争不激烈的场景，使用CAS完成锁的获取和释放
- 适应性自旋：当CAS获取轻量级锁失败时，会进行一定的自旋重试，到达一定失败次数后才升级为重量级锁

### synchronized 和 volatile 有什么区别？

- volatile修饰变量，保证可见性，不保证原子性
- synchronized修饰方法、代码块，保证可见性和原子性

### Synchronized在使用时有何注意事项

- 范围不要太大，影响性能
- 锁对象不能为空
- 避免死锁
- 优先选择并发集合来应对多线程
- 抛出异常会自动释放锁

###  synchronized 和 ReentrantLock 有什么区别

 synchronized依赖于JVM，许多优化都是在JVM层面进行的

 ReentrantLock实现于API层面

 ReentrantLock具有许多高级功能：

- 等待可中断：提供一个方法，可以在等待获取锁时终端等待，去做别的事情
- 可实现公平锁：默认非公平锁，可以支持非公平锁
- 可以绑定多个通知条件（Condition）

### final修饰的变量都是编译器常量吗

不是，例如生成随机数

### 如何拓展一个final修饰的类

装饰器模式

### final修饰的方法可以重载吗

可以（不能重写）

### 基本类型的final域重排序规则

- 写final域时会禁止将写操作重排序到构造函数之外，通过在构造函数return前插入一个storestore内存屏障实现
- 读final域时会禁止将读操作重排序到读对象引用之前，通过在读操作前插入一个loadload内存屏障实现

具体插不插内存屏障得看处理器会不会重排序

## JUC锁

### AtomicInteger底层实现

volatile+CAS

### 原子类的理解

原子类可以分为四类

- 基本类型原子类：用于原子更新基本类型，包括整型、长整型、布尔类型
- 数组类型原子类：用于原子更新数组类型，包括整型数组、长整型数组、引用类型数组
- 引用类型原子类：用于原子更新引用类型，包括引用类型原子类、带有版本号的引用类型原子类、带标记的引用类型原子类
- 字段类型原子类：用于原子更新类中的某个属性，包括用于更新整型字段、长整型字段、引用类型字段

### Thread.sleep()和Object.wait()的区别

- sleep不释放锁资源；wait释放锁资源
- sleep必须设置时间，到时自动唤醒；wait可以不设置时间，由其他线程通知唤醒
- sleep可以在任何地方调用；wait只能在同步块中使用

### Object.wait()和Condition.await()的区别

效果差不多，不过await底层调用LockSupport.park()来阻塞线程的

### Thread.sleep()和LockSupport.park()的区别

- sleep到时间自己唤醒，park需要别人unpark
- sleep抛出中断异常需要进行处理，park不抛异常
- sleep本身就是一个native方法，park底层调用UnSafe的native方法

### Object.wait()和LockSupport.park()的区别

- wait只能在同步代码块中；park可以在任何地方
- wait要抛出中断异常；park不抛异常
- wait后需要notify唤醒，但不一定执行后面的代码；park后需要unpark唤醒，一定会执行后面的代码
- 若wait之前执行了notify会发生堵塞；若park之前执行了unpark，则不会发生阻塞

### 什么是AQS以及核心思想

AQS是一个用来构建锁和同步器的框架

其核心思想是，当线程访问共享资源时，如果资源是空闲的，则将线程设为有效工作线程；如果资源已经被占用，则将线程阻塞，在资源释放后再唤醒并分配锁

底层实现使用了CHL，一个虚拟的双向队列，每个请求资源的线程都封装为一个节点

### AQS有哪些核心方法

- `isHeldExclusively()`：该线程是否正在独占资源。只有用到condition才需要去实现它
- `tryAcquire(int)`：独占方式。尝试获取资源，成功则返回true，失败则返回false。
- `tryRelease(int)`：独占方式。尝试释放资源，成功则返回true，失败则返回false。
- `tryAcquireShared(int)`：共享方式。尝试获取资源。负数表示失败；0表示成功，但没有剩余可用资源；正数表示成功，且有剩余资源。
- `tryReleaseShared(int)`：共享方式。尝试释放资源，成功则返回true，失败则返回false。

### AOS有哪些资源获取方式

- 独占：同一时间只能一个线程进行访问
- 共享：同一时间允许多个线程进行访问

### ReentrantLock如何实现AQS

ReentrantLock有三个内部类：

- sync：继承自AQS
- NonfairSync：实现非公平锁
- FairSync：实现公平锁

### ReentrantReadWriteLock底层读写状态如何设计的

高位16为是读锁，地位16位是写锁

因此读写和写锁的最大数量都是2的16次方-1

## JUC集合

### ConcurrentHashMap实现的原理是什么

在jdk1.7及之前，将hash表进行分段，各个分段都通过继承ReentrantLock来进行加锁，因此单访问数据时，只会对所在的分段进行加锁，从而支持并发访问。分段最大16个，因此最多支持16个线程同时访问

在jdk1.8及之后，采用数组+链表+红黑树结构，采用CAS+synchronized实现线程安全，且synchronized只作用在链表的头节点上，锁的粒度更小，从而支持并发

### CopyOnWriteArrayList的实现原理

对数组写操作时，会创建一个新的数组对象，然后复制元素后进行修改，修改完成后再将引用指向新的数组完成修改。这个过程中读操作不会堵塞，而写操作会堵塞。因此适用于读操作比较多的场景。

### 弱一致性的迭代器原理是怎么样的

在迭代时维护一个数组的引用作为快照，这个引用在迭代时不会变更，由于修改会产生新的引用，所以引用的数组内数据也不会发生修改。因此迭代时其他线程进行修改数组不会产生影响，但如果在迭代时线程自己修改数组还是会抛异常。

### CopyOnWriteArrayList为什么并发安全且性能比Vector好

Vector对增删改查都加了互斥锁导致性能低，而CopyOnWriteArrayList读操作不会加锁

### CopyOnWriteArrayList有何缺陷，说说其应用场景

- 写操作要复制数组开销较大
- 无法保证数据的及时一致性

适合于读多写少的场景

### ConcurrentLinkedQueue底层原理

是一个线程安全的队列，底层维护一个链表

### 说说ConcurrentLinkedQueue的HOPS(延迟更新的策略)的设计?

ConcurrentLinkedQueue内部维护头节点和尾节点，不过它们是延迟更新，也就是在入队时不会即时的更新头节点和尾节点，而是在一定的时机进行更新：

- 对于尾节点：当尾节点的next不为null时进行，会执行定位尾节点的操作，找到真正的尾节点后通过CAS操作进行入队和更新尾节点；当尾节点的next为null时入队不会更新尾节点
- 对于头节点：当头节点的item域为null时，会执行定位头节点的操作，找到真正的头节点后通过CAS操作删除和更新头节点；当头节点的item不会null时，出队不会更新头节点

这样设计使得更新头尾节点是间隔性的，从而减少了CAS操作次数

### 什么是BlockingDeque? 适合用在什么样的场景

阻塞队列，用于一个线程生产（put），一个线程消费（take）

当阻塞队列空间被占满，则生产者会阻塞；当阻塞队列为空，则消费者会阻塞

BlockingQueue是一个接口，常见的实现类有ArrayBlockingQueue、LinkedBlockingQueue、DelayQueue,、SynchronousQueue

### 什么是BlockingDeque? 适合用在什么样的场景

双端阻塞队列，两端既可以生产也可以消费

### BlockingDeque 与BlockingQueue有何关系，请对比下它们的方法

BlockingDeque接口继承自BlockingQueue接口，因此具有BlockingQueue的所有功能，而BlockingQueue提供了两端添加、生成或删除、消费元素的方法（putFirst、putLast等等）

### FutureTask用来解决什么问题的? 为什么会出现

常用于封装Runable接口和Rallable接口，可以视作一个线程任务，既可以作为Runable类放入Thread构造器中，也能作为Callable获取返回结果，提供方法查看线程的执行结果或者取消线程等等。线程安全由CAS实现

## 线程池

### ThreadPoolExecutor的常见参数

重要的：

- corePoolSize：在任务未达到队列最大容量时的同时运行的线程最大数量

- maximumPoolSize：在任务到达队列最大容量时同时运行的线程最大数量
- workQueue：当核心线程全部被占用时。任务存放的队列

常见的：

- keepAliveTime：当线程数量大于核心时，如果此时线程空闲，不会立即销毁，而是等待一段时间后销毁
- unit：时间单位
- threadFactory：线程gongchang
- handler：饱和策略

### 线程池创建的两个方式

- 通过ThreadPoolExecutor来创建（推荐）
- 通过Executor框架的工具类Executor来创建

### ThreadPoolExecutor可以创建哪是哪三种线程池

- newFixedThreadPool：固定线程数量的线程池，工作队列无界，永远不会到饱和
- newSingleThreadExecutor：只有一个线程的线程池，工作队列无界，永远不会到饱和
- newCachedThreadPool：线程数量不限制，但线程空闲一定时间后会释放线程资源
- newScheduledThreadPool：可以执行延时任务和定时任务
- newSingleThreadScheduledExecutor：只有一个线程的延时任务线程池

### ScheduledThreadPoolExecutor有哪两个关闭策略? 区别是什么

- shutdown：在线程池关闭后取消并清除由于关闭策略不应该运行的任务，根据run-after-shutdown来判断
- shutdownNow：立即关闭

### 简要说下线程池的任务执行机制

1. 线程池中通过Worker类实现工作线程，在ReentrantLock的保证下，将Worker插入set集合，然后启动其中的线、线程
2. 通过getTask方法获取任务并执行，如果没有任务就阻塞并挂起不会占用CPU资源

### 线程池的饱和策略有哪些

- **`ThreadPoolExecutor.AbortPolicy`**：抛出异常
- **`ThreadPoolExecutor.CallerRunsPolicy`**：回退给调用者来执行
- **`ThreadPoolExecutor.DiscardPolicy`**：直接丢弃
- **`ThreadPoolExecutor.DiscardOldestPolicy`**：将最早未处理的任务丢弃

### 如何监控线程池的状态

可以使用ThreadPoolExecutor的相关方法

- getTaskCount
- getCompleteTaskCount
- getLargestPoolSize
- getPoolSize
- getActiveCount

### 线程池常用的阻塞队列

- 无界队列：单队列新增时会扩容，因此队列永远放不满，队列最大容量Integer.MAX_VALUE
- 同步队列：没有容量，如果任务提交时没有空闲线程则创建新线程，最大Integer.MAX_VALUE
- 延迟阻塞队列：是无界的，底层用堆来实现，按延迟时间进行排序，最大容量Integer.MAX_VALUE

### 线程处理任务的流程

1. 如果当前运行线程小于核心线程数，就创建一个新线程来运行
2. 如果当前运行线程大于核心线程树，但任务队列没有放满，就将任务放入任务队列
3. 如果任务放入队列失败，同时当前运行线程数量小于最大线程数，则创建新的线程执行任务
4. 如果当前运行线程数量达到最大线程数，且任务队列占满，则调用饱和策略

### 如何设置线程池的大小

- 如果是CPU密集型任务，设置为CPU核心数+1（+1为了突发的线程中断情况，仍有一个线程可以来使用CPU）
- 如果是IO密集型任务，在处理IO时可以不占用CPU，因此可以多设置一些线程，设置为CPU核心数*2
- 尽可能使用有界工作队列

### Fork/Join主要用来解决什么样的问题

ForkJoinPool JDK7引入的一个线程池类，是分治算法的并行实现。作用是更好地发挥多处理器的优势，从而发挥出更好的并发性能。

### Fork/Join框架主要包含哪三个模块? 模块之间的关系是怎么样的

- 任务对象：ForkJoinTask
- 执行线程：ForkJoinThreadWorker
- 线程池：ForkJoinPool

三者的关系为：ForkJoinPool通过其中的ForkJoinThreadWorker来执行ForkJoinTask

### 具体阐述Fork/Join的分治思想和work-stealing 实现方式

分治思想：将一个任务递归拆分成许多的小任务，从而充分地利用计算机资源

work-stealing（窃取算法）：每个工作线程都有自己的工作队列，这个工作队列支持pop、push以及poll操作。当工作线程要执行任务时，就会从工作队列中pop获取任务执行，当工作线程将任务拆分成小任务时（fork），会将小任务push到工作队列。而工作线程如果空闲时，就会尝试去别的线程的工作队列末尾poll操作窃取任务来执行。

## JUC工具类

### CountDownLatch底层实现原理

底层由AQS提供支持，数据结构类似于AQS数据结构。CountDownLatch维护一个锁计数器，当线程调用countDown()可以使计数减一，而调用await()可以使自己阻塞，当锁计数器减到0时，就唤醒所有被阻塞的线程。

### Future类有什么作用

是一个泛型接口，提供一下5个方法：

- 取消任务
- 判断任务是否取消
- 判断任务是否执行完成
- 获取执行结果

### Semaphore 有什么用？

可以设置同时访问资源的线程最大数量，当设为1时，退化为排他锁

acquire()申请获取令牌，release()释放令牌（实际就是增加令牌数量，无可无限量增加）

### CountDownLatch 有什么用

允许n个线程阻塞，直到所有线程都执行完任务将所有线程释放（一次性使用）

使用场景：多个线程处理文件，由于要统计完成情况，只有等全部处理完才执行后续逻辑

### CyclicBarrier 有什么用

于CountDownLatch类似，功能更加强大和复杂

### Phaser主要用来解决什么问题

JDK7新增的辅助同步类，支持动态调整任务，并可以分阶段同步

可以设定不同的阶段，在一个阶段内，可以随时注册任务，等待所有任务都完成再进入下一个阶段

### Exchanger主要解决什么问题

用于两个线程之间进行数据同步，提供一个数据同步点。两个线程可以通过Exchanger实现数据交换

### ThreadLocal 有什么用

使每个线程可以有自己的专属变量，常用于session管理和数据库连接管理，在黑马点评项目中，用来保存用户对象

### ThreadLocal底层原理

每个线程都有自己的ThreadLocalMap，当使用ThreadLocal时，会先获取到当前线程，再获取当前线程的ThreadLocalMap，其中键就是ThreadLocal，值就是数据，从而获取到每个线程独有的数据

### ThreadLocal 内存泄露问题是怎么导致的

由于在ThreadLocalMap中，键是弱引用，而值是强引用，因此当键被内存清理时会变成null导致值无法清除（ThreadLocalMap中考虑了这一情况，在调用set，get，remove时会清理key为null的值）

