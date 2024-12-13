<h1 align="center">DesignPatterns</h1>

## 适应设计模式

### Iterator模式

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

#### 概念類圖

![](Resources\ObjectAdapterPatternConcept.png)

#### 案例類圖

![](Resources\ObjectAdapterPatternExample.png)

#### 案例關鍵代碼

![](Resources\ObjectAdapterPatternExampleCode.png)

## 交给子类

### TemplateMethod模式

> 在父类定义处理流程的框架，在子类实现具体处理的模式成为TemplateMethod模式

#### 示例类图

![](Resources\TemplateMethodExample.png)



#### 示例代码

![](Resources\TemplateMethodExampleCode1.png)

![](Resources\TemplateMethodExampleCode2.png)

![](Resources\TemplateMethodExampleCode3.png)

![](Resources\TemplateMethodExampleCode4.png)



#### 优势

1. 父类定义了处理流程，保证了行为的一致性
2. 子类给出不同的实现，以适应不同需求

#### 注意

TemplateMethod模式中，父类负责流程定义，子类负责具体实现，但具体哪部分该由父类处理，哪部分由子类处理没有确切的分界。需开发人员权衡代码复用性和复杂性作出权衡



### FactoryMethod模式

#### 示例类图

![](Resources\FactoryMethodExample.png)

#### 示例代码

![](Resources\FactoryMethodExampleCode1.png)

![](Resources\FactoryMethodExampleCode2.png)

![](Resources\FactoryMethodExampleCode3.png)

![](Resources\FactoryMethodExampleCode4.png)

![](Resources\FactoryMethodExampleCode5.png)

#### 概念类图

![](G:\gitRepos\MarkDowns\MarkDowns\DesignPatterns\Resources\FactoryMethodConcept.png)

##### 注意

在框架类Creator中，创建对象不要使用new，而是使用抽象方法，由ConcreteCreator实现，避免框架代码耦合具体实现代码

##### 生成实例方法的具体实现

1. 如示例中，将createProduct定义为抽象方法，由子类实现
2. 提供默认实现new Product(owner)，子类没实现则走默认
3. createProduct中默认实现抛出运行时异常，提醒开发者实现

#### 优势

1. 框架代码可复用，示例中，再新增Television类和对应工厂类不需要改框架代码