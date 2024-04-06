# Spring知识点

## 1.SpringIOC

什么是IOC？ （1）控制反转（把对象的创建的对象之间的调用过程交给spring管理）

（2）使用IOC的目的，为了降低耦合度

### 1.1 IOC容器

<mark>IOC容器底层原理</mark>

![](C:\Users\lenovo\Desktop\新建文件夹\a.png)

（1）xml解析，工厂模式，反射

过程：（1）在xml配置创建的对象（2）创建工厂类（XML解析，通过反射创建对象）

<mark> IOC接口（BeanFactory和ApplicationContext）</mark>

1. IOC思想基于IOC容器完成，IOC容器就是对象工厂

2. Spring提供IOC容器实现有两种方式（两个接口）

   （1）BeanFactory：IOC容器基本实现，是Spring内部的使用接口，不提供开发人员使用

   <mark>加载配置文件时不会创建对象，在获取对象（使用）才去创建对象</mark>

   （2）ApplicationContext：BeanFactory的子接口，提供更多更强大的功能，一般由开发人员进行使用

   <mark>加载配置文件时就会把在配置文件中的对象进行创建</mark>

3. ApplicationContext的实现类

   ![](C:\Users\lenovo\Desktop\新建文件夹\b.png)

<mark>IOC 操作 Bean 管理（概念）</mark>

1. 什么是 Bean 管理（Bean 管理指的是两个操作） （1）Spring 创建对象 （2）Spirng 注入属性
2. Bean 管理操作有两种方式 （1）基于 xml 配置文件方式实现 （2）基于注解方式实现

<mark>IOC操作（基于XML）</mark>

（1）在 spring 配置文件中，使用 bean 标签，标签里面添加对应属性，就可以实现对象创建 （2）在 bean 标签有很多属性，介绍常用的属性

<mark>id 属性：唯一标识</mark>
<mark> class 属性：类全路径（包类路径）</mark>
（3）创建对象时候，默认也是执行无参数构造方法完成对象创建

IOC操作（基于注解）

### 1.2 Spring注入属性的方式

一、xml（DI：依赖注入，就是注入属性）

1. <mark>第一种注入方式：使用 set 方法进行注入</mark>

   （1）创建类，定义属性和对应的 set 方法

   （2）在 spring 配置文件配置对象创建，配置属性注入

2. <mark>第二种注入方式：使用有参数构造进行注入</mark>

   （1）创建类，定义属性，创建属性对应有参数构造方法

   （2）在 spring 配置文件中进行配置

3. p 名称空间注入（了解） IOC 操作 Bean 管理（xml 注入其他类型属性）

   1、字面量

   2、注入属性-外部 bean

   3、注入属性-内部 bean

   4、注入属性-级联赋值

   4、在集合里面设置对象类型值

   5、把集合注入部分提取出来

### 1.3 FactoryBean

**①简介**

FactoryBean是Spring提供的一种整合第三方框架的常用机制。和普通的bean不同，配置一个FactoryBean类型的bean，在获取bean的时候得到的并不是class属性中配置的这个类的对象，而是getObject()
方法的返回值。通过这种机制，Spring可以帮我们把复杂组件创建的详细过程和繁琐细节都屏蔽起来，只把最简洁的使用界面展示给我们。

将来我们整合Mybatis时，Spring就是通过FactoryBean机制来帮我们创建SqlSessionFactory对象的。

<mark> Spring 有两种类型 bean，一种普通 bean，另外一种工厂 bean（FactoryBean）</mark>

- 普通 bean：在配置文件中定义 bean 类型就是返回类型

- 工厂 bean：在配置文件定义 bean 类型可以和返回类型不一样 第一步 创建类，让这个类作为工厂 bean，实现接口 FactoryBean 第二步 实现接口里面的方法，在实现的方法中定义返回的 bean 类型

### 1.4 Bean的作用域

<mark>①概念</mark>

在Spring中可以通过配置bean标签的scope属性来指定bean的作用域范围，各取值含义参加下表：

| 取值            | 含义                      | 创建对象的时机   |
| ------------- | ----------------------- | --------- |
| singleton（默认） | 在IOC容器中，这个bean的对象始终为单实例 | IOC容器初始化时 |
| prototype     | 这个bean在IOC容器中有多个实例      | 获取bean时   |

如果是在WebApplicationContext环境下还会有另外几个作用域（但不常用）：

| 取值      | 含义         |
| ------- | ---------- |
| request | 在一个请求范围内有效 |
| session | 在一个会话范围内有效 |

### 1.5 Bean的生命周期

<mark>**①具体的生命周期过程**</mark>

1. bean对象创建（调用无参构造器）

2. 给bean对象设置属性

