# SpringMVC

## 相关概念



### 什么是MVC？

        MVC英文是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计规范。本质上也是一种解耦。

![spring-springframework-mvc-4](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\spring-springframework-mvc-4.png)

* **Model**（模型）是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据。
* **View**（视图）是应用程序中处理数据显示的部分。通常视图是依据模型数据创建的。
* **Controller**（控制器）是应用程序中处理用户交互的部分。通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据。
  
  

### 什么是Spring MVC？

        Spring Web MVC 是一种基于Java 的实现了Web MVC 设计模式的请求驱动类型的轻量级Web 框架，即使用了MVC 架 构模式的思想，将 web 层进行职责解耦，基于请求驱动指的就是使用请求-响应模型，框架的目的就是帮助我们简化开 发，Spring Web MVC 也是要简化我们日常Web 开发的。

**相关特性如下**：

* 让我们能非常简单的设计出干净的Web 层和薄薄的Web 层；
* 进行更简洁的Web 层的开发；
* 天生与Spring 框架集成（如IoC 容器、AOP 等）；
* 提供强大的约定大于配置的契约式编程支持；
* 能简单的进行Web 层的单元测试；
* 支持灵活的URL 到页面控制器的映射；
* 非常容易与其他视图技术集成，如 Velocity、FreeMarker 等等，因为模型数据不放在特定的 API 里，而是放在一个 Model 里（Map 数据结构实现，因此很容易被其他框架使用）；
* 非常灵活的数据验证、格式化和数据绑定机制，能使用任何对象进行数据绑定，不必实现特定框架的API；
* 提供一套强大的JSP 标签库，简化JSP 开发；
* 支持灵活的本地化、主题等解析；
* 更加简单的异常处理；
* 对静态资源的支持；
* 支持Restful 风格。
  
  

### 说说你对Spring MVC的理解？

        Spring MVC 是 Spring 框架中的一个模块，用于开发基于 MVC（Model-View-Controller）架构的 Web 应用程序。它提供了一种结构化的方式来处理 HTTP 请求和响应，并将应用程序逻辑、数据模型和用户界面分离开来，以提高代码的可维护性和可扩展性。



### SpringMVC 主要组件(必会)

那么接下来就简单介绍一下 `DispatcherServlet` 和九大组件（按使用顺序排序的）：

| 组件                          | 说明                                                                                                                                                                                                                             |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DispatcherServlet           | Spring MVC 的核心组件，是请求的入口，负责协调各个组件工作                                                                                                                                                                                             |
| MultipartResolver           | 内容类型( `Content-Type` )为 `multipart/*` 的请求的解析器，例如解析处理文件上传的请求，便于获取参数信息以及上传的文件                                                                                                                                                    |
| HandlerMapping              | 请求的处理器匹配器，负责为请求找到合适的 `HandlerExecutionChain` 处理器执行链，包含处理器（`handler`）和拦截器们（`interceptors`）                                                                                                                                      |
| HandlerAdapter              | 处理器的适配器。因为处理器 `handler` 的类型是 Object 类型，需要有一个调用者来实现 `handler` 是怎么被执行。Spring 中的处理器的实现多变，比如用户处理器可以实现 Controller 接口、HttpRequestHandler 接口，也可以用 `@RequestMapping` 注解将方法作为一个处理器等，这就导致 Spring MVC 无法直接执行这个处理器。所以这里需要一个处理器适配器，由它去执行处理器 |
| HandlerExceptionResolver    | 处理器异常解析器，将处理器（ `handler` ）执行时发生的异常，解析( 转换 )成对应的 ModelAndView 结果                                                                                                                                                                |
| RequestToViewNameTranslator | 视图名称转换器，用于解析出请求的默认视图名                                                                                                                                                                                                          |
| LocaleResolver              | 本地化（国际化）解析器，提供国际化支持                                                                                                                                                                                                            |
| ThemeResolver               | 主题解析器，提供可设置应用整体样式风格的支持                                                                                                                                                                                                         |
| ViewResolver                | 视图解析器，根据视图名和国际化，获得最终的视图 View 对象                                                                                                                                                                                                |
| FlashMapManager             | FlashMap 管理器，负责重定向时，保存参数至临时存储（默认 Session）                                                                                                                                                                                      |

Spring MVC 对各个组件的职责划分的比较清晰。`DispatcherServlet` 负责协调，其他组件则各自做分内之事，互不干扰。





记住了下面这些组件，也就记住了 SpringMVC 的工作原理。

* **`DispatcherServlet`**：**核心的中央处理器**，负责接收请求、分发，并给予客户端响应。
* **`HandlerMapping`**：**处理器映射器**，根据 URL 去匹配查找能处理的 `Handler` ，并会将请求涉及到的拦截器和 `Handler` 一起封装。
* **`HandlerAdapter`**：**处理器适配器**，根据 `HandlerMapping` 找到的 `Handler` ，适配执行对应的 `Handler`；
* **`Handler`**：**请求处理器**，处理实际请求的处理器。
* **`ViewResolver`**：**视图解析器**，根据 `Handler` 返回的逻辑视图 / 视图，解析并渲染真正的视图，并传递给 `DispatcherServlet` 响应客户端
  
  

