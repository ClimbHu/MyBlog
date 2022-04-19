[TOC]



# 练习题

## IO

### 填空

1. IO当中4个父类分别是(OutputStream ) (InputStream )  (Writer )  (Reader )

2. IO当中分类

   1. 按照数据流向分,可以分为( 输入 )流, ( 输出 )流,  以( 内存 )为参照物
   2. 按照数据类型分, 可以分为( 字节 )流,  ( 字符 )流.

3. 可以通过( "\n" ),  ( "\r") , ("\r\n")方式实现换行功能

4. 实现文件追加功能,应该使用FileOutputStream的哪个构造方法( FileOutputStream(File file,  boolean append)   )

5. 使用FileInputStream,    用while循环读取数据的时候,   我们判断读取到末尾的判断依据是( (readData = in.read()) != -1  )

6. 使用InputStream中的read() 方法的返回值代表什么意思? (返回 0 到 255 范围内的 int 字节值 )

7. 使用InputStream中的read(byte[] b) 方法的返回值代表什么意思? ( 读入的数据在数组中的长度 )

8. ```java 
   // 假设a.txt当中有一个字符串    "abcdef" 
   // 代码片段
   FileInputStream in = new FileInputStream("a.txt");
   byte[] bytes = new byte[4];
   readCount1 = in.read(bytes);
   // 请问 此时 bytes数组中的值是什么??  readCount1的值是几??
   abcd 4
   readCount2 = in.read(bytes);
   //  请问 此时 bytes数组中的值是什么??  readCount2的值是几??
   efcd 2
   
   ```

9. ```java
   //有个a.txt文件,里面有一行字符串abcdef
   FlieOutputStrem out = new FileOutputStream("a.txt")
   // 此时a.txt文件中是什么? 空
   // 创建之前,jvm会到操作系统看一下文件是否存在
   // 如果不存在,帮我们创建
   // 如果存在,覆盖,从头开始写
   out.write(97);
   // 此时a.txt文件中是什么? a
   out.close()
   ```

   

10. ```java 
    // a.txt中有字符串   "五五开卢本伟white"
    public static void main(String[] args){
        FileInputStream in = new FileInputStream("a.txt")
        FileOutputStream out1 = new FileOutputStream("b.txt")
        FileOutputStream out2 = new FileOutputStream("c.txt")
        copyFile(in , out1);
        copyFile(in , out2); 
        in.close();
        out1.close();
        out2.close();
    }
    
    
    public void copyFile(InputStream in, OutputStream out){
        int readCount;
        byte[] bytes = new byte[1024];
        while((readCount = in.read(bytes)) !=-1){
            out.write(bytes,0,readCount);
        }
    }
    // 请问,b.txt文件的内容是什么?? 五五开卢本伟white
    // 请问,c.txt文件中内容是什么?? 空
    
    ```

11. BufferedInputStream与BufferedOutputStream中默认缓冲区大小是(8kb)

12. BufferedWriter与BufferedReader中默认缓冲区大小是(16kb)

13. BufferedWriter中特有的方法是(  newLine()  )

14. BufferedReader中特有的方法是(  readLine()  )

15. 使用BufferedReader中特有的方法,使用while循环读取的时候,我们判断读取结束的依据是什么( (line = br.readLine()) != null )

16. ```java
    FileWirter out= new FileWirter("a.txt")
    out.write("哈哈哈")
    // 执行到这里 请问此时a.txt文件中的内容是什么?? 空
    out.flush();
    // 执行到这里 请问此时a.txt文件中的内容是什么?? 哈哈哈
    ```

17. 采用DataOutputStream先writeByte, 再writeInt, 读取的时候采用DataInputStream, 先使用( readByte )方法, 再使用( readInt )

18. System.out的默认输出设备是( 显示器 ), System.out是( 字节打印流 )类型

19. System.in的默认输入设备是( 键盘 ), System.in的是( 字节输入流 )类型

20. 序列化反序列化对象使用( ObjectOutputStream ) ,  ( ObjectInputStream ) 类, 对象所在的类必须实现( Serializeable ) 接口,才可以自动序列化所有的内容

21. ( tranisent )关键字可以让类中的属性不被序列化

22. | 类型       | 字节输出流           | 字节输入流          | 字符输出流         | 字符输入流        |
    | ---------- | -------------------- | ------------------- | ------------------ | ----------------- |
    | 抽象基类   | OutputStream         | InputStream         | Writer             | Reader            |
    | 文件相关的 | FileOutputStream     | FileInputStream     | FileWriter         | FileReader        |
    | 缓冲相关的 | BufferedOutputStream | BufferedInputStream | BufferedWriter     | BufferedReader    |
    | 转换相关的 |                      |                     | OutputStreamWriter | InputStreamReader |
    | 数据相关的 | DataOutputStream     | DataInputStream     |                    |                   |
    | 打印相关的 | PrintStream          |                     | PrintWriter        |                   |
    | 对象相关的 | ObjectOutputStream   | ObjectInputStream   |                    |                   |

    