3. bean的后置处理器（初始化之前）

4. bean对象初始化（需在配置bean时指定初始化方法）

5. bean的后置处理器（初始化之后）

6. bean对象就绪可以使用

7. bean对象销毁（需在配置bean时指定销毁方法）

8. IOC容器关闭

### 1.6 基于xml自动装配

> 自动装配：
>
> 根据指定的策略，在IOC容器中匹配某一个bean，自动为指定的bean中所依赖的类类型或接口类型属性赋值

    

二、基于注解（@Autowried(默认Bytype)）(@Resource（默认Byname）)

1. 属性注入（byType(类型)）

2. set注入（创建set方法）

3. 构造方法注入（创建构造方法）

4. 形参

<img src="file:///C:/Users/lenovo/Desktop/5{K9W`$UJV5RY1]RDLW2XV2.png" title="" alt="" data-align="inline">

5. @Autowired+@Qulif(Byname)

### 实现IOC

```java
    @Test
    public void test01() throws Exception {
        //获取class文件
        Class<Car> carClass = Car.class;
        Class<? extends Car> aClass = new Car().getClass();
        Class<?> aClass1 = Class.forName("com.gzh.spring_demo.reflact.Car");
        //实例化
        Car o = (Car) aClass1.getDeclaredConstructor().newInstance();
        //获取方法
        Constructor<?>[] constructors = carClass.getConstructors();
        for (Constructor c: constructors){
            System.out.println(c.getName()+(c.getParameterCount()));
        }
    }
```

## 2. SpringAOP

### 2.1 概念

AOP（Aspect Oriented
Programming）是一种设计思想，是软件设计领域中的面向切面编程，它是面向对象编程的一种补充和完善，它以通过预编译方式和运行期动态代理方式实现，在不修改源代码的情况下，给程序动态统一添加额外功能的一种技术。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

## 3. JdbcTemplate

<mark>Spring 框架对 JDBC 进行封装，使用 JdbcTemplate 方便实现对数据库操作</mark>

## 4. 事务

##### ①什么是事务

数据库事务( transaction)是访问并可能操作各种数据项的一个数据库操作序列，这些操作要么全部执行,要么全部不执行，是一个不可分割的工作单位。事务由事务开始与事务结束之间执行的全部数据库操作组成。

##### ②事务的特性

**A：原子性(Atomicity)**

一个事务(transaction)中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。

**C：一致性(Consistency)**

事务的一致性指的是在一个事务执行之前和执行之后数据库都必须处于一致性状态。

如果事务成功地完成，那么系统中所有变化将正确地应用，系统处于有效状态。

如果在事务中出现错误，那么系统中的所有变化将自动地回滚，系统返回到原始状态。

**I：隔离性(Isolation)**

指的是在并发环境中，当不同的事务同时操纵相同的数据时，每个事务都有各自的完整数据空间。由并发事务所做的修改必须与任何其他并发事务所做的修改隔离。事务查看数据更新时，数据所处的状态要么是另一事务修改它之前的状态，要么是另一事务修改它之后的状态，事务不会查看到中间状态的数据。

**D：持久性(Durability)**

指的是只要事务成功结束，它对数据库所做的更新就必须保存下来。即使发生系统崩溃，重新启动数据库系统后，数据库还能恢复到事务成功结束时的状态。

**<mark>事务管理介绍</mark>**

**1、事务添加到 JavaEE 三层结构里面 Service 层（业务逻辑层） 2、在 Spring 进行事务管理操作 （1）有两种方式：编程式事务管理和声明式事务管理（使用） 3、声明式事务管理 （1）基于注解方式（使用） （2）基于
xml 配置文件方式 4、在 Spring 进行声明式事务管理，底层使用 AOP 原理**

**<mark>Spring 事务管理 API</mark>**

（1）提供一个接口（PlatfromTransactionManager），代表事务管理器，这个接口针对不同的框架提供不同的实现类

![](C:\Users\lenovo\Desktop\新建文件夹\d.png)

### 4.1 声明式事务概念

既然事务控制的代码有规律可循，代码的结构基本是确定的，所以框架就可以将固定模式的代码抽取出来，进行相关的封装。

封装起来后，我们只需要在配置文件中进行简单的配置即可完成操作。

- 好处1：提高开发效率
- 好处2：消除了冗余的代码
- 好处3：框架会综合考虑相关领域中在实际开发环境下有可能遇到的各种问题，进行了健壮性、性能等各个方面的优化

所以，我们可以总结下面两个概念：

- **编程式**：**自己写代码**实现功能
- **声明式**：通过**配置**让**框架**实现功能

**<mark>XML 声明式事务管理</mark>**

