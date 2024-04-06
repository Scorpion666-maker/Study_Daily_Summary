# Spring

![Spring](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\Spring.png)

---

## Spring的相关概述

---

### 什么是Spring？

        Spring 是一个开源的轻量级框架，用于构建企业级 Java 应用程序。它提供了全面的基础设施支持，使得开发者可以专注于应用程序的业务逻辑而不必处理底层的基础设施配置。

        Spring 框架的核心特点包括：

1. **IoC（控制反转）容器**：Spring IoC 容器管理 Java 对象的生命周期和配置。通过 IoC，Spring 将对象的创建、依赖解析和注入都交由容器来管理，降低了组件之间的耦合度。

2. **AOP（面向切面编程）支持**：Spring 提供了 AOP 功能，允许开发者通过定义横切关注点（如日志记录、性能监控等）来实现与业务逻辑解耦。

3. **声明式事务管理**：Spring 提供了声明式事务管理的支持，简化了事务的配置和管理，开发者可以通过注解或 XML 配置来实现事务管理。

4. **模块化**：Spring 框架分为多个模块，包括核心容器、数据访问、Web、AOP 等，开发者可以根据需要选择使用其中的模块，实现轻量级的定制化开发。

5. **集成其他框架**：Spring 提供了与其他流行框架（如 Hibernate、MyBatis、Spring MVC 等）的集成支持，使得开发者可以方便地将 Spring 与这些框架结合使用。

6. **简化开发**：Spring 提供了许多工具和辅助类，简化了开发过程，如资源管理、数据校验、国际化等。
   
   

### 使用Spring框架的好处是什么？

* **轻量：** Spring 是轻量的，基本的版本大约2MB
* **控制反转：** Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们
* **面向切面的编程(AOP)：** Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开
* **容器：** Spring 包含并管理应用中对象的生命周期和配置
* **MVC框架：** Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品
* **事务管理：** Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）
* **异常处理：** Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。
  
  

### 什么是 spring 装配（DI）？

        Spring 装配（Spring Dependency Injection）是 Spring 框架的核心特性之一，用于管理组件之间的依赖关系。它通过将对象之间的依赖关系外部化，由容器来负责管理和注入依赖，从而实现了松耦合、高内聚的设计原则。

        Spring 提供了多种方式来实现依赖注入，包括构造函数注入、Setter 方法注入、字段注入以及自动装配等。下面是 Spring 中常用的装配方式：

1. **构造函数注入**：通过构造函数来注入依赖。开发者可以在类的构造函数中定义需要注入的依赖对象，Spring 容器会根据配置将依赖对象注入到相应的构造函数参数中。

2. **Setter 方法注入**：通过 Setter 方法来注入依赖。开发者可以在类中定义 Setter 方法，Spring 容器会通过调用这些 Setter 方法来注入依赖对象。

3. **字段注入**：通过字段来注入依赖。开发者可以在类中直接声明依赖对象的字段，并使用 `@Autowired` 注解来标注需要注入的字段，Spring 容器会自动将依赖对象注入到这些字段中。

4. **自动装配**：Spring 还提供了自动装配的功能，可以根据一定的规则自动注入依赖。常用的自动装配方式包括 byName、byType、constructor 和 autowire-candidate 等。

        当 bean 在 Spring 容器中组合在一起时，它被称为装配或 bean 装配。 Spring 容器需要知道需要什么 bean 以及容器应该如何使用依赖注入来将 bean 绑定在一起，同时装配 bean。

        Spring 容器能够自动装配 bean。也就是说，可以通过检查 BeanFactory 的内容让 Spring 自动解析 bean 的协作者。

自动装配的不同模式：

* **no** - 这是默认设置，表示没有自动装配。应使用显式 bean 引用进行装配。
* **byName** - 它根据 bean 的名称注入对象依赖项。它匹配并装配其属性与 XML 文件中由相同名称定义的 bean。
* **byType** - 它根据类型注入对象依赖项。如果属性的类型与 XML 文件中的一个 bean 名称匹配，则匹配并装配属性。
* **构造函数** - 它通过调用类的构造函数来注入依赖项。它有大量的参数。
* **autodetect** - 首先容器尝试通过构造函数使用 autowire 装配，如果不能，则尝试通过 byType 自动装配。
  
  

### 自动装配有什么局限？

1. **命名冲突**：当容器中存在多个类型相同的 Bean 时，自动装配可能会导致命名冲突，难以确定应该注入哪个 Bean。为了解决这个问题，可以使用 `@Qualifier` 注解或者限定符来指定具体的 Bean。

2. **不适用于多个实现的情况**：当一个接口有多个实现时，自动装配可能无法确定要注入哪个实现。在这种情况下，需要显式地指定要注入的 Bean。

