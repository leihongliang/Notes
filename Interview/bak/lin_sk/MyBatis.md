# MyBatis

### 什么是MyBatis

对象关系映射框架，内部封装了JDBC，并且通过xml配置文件以及注解的方式建立对象与数据库之间的映射关系，无需手动编写结果集

### MyBatis的优点

- 编写SQL语句更加灵活，支持动态SQL
- 封装了JDBC，省去手动建立连接的过程
- 提供对象与数据库的映射，方便地获取结果集
- 完美继承Spring

### #{}和${}的区别是什么

- #{}是占位符，会进行预编译，防止注入
- ${}是拼接符，使用字符串替换来构成SQL

### DAO接口的工作原理

一个xml文件都会对应一个DAO接口，接口的权限名对应xml文件中的namespace，接口中的方法名对应xml文件中的id。这样将xml文件与接口方法向对应起来。xml文件中，每一个增删改查的标签都会生成一个`MappedStateMent`与之对应。当调用DAO方法时，MyBatis基于动态代理的方式对方法进行拦截，转而去执行相对应的`MappedStateMent`来执行SQL。

### 分页原理

MyBatis使用RowBounds来进行分页，属于内存分页不是物理分页，因此不怎么用

可以使用插件进行分页，自定义插件拦截待执行的sql，然后根据分页参数来改写sql（加limit 0, 10）

### 如何获取自增主键

在 `<insert />` 标签中添加`useGeneratedKeys="true"` 等属性

### 如何编写一个MyBaits插件

实现 MyBatis 的 `Interceptor` 接口并复写 `intercept()` 方法，然后在给插件编写注解，指定要拦截哪一个接口的哪些方法即可，最后在配置文件中配置编写的插件

### MyBatis动态SQL原理

基于ONOL（数据与视图交互数据），计算动态值拼接SQL，常用的动态标签有trim | where | set | foreach | if | choose | when | otherwise
| bind。

### MyBatis的工作原理

1. 读取配置文件
2. 加载映射文件
3. 创建会话工厂
4. 创建会话对象
5. Executor执行器：负责根据传递的参数动态生成SQL
6. 生成MappedStateMent：对映射信息进行封装
7. 输入参数映射
8. 输出参数映射

### 什么是MyBatis的接口绑定，有哪些实现方式

将接口中的方法与SQL语句进行绑定，调用接口方法就可以执行对应的SQL，可以通过xml配置或注解来实现