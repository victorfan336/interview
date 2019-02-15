# Android-Interview

----------

# Java

## 基础

1. [什么是面向对象（OOP）？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_1)
2. [什么是多态？实现多态的机制是什么？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_2)
3. [接口（Interface）与抽象类（Abstract Class）的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_3)
4. [重写（Override）与重载（Overload）的区别?](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_4)
5. 父类的静态方法能否被子类重写？
6. 静态属性和静态方法是否可以被继承？是否可以被重写？为什么？
7. 什么是内部类？内部类、静态内部类、局部内部类和匿名内部类的区别及作用？
8. == 和 equals() 和 hashCode() 的区别？
9. Integer 和 int 之间的区别？
10. String 转换成 Integer 的方式及原理？
11. 自动装箱实现原理？类型转换实现原理？
12. 对 String 的了解？
13. String 为什么要设计成不可变的？
14. [final、finally 和 finalize 的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_14)
15. [static 关键字有什么作用？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_15)
16. 列举 Java 的集合以及集合之间的继承关系?
17. List、Set、Map 的区别？
18. [ArrayList、LinkedList 的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_18)
19. HashMap，HashTable，ConcurrentHashMap 实现原理以及区别？
20. HashSet 与 HashMap 怎么判断集合元素重复？
21. String、StringBuffer、StringBuilder 之间的区别？
22. [什么是序列化？怎么实现？有哪些方式？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_22)
23. 对反射的了解？
24. 对注解的了解？
25. 对依赖注入的了解？
26. 对泛型的了解？
27. 泛型中 extends 和 super 的区别？
28. 对 Java 的异常体系的了解？
29. 对解析与分派的了解？
30. 静态代理和动态代理的区别？有什么场景使用？
	https://www.cnblogs.com/gonjan-blog/p/6685611.html
31. 谈谈对 Java 状态机理解？
	https://www.cnblogs.com/pony1223/p/7518226.html

## 线程与并发
  
1. 线程和进程的区别？
2. 开启线程的三种方式  
   1) new Thread().start();  
   2) class MyRunnable immplement Runnable{}  
      new Thread(new MyRunnable).start();  
   3) hanlder.post(new Runnable() {});  
   
3. 如何正确的结束一个Thread?  
	设置结束标志位，再调用thread.interrupt();  
   
4. Thread 与 Runnable 的区别？   
	runnable只是一个接口而已，不会开启一个线程；而thread是一个线程，实现了Runnable接口，通过传入一个runnable实例可以在线程中启动。   
   
5. run() 与 start() 方法的区别？   
	start : 用start方法来启动线程，真正实现了多线程运行，这时无需等待run方法体代码执行完毕而直接继续执行下面的代码。通过调用Thread类的start()方法来启动一个线程，这时此线程处于就绪（可运行）状态，并没有运行，一旦得到cpu时间片，就开始执行run()方法，这里方法 run()称为线程体，它包含了要执行的这个线程的内容，Run方法运行结束，此线程随即终止。   
	run : run()方法只是类的一个普通方法而已，如果直接调用Run方法，程序中依然只有主线程这一个线程，其程序执行路径还是只有一条，还是要顺序执行，还是要等待run方法体执行完毕后才可继续执行下面的代码，这样就没有达到写线程的目的。  
     
6. sleep() 与 wait() 方法的区别？      
	1、这两个方法来自不同的类，sleep来自Thread类，wait 来自Object类。    
	2、最主要是sleep方法没有释放锁，而wait方法释放了锁，使其他线程可以使用同步控制块或者方法。sleep不出让系统资源；wait是进入线程等待池等待，出让系统资源，其他线程可以占用CPU。   
	3、使用范围：wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用  
	4、sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常。   
   
7. wait 与 notify 关键字的区别？    
   
8. synchronized 关键字的用法、作用及实现原理？   
	synchronized关键字最主要有以下3种应用方式   
	修饰实例方法,对当前实例加锁，进入同步代码前要获得当前实例的锁   
	修饰静态方法,对当前类对象(当前类的Class对象)加锁，进入同步代码前要获得当前类对象的锁    
	修饰代码块,对代码块{}中的内容加锁，进入同步代码块前要获得给定对象的锁。   
   
9. volatile 关键字的用法、作用及实现原理？   
	作用：用于保持内存可见性和防止指令重排序，    
	可见性实现：（1）修改volatile变量时会强制将修改后的值刷新的主内存中。 （2）修改volatile变量后会导致其他线程工作内存中对应的变量值失效。因此，再读取该变量值的时候就需要重新从读取主内存中的值。  
	重排序：使用volatile的变量在读和写的时候，会在读和写操作的前后加入内存屏障，防止指令重排序。    
    