### Spring MVC 和 Struts2 的异同？

**入口**不同

* Spring MVC 的入门是一个 Servlet **控制器**。
* Struts2 入门是一个 Filter **过滤器**。

**配置映射**不同，

* Spring MVC 是基于**方法**开发，传递参数是通过**方法形参**，一般设置为**单例**。
* Struts2 是基于**类**开发，传递参数是通过**类的属性**，只能设计为**多例**。

**视图**不同

* Spring MVC 通过参数解析器是将 Request 对象内容进行解析成方法形参，将响应数据和页面封装成 **ModelAndView** 对象，最后又将模型数据通过 **Request** 对象传输到页面。其中，如果视图使用 JSP 时，默认使用 **JSTL** 。
* Struts2 采用**值栈**存储请求和响应的数据，通过 **OGNL** 存取数据。
  
  

### 在 SpringMVC 中文件上传的使用步骤是什么样的? 前台三要素是什么?(必会)

文件上传步骤:
1.加入文件上传需要的 commons-fileupload 包
2.配置文件上传解析器,springmvc 的配置文件的文件上传解析器的 id 属性必须为 multipartResolver
3.后端对应的接收文件的方法参数类型必须为 MultipartFile,参数名称必须与前端的 name 属性保持一致
文件上传前端三要素:
1.form 表单的提交方式必须为 post
2.enctype 属性需要修改为:multipart/form-data
3.必须有一个 type 属性为 file 的 input 标签,其中需要有一个 name 属性;如果需要上传多个文件需要添加
multiple 属性



### 统一异常处理怎么做？

推荐使用注解的方式统一异常处理，具体会使用到 `@ControllerAdvice` + `@ExceptionHandler` 这两个注解 。

```java
@ControllerAdvice
@ResponseBody
public class GlobalExceptionHandler {

    @ExceptionHandler(BaseException.class)
    public ResponseEntity<?> handleAppException(BaseException ex, HttpServletRequest request) {
      //......
    }

    @ExceptionHandler(value = ResourceNotFoundException.class)
    public ResponseEntity<ErrorReponse> handleResourceNotFoundException(ResourceNotFoundException ex, HttpServletRequest request) {
      //......
    }
}

```

这种异常处理方式下，会给所有或者指定的 `Controller` 织入异常处理的逻辑（AOP），当 `Controller` 中的方法抛出异常的时候，由被`@ExceptionHandler` 注解修饰的方法进行处理。

`ExceptionHandlerMethodResolver` 中 `getMappedMethod` 方法决定了异常具体被哪个被 `@ExceptionHandler` 注解修饰的方法处理异常。

```java
@Nullable
  private Method getMappedMethod(Class<? extends Throwable> exceptionType) {
    List<Class<? extends Throwable>> matches = new ArrayList<>();
    //找到可以处理的所有异常信息。mappedMethods 中存放了异常和处理异常的方法的对应关系
    for (Class<? extends Throwable> mappedException : this.mappedMethods.keySet()) {
      if (mappedException.isAssignableFrom(exceptionType)) {
        matches.add(mappedException);
      }
    }
    // 不为空说明有方法处理异常
    if (!matches.isEmpty()) {
      // 按照匹配程度从小到大排序
      matches.sort(new ExceptionDepthComparator(exceptionType));
      // 返回处理异常的方法
      return this.mappedMethods.get(matches.get(0));
    }
    else {
      return null;
    }
  }

```

从源代码看出：**`getMappedMethod()`会首先找到可以匹配处理异常的所有方法信息，然后对其进行从小到大的排序，最后取最小的那一个匹配的方法(即匹配度最高的那个)。**



---

## SpringMVC 工作原理

---

### Spring MVC ⼯作流程

![de6d2b213f112297298f3e223bf08f28](C:\Users\lenovo\Desktop\Study_Daily_Summary\Study%20daily%20summary%204月6日\图片\de6d2b213f112297298f3e223bf08f28.png)

**流程说明（重要）：**

1. 客户端（浏览器）发送请求， `DispatcherServlet`拦截请求。
2. `DispatcherServlet` 根据请求信息调用 `HandlerMapping` 。`HandlerMapping` 根据 URL 去匹配查找能处理的 `Handler`（也就是我们平常说的 `Controller` 控制器） ，并会将请求涉及到的拦截器和 `Handler` 一起封装。
3. `DispatcherServlet` 调用 `HandlerAdapter`适配器执行 `Handler` 。
4. `Handler` 完成对用户请求的处理后，会返回一个 `ModelAndView` 对象给`DispatcherServlet`，`ModelAndView` 顾名思义，包含了数据模型以及相应的视图的信息。`Model` 是返回的数据对象，`View` 是个逻辑上的 `View`。
5. `ViewResolver` 会根据逻辑 `View` 查找实际的 `View`。
6. `DispaterServlet` 把返回的 `Model` 传给 `View`（视图渲染）。
7. 把 `View` 返回给请求者（浏览器）
   
   

