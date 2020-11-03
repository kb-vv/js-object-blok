# 《js对象的基本用法》
## 1.定义：
* 是无序的数据集合，键值对的集合。
## 2.写法：
* 简单写法：
  ```javascript
  let obj = { 'name': 'llw', 'age': 18 }
  ```
* 正规写法：
  ```javascript
  let obj = new Object({'name': 'llw'})
  ```
* 每个对象里面可以没有或一对或者多对属性名和属性值
   
   1.属性名：属性名是字符串可以包含任意字符。（每个 key 都是对象的属性名）；查看对象属性名`Object.keys(obj)`
   
   
   2.属性值：每个属性名后面接一个属性值，用冒号：连接，冒号可以省略，但省略后属性名就只能是标识符，但是中还是一个字符串。查看属性值`Object.values(obj)`

## 3.对象属性的删除：
* `delete obj.xxx` 或 `delete obj['xxx']`
即可删除 obj 的 xxx 属性


   注意：请区分属性值为 undefined和不含属性名，不含属性名的意思是没有属性名和属性值，属性值为 undefined是含有属性名

   1.查看该对象是否含有该属性名`'xxx' in obj` false表示没有，true表示有。

   2.查看含有属性名，但是值为 undefined，`'xxx' in obj && obj.xxx === undefined` true为是，false为不是。

## 4.查看所有属性（读属性）
* 查看自身所有属性
    
    `Object.keys(obj)`
* 查看自身+共有属性
    
    `console.dir(obj)`
* 判断一个属性是自身的还是共有的
`obj.hasOwnProperty('toString')`
* 查看属性值
  
   1.中括号语法：`obj['key']`。

   2.点语法：`obj.key`

   注意：obj.name 等价于 obj['name']但是obj.name 不等价于 obj[name]

## 5.修改或增加属性（写属性）
* 直接赋值
   
   1.`let obj = {name: 'llw'}` // name 是字符串
   
   2.`obj.name = 'llw'` // name 是字符串
   
   3.`obj['name'] = 'llw'` 

   4.`obj['na'+'me'] = 'llw'`
   
   5.`let key = 'name'; obj[key] = 'llw'`
* 批量赋值
  
  `Object.assign(obj, {age: 18, gender: 'man'})`
* 修改或增加原型上的属性
  
  `obj.__proto__.toString = 'xxx'` // 不推荐用

  `Object.prototype.toString = 'xxx'` 

  一般来说，不要修改原型，会引起很多问题
* 修改隐藏属性

   不推荐使用 `__proto__`

   `let obj = {name:'llw'}`

   `let obj2 = {name: 'jack'}`

   `let common = {kind: 'human'}`

   `obj.__proto__ = common`

   `obj2.__proto__ = common`
   
   推荐使用 `Object.create`

  `let obj = Object.create(common)`

  `obj.name = 'llw'`

  `let obj2 = Object.create(common)`

  `obj2.name = 'jack'`

  规范大概的意思是，要改就一开始就改，别后来再改
## 原型
* 每个对象都有原型
  
  1.原型里存着对象的共有属性比如obj 的原型就是一个对象obj.__proto__ 存着这个对象的地址这个对象里有 toString /constructor / valueOf 等属性
* 对象的原型也是对象

  1.所以对象的原型也有原型obj = {} 的原型即为所有对象的原型这个原型包含所有对象的共有属性，是对象的根，这个原型也有原型，是 null