### 选择

- 提供printLn()方法和print()方法的类是(A)

> A. PrintStream		B. System		C. InputStream		D. DataOutputStream

- 下列说法不正确的是(D)
  - A.  InputStream与OutputStream类通常用来处理字节流
  - B. Reader与Writer通常来处理字符流
  - C. Java中IO流的处理通常分为输入流和输出流2个部分
  - D. File类是输入/输出流的子类
- 与InputStream相对应的Java系统中的标准输入对象是(A)

> A. System.in		B. System.out		C. System.error		D. System.exit()

- InputStreamReader 类提供的功能是(D) 

> A. 数据校验		B.文本行计数		C. 压缩		D.将字节流变为字符流

- 如果打印流PrintWriter开启了自动刷新功能,下列使用哪个方法不会启动自动刷新(A)

> A . print()		B . printLn()		C. format()		D. printf()

### 简答

1. 为什么要close?

   释放系统资源

2. ```java
   try-with-resources 语法结构怎么写?有什么特点?
       
   try(资源,实现了AutoCloseable接口的类都能视作资源){
   	出了try代码块之后 ,资源会自动释放
   }catch{
   
   }
   
   使用try-with-resources的代码通常更清晰易读，因此使代码更易于管理，尤其是当我们处理许多try块时。
       
   跟传统try-catch有啥不一样?
   try-with-resources，系统会自动调用close()方法释放资源，不需要用户手动关闭    
   ```

3. 字符流的本质是什么?

   字节流+编码表

4. 常见编码表有哪些? 分别几个字节代表一个字符?

   GBK ：2个字节代表一个中文字符

   UTF-8 : 3个字节代表一个中文字符

5. 对于字符输出流, 为什么可以直接close文件中就有数据?

   会自动有刷新

6. 序列化流主要有什么作用?

   把对象数据转为二进制数据保存到外部设备

7. transient关键字有啥作用?

   可以让类中的属性不被序列化

8. serialVersionUID有啥作用?

   判断能否进行反序列化

   字节流中的serialVersionUID于本地相应实体类的serialVersionUID进行比较。如果相同说明是一致的，可以进行反序列化，否则会出现反序列化版本一致的异常，即是InvalidCastException。



## 多线程

### 填空

1. java多线程可以依靠( 继承Thread类 ) , ( 实现Runnable接口 ) , ( 实现Callable接口 ) 三种方式实现
2. java程序运行时,至少启动( 2 ) 个线程, 分别是( 垃圾回收线程 ) , ( main线程 ).
3. java采用( 抢占式 )线程的调度方式, 所以线程的执行是( 随机 )的.
4. 对于join方法
   - 谁等待?  ( join这行代码在哪个线程上执行,哪个线程等待 )
   - 等待谁? (等待的是调用join方法的这个线程 )
5. 通过( setDaemon  )API 把一个线程设置为守护线程.
6. 线程的优先级范围是(1) - ( 10 )
7. 获取当前线程对象的引用,使用哪个API ( currentThread  )
8. 线程的生命周期要经历5种状态 , 分别是( 新建 ) ，( 就绪 ) , ( 执行 ) , ( 阻塞 ) , ( 死亡 ),状态
9. 多线程产生数据安全问题的原因有3个,分别是
   - ( 多线程的运行环境 )
   - ( 多线程共享数据 )
   - ( 存在一个非原子操作  )
10. 什么是原子操作? ( 不可分割的操作 )
11. Object中提供的( wait ), ( notify ) , ( notifyAll ) 三个方法可以控制线程
12. 当前有3个线程处于阻塞状态, 此时执行notify方法将会唤醒其中 ( 一个 ) 线程
13. Executors中产生3种线程池,分别是
    - 带缓存的线程池( newCachedThreadPool  )
    - 固定数量的线程池( newFixedThreadPool  )
    - 固定1个数量的线程池( newSingleThreadExecutor  )
14. 关闭线程池可以采用哪两种方式?
    - ( shutdown )API,  特点是( 启动一次顺序关闭，执行以前提交的任务，但不接受新任务。 ) 
    - ( shutdownNow  )API, 特点是(  试图停止所有正在执行的活动任务，暂停处理正在等待的任务，并返回等待执行的任务列表。 )

### 选择

