# Java开发规范


> > > > > > > > 
> > > > > > > >
> > > > > > > > 
> > > > >
> > > > > 
> > > >
> > > > > > > >


>>> Less coding, More thinking!!!

## 基本类型

**1、[<font face='黑体' color='yellow'>推荐</font>]在代码中使用魔鬼数字（没有具体含义的数字、字符串）会使代码变得难以理解，应该将数字或字符串定义成有名称有含义的常量。**

- 说明 魔鬼数字不仅不好理解，而且代码中出现多处相同的数字，修改起来也很不方便。
- 将数字定义为常量的最终目的是为了使代码更容易理解，所以并不是只要将数字定义为常量就不是魔鬼数字了。如果常量的名称没有意义，无法帮助理解代码，同样是一种魔鬼数字。
- 在个别情况下，将数字定义为常量反而会导致代码更难以理解，此时就不应该强求将数字定义为常量。



## 函数





## 集合约束





## 泛型



## Java I/O

**1、[<font face='黑体' color='red'>强制</font>] 当使用外部资源（网络I/O、数据库连接、文件流等），请使用jdk1.7提供的try-with-resource处理机制来自动关闭资源，外部对象的句柄必须实现了AutoCloseable接口。**

> > - 说明 传统关闭资源方式
> >
> >   ```java
> >   InputStream inputStream = null;
> >   try {
> >   	inputStream = new FileInputStream(new File("test"));
> >       // 处理InputStream流    
> >   } catch (IOException e) {
> >       e.printStackTrace();
> >   } finally {
> >       if (null != inputStream) {
> >           try {
> >               inputStream.close();            
> >           } catch(IOException e) {
> >               e.printStackTrace();
> >           }
> >       }
> >   }
> >   ```
> >
> >   这种关闭资源方式存在三种问题：
> >
> >   - 如果不显示关闭外部资源，则有可能导致外部资源泄露。
> >   - 显示关闭外部资源过程繁琐，需要写大量模板代码
> >   - 不符合面向对象编程思想，当外部资源使用完毕后，应该由外部资源句柄自动关闭连接，这样更加符合面向对象编程理念。

- 使用try-with-resource自动关闭资源

  ```java
  try (InputStream inputStream = new FileInputStream(new File("test"));
      BufferedReader reader = new BufferedReader(new InputStreamReader(inputStream, "utf-8"))) {
      // 处理输入流
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

- 异常抑制：这是try-with-resource涉及到的另一个知识点，当对外部资源进行处理时（读或写），遭遇到了异常，且在随后的关闭资源时，又遭遇到了异常，那么catch代码块捕捉到的将是在对外部资源进行处理时遭遇到的异常。而关闭资源时的异常将会被抑制，但是不丢弃，通过调用异常类的getSuppressed()方法提取出被抑制的异常。



## 多线程











> > > > > > > > 
> > > > > > > >
> > > > > > > > 
> > > > >
> > > > > 
> > > >
> > > > > > > 