3. **隐藏的依赖关系**：自动装配可能隐藏了组件之间的依赖关系，使得代码难以理解和维护。在大型项目中，过度使用自动装配可能导致代码的可读性下降。

4. **自动装配的行为难以预测**：自动装配依赖于容器的配置和规则，其行为可能难以预测。如果不了解容器的配置规则，可能会导致意外的装配结果。

5. **性能开销**：在启动时，自动装配需要扫描并解析所有的 Bean 定义，这可能会带来一定的性能开销。对于性能要求较高的应用程序，可能需要考虑手动装配以减少启动时间。
   
   

### Spring 怎么解决循环依赖问题？

        spring对循环依赖的处理有三种情况： ①构造器的循环依赖：这种依赖spring是处理不了的，直接抛出BeanCurrentlylnCreationException异常。 ②单例模式下的setter循环依赖：通过“三级缓存”处理循环依赖。 ③非单例循环依赖：无法处理。

        下面分析单例模式下的setter循环依赖如何解决

        Spring的单例对象的初始化主要分为三步：

![1584761413341_12](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\1584761413341_12.png)

（1）createBeanInstance：实例化，其实也就是调用对象的构造方法实例化对象

（2）populateBean：填充属性，这一步主要是多bean的依赖属性进行填充

（3）initializeBean：调用spring xml中的init 方法。

        从上面讲述的单例bean初始化步骤我们可以知道，循环依赖主要发生在第一、第二部。也就是构造器循环依赖和field循环依赖。

![1584758309616_10](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\1584758309616_10.png)

        举例：A的某个field或者setter依赖了B的实例对象，同时B的某个field或者setter依赖了A的实例对象”这种循环依赖的情况。A首先完成了

初始化的第一步（createBeanINstance实例化），并且将自己提前曝光到singletonFactories中。

        此时进行初始化的第二步，发现自己依赖对象B，此时就尝试去get(B)，发现B还没有被create，所以走create流程，B在初始化第一步的时候发现自己依赖了对象A，于是尝试get(A)，尝试一级缓存singletonObjects(肯定没有，因为A还没初始化完全)，尝试二级缓存earlySingletonObjects（也没有），尝试三级缓存singletonFactories，由于A通过ObjectFactory将自己提前曝光了，所以B能够通过

        ObjectFactory.getObject拿到A对象(虽然A还没有初始化完全，但是总比没有好呀)，B拿到A对象后顺利完成了初始化阶段1、2、3，完全初始化之后将自己放入到一级缓存singletonObjects中。

            此时返回A中，A此时能拿到B的对象顺利完成自己的初始化阶段2、3，最终A也完成了初始化，进去了一级缓存singletonObjects中，而且更加幸运的是，由于B拿到了A的对象引用，所以B现在hold住的A对象完成了初始化。



### Spring 框架中用到了哪些设计模式？

**工厂设计模式** : Spring使用工厂模式通过 `BeanFactory`、`ApplicationContext` 创建 bean 对象。

**代理设计模式** : Spring AOP 功能的实现。

**单例设计模式** : Spring 中的 Bean 默认都是单例的。

**模板方法模式** : Spring 中 `jdbcTemplate`、`hibernateTemplate` 等以 Template 结尾的对数据库操作的类，它们就使用到了模板模式。

**包装器设计模式** : 我们的项目需要连接多个数据库，而且不同的客户在每次访问中根据需要会去访问不同的数据库。这种模式让我们可以根据客户的需求能够动态切换不同的数据源。

**观察者模式:** Spring 事件驱动模型就是观察者模式很经典的一个应用。

**适配器模式** :Spring AOP 的增强或通知(Advice)使用到了适配器模式、spring MVC 中也是用到了适配器模式适配`Controller`。



### Spring容器启动流程是怎样的

1. 在创建Spring容器，也就是启动Spring时：

2. ⾸先会进⾏扫描，扫描得到所有的BeanDefinition对象，并存在⼀个Map中

3. 然后筛选出⾮懒加载的单例BeanDefinition进⾏创建Bean，对于多例Bean不需要在启动过程中去进⾏创建，对于多例Bean会在每次获取Bean时利⽤BeanDefinition去创建

4. 利⽤BeanDefinition创建Bean就是Bean的创建⽣命周期，这期间包括了合并BeanDefinition、推断构造⽅法、实例化、属性填充、初始化前、初始化、初始化后等步骤，其中AOP就是发⽣在初始化后这⼀步骤中

5. 单例Bean创建完了之后，Spring会发布⼀个容器启动事件

