# JVM概述

## Java代码-电脑

![image-20250207184955242](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207184955242.png)

## Java是跨平台语言

![image-20250207185216444](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207185216444.png)

## JDK JRE JVM

![image-20250207185337180](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207185337180.png)

![image-20250217150647314](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250217150647314.png)



## 学习JVM

![image-20250207185632522](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207185632522.png)



# JVM运行时数据区

## 运行时数据区

Java 运行时数据区（Runtime Data Area）是 JVM 在执行 Java 程序时，为了管理内存和数据而划分的不同区域。

![image-20250207185811817](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207185811817.png)



# 解析运行时数据区

## 方法区（Method Area）

![image-20250207190251773](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207190251773.png)

​                 3. 在 JDK 8 及以后的版本中，方法区的实现为元空间（Metaspace），元空间并不在堆内存中，而是使用本地内存。它与 Java  堆一样，是线程共享的内存区域，主要用于存储类的结构信息、方法信息、常量池等数据。

## Java堆（Java Heap）

![image-20250207190834574](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207190834574.png)

## 程序计数器 （PC Register）

![image-20250207191047255](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207191047255.png)

![image-20250207191225419](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207191225419.png)

![image-20250207191256122](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207191256122.png)

## Java虚拟机栈（JVM Stacks）

![image-20250207191518316](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207191518316.png)

![image-20250207191837352](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207191837352.png)

## 本地方法栈（Native Met Stack）

![image-20250207192050406](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207192050406.png)



# Java内存结构

## 内存结构

![image-20250207193528134](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207193528134.png)

**Java 内存结构主要指的就是 JVM 运行时数据区，但它还可能涉及到一些与之相关的周边概念**

- **运行时常量池**：是方法区的一部分，用于存放编译期生成的各种字面量和符号引用，它具备动态性，运行期间也能将新的常量放入池中。
- **直接内存**：它不是 JVM 运行时数据区的一部分，但也会被频繁使用。在 NIO（New Input/Output）中，可使用`DirectByteBuffer`对象直接分配堆外内存，然后通过一个存储在 Java 堆里的`DirectByteBuffer`对象作为这块内存的引用进行操作，能在一些场景中显著提高性能，但如果使用不当，也可能导致内存溢出。

![image-20250207193833913](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207193833913.png)



# JVM垃圾回收机制

![image-20250207193929676](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207193929676.png)

## 垃圾回收机制

![image-20250207194100766](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194100766.png)

##  finalize方法作用

![image-20250207194234383](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194234383.png)

## 新生代 老年代 永久代(方法区)

![image-20250207194330998](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194330998.png)

![image-20250207194512922](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194512922.png)

### 为什么要这样分代

![image-20250207194638045](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194638045.png)

### MinorGC MajorGC FullGC

![image-20250207194847007](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194847007.png)

![image-20250207194946383](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207194946383.png)

## 如何判断对象是否存活

### 引用计数法

![image-20250207195120408](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207195120408.png)

### 可达性分析法

![image-20250207195245890](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207195245890.png)



# JVM垃圾回收策略（GC算法）

## 引用计数算法



## 标记–清除算法

![image-20250207195809379](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207195809379.png)



## 标记–(压缩)整理算法

![image-20250207200010494](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200010494.png)



## 复制算法

![image-20250207200102045](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200102045.png)



## 分代算法

![image-20250207200201237](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200201237.png)



# JVM垃圾收集器

## 什么是垃圾收集器

![image-20250207200330109](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200330109.png)

![image-20250207200411537](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200411537.png)



##  垃圾回收器详解

![image-20250207200457275](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200457275.png)

**Serial**

![image-20250207200603109](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200603109.png)

**ParNew**

![image-20250207200635025](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200635025.png)

 **Parallel Scavenge**

![image-20250207200707905](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200707905.png)

**Serial Old**

![image-20250207200743207](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200743207.png)

**Parallnel old**

![image-20250207200811177](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200811177.png)

**CMS**

![image-20250207200834992](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200834992.png)

**G1**

![image-20250207200859182](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207200859182.png)



# 垃圾回收机制/策略/收集器

## 区分一下

```
垃圾回收机制 -》描述的是干什么事 
垃圾回收策略 -》描述的是怎么干这个事 
垃圾收集机器 -》描述的谁去干这个事（对垃圾回收策略的具体实现），后续主流是G1
```



# JVM参数配置

## JVM内存参数简述

