<h1 align="center">DesignPatterns</h1>

## Iterator模式

### 概念类图

![Iterator模式](G:\gitRepos\MarkDowns\MarkDowns\DesignPatterns\Resources\IteratorPatternConcept.png)

### 案例类图

![](G:\gitRepos\MarkDowns\MarkDowns\DesignPatterns\Resources\IteratorPatternExample.png)

### 要点

1. 编程过程中尽量面向接口和抽象类编程，iterator使用抽象方法，尽量不使用具体实现类。如下，因使用了抽象类，若后续BookShelf实现有变，while中的迭代仍可保持不变

![](G:\gitRepos\MarkDowns\MarkDowns\DesignPatterns\Resources\IteratorPatternCode.png)

2. 将遍历功能置于Aggregate角色之外是Iterator模式的一个特征，据此，可以编写多个Iterator实现类
3. 多种迭代器，迭代不止可以由前往后，还可以由后往前、双向遍历、跳跃式遍历等