6. Spring启动结束，在源码中会更复杂，⽐如源码中会提供⼀些模板⽅法，让⼦类来实现，⽐如源码中还涉及到⼀些BeanFactoryPostProcessor和BeanPostProcessor的注册，Spring的扫描就是通过BenaFactoryPostProcessor来实现的，依赖注⼊就是通过BeanPostProcessor来实现的
       在Spring启动过程中还会去处理@Import等注解
           **加载配置文件**：Spring 容器会读取应用程序的配置文件，通常是 XML 配置文件（如 `applicationContext.xml`）或者基于 Java 注解的配置类（如 `@Configuration` 注解标注的类）。
           **解析配置文件**：Spring 容器会解析配置文件，将配置信息转化为容器内部的数据结构，如 BeanDefinition 对象等。这个过程包括对 Bean 的定义、依赖关系、初始化方法、销毁方法等信息的解析和处理。
           **创建 Bean 实例**：根据配置文件中的 Bean 定义，Spring 容器开始创建 Bean 实例。这包括调用构造函数创建对象、设置属性值、调用初始化方法等步骤。如果某个 Bean 的创建依赖于其他 Bean，Spring 容器会递归地解析和创建依赖的 Bean。
           **依赖注入**：一旦所有 Bean 实例都创建完成，Spring 容器会根据配置文件中的依赖关系，对 Bean 实例进行依赖注入。这包括构造函数注入、Setter 方法注入、字段注入等方式，将依赖的 Bean 注入到目标 Bean 中。
           **初始化 Bean**：一旦所有的依赖注入完成，Spring 容器会调用 Bean 的初始化方法（如 `init-method` 属性指定的方法、实现 `InitializingBean` 接口的 `afterPropertiesSet()` 方法等）对 Bean 进行初始化操作。
           **添加 Bean 到容器中**：初始化完成的 Bean 实例会被添加到 Spring 容器中进行管理。
           **完成启动**：一旦所有 Bean 实例都创建、依赖注入和初始化完成，Spring 容器启动流程就完成了。此时容器就可以提供服务，响应应用程序的请求。

---

## IOC

---

### 什么是 Spring IOC 容器？

        Spring 框架的核心是 Spring 容器。容器创建对象，将它们装配在一起，配置它们并管理它们的完整生命周期。Spring 容器使用依赖注入来管理组成应用程序的组件。容器通过读取提供的配置元数据来接收对象进行实例化，配置和组装的指令。该元数据可以通过 XML，Java 注解或 Java 代码提供。

        Spring IOC（控制反转）容器是 Spring 框架的核心组件之一，它负责管理应用程序中的对象，实现了对象之间的依赖关系的外部化和解耦。IOC 容器通过创建、组装和管理 Bean 对象，实现了对象的生命周期的管理，并提供了依赖注入（Dependency Injection，DI）功能。



### 如何理解IoC和DI？

        IOC就是**控制反转**，通俗的说就是我们**不用自己创建实例对象，这些都交给Spring的bean工厂帮我们创建管理**。这也是Spring的核心思想，**通过面向接口编程的方式来是实现对业务组件的动态依赖**。这就意味着IOC是Spring针对解决程序耦合而存在的。

        在实际应用中，Spring通过配置文件（xml或者properties）指定需要实例化的java类（类名的完整字符串），包括这些java类的一组初始化值，通过加载读取配置文件，用Spring提供的方法（getBean()）就可以获取到我们想要的根据指定配置进行初始化的实例对象。

### 谈谈自己对于 Spring IoC 的了解

        **IoC（Inversion of Control:控制反转）** 是一种设计思想，而不是一个具体的技术实现。IoC 的思想就是将原本在程序中手动创建对象的控制权，交由 Spring 框架来管理。不过， IoC 并非 Spring 特有，在其他语言中也有应用。

**为什么叫控制反转？**

* **控制**：指的是对象创建（实例化、管理）的权力
* **反转**：控制权交给外部环境（Spring 框架、IoC 容器

![frc-365faceb5697f04f31399937c059c162](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\frc-365faceb5697f04f31399937c059c162.png)

         将对象之间的相互依赖关系交给 IoC 容器来管理，并由 IoC 容器完成对象的注入。这样可以很大程度上简化应用的开发，把应用从复杂的依赖关系中解放出来。 IoC 容器就像是一个工厂一样，当我们需要创建一个对象的时候，只需要配置好配置文件/注解即可，完全不用考虑对象是如何被创建出来的。

        在实际项目中一个 Service 类可能依赖了很多其他的类，假如我们需要实例化这个 Service，你可能要每次都要搞清这个 Service 所有底层类的构造函数，这可能会把人逼疯。如果利用 IoC 的话，你只需要配置好，然后在需要的地方引用就行了，这大大增加了项目的可维护性且降低了开发难度。

在 Spring 中， IoC 容器是 Spring 用来实现 IoC 的载体， IoC 容器实际上就是个 Map（key，value），Map 中存放的是各种对象。

        Spring 时代我们一般通过 XML 文件来配置 Bean，后来开发人员觉得 XML 文件来配置不太好，于是 SpringBoot 注解配置就慢慢开始流行起来。

* * *