- 线程的启动方法是(B)

> A. run()		B. start()		C. begin()		D. accept() 

- 设置优先级的方法是(A)

> A. setPriority()		B. gerPriority()		C. getName()		D.setName()

- 下列(C) 关键字用来对对象加锁

> A. serialize		B. transient		C. synchronized		D. static

- 下面(A 父类或父类接口是无法实现多线程子类定义的?

> A. Serializable		B. Thread		C. Runnable		D. Callable

### 简答题

1. 什么是线程?什么是进程?两者什么关系?

   进程：正在运行的程序或软件。

   线程：进程中分多个子任务,每个子任务就是一个线程。

   关系：线程依赖于进程而存在,线程共享进程资源，进程可以有多个线程。

2. 什么是串行,并行,并发?

   串行

   - 一个任务接一个任务按顺序执行

   并行

   - 在同一时间点,多个任务同时执行

   并发

   - 在同一时间段内,多个任务同时执行

3. 什么是同步,异步?

   同步：本次调用能得到结果

   异步：本次调用不一定拿到结果

4. 启动线程是start方法不是run方法,这2个有什么区别?

   启动线程用start方法，通过对象.run去调用,作用就是普通方法调用,执行顺序是在main线程中按顺序依次执行的.run方法并没有去开启一个新的线程
   通过对象.

5. 守护线程的特点是什么?

   当正在运行的线程都是守护线程时，Java 虚拟机退出。

6. 为什么Runnable中的run方法会运行在子线程中?

   

7. 简述3种多线程实现方式的区别?

   继承Thread类：是单继承的

   实现Runnable接口：可以避免单继承局限但run()方法不能返回操作结果

   实现Callable接口：可以避免单继承局限且run()方法可以返回操作结果

8. 什么是死锁?怎么解决?

   2个或以上线程争抢资源而造成的互相等待的现象，可以再加一把锁或者更改加锁顺序

9. wait方法与sleep方法有什么区别?

   1. 所属不同：
      a. sleep定义在Thread类，静态方法
      b. wait定义在 Object类中，非静态方法

   2. 唤醒条件不同
      a. sleep: 休眠时间到
      b. wait: 在其他线程中，在同一个锁对象上，调用了notify或notifyAll方法

   3. 使用条件不同：
      a. sleep 没有任何前提条件
      b. wait(), 必须当前线程，持有锁对象，锁对象上调用wait()

   4. 休眠时，对锁对象的持有，不同：（最最核心的区别）
      a. 线程因为sleep方法而处于阻塞状态的时候，在阻塞的时候不会放弃对锁的持有
      b. 但是wait()方法，会在阻塞的时候，放弃锁对象持有

10. synchronized同步代码块中的锁对象是谁?同步方法中锁对象是谁?静态方法?

    同步代码块：任意的java对象

    同步方法：this

    静态方法：字节码文件对象

11. 为什么wait notify方法是定义在Object中 而不是在Thread中?

    因为每个对象都可以作为锁。

## 网络编程

### UDP

#### 填空

- UDP以( 无连接 ) 方式进行传输.

- UDP客户端步骤(B ), (C ), ( A), ( E)

  - > A. 发送数据报包到目的IP的目的端口(send方法)
    >
    > B. 创建UDP的socket对象
    >
    > C. 将要发送的数据封装到数据报包
    >
    > E. 释放资源

- UDP接收端步骤( B), (C ) , ( A), ( D) ( E)

  - > A . 接收数据报包(receive方法)
    >
    > B. 创建接收端的Socket对象
    >
    > C. 创建用于接收端的数据报包
    >
    > D. 解析数据报包中的数据
    >
    > E. 释放资源

- 通过( InetAddress.getName  )API获取InetAddress对象

- 通过( DatagramPacket(byte[] buf,  int offset, int length, InetAddress address, int port)    )构造方法创建用于发送的数据报包对象DatagramPacket对象

- 通过( DatagramPacket(byte[] buf,  int offset, int length)   )构造方法创建用于接收的数据报包对象

- 通过(  getData  )API获取数据报包中的信息 

#### 简答题

1. UDP协议什么特点?

   UDP无连接，不可靠的

2. 端口号可用范围?

   1024-65535

3. 先启动接收端还是发送端? 如果先启动发送端会报错吗?

   先启动接收端，先启动发送端不会报错但不合理

4. 端口号被占用会有什么异常?

   BindExecption

### TCP

#### 填空题

- TCP以( 有连接  ) 方式进行传输

- TCP客户端的步骤是( B )   ( C )    (  A)  ( D )   

  - > A. 从流中读写数据
    >
    > B. 创建客户端Socket对象
    >
    > C. 从Socket对象中获取输入输出流
    >
    > D .释放资源

- TCP服务端的步骤是( B)  ( C )   (D  )  ( E )   (A)

  - > A. 释放资源
    >
    > B. 创建服务端Socket对象(ServerSocket)
    >
    > C. 建立连接(accept)
    >
    > D. 从socket中获取输入输出流
    >
    > E. 从流中读取写入数据

#### 简答题

- TCP协议什么特点?

  TCP是面向连接的，可靠的

- 有1个服务端,多个客户端的时候怎么办?

  使用多线程

## 反射

### 选择题

- 编译java源文件产生的字节码文件的扩展名是什么( B )?

> A. java 		B. class 		C. html 		D. exe

- 下面关于Class类对象的实例化对象取得,错误的是( B )

> A. 利用Object类中的getClass方法
>
> B.利用Class类的构造方法取得
>
> ​     //构造方法私有，不能在外面new
>
> C.利用类.class方法取得
>
> D.通过Class.forName() 取得

- 下面的Class类中的方法( A ) 个可以取得指定类型中全部public方法的定义

> A. public Method \[] getMethods()
>
> B. public Field [] getFields()
>
> C. public Field [] getDeclaredFields()
>
> D. public Constructor [] getConsts()

### 填空

1. 忽略java语法检查使用哪个API (setAccessible)
2. 从.properties文件中获取相应Key对应的value,应该用哪个API ( getProperty)
3. 使用字节码文件对象(Class对象)可以直接实例化对象, 有一个前提条件是(有一个无参的构造方法  )

### 简答题

1. 类加载过程是什么?

   加载--连接--初始化

2. jvm规范中的类加载时机是哪些?

   - 创建类的实例(首次创建该类对象)
   - 访问类的静态变量(首次)
   - 调用类的静态方法(首次)
   - 使用反射方式来强制创建某个类或接口对应的java.lang.Class对象
   - 加载某个类的子类，会先触发父类的加载
   - 直接使用java.exe命令来运行某个主类，也就是执行了某个类的main()方法

3. 类加载器都有哪些?

   根类加载器

   扩展类加载器

   统类加载器/应用加载器

4. 双亲委派模型是什么?

   

5. 什么是反射技术?

   获取类运行时信息的一种技术.

6. 带declared跟不带的API有什么区别? 带s跟不带s的API有什么区别?

   不带declared只能获得public，带declared的能获取全部

   不带s的是获取指定成员方法，带s的是获取所有方法

7. 获取字节码文件对象的方式有哪三种?

   - 对象.getClass()
   - 类名.class
   - Class.forName(String classname)   是全类名

## 注解

### 选择题

- 下面哪个不属于java语言?（B）

> A. // 注释		B. -- 注释 		C. /** 注释 */ 		D. / * 注释*/

### 填空

- 定义注解的关键字是什么( @interface )

- 使用value作为注解的属性时,有一个前提条件是(  只能有一个  )
- 给注解设置默认值的关键字是(  default  )
- 注解的默认保留级别是( CLASS  )
- 想要把注解加到成员变量上, 应该使用( @Target )注解的( ElementType.FIELD )属性
- 判断是否使用了注解使用哪个API( isAnnotationPresent )
- 获取注解实例使用哪个API( getAnnotation )

### 简单题

1. @Target注解作用是啥?

   来确定注解可以作用的目标

2. @Retention注解作用是啥?

   来定义我们自己定义的注解的保留级别.

3. 注解的属性可以是哪些数据类型?
   java基本数据类型
   String类型
   Class类型
   枚举类型
   注解类型
   以及以上类型的数组形式

## GC(了解)

### 简答题

1. jvm运行时数据区怎样划分的?

   1. 哪些是线程私有的?
   2. 哪些是共享的?

2. 显式内存管理与隐式内存管理的特点?

   1. 显式的优点?
   2. 显式的缺点?
   3. 隐式的优点?
   4. 隐式的缺点?

3. 什么是内存泄漏?

4. 引用计数法思想是什么?

   - 弊端是什么?

5. 根搜索算法思想是什么?

   1. 哪些可以作为GC Roots?

6. 标记清除算法思想是什么?

   - 弊端是什么

7. 标记复制算法思想是什么?

   - 弊端是什么?

8. 标记整理算法思想是什么?

   - 弊端是什么?

9. 分代收集理论

   - 2个假说是什么?
   - 分代收集算法分为哪两个代?
   - 新生代分为哪些区域?
   - 什么时候新生代的对象被移动到老年代?
   - 新生代采用什么算法回收垃圾?
   - 老年代采用什么算法回收垃圾?

   

