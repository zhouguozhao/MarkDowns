<h1 align="center">JVM</h1>



#### 2.2 運行時數據區域

![](G:\gitRepos\MarkDowns\MarkDowns\JVM\Resources\JVM runtime area.jpg)



#### 2.3.2 對象的內存佈局

**1. 對象頭MarkWord**

![](G:\gitRepos\MarkDowns\MarkDowns\JVM\Resources\ObjectHeaderMarkWord.bmp)

**2. 用句柄訪問對象**

![](G:\gitRepos\MarkDowns\MarkDowns\JVM\Resources\ObjectAccessByHandle.png)

**3. 直接訪問對象**

![](G:\gitRepos\MarkDowns\MarkDowns\JVM\Resources\ObjectAccessDirectly.png)

















##### 產生heapdump文件

> 實時導出：
>
> *jmap -dump:live,format=b,file=heap.hprof <pid>*
>
> 發生OOM報錯時自動導出
>
> -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=目錄





## 解决JDK11目录下没有jre的问题

> JDK11开始已经不会自动生成jre目录了，需要自己在jdk根目录下执行一下命令
>
> linux下
>
> `bin/jlink --module-path jmods --add-modules java.desktop --output jre`
>
> windows下
>
> `bin\jlink.exe --module-path jmods --add-modules java.desktop --output jre`



## 启动参数

```java
-XX:+UseParallelGC
    //使用Parallel Scavenge+Parallel old收集器
```



## 命令

```java
jinfo -flags pid(进程号) //查看java进程的JVM参数
```



## JVM源码编译

1. 进入JDK源码根目录执行一下命令(比深入理解JAVA虚拟机中多了一个--disable-warnings-as-errors参数，原因是在编译时将warning视为error导致编译失败)

   `bash configure --disable-warnings-as-errors --enable-debug --with-jvm-variants=server`

2. 执行`make images`



## 收集器

### CMS(CONCURRENCY MARK SWEEP)收集器

> -XX:CMSInitiatingOccu-pancyFraction  
>
> 该参数设定当老年代空间使用达到一定百分比后边开启CMS收集



## 內存管理

### 內存的分配與回收

1. 對象優先在Eden分配

2. 大對象直接進入老年代

   如長字符串和元素數量龐大的數組

   -XX:PretenureSizeThreshold=3145728  設置對象超過3M直接在老年代分配

   

3. 長期存活對象直接進入老年代（默認GC年齡達到15則進入老年代）



# 問題

#### 使用`jps -l`無法顯示進程具體類名/jconsole無法連接到本地進程/visualVM啟動報錯Local Applications Cannot Be Monitored

> **Description:** An error dialog saying that local applications cannot be monitored is shown immediately after VisualVM startup. Locally running Java applications are displayed as <Unknown Application> (pid ###).
>
> **Resolution:** This can happen on Windows systems if the username contains capitalized letters. In this case, username is `UserName` but the jvmstat directory created by JDK is `%TMP%\hsperfdata_username`. To workaround the problem, exit all Java applications, delete the `%TMP%\hsperfdata_username` directory and create new `%TMP%\hsperfdata_UserName` directory.

此問題一般發生在windows系統，原因是進程文件夾名稱中的用戶名大小寫與windows用戶大小寫不一致，將`%TMP%\hsperfdata_username`文件夾刪掉，重新新建一個`%TMP%\hsperfdata_UserName`文件夾即可，其中UserName大小寫要與windows用戶大小寫一致。