著作权归JavaGuide(javaguide.cn)所有基于MIT协议原文链接：https://javaguide.cn/system-design/framework/spring/spring-knowledge-and-questions-summary.html

       **DI：DI—Dependency** Injection，即“依赖注入”：**组件之间依赖关系由容器在运行期决定**，形象的说，即由容器动态的将某个依赖关系注入到组件之中。依赖注入的目的并非为软件系统带来更多功能，而是为了提升组件重用的频率，并为系统搭建一个灵活、可扩展的平台。通过依赖注入机制，我们只需要通过简单的配置，而无需任何代码就可指定目标需要的资源，完成自身的业务逻辑，而不需要关心具体的资源来自何处，由谁实现。



        ioc容器：实际上就是个map（key，value），⾥⾯存的是各种对象（在xml⾥配置的bean节点、@repository、@service、@controller、@component），在项⽬启动的时候会读取配置⽂件⾥⾯的bean节点，根据全限定类名使⽤反射创建对象放到map⾥、扫描到打上上述注解的类还是通过反射创建对象放到map⾥。这个时候map⾥就有各种对象了，接下来我们在代码⾥需要⽤到⾥⾯的对象时，再通过DI注⼊（autowired、resource等注解，xml⾥bean节点内的ref属性，项⽬启动的时候会读取xml节点ref属性根据id注⼊，也会扫描这些注解，根据类型或id注⼊；id就是对象名）。
        控制反转：没有引⼊IOC容器之前，对象A依赖于对象B，那么对象A在初始化或者运⾏到某⼀点的时候，⾃⼰必须主动去创建对象B或者使⽤已经创建的对象B。⽆论是创建还是使⽤对象B，控制权都在⾃⼰⼿上。引⼊IOC容器之后，对象A与对象B之间失去了直接联系，当对象A运⾏到需要对象B的时候，IOC容器会主动创建⼀个对象B注⼊到对象A需要的地⽅。通过前后的对⽐，不难看出来：对象A获得依赖对象B的过程,由主动⾏为变为了被动⾏为，控制权颠倒过来了，这就是“控制反转”这个名称的由来。全部对象的控制权全部上缴给“第三⽅”IOC容器，所以，IOC容器成了整个系统的关键核⼼，它起到了⼀种类似“粘合剂”的作⽤，把系统中的所有对象粘合在⼀起发挥作⽤，如果没有这个“粘合剂”，对象与对象之间会彼此失去联系，这就是有⼈把IOC容器⽐喻成“粘合剂”的由来。
        依赖注⼊： “获得依赖对象的过程被反转了”。控制被反转之后，获得依赖对象的过程由⾃身管理变为了由IOC容器主动注⼊。依赖注⼊是实现IOC的⽅法，就是由IOC容器在运⾏期间，动态地将某种依赖关系注⼊到对象
之中。





### 什么是依赖注入？可以通过多少种方式完成依赖注入？

        在依赖注入中，您不必创建对象，但必须描述如何创建它们。您不是直接在代码中将组件和服务连接在一起，而是描述配置文件中哪些组件需要哪些服务。由 IoC 容器将它们装配在一起。

        通常，依赖注入可以通过三种方式完成，即：

* 构造函数注入
* setter 注入
* 接口注入

        在 Spring Framework 中，仅使用构造函数和 setter 注入。

### 区分 BeanFactory 和 ApplicationContext？

BeanFactory：
        Spring 最顶层的接口,实现了 Spring 容器的最基础的一些功能, 调用起来比较麻烦, 一般面向 Spring 自身使用BeanFactory 在启动的时候不会去实例化 Bean，从容器中拿 Bean 的时候才会去实例化
ApplicationContext：
        是 BeanFactory 的子接口,扩展了其功能, 一般面向程序员身使用 ApplicationContext 在启动的时候就把所有的 Bean 全部实例化了

        BeanFactory是Spring中⾮常核⼼的组件，表示Bean⼯⼚，可以⽣成Bean，维护Bean，⽽ApplicationContext继承了BeanFactory，所以ApplicationContext拥有BeanFactory所有的特点，也是⼀个Bean⼯⼚，但是ApplicationContext除开继承了BeanFactory之外，还继承了诸如EnvironmentCapable、MessageSource、ApplicationEventPublisher等接⼝，从⽽
ApplicationContext还有获取系统环境变量、国际化、事件发布等功能，这是BeanFactory所不具备的

| BeanFactory   | ApplicationContext |
|:-------------:|:------------------:|
| 它使用懒加载        | 它使用即时加载            |
| 它使用语法显式提供资源对象 | 它自己创建和管理资源对象       |
| 不支持国际化        | 支持国际化              |
| 不支持基于依赖的注解    | 支持基于依赖的注解          |

        BeanFactory和ApplicationContext的优缺点分析：

        BeanFactory的优缺点：

