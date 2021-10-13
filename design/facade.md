---
permalink: /design/facade/
---

## 结构型 - 外观(Facade)

> 本文主要分析设计模式 - 结构型 - 外观(Facade)，它提供了一个统一的接口，用来访问子系统中的一群接口，从而让子系统更容易使用

* 意图
* 类图
* 实现
* 设计原则

### 意图

提供了一个统一的接口，用来访问子系统中的一群接口，从而让子系统更容易使用。

### 类图

![facade](/knowledge/assets/images/design/facade.png)

### 实现

观看电影需要操作很多电器，使用外观模式实现一键看电影功能。

```java
public class SubSystem {
    public void turnOnTV() {
        System.out.println("turnOnTV()");
    }

    public void setCD(String cd) {
        System.out.println("setCD( " + cd + " )");
    }

    public void starWatching(){
        System.out.println("starWatching()");
    }
}
```

```java
public class Facade {
    private SubSystem subSystem = new SubSystem();

    public void watchMovie() {
        subSystem.turnOnTV();
        subSystem.setCD("a movie");
        subSystem.starWatching();
    }
}
```

```java
public class Client {
    public static void main(String[] args) {
        Facade facade = new Facade();
        facade.watchMovie();
    }
}
```

### 设计原则

最少知识原则: 只和你的密友谈话。也就是说客户对象所需要交互的对象应当尽可能少。