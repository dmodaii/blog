
# 属性说明

constructor 属性返回对创建此对象的数组函数的引用

- 判断类型
  - data.constructor 
  
    Array Boolean Date Date
  - Object.prototype.toString.call(data)

```javascript

//  [].constructor === Array    Array === Array.prototype.constructor
function Father() {}
Father === Father.prototype.constructor

```

# 原型链中的使用

constructor是原型对象上的一个属性，默认指向这个原型的构造函数。


```javascript
function F() {
// some code
}
// JavaScript 内部会执行如下几个动作：
1.为该函数添加一个原形（即 prototype）属性 
2. 为 prototype 对象额外添加一个 constructor 属性，并且该属性保存指向函数F 的一个引用
```


```javascript
function Person(area){
  this.type = 'person';
  this.area = area;
}
Person.prototype.sayArea = function(){
  console.log(this.area);
}
// Father的prototype 有一个constructor 为 Father(age){this.age = age;}  的函数
function Father(age){
  this.age = age;
} 
// 更改了Father的原型属性， 此时constructor 为Person
Father.prototype = new Person('Beijin');  // 此时 Person.prototype.constructor和Father.prototype.constructor 都是function Person()

Father.prototype.constructor = Father; // 修正原型属性中的constructor属性
```