* 优点：应用启动的时候占用资源很少，对资源要求较高的应用，比较有优势；
* 缺点：运行速度会相对来说慢一些。而且有可能会出现空指针异常的错误，而且通过Bean工厂创建的Bean生命周期会简单一些。

        ApplicationContext的优缺点：

* 优点：所有的Bean在启动的时候都进行了加载，系统运行的速度快；在系统启动的时候，可以发现系统中的配置问题。
* 缺点：把费时的操作放到系统启动中完成，所有的对象都可以预加载，缺点就是内存占用较大。
  
  

### 区分构造函数注入和 setter 注入

| 构造函数注入         | setter 注入     |
|:--------------:|:-------------:|
| 没有部分注入         | 有部分注入         |
| 不会覆盖 setter 属性 | 会覆盖 setter 属性 |
| 任意修改都会创建一个新实例  | 任意修改不会创建一个新实例 |
| 适用于设置很多属性      | 适用于设置少量属性     |



### spring 提供了哪些配置方式？

* 基于 xml 配置

bean 所需的依赖项和服务在 XML 格式的配置文件中指定。这些配置文件通常包含许多 bean 定义和特定于应用程序的配置选项。它们通常以 bean 标签开头。例如：

```java
<bean id="studentbean" class="org.edureka.firstSpring.StudentBean">
 <property name="name" value="Edureka"></property>
</bean>
```

* 基于注解配置

您可以通过在相关的类，方法或字段声明上使用注解，将 bean 配置为组件类本身，而不是使用 XML 来描述 bean 装配。默认情况下，Spring 容器中未打开注解装配。因此，您需要在使用它之前在 Spring 配置文件中启用它。例如：

```xml
<beans>
<context:annotation-config/>
<!-- bean definitions go here -->
</beans>
```

* 基于 Java API 配置

Spring 的 Java 配置是通过使用 @Bean 和 @Configuration 来实现。

1. @Bean 注解扮演与 `<bean />` 元素相同的角色。
2. @Configuration 类允许通过简单地调用同一个类中的其他 @Bean 方法来定义 bean 间依赖关系。

例如：

```java
@Configuration
public class StudentConfig {
    @Bean
    public StudentBean myStudent() {
        return new StudentBean();
    }
}
```

----

## AOP

---

### 什么是 AOP？

        AOP(Aspect-Oriented Programming), 即 **面向切面编程**, 它与 OOP( Object-Oriented Programming, 面向对象编程) 相辅相成, 提供了与 OOP 不同的抽象软件结构的视角. 在 OOP 中, 我们以类(class)作为我们的基本单元, 而 AOP 中的基本单元是 **Aspect(切面)**



### AOP 有哪些实现方式？

        实现 AOP 的技术，主要分为两大类：

* 静态代理 - 指使用 AOP 框架提供的命令进行编译，从而在编译阶段就可生成 AOP 代理类，因此也称为编译时增强；
  * 编译时编织（特殊编译器实现）
  * 类加载时编织（特殊的类加载器实现）。
* 动态代理 - 在运行时在内存中“临时”生成 AOP 动态代理类，因此也被称为运行时增强。
  * `JDK` 动态代理：通过反射来接收被代理的类，并且要求被代理的类必须实现一个接口 。JDK 动态代理的核心是 InvocationHandler 接口和 Proxy 类 。
  * `CGLIB`动态代理： 如果目标类没有实现接口，那么 `Spring AOP` 会选择使用 `CGLIB` 来动态代理目标类 。`CGLIB` （ Code Generation Library ），是一个代码生成的类库，可以在运行时动态的生成某个类的子类，注意， `CGLIB` 是通过继承的方式做的动态代理，因此如果某个类被标记为 `final` ，那么它是无法使用 `CGLIB` 做动态代理的。
    
    

### Spring AOP and AspectJ AOP 有什么区别？

        Spring AOP 基于动态代理方式实现；AspectJ 基于静态代理方式实现。 Spring AOP 仅支持方法级别的 PointCut；提供了完全的 AOP 支持，它还支持属性级别的 PointCut。



---

## DI

---





---

## Spring注解

---

### 将一个类声明为Spring的 bean 的注解有哪些?

我们一般使用 @Autowired 注解自动装配 bean，要想把类标识成可用于 @Autowired 注解自动装配的 bean 的类,采用以下注解可实现：

* @Component ：通用的注解，可标注任意类为 Spring 组件。如果一个Bean不知道属于哪个层，可以使用@Component 注解标注。 8 @Repository : 对应持久层即 Dao 层，主要用于数据库相关操作。
* @Service : 对应服务层，主要涉及一些复杂的逻辑，需要用到 Dao层。
* @Controller : 对应 Spring MVC 控制层，主要用户接受用户请求并调用 Service 层返回数据给前端页面。
  
  

