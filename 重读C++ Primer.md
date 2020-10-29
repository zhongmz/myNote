---
title: 重读C++ Primer
date: 2020-5-7 22:56:52
categories: Read
---

#### 列表初始化



#### vector是如何增长的

​	容器内元素是连续存储的，若容器需要的空间大于现在位置所拥有的空间，那么vector会执行一次内存分配和内存释放操作。而标准库的实现者为了重新分配的次数减少，每次重新分配时都会分配比需求更大的内存空间。



- 栈内存
- 静态内存
- 动态内存

#### deque是如何增长的

- `deque`是`list`与`vector`这两个顺序容器的结合体。

  ![image-20200513112016158.png](https://i.loli.net/2020/05/20/o9ulHIRFbyfXtxG.png)

  

- 不过在进行中间元素的插入和删除的时候，其效率远远低于`list`和`vector`，这也是其使用复杂的迭代器框架所带来的代价。
- 支持随机访问。
- 前端插入与删除效率比`vector`高。
- 插入与删除不会导致重新分配空间。

#### 使用动态内存的原因

- 程序不知道自己需要使用多少对象
- 程序不知道所需对象的准确类型
- 程序需要在多个对象间共享数据



##### 区分

- `string *ps1=new string`
- `string *ps2=new string()`
- `int *pi1=new int`
- `int *pi2=new int()`

##### 智能指针

- `shared_ptr<int>p=make_shared<int>(10);`
- `auto p=make_shared<int>(10);`
- 引用计数`reference count`，每拷贝一次`shared_ptr`，计数器加一。
- 当`reference count `变为0时，自动销毁。
- 不要混用`shared_ptr和内置指针`



##### 动态数组

- 动态数组不是数组类型
- `int *pia=new int[10];`
- `pia[1]=10; cout<<pia[1]<<endl;`
- `delete [] pia;`



- `unique_ptr `支持动态数组，`shared_ptr`不支持管理动态数组，因为`shared_ptr`没有动态数组的删除器。





# 泛型算法



## 初识

- ```c++
  string sum
      =accumulate(V.cbegin(),V.cend(),string(""));
  //正确
  string sum
      =accumulate(V.cbegin(),V.cend(),"");
  //错误，const char *上没有定义+运算符
  ```

  

## 容器适配器

- 容器，迭代器，函数都有适配器。本质上，一个适配器是一种机制，使得事物的行为看起来像另外一种事物。

- 默认情况下`stack`和`queue`是基于`deque`实现；而`priority_queue`则是基于`vector`实现。

  









## 测试修改内容