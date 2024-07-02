# Spring

## IoC

### 什么是Spring IoC

IoC意思为控制反转：

- 控制：对于对象的控制权（实例化、管理）
- 反转：将控制权交给外部进行管理（框架、IoC容器）

作用：可以将复杂的对象依赖关系将给IoC容器进行统一的管理，从而简化应用的开发

实现原理：工厂模式+反射

### 什么是Bean

被Spring容器管理的对象

### @Component和@Bean的区别

- `@Component`作用于类，而`@Bean`作用于方法
- `@Component`通过类路径搜索自动加载到容器中，而`@Bean`一般在方法中自定义产生bean然后提交给容器
- 一些场景，例如第三方的库，只能通过`@Bean`注册bean

### @Autowired和@Resource的区别

- `@Aurowired`是Spring提供的注解，`@Resource`是JDK提供的注解
- `@Autowired`默认匹配类型，`@Resource`默认匹配名字
- 当一个接口有多个实现类时，两者都无法匹配，`@Autowired`通过`@Qualifier`指定名字，`@Resource`通过name指定名字

### Bean的作用域有哪些

- singleton：单例模式，在容器中唯一
- prototype：每次获取Bean都会创建新对象

针对Web环境：

- request：每次请求都会创建新的Bean
- session：每次新的会话都会创建新的Bean
- application：每次启动新的Web应用时创建新的Bean
- websocket：每次开启一个websocket创建新的Bean

### 单例Bean的线程安全问题有了解吗

单例Bean是线程不安全的，一般有两种解决方案：

- 尽量避免在Bean中定义可变的变量
- 在Bean中使用ThreadLocal来保存变量

Bean一般都是无状态的（没有成员变量），这种情况下可以不考虑线程安全问题

### Bean的生命周期

1. 根据Bean定义利用反射创建实例
2. 设置Bean的属性值
3. 检查Bean是否实现了`Aware`相关接口并执行
4. 调用容器的`BeanPostProcessor`的前置处理方法
5. 检查Bean是否实现了`InitializingBean`接口并执行`afterPropertiesSet`方法
6. 检查是否配置了Bean的inti-method方法并执行
7. 调用容器的`BeanPostProcessor`的后置处理方法
8. 使用中
9. 销毁Bean时，检查是否实现了`DisposableBean`接口并执行`destoty`方法
10. 销毁Bean时，检查是否配置了destory-method并执行

## AOP

### 什么是Spring AOP

意思为面向切面编程，将与业务无关的通用代码（例如事务管理、日志管理、权限控制等等）进行封装，从而降低耦合性，使代码易于拓展和维护

Spring AOP是基于动态代理来实现AOP的，当目标对象实现了某个接口时，那么Spring AOP会通过JDK Proxy来创建代理对象；当目标对象没有实现接口时，会通过CGlib生成一个目标对象的子类来作为代理对象。

### AspectJ 定义的通知类型有哪些？

- Before：方法调用前执行
- After：方法调用后执行
- AferReturning：方法返回后执行
- AfterThrowing：抛出异常后执行
- Around：可以拿到目标对象和调用方法，从而在调用方法前后随意操作

### Spring AOP和AspectJ AOP有什么区别

AOP是运行时增强，而Aspect是编译时增强；在Spring AOP框架中也整合了AspectJ AOP

在切面较少时，两者性能差不多；在切面很多时，AspectJ性能更好

### 多个切面的执行顺序如何决定

通常使用`@order`决定，值越小优先级越高

## SpringMVC

### 什么是MVC

一种设计思想。模型、视图、控制器的缩写。其核心思想是将业务逻辑、数据、显示进行分离

### SpringMVC的核心组件

- `DispatcherServlet`：前置控制器，用于接受网络请求、分发、返回结果
- `HandlerMaping`：根据uri匹配能够处理请求的handler（控制器）
- `HandlerAdapter`：调用Handler执行方法
- `Handler`：实际处理请求的控制器
- `ViewResolver`：视图解析器

### SpringMVC控制流程

1. 客户端发送请求，`DispatcherServlet`进行拦截
2. `DispatcherServlet`调用`HandlerMapping`匹配可以处理请求的`Handler`
3. `DispatchServlet`调用`HandlerAdapter`执行`Handler`
4. `Handler`处理完请求后会返回一个`ModelAndView`对象（包含数据和逻辑视图）给`DispatchServlet`
5. `DispatchServlet`调用`ViewResolver`由逻辑视图获取实际的视图
6. `DispatchServlet`进行视图渲染
7. 将渲染玩的视图返回给客户端

### 统一异常处理怎么做

使用`@ControllerAdvice`指定异常拦截类，`@ExceptionHandler`指定处理异常的方法

### Spring中有哪几种事务传播行为

- `REQUIRED`：当前有事务，就加入事务；没有就创建新事务（默认）
- `NEW`：当前有事务，就将当前事务挂起，自己开新的；没有就创建新事务
- `NESTED`：当前有事务，就创建一个事务作为嵌套；没有就创建新事务
- `MANDATORY`：当前有事务，就加入；没有就抛出异常
- `SUPPORTS`：当前有事务，就加入事务；没有就以非事务方式进行
- `NOT_SUPPORTS`：当前有事务，就挂起当前事务；没有就以非事务方式进行
- `NEVER`：当前有事务，就抛出异常；没有就以非事务方式进行

### Spring 事务中的隔离级别有哪几种?

和MySQL一样

###  @Transactional(rollbackFor = Exception.class)注解了解吗？

默认情况下Spring事务只有在遇到RuntimeException时才会回滚，使用了这个值后，遇到其余异常也可以触发回滚

### Spring框架中用到了哪些设计模式

- 单例模式：所有bean默认单例
- 工厂模式：创建bean
- 代理模式：AOP的实现
- 模板模式：如jdbcTemplate
- 观察者模式：Spring时间驱动模型
- 适配器模式：如SpringMVC适配具体的Controller