### Autowired和Resource关键字的区别？

@Resource
        只能放在属性上，表示先按照属性名匹配 IOC 容器中对象 id 给属性注入值若没有成功，会继续根据当前属性的类型匹配 IOC 容器中同类型对象来注入值
若指定了 name 属性@Resource(name = "对象 id")，则只能按照对象 id 注入值。
@Autowird
        放在属性上：表示先按照类型给属性注入值如果 IOC 容器中存在多个与属性同类型的对象，则会按照属性名注入值也可以配合@Qualifier("IOC 容器中对象 id")注解直接按照名称注入值。
        放在方法上：表示自动执行当前方法，如果方法有参数，会自动从 IOC 容器中寻找同类型的对象给参数传值也可以在参数上添加@Qualifier("IOC 容器中对象 id")注解按照名称寻找对象给参数传值。
@Qualifier 使用场景：
        @Qualifier("IOC 容器中对象 id")可以配合@Autowird 一起使用, 表示根据指定的 id 在 Spring 容器中匹配
对象



### 事务注解的本质是什么？

        @Transactional 这个注解仅仅是一些（和事务相关的）元数据，在运行时被事务基础设施读取消
费，并使用这些元数据来配置bean的事务行为。 大致来说具有两方面功能，一是表明该方法要参
与事务，二是配置相关属性来定制事务的参与方式和运行行为
        声明式事务主要是得益于Spring AOP。使用一个事务拦截器，在方法调用的前后/周围进行事务性
增强（advice），来驱动事务完成。
        @Transactional注解既可以标注在类上，也可以标注在方法上。当在类上时，默认应用到类里的所
有方法。如果此时方法上也标注了，则方法上的优先级高。 另外注意方法一定要是public的。



### Spring 的常用注解(必会)

1. @Component(任何层)@Controller@Service@Repository（dao）: 用于实例化对象
2. @Scope : 设置 Spring 对象的作用域
3. @PostConstruct @PreDestroy : 用于设置 Spring 创建对象在对象创建之后和销毁之前要执行的方法
4. @Value: 简单属性的依赖注入
   武汉黑马程序员
   41
5. @Autowired: 对象属性的依赖注入
6. @Qualifier: 要和@Autowired 联合使用，代表在按照类型匹配的基础上，再按照名称匹配。
7. @Resource 按照属性名称依赖注入
8. @ComponentScan: 组件扫描
9. @Bean: 表在方法上,用于将方法的返回值对象放入容器
10. @PropertySource: 用于引入其它的 properties 配置文件
11. @Import: 在一个配置类中导入其它配置类的内容
12. @Configuration: 被此注解标注的类,会被 Spring 认为是配置类。Spring 在启动的时候会自动扫描并加
    载所有配置类，然后将配置
    类中 bean 放入容器
13. @Transactional 此注解可以标在类上，也可以表在方法上，表示当前类中的方法具有事务管理功能。
    
    

---

## Spring Bean

---

### 什么是 Spring Bean？

        简单来说，Bean 代指的就是那些被 IoC 容器所管理的对象。

我们需要告诉 IoC 容器帮助我们管理哪些对象，这个是通过配置元数据来定义的。配置元数据可以是 XML 文件、注解或者 Java 配置类。

```xml
<!-- Constructor-arg with 'value' attribute -->
<bean id="..." class="...">
   <constructor-arg value="..."/>
</bean>

```

下图简单地展示了 IoC 容器如何使用配置元数据来管理对象。

![062b422bd7ac4d53afd28fb74b2bc94d](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\062b422bd7ac4d53afd28fb74b2bc94d.png)

### 什么是 spring 的内部 bean？

只有将 bean 用作另一个 bean 的属性时，才能将 bean 声明为内部 bean。为了定义 bean，Spring 的基于 XML 的配置元数据在 `<property>` 或 `<constructor-arg>` 中提供了 `<bean>` 元素的使用。内部 bean 总是匿名的，它们总是作为原型。

例如，假设我们有一个 Student 类，其中引用了 Person 类。这里我们将只创建一个 Person 类实例并在 Student 中使用它。

Student.java

```java
public class Student {
    private Person person;
    //Setters and Getters
}
public class Person {
    private String name;
    private String address;
    //Setters and Getters
}
```

bean.xml

```xml
<bean id=“StudentBean" class="com.edureka.Student">
    <property name="person">
        <!--This is inner bean -->
        <bean class="com.edureka.Person">
            <property name="name" value=“Scott"></property>
            <property name="address" value=“Bangalore"></property>
        </bean>
    </property>
</bean>
```



### Spring 中的 bean 的作用域有哪些?