1、在 spring 配置文件中进行配置 第一步 配置事务管理器 第二步 配置通知 第三步 配置切入点和切面

### 4.2 基于注解的声明式事务

1. 在 spring 配置文件配置事务管理器

2. 在 spring 配置文件，开启事务注解

   （1）在 spring 配置文件引入名称空间 tx

   （2）开启事务注解

3. <mark> 在 service 类上面（或者 service 类里面方法上面）添加事务注解</mark>
   （1）@Transactional，这个注解添加到类上面，也可以添加方法上面
   （2）如果把这个注解添加类上面，这个类里面所有的方法都添加事务
   （3）如果把这个注解添加方法上面，为这个方法添加事务

4. <mark>声明式事务管理参数配置</mark>

    1. 在 service 类上面添加注解@Transactional，在这个注解里面可以配置事务相关参数

    2. propagation：事务传播行为 （1）多事务方法直接进行调用，这个过程中事务 是如何进行管理的

    3. <mark>ioslation：事务隔离级别</mark>

       （1）事务有特性成为隔离性，多事务操作之间不会产生影响。不考虑隔离性产生很多问题 （2）有三个读问题：脏读、不可重复读、虚（幻）读 （3）脏读：一个未提交事务读取到另一个未提交事务的数据

    4. timeout：超时时间 （1）事务需要在一定时间内进行提交，如果不提交进行回滚 （2）默认值是 -1 ，设置时间以秒单位进行计算

    5. readOnly：是否只读 （1）读：查询操作，写：添加修改删除操作 （2）readOnly 默认值 false，表示可以查询，可以添加修改删除操作 （3）设置 readOnly 值是 true，设置成 true
       之后，只能查询

    6. rollbackFor：回滚

       （1）设置出现哪些异常进行事务回滚

    7. noRollbackFor：不回滚 （1）设置出现哪些异常不进行事务回滚

### 4.3事务传播行为

**①介绍**

什么是事务的传播行为？

在service类中有a()方法和b()方法，a()方法上有事务，b()方法上也有事务，当a()方法执行过程中调用了b()方法，事务是如何传递的？合并到一个事务里？还是开启一个新的事务？这就是事务传播行为。

一共有七种传播行为：

- REQUIRED：支持当前事务，如果不存在就新建一个(默认)**【没有就新建，有就加入】**
- SUPPORTS：支持当前事务，如果当前没有事务，就以非事务方式执行**【有就加入，没有就不管了】**
- MANDATORY：必须运行在一个事务中，如果当前没有事务正在发生，将抛出一个异常**【有就加入，没有就抛异常】**
- REQUIRES_NEW：开启一个新的事务，如果一个事务已经存在，则将这个存在的事务挂起**【不管有没有，直接开启一个新事务，开启的新事务和之前的事务不存在嵌套关系，之前事务被挂起】**
- NOT_SUPPORTED：以非事务方式运行，如果有事务存在，挂起当前事务**【不支持事务，存在就挂起】**
- NEVER：以非事务方式运行，如果有事务存在，抛出异常**【不支持事务，存在就抛异常】**
- NESTED：如果当前正有一个事务在进行中，则该方法应当运行在一个嵌套式事务中。被嵌套的事务可以独立于外层事务进行提交或回滚。如果外层事务不存在，行为就像REQUIRED一样。**
  【有事务的话，就在这个事务里再嵌套一个完全独立的事务，嵌套的事务可以独立的提交和回滚。没有事务就和REQUIRED一样。】**

## 4.4全注解配置事务

```java
@Configuration //配置类
@ComponentScan(basePackages = "com.atguigu") //组件扫描
@EnableTransactionManagement //开启事务
public class TxConfig {
//创建数据库连接池
@Bean
public DruidDataSource getDruidDataSource() {
DruidDataSource dataSource = new DruidDataSource();
dataSource.setDriverClassName("com.mysql.jdbc.Driver");
dataSource.setUrl("jdbc:mysql:///user_db");
dataSource.setUsername("root");
dataSource.setPassword("root");
return dataSource;
}
//创建 JdbcTemplate 对象
@Bean
public JdbcTemplate getJdbcTemplate(DataSource dataSource) {
//到 ioc 容器中根据类型找到 dataSource
JdbcTemplate jdbcTemplate = new JdbcTemplate();
//注入 dataSource
jdbcTemplate.setDataSource(dataSource);
return jdbcTemplate;
}
//创建事务管理器
@Bean
public DataSourceTransactionManager
getDataSourceTransactionManager(DataSource dataSource) {
DataSourceTransactionManager transactionManager = new
DataSourceTransactionManager();
transactionManager.setDataSource(dataSource);
return transactionManager;
}
}
```
