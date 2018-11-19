---
layout: post
title: 设计模式（一）：单例模式
date: 2018-8-21 11:45:34
categories: 
- design pattern
tags:
- gof
description: 系统性的总结设计模式的应用
---

# 单例模式

单例模式确保一个类只有一个实例,而且自行实例化并向整个系统提供这个实例.

单例模式的主要作用是确保一个类只有一个实例存在. 单例模式可以在建立目录,数据库连接,等需要单线程操作的场合,用于实现对系统资源的整合.

- 饿汉模式：类加载时，就进行对象实例化。
- 懒汉模式：第一次引用时，才进行对象的实例化。

饿汉模式代码：
```
public class Singleton {
    private static Singleton m_instance = new Singleton();
    private Singleton(){}
    
    public static Singleton getInstance(){
        return m_instance;
    }
}
```

懒汉模式代码：
```
public class Singleton {
    private static Singleton _instance = null;
    private Singleton(){}

    synchronized public static Singleton getInstance() {
        if (_instance == null) {
            _instance = new Singleton();
        }
        return _instance;
    }
}
```

- DCL 双检查锁机制
```
public class MyObject{
    private volatile static MyObject myObject;
    private MyObject(){
    }
    public static MyObject getInstance(){
        try{
            synchorized(MyObject.class){
                if(myObject==null){
                    myObject = new MyObject();
                }
            }
        } catch(InterruptedException e){
            e.printStackTrace();
        }
        return myObject();
    }
}
```

- 静态内置类
```
public class MyObject{
    private static class MyObjectHandler{
        private static MyObject myObject = new MyObject();
    }
    
    private MyObject(){
    }
    public static MyObject getInstance(){
        return MyObjectHandler.myObject;
    }
}
```

- 静态代码块
```
public class MyObject{
    private static MyObject instance = null;
    private MyObject(){
    }
    static{
        instance = new MyObject();
    }
    public static MyObject getInstance(){
        return instance;
    }
}
```

- 使用enum枚举数据类型