* singleton : 唯一 bean 实例，Spring 中的 bean 默认都是单例的。
* prototype : 每次请求都会创建一个新的 bean 实例。
* request : 每一次HTTP请求都会产生一个新的bean，该bean仅在当前HTTP request内有效。
* session : ：在一个HTTP Session中，一个Bean定义对应一个实例。该作用域仅在基于web的Spring ApplicationContext情形下有效。
* global-session： 全局session作用域，仅仅在基于portlet的web应用中才有意义，Spring5已经没有了。Portlet是能够生成语义代码(例如：HTML)片段的小型Java Web插件。它们基于portlet容器，可以像servlet一样处理HTTP请求。但是，与 servlet 不同，每个 portlet 都有不同的会话
  
  

### spring 支持几种 bean scope？

Spring bean 支持 5 种 scope：

* **Singleton** - 每个 Spring IoC 容器仅有一个单实例。
* **Prototype** - 每次请求都会产生一个新的实例。
* **Request** - 每一次 HTTP 请求都会产生一个新的实例，并且该 bean 仅在当前 HTTP 请求内有效。
* **Session** - 每一次 HTTP 请求都会产生一个新的 bean，同时该 bean 仅在当前 HTTP session 内有效。
* **Global-session** - 类似于标准的 HTTP Session 作用域，不过它仅仅在基于 portlet 的 web 应用中才有意义。Portlet 规范定义了全局 Session 的概念，它被所有构成某个 portlet web 应用的各种不同的 portlet 所共享。在 global session 作用域中定义的 bean 被限定于全局 portlet Session 的生命周期范围内。如果你在 web 中使用 global session 作用域来标识 bean，那么 web 会自动当成 session 类型来使用。

仅当用户使用支持 Web 的 ApplicationContext 时，最后三个才可用。



### Spring 中的 bean 生命周期?

        Bean的生命周期是由容器来管理的。主要在创建和销毁两个时期。

![1583675090641_51](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\1583675090641_51.png)

**创建过程**

        1，实例化bean对象，以及设置bean属性； 

        2，如果通过Aware接口声明了依赖关系，则会注入Bean对容器基础设施层面的依赖，Aware接口是为了感知到自身的一些属性。容器管理的Bean一般不需要知道容器的状态和直接使用容器。但是在某些情况下是需要在Bean中对IOC容器进行操作的。这时候需要在bean中设置对容器的感知。SpringIOC容器也提供了该功能，它是通过特定的Aware接口来完成的。 比如BeanNameAware接口，可以知道自己在容器中的名字。 如果这个Bean已经实现了BeanFactoryAware接口，可以用这个方式来获取其它Bean。 （如果Bean实现了BeanNameAware接口，调用setBeanName()方法，传入Bean的名字。 如果Bean实现了BeanClassLoaderAware接口，调用setBeanClassLoader()方法，传入ClassLoader对象的实例。 如果Bean实现了BeanFactoryAware接口，调用setBeanFactory()方法，传入BeanFactory对象的实例。） 

        3，紧接着会调用BeanPostProcess的前置初始化方法postProcessBeforeInitialization，主要作用是在Spring完成实例化之后，初始化之前，对Spring容器实例化的Bean添加自定义的处理逻辑。有点类似于AOP。 

        4，如果实现了BeanFactoryPostProcessor接口的afterPropertiesSet方法，做一些属性被设定后的自定义的事情。 

        5，调用Bean自身定义的init方法，去做一些初始化相关的工作。 

        6，调用BeanPostProcess的后置初始化方法，postProcessAfterInitialization去做一些bean初始化之后的自定义工作。 

        7，完成以上创建之后就可以在应用里使用这个Bean了。

**销毁过程**

        当Bean不再用到，便要销毁 1，若实现了DisposableBean接口，则会调用destroy方法； 2，若配置了destry-method属性，则会调用其配置的销毁方法；

**总结**

主要把握创建过程和销毁过程这两个大的方面； 创建过程：首先实例化Bean，并设置Bean的属性，根据其实现的Aware接口（主要是BeanFactoryAware接口，BeanFactoryAware，ApplicationContextAware）设置依赖信息， 接下来调用BeanPostProcess的postProcessBeforeInitialization方法，完成initial前的自定义逻辑；afterPropertiesSet方法做一些属性被设定后的自定义的事情;调用Bean自身定义的init方法，去做一些初始化相关的工作;然后再调用postProcessAfterInitialization去做一些bean初始化之后的自定义工作。这四个方法的调用有点类似AOP。 此时，Bean初始化完成，可以使用这个Bean了。 销毁过程：如果实现了DisposableBean的destroy方法，则调用它，如果实现了自定义的销毁方法，则调用之。

### Spring中出现同名bean怎么办？

* 同一个配置文件内同名的Bean，以最上面定义的为准
* 不同配置文件中存在同名Bean，后解析的配置文件会覆盖先解析的配置文件
* 同文件中ComponentScan和@Bean出现同名Bean。同文件下@Bean的会生效，@ComponentScan扫描进来不会生效。通过@ComponentScan扫描进来的优先级是最低的，原因就是它扫描进来的Bean定义是最先被注册的~
  
  

