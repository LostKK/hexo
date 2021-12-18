---
title: 对象遍历
date: 2021-09-22 10:40:31
tags:
image: '/image/wallhaven-1kr323.jpg'
---

# 对象遍历
在对象遍历中，经常需要遍历对象的键、值，ES5 提供了 for...in 用来遍历对象，然而其涉及对象属性的“可枚举属性”、原型链属性等，下面将从 Object 对象本质探寻各种遍历对象的方法，并区分常用方法的一些特点。

## for in
```
Object.prototype.fun = () => {};
const obj = { 2: 'a', 1: 'b' };
  for (const i in obj) {  
    console.log(i, ':', obj[i]);
  }
  // 1: b
  // 2: a
  // fun : () => {} Object 原型链上扩展的方法也被遍历出来for (const i in obj) {  
   if (Object.prototype.hasOwnProperty.call(obj, i)) {      
        console.log(i, ':', obj[i]);    
   }}
  // name : a 不属于自身的属性将被 hasOwnProperty 过滤
```
使用 for in 循环时，返回的是所有能够通过对象访问的、可枚举的属性，既包括存在于实例中的属性，也包括存在于原型中的实例。如果只需要获取对象的实例属性，可以使用 hasOwnProperty 进行过滤。
使用时，要使用(const x in a)而不是(x in a)后者将会创建一个全局变量。
for in 的循环顺序，参考【JavaScript 权威指南】（第七版）6.6.1。
- 先列出名字为非负整数的字符串属性，按照数值顺序从最小到最大。这条规则意味着数组和类数组对象的属性会按照顺序被枚举。
- 在列出类数组索引的所有属性之后，在列出所有剩下的字符串名字（包括看起来像整负数或浮点数的名字）的属性。这些属性按照它们添加到对象的先后顺序列出。对于在对象字面量中定义的属性，按照他们在字面量中出现的顺序列出。
- 最后，名字为符号对象的属性按照它们添加到对象的先后顺序列出。

## Object.keys
```
Object.prototype.fun = () => {};
const str = 'ab';
console.log(Object.keys(str));
// ['0', '1']
const arr = ['a', 'b'];
console.log(Object.keys(arr));
// ['0', '1']
const obj = { 1: 'b', 0: 'a' };
console.log(Object.keys(obj));
// ['0', '1']
```
用于获取对象自身所有的可枚举的属性值，但不包括原型中的属性，然后返回一个由属性名组成的数组。

## Object.values
```
Object.prototype.fun = () => {};
const str = 'ab';
console.log(Object.values(str));
// ['a', 'b']
const arr = ['a', 'b'];
console.log(Object.values(arr));
// ['a', 'b']
const obj = { 1: 'b', 0: 'a' };
console.log(Object.values(obj));
// ['a', 'b']
```
用于获取对象自身所有的可枚举的属性值，但不包括原型中的属性，然后返回一个由属性值组成的数组。


## Object.entries
```
const str = 'ab';
for (const [key, value] of Object.entries(str)) 
{    
    console.log(`${key}: ${value}`)
;}
// 0: a
// 1: bconst arr = ['a', 'b'];
for (const [key, value] of Object.entries(arr)) 
{    
    console.log(`${key}: ${value}`);
}
// 0: a
// 1: bconst obj = { 1: 'b', 0: 'a' };
for (const [key, value] of Object.entries(obj)) 
{   
 console.log(`${key}: ${value}`);
 }
// 0: a
// 1: b
```
用于获取对象自身所有的可枚举的属性值，但不包括原型中的属性，然后返回二维数组。每一个子数组由对象的属性名、属性值组成。可以同时拿到属性名与属性值的方法。

## Object.getOwnPropertyNames
```
Object.prototype.fun = () => {};
Array.prototype.fun = () => {};
const str = 'ab';
console.log(Object.getOwnPropertyNames(str));
// ['0', '1', 'length']
const arr = ['a', 'b'];
console.log(Object.getOwnPropertyNames(arr));
// ['0', '1', 'length']
const obj = { 1: 'b', 0: 'a' };
console.log(Object.getOwnPropertyNames(obj));
// ['0', '1']
```
用于获取对象自身所有的可枚举的属性值，但不包括原型中的属性，然后返回一个由属性名组成的数组。