```
#常用的设置
-Xms：初始堆大小，JVM 启动的时候，给定堆空间大小。 

-Xmx：最大堆大小，JVM 运行过程中，如果初始堆空间不足的时候，最大可以扩展到多少。 

-Xmn：设置堆中年轻代大小。整个堆大小=年轻代大小+年老代大小+持久代大小。 

-XX:NewSize=n 设置年轻代初始化大小大小 

-XX:MaxNewSize=n 设置年轻代最大值

-XX:NewRatio=n 设置年轻代和年老代的比值。如: -XX:NewRatio=3，表示年轻代与年老代比值为 1：3，年轻代占整个年轻代+年老代和的 1/4 

-XX:SurvivorRatio=n 年轻代中 Eden 区与两个 Survivor 区的比值。注意 Survivor 区有两个。8表示两个Survivor :eden=2:8 ,即一个Survivor占年轻代的1/10，默认就为8

-Xss：设置每个线程的堆栈大小。JDK5后每个线程 Java 栈大小为 1M，以前每个线程堆栈大小为 256K。

-XX:ThreadStackSize=n 线程堆栈大小

-XX:PermSize=n 设置持久代初始值	

-XX:MaxPermSize=n 设置持久代大小
 
-XX:MaxTenuringThreshold=n 设置年轻带垃圾对象最大年龄。如果设置为 0 的话，则年轻代对象不经过 Survivor 区，直接进入年老代。

#下面是一些不常用的

-XX:LargePageSizeInBytes=n 设置堆内存的内存页大小

-XX:+UseFastAccessorMethods 优化原始类型的getter方法性能

-XX:+DisableExplicitGC 禁止在运行期显式地调用System.gc()，默认启用	

-XX:+AggressiveOpts 是否启用JVM开发团队最新的调优成果。例如编译优化，偏向锁，并行年老代收集等，jdk6纸之后默认启动

-XX:+UseBiasedLocking 是否启用偏向锁，JDK6默认启用	

-Xnoclassgc 是否禁用垃圾回收

-XX:+UseThreadPriorities 使用本地线程的优先级，默认启用	

等等等......

```

## JVM的GC收集器设置

```
-XX:+UseSerialGC:设置串行收集器，年轻带收集器 

 -XX:+UseParNewGC:设置年轻代为并行收集。可与 CMS 收集同时使用。JDK5.0 以上，JVM 会根据系统配置自行设置，所以无需再设置此值。

-XX:+UseParallelGC:设置并行收集器，目标是目标是达到可控制的吞吐量

-XX:+UseParallelOldGC:设置并行年老代收集器，JDK6.0 支持对年老代并行收集。 

-XX:+UseConcMarkSweepGC:设置年老代并发收集器

-XX:+UseG1GC:设置 G1 收集器，JDK1.9默认垃圾收集器

```

##  JVM参数在哪设置

![image-20250207201113767](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201113767.png)

![image-20250207201128859](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201128859.png)

## 调优总结

![image-20250207201227735](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201227735.png)

```
服务器配置：cpu,内存，存储（机械硬盘，固态硬盘），网卡，其他组件
中型公司的服务器内存配置多为64GB
```



# 类加载器

## 类加载的机制及过程

![image-20250207201321435](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201321435.png)

![image-20250207201404379](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201404379.png)

![image-20250207201417645](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201417645.png)

![image-20250207201456483](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201456483.png)

简单总结一下 类加载机制的5个过程

```
加载：主要负责通过类的全限定名获取类的字节码文件的二进制字节流，将其加载到内存空间，生成一个代表该类的java.lang.Class对象，作为方法区中该类的各种数据的访问入口。
验证：确保加载的字节码文件符合 Java 虚拟机规范，如文件格式是否正确、是否有安全问题等，以保证类的安全性和完整性。
准备：为类的静态变量分配内存并设置默认初始值，如public static int num = 10; 在准备阶段会为num分配内存并初始化为 0，而非10。
解析：将类的二进制数据中的符号引用替换为直接引用，比如将类名、方法名等符号引用转换为指向方法区中具体数据结构的指针或句柄等。
初始化：执行类构造器<clinit>()方法，对类的静态变量进行显式初始化等操作，真正赋予静态变量初始值，此时才会执行public static int num = 10;中的赋值操作。
```



## 类加载器的介绍

**启动 扩展 应用程序 自定义**

![image-20250207202007452](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202007452.png)

![image-20250207201555425](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207201555425.png)

## 理解双亲委派模式

![image-20250207202027133](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202027133.png)

## 类加载器间的关系

![image-20250207202131080](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202131080.png)



# JVM可视化工具

![image-20250207202256816](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202256816.png)

![image-20250207202313991](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202313991.png)

![image-20250207202334061](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202334061.png)

![image-20250207202348073](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202348073.png)

![image-20250207202409083](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202409083.png)

![image-20250207202424375](C:\Users\10385\AppData\Roaming\Typora\typora-user-images\image-20250207202424375.png)