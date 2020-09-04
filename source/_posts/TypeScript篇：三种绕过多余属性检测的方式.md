title: TypeScript篇：三种绕过多余属性检测的方式
author: Hoophony Yu
date: 2020-09-04 09:22:52
tags:
---
** TypeScript的核心原则之一是对值所具有的结构进行类型检查。 **  
** 接口（interface）可以限定我们所定义对象的结构。**

就是因为这种限定，让我们所写的接口变得似乎有点不智能。为了更能让我们所定义的接口灵活自如，下面我将会以一个例子来讲述灵活地跳过类型检查器检测又能写出一个合格的接口。

----
```
// 定义接口
interface NameInfo {
    firstName: string,
    lastName: string
}
// 定义方法
const getUserInfo = ({firstName, lastName}: NameInfo):string => {
   return `${firstName} ${lastname}`
}
```
```
// 调用方法
getUserInfo({
   firstName: 'yutou',
   lastName: 'yu',
   age: 18
})
```
---
`报错：TS2345: Argument of type '{ firstName: string; lastName: string; age: number; }' is not assignable to parameter of type 'NameInfo'.Object literal may only specify known properties, and 'age' does not exist in type 'NameInfo'`  
表示age属性不存在在NameInfo类型里。类型检查器检查到传入的age属性是额外的属性，所以编译失败。  
#### 以下介绍三种方法可以绕过类型编译器的检测：  
+ 使用类型断言（interface不变）  
```
getUserInfo({
    firstName: 'yutou',
    lastName: 'yu',
    age: 18
} as NameInfo)
```
+ 利用索引签名（interface增加字符串索引签名）  
```
interface NameInfo {
    firstName: string,
    lastName: string, 
    `[prop: string]: any
}
```
+ 类型兼容性（interface不变，调用方式改变）  
```
const newNameInfo = {
   firstName: 'yutou',
   lastName: 'yu',
   age: 18
}
getUserInfo(newNameInfo)
```
** 以上就是ts三种绕过多余属性检测的方式 **
+ 文中如有错误，欢迎在公众号（前端学习风车行）指正😊
+ 本文首发于公众号：前端学习风车行，未经许可禁止转载。并同步于该博客。
+ 更多学习有兴趣可以关注微信公众号： 前端学习风车行。