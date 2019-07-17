title: ES5和ES6的数组去重方法汇总
author: Hoophony Yu
date: 2019-07-17 19:34:53
tags:
---
####数组去重的方法有多种，前端面试题经常出现，下面我来总结总结：
1、indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置,重点是首次哈！！！如果要检索的字符串值没有出现，则该方法返回 -1。
例：arrArray = [1,2,3,4,3,6,3];
```bash
  // ES6方法
 let result = arrArray.filter((el,index,arr) => {
 				return arr.indexOf(el) == index
    		})
 console.log(result)  // 去重后的数组
 // ES5方法
 function unique(arr){
 	var newArr = [arr[0]];
   for (var i = 1; i < arr.length; i++) {
   	if(newArr.indexOf(arr[i]) == -1) {
    	newArr.push(arr[i])
    }
   }
 }
```
注：由于时间关系，不一一列举啦，后续会更新