10. transient 关键字的用法、作用及实现原理？ 
	java 的transient关键字为我们提供了便利，你只需要实现Serilizable接口，将不需要序列化的属性前添加关键字transient，序列化对象的时候，这个属性就不会序列化到指定的目的地中。     
    
11. ReentrantLock、synchronized、volatile 之间的区别？     
	synchronized的使用可以保证代码具有 原子性（atomicity）和 可见性（visibility）。     
	volatile则可以保证单次读或写操作的原子性和可见性。 
	ReentrantLock 类实现了 Lock ，它拥有与 synchronized 相同的并发性和内存语义，但是添加了类似锁投票、定时锁等候和可中断锁等候的一些特性。此外，它还提供了在激烈争用情况下更佳的性能。   
	在确实需要一些 synchronized 所没有的特性的时候，比如时间锁等候、可中断锁等候、无块结构锁、多个条件变量或者锁投票。 ReentrantLock 还具有可伸缩性的好处，应当在高度争用的情况下使用它。   
   
12. 什么是线程池，如何使用?   
	线程池就是提前创建若干个线程，如果有任务需要处理，线程池里的线程就会处理任务，处理完之后线程并不会被销毁，而是等待下一个任务。由于创建和销毁线程都是消耗系统资源的，所以当你想要频繁的创建和销毁线程的时候就可以考虑使用线程池来提升系统的性能。    
	Java中有四个比较常用的线程池，分别是FixedThreadPool，SingleThreadExecutor，CachedThreadPool、ScheduledThreadPoolExecutor。    
     
13. 多线程断点续传的实现原理？    
	多线程下载的思想是客户端开启多个线程同时下载,每个线程只负责下载文件的一部分, 当所有线程下载完成的时候,文件下载完毕.    
   
14. 什么是深拷贝和浅拷贝？     
	浅拷贝（Shallow Copy）：①对于数据类型是基本数据类型的成员变量，浅拷贝会直接进行值传递，也就是将该属性值复制一份给新的对象。因为是两份不同的数据，所以对其中一个对象的该成员变量值进行修改，不会影响另一个对象拷贝得到的数据。②对于数据类型是引用数据类型的成员变量，比如说成员变量是某个数组、某个类的对象等，那么浅拷贝会进行引用传递，也就是只是将该成员变量的引用值（内存地址）复制一份给新的对象。因为实际上两个对象的该成员变量都指向同一个实例。在这种情况下，在一个对象中修改该成员变量会影响到另一个对象的该成员变量值。      
	对于深拷贝来说，不仅要复制对象的所有基本数据类型的成员变量值，还要为所有引用数据类型的成员变量申请存储空间，并复制每个引用数据类型成员变量所引用的对象，直到该对象可达的所有对象。也就是说，对象进行深拷贝要对整个对象图进行拷贝！   
	简单地说，深拷贝对引用数据类型的成员变量的对象图中所有的对象都开辟了内存空间；而浅拷贝只是传递地址指向，新的对象并没有对引用数据类型创建内存空间。   

15. Java 中对象的生命周期？   
	1.      创建阶段(Created)    
	2.      应用阶段(In Use)   
	3.      不可见阶段(Invisible)    
	4.      不可达阶段(Unreachable)   
	5.      收集阶段(Collected)    
	6.      终结阶段(Finalized)  
	7.      对象空间重分配阶段(De-allocated)   

