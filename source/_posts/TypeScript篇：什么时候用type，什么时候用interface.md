title: TypeScript篇：什么时候用type，什么时候用interface
author: Hoophony Yu
tags: []
categories: []
date: 2020-09-04 13:41:00
---
** 类型别名(type)会给一个类型起个新名字。 类型别名有时和接口很像，但是可以作用于原始值，联合类型，元组以及其它任何你需要手写的类型。**

** 接口(interface)接口的作用就是为这些类型命名和为你的代码或第三方代码定义契约。这个怎么理解呢？就是限制我们所定义对象的属性类型。 **
____
以下来说明两者之间的不同点：
###### type不同点：
 + type用于原始值
 ```
 type Numtype = number
 ```
 + type用于联合类型
 ```
 type TypeA = { a：number }
 type TypeB = { b：number }
 type UnionType = TypeA | TypeB

 ```
 + type用于元组
 ```
 type TupleType = [number, string]
 ```
 ---
######  interface不同点：
定义个接口 
```
interface Interface {
   num: number
}
 ```
+ extends(类、接口）
```
class myClass extends Interface {
	str: string
}
interface myInterface extends Interface {
	str: string
}
```
+ implements (类）
```
class myClass implements Interface {
	str: string
}
```
两者的相同点：都可以为变量设置限制类型。
```
  type Alias = {
    num: number
  }
  interface Interface {
    num: number
  }
  let _alias: Alias = {
    num: 123
  }
  let _interface: Interface = {
    num: 321
  }
```
---
总结：
+ 类型别名：无法使用接口，需要用到联合类型或者元组类型
+ 接口：当你要定义的类型用于扩展。即要使用extends、implements修饰
----
+ 文中如有错误，欢迎在公众号（前端学习风车行）指正😊
+ 本文首发于公众号：前端学习风车行，未经许可禁止转载。并同步于该博客。
+ 更多学习有兴趣可以关注微信公众号： 前端学习风车行。