---

## SpringMVC拦截器

---



### 什么是SpringMVC拦截器以及如何使用它？

        Spring的处理程序映射机制包括处理程序拦截器，当你希望将特定功能应用于某些请求时，例如，检查用户主题时，这些拦截器非常有用。拦截器必须实现org.springframework.web.servlet包的HandlerInterceptor。此接口定义了三种方法：

* preHandle：在执行实际处理程序之前调用。
* postHandle：在执行完实际程序之后调用。
* afterCompletion：在完成请求后调用。
  
  

### 在 SpringMVC 中拦截器的使用步骤是什么样的?(必会)

1 定义拦截器类:
SpringMVC 为我们提供了拦截器规范的接口,创建一个类实现 HandlerInterceptor,重写接口中的抽象方法;
preHandle 方法：在调用处理器之前调用该方法，如果该方法返回 true 则请求继续向下进行，否则请求
不会继续向下进行,处理器也不会调用
postHandle 方法：在调用完处理器后调用该方法
afterCompletion 方法：在前端控制器渲染页面完成之后调用此方法
2 注册拦截器:
在 SpringMVC 核心配置文件中注册自定义的拦截器



```xml
<mvc:interceptors>
<mvc:interceptor>
<mvc:mapping path="拦截路径规则"/>
<mvc:exclude-mapping path="不拦截路径规则"/>
<bean class="自定义拦截器的类全限定名"/></mvc:interceptor></mvc:interceptors>
```

---

## SpringMVC注解

---



### SpringMVC 的常用注解(必会)

        @RequestMapping：用于处理请求 url 映射的注解，可用于类或方法上。用于类上，则表示类中的所有响应
请求的方法都是以该地址作为父路径。
        @RequestBody：注解实现接收 http 请求的 json 数据，将 json 转换为 java 对象。
        @ResponseBody：注解实现将 conreoller 方法返回对象转化为 json 对象响应给客户。
        @PathVariable 用户从 url 路径上获取指定参数，标注在参数前 @PathVariabel("要获取的参数名")。
        @RequestParam: 标注在方法参数之前，用于对传入的参数做一些限制，支持三个属性:

- value：默认属性，用于指定前端传入的参数名称
- required：用于指定此参数是否必传
- defaultValue：当参数为非必传参数且前端没有传入参数时，指定一个默认值

        @ControllerAdvice 标注在一个类上，表示该类是一个全局异常处理的类。

        @ExceptionHandler(Exception.class) 标注在异常处理类中的方法上，表示该方法可以处理的异常类型。

### @Controller 注解有什么用？

`@Controller` 注解标记一个类为 Spring Web MVC **控制器** Controller。Spring MVC 会将扫描到该注解的类，然后扫描这个类下面带有 `@RequestMapping` 注解的方法，根据注解信息，为这个方法生成一个对应的**处理器**对象，在上面的 HandlerMapping 和 HandlerAdapter组件中讲到过。

当然，除了添加 `@Controller` 注解这种方式以外，你还可以实现 Spring MVC 提供的 `Controller` 或者 `HttpRequestHandler` 接口，对应的实现类也会被作为一个**处理器**对象



### @RequestMapping 注解有什么用？

`@RequestMapping` 注解，在上面已经讲过了，配置**处理器**的 HTTP 请求方法，URI等信息，这样才能将请求和方法进行映射。这个注解可以作用于类上面，也可以作用于方法上面，在类上面一般是配置这个**控制器**的 URI 前缀

### @RestController 和 @Controller 有什么区别？

`@RestController` 注解，在 `@Controller` 基础上，增加了 `@ResponseBody` 注解，更加适合目前前后端分离的架构下，提供 Restful API ，返回例如 JSON 数据格式。当然，返回什么样的数据格式，根据客户端的 `ACCEPT` 请求头来决定。

### @RequestMapping 和 @GetMapping 注解的不同之处在哪里？

1. `@RequestMapping`：可注解在类和方法上；`@GetMapping` 仅可注册在方法上
2. `@RequestMapping`：可进行 GET、POST、PUT、DELETE 等请求方法；`@GetMapping` 是 `@RequestMapping` 的 GET 请求方法的特例，目的是为了提高清晰度。

### @RequestParam 和 @PathVariable 两个注解的区别

两个注解都用于方法参数，获取参数值的方式不同，`@RequestParam` 注解的参数从请求携带的参数中获取，而 `@PathVariable` 注解从请求的 URI 中获取

### 返回 JSON 格式使用什么注解？

可以使用 **`@ResponseBody`** 注解，或者使用包含 `@ResponseBody` 注解的 **`@RestController`** 注解。

当然，还是需要配合相应的支持 JSON 格式化的 HttpMessageConverter 实现类。例如，Spring MVC 默认使用 MappingJackson2HttpMessageConverter。

---

REST API
--------

---
