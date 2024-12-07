<h1 align="center">DesignPatterns</h1>

## Iterator模式

### 概念类图

![Iterator模式](.\Resources\IteratorPatternConcept.png)

### 案例类图

![](.\Resources\IteratorPatternExample.png)

### 要点

1. 编程过程中尽量面向接口和抽象类编程，iterator使用抽象方法，尽量不使用具体实现类。如下，因使用了抽象类，若后续BookShelf实现有变，while中的迭代仍可保持不变

![](.\Resources\IteratorPatternCode.png)

2. 将遍历功能置于Aggregate角色之外是Iterator模式的一个特征，据此，可以编写多个Iterator实现类
3. 多种迭代器，迭代不止可以由前往后，还可以由后往前、双向遍历、跳跃式遍历等



## 適配器模式

适配器有以下两种：

* 类适配器模式（使用继承的适配器）
* 对象适配器模式（使用委托的适配器）

### 類適配器模式

適用於將一個已存在的類包裝起來，從而對外提供統一接口

#### 案例類圖

![](Resources\ClassAdapterPatternExample.png)



#### 案例关键代码

![](Resources\ClassAdapterPatternExampleCode.png)

banner、shouWithParen、shouWithAster实现被隐藏，可以在不修改main的情况下改变PrintBanner实现类



### 对象适配器模式