### Spring 中的单例 bean 的线程安全问题？

        当多个用户同时请求一个服务时，容器会给每一个请求分配一个线程，这时多个线程会并发执行该请求对应的业务逻辑（成员方法），此时就要注意了，如果该处理逻辑中有对单例状态的修改（体现为该单例的成员属性），则必须考虑线程同步问题。 **线程安全问题都是由全局变量及静态变量引起的。** 若每个线程中对全局变量、静态变量只有读操作，而无写操作，一般来说，这个全局变量是线程安全的；若有多个线程同时执行写操作，一般都需要考虑线程同步，否则就可能影响线程安全.

**无状态bean和有状态bean**

* 有状态就是有数据存储功能。有状态对象(Stateful Bean)，就是有实例变量的对象，可以保存数据，是非线程安全的。在不同方法调用间不保留任何状态。
* 无状态就是一次操作，不能保存数据。无状态对象(Stateless Bean)，就是没有实例变量的对象 .不能保存数据，是不变类，是线程安全的。

        在spring中无状态的Bean适合用不变模式，就是单例模式，这样可以共享实例提高性能。有状态的Bean在多线程环境下不安全，适合用Prototype原型模式。 Spring使用ThreadLocal解决线程安全问题。如果你的Bean有多种状态的话（比如 View Model 对象），就需要自行保证线程安全 。



---

## Spring事务

---

### Spring中的事务是如何实现的

1. Spring事务底层是基于数据库事务和AOP机制的
2. ⾸先对于使⽤了@Transactional注解的Bean，Spring会创建⼀个代理对象作为Bean
3. 当调⽤代理对象的⽅法时，会先判断该⽅法上是否加了@Transactional注解
4. 如果加了，那么则利⽤事务管理器创建⼀个数据库连接
5. 并且修改数据库连接的autocommit属性为false，禁⽌此连接的⾃动提交，这是实现Spring事务⾮
   常重要的⼀步
6. 然后执⾏当前⽅法，⽅法中会执⾏sql
7. 执⾏完当前⽅法后，如果没有出现异常就直接提交事务
8. 如果出现了异常，并且这个异常是需要回滚的就会回滚事务，否则仍然提交事务
9. Spring事务的隔离级别对应的就是数据库的隔离级别
10. Spring事务的传播机制是Spring事务⾃⼰实现的，也是Spring事务中最复杂的
11. Spring事务的传播机制是基于数据库连接来做的，⼀个数据库连接⼀个事务，如果传播机制配置为
    需要新开⼀个事务，那么实际上就是先建⽴⼀个数据库连接，在此新数据库连接上执⾏sql
    
    

### Spring中什么时候@Transactional会失效?

因为Spring事务是基于代理来实现的，所以某个加了@Transactional的⽅法只有是被代理对象调⽤时，
那么这个注解才会⽣效，所以如果是被代理对象来调⽤这个⽅法，那么@Transactional是不会失效的。
同时如果某个⽅法是private的，那么@Transactional也会失效，因为底层cglib是基于⽗⼦类来实现
的，⼦类是不能重载⽗类的private⽅法的，所以⽆法很好的利⽤代理，也会导致@Transactianal失效



### Spring 事务实现方式有哪些？

* 编程式事务管理：这意味着你可以通过编程的方式管理事务，这种方式带来了很大的灵活性，但很难维护。
* 声明式事务管理：这种方式意味着你可以将事务管理和业务代码分离。你只需要通过注解或者XML配置管理事务。
  
  

### Spring框架的事务管理有哪些优点？

* 它提供了跨不同事务api（如JTA、JDBC、Hibernate、JPA和JDO）的一致编程模型。

* 它为编程事务管理提供了比JTA等许多复杂事务API更简单的API。

* 它支持声明式事务管理。

* 它很好地集成了Spring的各种数据访问抽象。
  
  

### spring事务定义的传播规则

* PROPAGATION_REQUIRED: 支持当前事务，如果当前没有事务，就新建一个事务。这是最常见的选择。
* PROPAGATION_SUPPORTS: 支持当前事务，如果当前没有事务，就以非事务方式执行。
* PROPAGATION_MANDATORY: 支持当前事务，如果当前没有事务，就抛出异常。
* PROPAGATION_REQUIRES_NEW: 新建事务，如果当前存在事务，把当前事务挂起。
* PROPAGATION_NOT_SUPPORTED: 以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。
* PROPAGATION_NEVER: 以非事务方式执行，如果当前存在事务，则抛出异常。
* PROPAGATION_NESTED:如果当前存在事务，则在嵌套事务内执行。如果当前没有事务，则进行与PROPAGATION_REQUIRED类似的操作。