16. [对并发编程的了解?](https://www.jianshu.com/p/01188fa8e511)   
   
## JVM
 
1. [简述 JVM 内存模型和内存区域？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#jvm_1)  
2. [简述垃圾回收器的工作原理？](https://blog.csdn.net/wuzhixiu007/article/details/80116560)  
3. 如何判断对象的生死？垃圾回收算法？新生代，老生代？    
	对虚拟机可用内存空间，即堆空间中的对象进行识别，如果对象正在被引用，那么称其为存活对象，反之，如果对象不再被引用，则为垃圾对象，可以回收其占据的空间，用于再分配。       
	通过引用计数算法或引用可达算法可以判断对象是否存活。    
	Serial收集器（复制算法)：   
	新生代单线程收集器，标记和清理都是单线程，优点是简单高效。   
	Serial Old收集器(标记-整理算法)：   
	老年代单线程收集器，Serial收集器的老年代版本。    
	ParNew收集器(停止-复制算法)：　    
	新生代收集器，可以认为是Serial收集器的多线程版本,在多核CPU环境下有着比Serial更好的表现。   
	Parallel Scavenge收集器(停止-复制算法)：   
	并行收集器，追求高吞吐量，高效利用CPU。吞吐量一般为99%， 吞吐量= 用户线程时间/(用户线程时间+GC线程时间)。适合后台应用等对交互相应要求不高的场景。    
	Parallel Old收集器(停止-复制算法)：   
	Parallel Scavenge收集器的老年代版本，并行收集器，吞吐量优先   
	CMS(Concurrent Mark Sweep)收集器（标记-清理算法）：   
	高并发、低停顿，追求最短GC回收停顿时间，cpu占用比较高，响应时间快，停顿时间短，多核cpu 追求高响应时间的选择   
      
4. 哪些情况下的对象会被垃圾回收机制处理掉？
5. 垃圾回收机制与调用 System.gc() 的区别？   
	Java语言建立了垃圾收集机制，用以跟踪正在使用的对象和发现并回收不再使用(引用)的对象。该机制可以有效防范动态内存分配中可能发生的两个危险：因内存垃圾过多而引发的内存耗尽，以及不恰当的内存释放所造成的内存非法引用。     
　　垃圾收集算法的核心思想是：对虚拟机可用内存空间，即堆空间中的对象进行识别，如果对象正在被引用，那么称其为存活对象，反之，如果对象不再被引用，则为垃圾对象，可以回收其占据的空间，用于再分配。   
	System.gc()函数的作用只是提醒虚拟机：程序员希望进行一次垃圾回收。但是它不能保证垃圾回收一定会进行，而且具体什么时候进行是取决于具体的虚拟机的，不同的虚拟机有不同的对策。    
   
6. [强引用、软引用、弱引用、虚引用之间的区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_53)
7. 强引用设置为 null，会不会被回收？

8. [简述 ClassLoader 类加载机制?](https://blog.csdn.net/m0_38075425/article/details/81627349)     
	当程序主动使用某个类时，如果该类还未被加载到内存中，则JVM会通过加载、连接、初始化3个步骤来对该类进行初始化。    
   
9. 对双亲委派模型的了解？   
	双亲委派模型的工作过程是：   
	如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成，每一层次的类加载器都是如此，因此所有的加载请求，最终都应该传送到顶层的启动类加载器中，只有当父加载器反馈自己无法完成这个加载请求（它的搜索范围中没有找到所需的类）时，子加载器才会尝试自己去加载。   
  
10. [String a = "a"+"b"+"c" 在内存中创建几个对象？](https://github.com/jeanboydev/Android-Interview/blob/master/Java.md#java_57)
11. 对 Dalvik、ART 虚拟机的了解？
12. 对动态加载（OSGI）的了解？
13. 常见编码方式有哪些？
14. utf-8 编码中的中文占几个字节？int 型占几个字节？

----------

# Android

## 基础

1. 四大组件是什么？

2. Activity 的生命周期？

3. Activity 之间的通信方式？

4. Activity 各种情况下的生命周期？

5. 横竖屏切换时 Activity 的生命周期

6. 前台切换到后台，然后再回到前台时 Activity 的生命周期

7. 弹出 Dialog 的时候按 Home 键时 Activity 的生命周期

8. 两个 Activity 之间跳转时的生命周期

9. 下拉状态栏时 Activity 的生命周期

10. Activity 与 Fragment 之间生命周期比较？

11. Activity 的四种 LaunchMode（启动模式）的区别？

12. Activity 状态保存与恢复？

13. Fragment 各种情况下的生命周期？

14. [Activity 和 Fragment 之间怎么通信， Fragment 和 Fragment 怎么通信？](https://github.com/jeanboydev/Android-Interview/blob/master/Android.md#android_base_14)

15. Service 的生命周期？

16. Service 的启动方式？

17. Service 与 IntentService 的区别?

18. [Service 和 Activity 之间的通信方式？](https://github.com/jeanboydev/Android-Interview/blob/master/Android.md#android_base_18)

19. 对 ContentProvider 的理解？

20. ContentProvider、ContentResolver、ContentObserver 之间的关系？

21. 对 BroadcastReceiver 的了解？

22. 广播的分类？使用方式和场景？

23. [动态广播和静态广播有什么区别？](https://github.com/jeanboydev/Android-Interview/blob/master/Android.md#android_base_23)

24. AlertDialog、popupWindow、Activity 之间的区别？

25. Application 和 Activity 的 Context 之间的区别？

26. Android 属性动画特性？

27. 请列举 Android 中常见的布局（Layout）类型，并简述其用法，以及排版效率。【猎豹移动】

    LinearLayout、RelativeLayout、FrameLayout 的特性对比及使用场景？

28. 对 SurfaceView 的了解？

29. Serializable 和 Parcelable 的区别？

30. Android 中数据存储方式有哪些？

31. 屏幕适配的处理技巧都有哪些?

32. Android 各个版本 API 的区别？

33. 动态权限适配方案，权限组的概念？

34. 为什么不能在子线程更新 UI？

35. ListView 图片加载错乱的原理和解决方案？

36. 对 RecycleView 的了解？

37. Recycleview 和 ListView 的区别？

38. RecycleView 实现原理？

39. Android Manifest 的作用与理解？

40. 多线程在 Android 中的使用？

41. 区别 Animation 和 Animator 的用法，概述实现原理？【猎豹移动】

## 进阶

1. [画出 Android 的大体架构图](https://github.com/jeanboydev/Android-Interview/blob/master/Android.md#android_advance_1)

2. 低版本 SDK 如何使用高版本 API？

3. AsyncTask 如何使用?

4. AsyncTask 机制、原理及不足？

5. 如果在 onStop() 的时候做了网络请求，onResume() 的时候怎么恢复？

6. Handler 机制和底层实现？

7. Handler、Thread、HandlerThread 区别？

   Thread、Looper、MessageQueue、Handler、Message，每个类的功能是什么，这些类之间是什么关系？【猎豹移动】

8. ThreadLocal 原理、实现及如何保证 Local 属性？

9. 自定义 View 的流程？如何机型适配？

10. 自定义 View 的时怎么获取 View 的大小？

11. View 的绘制流程？

12. View 的事件传递分发机制？

13. requestLayout()，onLayout()，onDraw()，drawChild() 区别与联系？

14. invalidate() 和 postInvalidate() 的区别？

15. 如何计算一个 View 的嵌套层级？

16. Android 动画框架及实现原理？

17. 进程和 Application 的生命周期的关系？

18. SpareArray 的实现原理？

19. SharedPreferences 的实现眼里？是否进程同步？如何做到同步？

20. ContentProvider 是如何实现数据共享的？

21. ContentProvider 的权限管理？

22. Android 系统为什么会设计 ContentProvider？

23. Android 线程有没有上限？

24. 怎么去除重复代码？

25. Android 中开启摄像头的主要流程？

26. 对 Bitmap 对象的了解？

27. 图片加载原理？

28. 图片压缩原理？

29. 图片框架实现原理？LRUCache 原理？

30. EventBus 实现原理？

31. ButterKnife 实现原理？

32. Volley 实现原理？

33. okhttp 实现原理？

34. 服务器只提供数据接收接口，在多线程或多进程条件下，如何保证数据的有序到达？

35. SQLite 数据库升级，数据迁移问题？

36. 数据库框架对比和源码分析？

37. CAS介绍，OAuth 授权机制？

38. 谈谈你对安卓签名的理解

39. App 是如何沙箱化，为什么要这么做？

## 混合开发

1. 混合开发的方式？各自优缺点和使用场景？
2. Hybird
3. React Native
4. Weex
5. Flutter
6. Dart
7. 快应用

## Framework

1. 请介绍一下 NDK？
2. 如何加载 ndk 库？如何在 jni 中注册 native 函数，有几种注册方式?【猎豹移动】
3. Android 进程分类？
4. 谈谈对进程共享和线程安全的认识？
5. 谈谈对多进程开发的理解以及多进程应用场景？
6. 什么是协程？
7. 逻辑地址与物理地址，为什么使用逻辑地址？
8. Android 为每个应用程序分配的内存大小是多少？
9. 进程保活的方式？
10. 系统启动流程是什么？
11. 一个应用程序安装到手机上的过程发生了什么？
12. App 启动流程，从点击桌面开始（Activity 启动流程）？
13. 什么是 AIDL？解决了什么问题？如何使用？
14. Binder 机制及工作原理？
15. App 中唤醒其他进程的实现方式？
16. Activity、Window、View 三者的关系与区别？
17. ApplicationContext 和 ActivityContext 的区别？
18. ActivityThread，ActivityManagerService，WindowManagerService 的工作原理？
19. PackageManagerService 的工作原理？
20. PowerManagerService 的工作原理？
21. 权限管理系统（底层的权限是如何进行 grant 的）？
22. 操作系统中进程和线程有什么区别？系统在什么情况下会在用户态和内核态中切换？【猎豹移动】
23. 如果一个 App 里面有多个进程存在，请列举你所知道的全部 IPC 方法。

## 性能优化

1. 如何对 Android 应用进行性能分析以及优化?

2. ANR 产生的原因是什么？怎么定位？

3. OOM 是什么？怎么解决？是否可以 try catch？

4. 内存泄露的解决方法？

5. ddms 和 traceView 的使用？

6. 性能优化如何分析 systrace？

7. 用 IDE 如何分析内存泄漏？

8. Java 多线程引发的性能问题，怎么解决？

9. 启动页白屏、黑屏、太慢怎么解决？

10. App 启动崩溃异常怎么捕捉？

    对于 Android App 闪退，可能有哪些原因？请针对每种情况简述分析过程。【猎豹移动】

11. 如何保持应用的稳定性？

12. RecyclerView 和 ListView 的性能对比？

13. Bitmap 如何处理大图？如何预防 OOM？

14. 如何缩小 Apk 的体积?

15. 如何统计启动时长？

##  Gradle

1. Glide 源码解析
2. 对热修复和插件化的理解？
3. 插件化原理分析
4. 模块化实现（好处，原因）
5. 项目组件化的理解
6. 描述清点击 Android Studio 的 build 按钮后发生了什么？

## Kotlin

1. 谈谈对 Kotlin 的理解
2. 闭包和局部内部类的区别?

----------

# 网络基础

1. [描述一次网络请求的流程?](https://github.com/jeanboydev/Android-Interview/blob/master/Network.md#quest_network_technological_process)
2. TCP 中 3 次握手和 4 次挥手的过程?
3. TCP 与 UDP 的区别及应用?
4. HTTP 协议
5. HTTP 1.0 与 2.0 的区别
6. HTTP 报文结构
7. HTTP 与 HTTPS 的区别以及如何实现安全性
8. HTTPS 原理
9. 谈谈你对 WebSocket 的理解
10. WebSocket 与 socket 的区别
11. 视频加密传输

----------

# 数据结构与算法

## 数据结构

- 简述常见的数据结构？
- 堆的结构？
- 树、B+ 树、二叉树、红黑树的了解？
- 二叉树的深度优先遍历和广度优先遍历？
- 堆和树的区别？
- 图的了解？

## 算法

- 排序算法有哪些？
- 最快的排序算法是哪个？
- 手写冒泡排序
- 手写快速排序
- 快速排序的过程、时间复杂度、空间复杂度
- 手写堆排序

## 常见算法问题

- 给阿里2万多名员工按年龄排序应该选择哪个算法？
- GC算法(各种算法的优缺点以及应用场景)
- 蚁群算法与蒙特卡洛算法
- 子串包含问题(KMP 算法)写代码实现
- 一个无序，不重复数组，输出N个元素，使得N个元素的和相加为M，给出时间复杂度、空间复杂度。手写算法
- 万亿级别的两个URL文件A和B，如何求出A和B的差集C(提示：Bit映射->hash分组->多文件读写效率->磁盘寻址以及应用层面对寻址的优化)
- 两个不重复的数组集合中，求共同的元素。
- 两个不重复的数组集合中，这两个集合都是海量数据，内存中放不下，怎么求共同的元素？
- 一个文件中有100万个整数，由空格分开，在程序中判断用户输入的整数是否在此文件中。说出最优的方法
- 一张Bitmap所占内存以及内存占用的计算
- 2000万个整数，找出第五十大的数字？
- 求1000以内的水仙花数以及40亿以内的水仙花数
- 烧一根不均匀的绳，从头烧到尾总共需要1个小时。现在有若干条材质相同的绳子，问如何用烧绳的方法来计时一个小时十五分钟呢？
- 5枚硬币，2正3反如何划分为两堆然后通过翻转让两堆中正面向上的硬8币和反面向上的硬币个数相同
- 时针走一圈，时针分针重合几次

----------

# 设计模式与架构

## 设计模式

- 谈谈你对 Android 设计模式的理解
- 项目中常用的设计模式有哪些？
- 手写生产者-消费者模式？
- 手写观察者模式？
- 适配器模式、装饰者模式、外观模式的异同？

## 架构

- MVC、MVP、MVVM 原理和区别？

  请画出 MVC、MVP 的差异？【猎豹移动】

- 对 RxJava 的理解，功能与原理，优缺点？

- 从 0 设计一款 App 整体架构，如何去做？

- Fragment 如果在 Adapter 中使用应该如何解耦？

- 对于应用更新这块是如何做的？(解答：灰度，强制更新，分区域更新)？

- 实现一个 Json 解析器（可以通过正则提高速度）？

----------

# 其他

- 请简单做个自我介绍？

- 为什么离开上家公司？您在前一家公司的离职原因是什么？

- 为什么要做 xxx 岗位（出现所学专业与求职岗位不同时提问）?

- 讲一个你认为做的最好的项目/案例

- 你应聘该岗位的优势是什么？

- 你上家公司的薪水/期望的薪金？

- 你对薪资的要求？

- 谈谈你对跳槽的看法？

- 对待加班看法？

- 自己最擅长的技术点，最感兴趣的技术领域和技术点，做了那些东西？

- 自己的优点和缺点是什么？并举例说明？

- 你朋友对你的评价？

- 说下项目中遇到的棘手问题，包括技术，交际和沟通？

  项目中遇到最大的困难是什么？如何解决的？

- 在五年的时间内，你的职业规划？

- 给你一个项目，你怎么看待他的市场和技术的关系？

- 你一般喜欢从什么渠道获取技术信息和提高自己的能力？

  你的学习方法是什么样的？实习过程中如何学习？实习项目中遇到的最大困难是什么以及如何解决的？

- 如果实际工作后发现自己不适合这个职位怎么办？

  如果通过这次面试我们单位录用了你，但工作一段时间却发现你根本不适合这个职位，你怎么办？

- 工作上与领导意见不同时，怎么办？

- 如果你的主管抢了你的功劳你该怎样？

- 若上司在公开会议上误会你了，该如何解决？

- 工作中你难以和同事、上司相处，你该怎么办？

- 因成绩比较突出，受同事们孤立你怎么看？

- 你和别人发生过争执吗？你是怎样解决的？

- 如果工作失误，给公司造成经济损失，你该怎么办？

- 你对于我们公司了解多少？

- 你为什么愿意到我们公司来工作？

- 你能为我们公司带来什么？

- 你最擅长的技术点，最感兴趣的技术领域和技术点？

- 说说你对行业、技术发展趋势的看法？

- 理想中的工作环境是什么？

- 说说你的家庭？

- 就你申请的这个职位，你认为你还欠缺什么？

- 你做过的哪件事最令自己感到骄傲？说一件最能证明你能力的事情？

- 对这项工作，你有哪些可预见的困难？

- 如果被录用，你将怎样开展工作？

- 希望与什么样的上级共事？

- 你工作经验欠缺，如何能胜任这项工作？ 

- 如果你在这次面试中没有被录用，你怎么打算？

- 除了本公司外，还应聘了哪些公司？

- 你还要什么了解和要问的吗？

- 实习过程中周围同事/同学有哪些值得学习的地方？

- 是否可以实习，可以实习多久？

- 实习过程中做了什么，有什么产出？

- 公司实习最大的收获是什么？

- 评价下自己，评价下自己的技术水平，个人代码量如何？

- 当前的 offer 状况；如果 BATH 都给了offer 该如何选？

- 你对一份工作更看重哪些方面？平台，技术，氛围，城市，还是 money？

- 假如你晚上要去送一个出国的同学去机场，可单位临时有事非你办不可，你怎么办？

- 你看中公司的什么？或者公司的那些方面最吸引你？

- 讲一件你印象最深的一件事情？

- 介绍你做过的哪些项目，介绍一个你影响最深的项目？

- 你做过的哪件事最令自己感到骄傲？

- 都使用过哪些框架、平台？

- 都使用过哪些自定义控件？

- 项目中用了哪些开源库，如何避免因为引入开源库而导致的安全性和稳定性问题？

- 有没有什么开源项目？

- 研究比较深入的领域有哪些？

- 对业内信息的关注渠道有哪些？

- 业余都有哪些爱好？

- 最近都读哪些书？

- 你的梦想是什么？

## 套路

如果有遇到以下这些情况，你可以继续投简历：

- 我们 xx 总不在，会叫 hr 联系你，你先回去等通知
- 面试叫你带上以往作品（工作成绩需要以往作品展示的除外，如：ui）然后面试官一直问你方案是怎么做的
- 遇到面试官敷衍随便问问题
