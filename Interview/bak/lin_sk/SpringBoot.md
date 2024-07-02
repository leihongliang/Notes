# SpringBoot

### SpringBoot的启动流程

总体分为两个阶段：

- 构造SpringApplication的实例：
  1. 将启动类添加到SpringApplication的属性当中
  2. 获取应用类型并判断是否是web工程，设置到属性中
  3. 创建并初始化所有的初始化器，添加到initializers属性中
  4. 创建并初始化所有的监听器，添加到listeners属性中
  5. 初始化主类mainApplicationClass
- 调用run方法：
  1. 获取监听器及参数配置，并启动
  2. 打印banner信息
  3. 创建并初始化容器
  4. 监听器发送通知告知启动完成

### SpringBoot的优点

- 可以快速构建项目
- 提供默认配置，减少重复开发
- 内嵌Http服务器，可以方便的测试和开发web应用
- 极大提高项目开发和部署效率
- 提供多种插件
- 提供运行时程序监测

### 什么是 Spring Boot Starters

依赖关系的集合，例如spring-boot-statrs-web，包含了springMVC、Tomcat、Jackson等依赖，解决了依赖配置复杂的问题

其他还有：spring-boot-statrs-jdbc、spring-boot-statrs-test、spring-boot-statrs-security

### SpringBoot支持哪些内嵌Servlet容器

tomcat（默认）、jetty、undertow

### 介绍⼀下@SpringBootApplication 注解

包含三个注解：

- `@EnableAutoConfiguration`：开启自动配置机制
- `@ComponentScan`：扫描该所在包下的`Component`
- `@Configuration`：允许上下文注册额外的Bean或配置类

### 开发 RESTful Web 服务常⽤的注解有哪些

Spring Bean相关：

- `@Autowired`：自动装配
- `@RestController`：`@controller`+`@ResponseBody`，可以将函数返回值直接填入响应体中
- `@Controller`
- `@Service`
- `@Repository`

Http请求处理相关：

- `@GetMapping`
- `@PostMapping`
- `@PutMapping`
- `@DeleteMapping`

前后端传值：

- `@RequestParam`：获取请求参数
- `@PathVariable`：从路径中获取参数
- `RequestBody`：⽤于读取 Request 请求的 body 部分并且 Content-Type为application/json 格式的数据，接受到数据后会自动转为Java对象

### Spirng Boot 常⽤的两种配置⽂件

application.properties和application.yml

### Spring Boot 常⽤的读取配置⽂件的⽅法有哪些

- `@Value("${property}`：读取某个值作为属性变量
- `@ConfigurationProperties`：读取配置并与Bean相绑定
- `@PropertySource`：读取指定配置文件（只支持properties格式）
- 使用Spring提供的Environment类读取配置
- 使用原始Properties类进行读取

### Spring Boot配置文件优先级

从高到低为：

- 项目根目录下的配置文件
- 项目根目录下config文件夹下的配置文件
- 类路径下的配置文件
- 类路径下config文件夹下的配置文件

### 常⽤的 Bean 映射⼯具有哪些

常⽤的 Bean 映射⼯具有：Spring BeanUtils、Apache BeanUtils、MapStruct、ModelMapper、Dozer、Orika、JMapper 。

### Spring Boot如何监控系统实际运行状况

可以集成Spring Boot Actuator来进行监控，其提供了许多API获取程序运行时的状态信息

例如通过GET方式访问/health来查看程序的健康指标

### Spring Boot何如校验参数

spring-boot-starters-web包含了用于校验参数的依赖（JSR、Hibernate Validator），在项目中可以通过注解的方法来进行校验

例如：`@NotNull`、`@NotBlank`

使用方法：

- 加在实体类的属性中，然后在请求参数中加上`@Vaild`注解
- 在参数前加上需要的校验注解，同时控制器类要加上`@Vaild`注解

### Spring Boot 中如何实现定时任务

使⽤ @Scheduled 注解就能很⽅便地创建⼀个定时任务

还需要在 SpringBoot 启动类上加上@EnableScheduling 注解，这样才可以启动定时任务。

### SpringBoot自动配置的原理

在主程序中添加@SpringBootApplication或者@EnableAutoConfiguration注解，就会自动去读取starter中的spring.factories文件，其中就配置了所需要的bean（约定）

### spring-boot-starter-parent有什么作用

新建一个SrpingBoot项目默认自带，具有以下功能：

- 定义java编译版本
- 继承自spring-boor-dependencies，其中确定了依赖版本
- 确定编码格式
- 执行打包操作的配置
- 自动化的资源过滤
- 自动化的插件配置

### 如何自定义SpringBoot Starter

1. 实现功能
2. 添加properties
3. 编写自动配置类
4. 添加spring.factories
5. 打包和安装

### SpringBoot 打成jar和普通的jar有什么区别？

SpringBoot打包的jar是可执行的，通过java -jar执行；但无法被其他java工程所依赖，原因在于文件结构不一样，解压后不是直接的类文件，类文件存放在 \BOOT-INF\classes中