<template>
<div class="ex-content">
    <div class="ex-card">
    <mark>
        <textarea class="ex-mark-text">
> 1、说说你对 this 的理解？

- this 是一个关键字，它代表函数运行时，自动生成的一个内部对象，只能在函数内
部使用。
- 作为纯粹的函数调用 this 指向全局对象
- 作为对象的方法调用 this 指向调用对象
- 作为构造函数被调用 this 指向新的对象（new 会改变 this 的指向）
- apply 调用 this 指向 apply 方法的第一个参数

> 2、介绍一下 JS 有哪些内置对象。

- Object 是 JavaScript 中所有对象的父对象
- 数据封装类对象：Object、Array、Boolean、Number、String
- 其他对象：Function、Argument、Math、Date、RegExp、Error

> 3、什么是闭包？

- 简单的说，作用域是针对变量的，比如我们创建一个函数 a1，函数里面又包了一
个子函数 a2。此时就存在三个作用域：
- 全局作用域、a1 作用域、a2 作用域；即全局作用域包含了 a1 的作用域，a2 的作用
域包含了 a1 的作用域。
- 当 a1 在查找变量的时候会先从自身的作用域区查找，找不到再到上一级 a2 的作用域
查找，如果还没找到就到全局作用域区查找，这样就形成了一个作用域链。
- 理解闭包首先要理解，js 垃圾回收机制，也就是当一个函数被执行完后，其作用域会被
收回，如果形成了闭包，执行完后其作用域就不会被收回。
- 如果某个函数被他的父函数之外的一个变量引用，就会形成闭包。
- 闭包的作用，就是保存自己私有的变量，通过提供的接口（方法）给外部使用，但外部
不能直接访问该变量。

> 4、什么是原型链？

Javascript 是面向对象的，每个实例对象都有一个__proto_属性，该属性指向它原
型对象，这个实例对象的构造函数有一个原型属性 prototype，与实例的__proto__属性指
向同一个对象。当一个对象在查找一个属性的时，自身没有就会根据__proto__ 向它的原型
进行查找，如果都没有，则向它的原型的原型继续查找，直到查到
Object.prototype._proto_为 null，这样也就形成了原型链。

> 5、js实现的几种继承方式

* 第一种： 借用构造函数继承 :可以继承实例属性。但是原型中的方法无法继承

```javascript
// - 设置需要被继承的构造函数Animal
function Animal(name,age){
    this.name = name;
    this.age = age;
}


Animal.prototype.eat = function(){
    console.log("吃各种吃的");
};

//再设置一个猫咪构造函数

//思考：已经存在的构造函数Animal中具有了一些属性和方法，这些属性与方法时Cat构造函数需要的
//      没有必要再书写一遍了，可以使用继承的方式获取
function Cat(name,age){
    //通过call的方式，修改Animal中的this指向为当前Cat的this，并设置参数
    Animal.call(this,name,age);
}

var c1 = new Cat("jack",18);
console.log(c1);
```

* 第二种：原型继承  

    好处：可以继承原型中的方法 <br>
    缺点：①实例属性虽然有，但是无法传参(跟没有一样) <br>
　　　   ②要想为子类新增属性和方法，必须要在new Animal()这样的语句之后执行 否则会被覆盖<br>
　　　   ③无法实现多继承<br>
　　　   ④需要重新设置被覆盖的constructor属性 让constructor重新指向Cat

```javascript
function Animal(name,age){
    this.name = name;
    this.age = age;
}
Animal.prototype.eat = function(){
    console.log("吃各种吃的");
};


function Cat(color){
    this.color = color;
}

//继承的核心代码：
Cat.prototype = new Animal("jack",18);///这点是重要点：必须写在前面 ，否则会覆盖子类的方法

//设置被覆盖的constructor属性 让constructor重新指向Cat
Cat.prototype.constructor = Cat;
Cat.prototype.shangShu = function(){
    console.log("猫咪可以爬树");
};

var c1=new Cat();
console.log(c1);
console.log(c1.name)//jack
console.log(c1.age)//18
通过原型链的方法可以查找到属性，但是无法传参
　　　　　

原型链：查找规则，优先查找自身，如果没有则查找__proto__中是否存在；
原型链是用来描述实例对象与原型对象之间关系的一种方式。
```

* 第三种:组合继承

使用前面两种继承方式时发现各有优缺点，所以将两种方式结合即可
这种结合使用的方式称为组合继承,组合继承是最常用的一种继承方式。   

```javascript

function Animal(name,age){
    this.name = name;
    this.age = age;
}
Animal.prototype.eat = function(){
    console.log("吃各种吃的");
};

function Cat(name,age,color){
//使用借用构造函数的方式继承：
    Animal.call(this,name,age);
    this.color = color;
}

//原型继承的核心代码：
//使用组合继承方式后，在构造函数体中就设置了实例属性，此处不需要传参
Cat.prototype = new Animal();

//设置被覆盖的constructor属性
Cat.prototype.constructor = Cat;
Cat.prototype.shangShu = function(){
console.log("猫咪可以爬树");
};

var c1 = new Cat("rose",20,"red");
console.log(c1);
在这总结一下原型链:
原型链：查找规则，优先查找自身，如果没有则查找__proto__中是否存在；
原型链是用来描述实例对象与原型对象之间关系的一种方式
①Animal构造函数在设置时没用继承自其它的构造函数
②Animal的原型对象也是一个对象
③对象都是通过Object这个构造函数创建的
④Animal.prototype这个对象__proto__就应该指向Object.prototype
⑤通过观察我们发现确实含有一个属性constructor，并且值为Object构造函数
⑥Object.prototype中没有__proto__属性了，说明这个对象是原型对象的终点。
若果使用一个对象的属性时，在整个原型对象中均没找到，值即为undefined 
Object.prototype.__proto__打印为null
扩展：在作用域中，都没有找到会报错
```

* 第四种:对组合继承的优化方式 

个人认为:
虽然可以省去不需要继承的实例属性
这种方式的确会比组合继承的方式性能更好，但是略麻烦(了解即可)

```javascript
function Animal(name,age){
    this.name = name;
    this.age = age;
}
Animal.prototype.eat = function(){
    console.log("吃各种吃的");
};


function Cat(name,age,color){
    //使用借用构造函数的方式继承：
    Animal.call(this,name,age);
    this.color = color;
}

//原型继承方式中希望获取到Animal的原型方法
//Cat.prototype = new Animal();


//可以省去不需要继承的实例属性
//这种方式的确会比组合继承的方式性能更好，但是略麻烦(了解即可)
function Fun (){}
Fun.prototype = Animal.prototype;
Cat.prototype = new Fun();

Cat.prototype.constructor = Cat;
Cat.prototype.shangShu = function(){
    console.log("猫咪可以爬树");
};

var c1 = new Cat("rose",20,"red");
console.log(c1);

```
* 第五种:拷贝继承 

使用继承的原型中的方法时，查找的次数会降低
效率较低，内存占用高（因为要拷贝父类的属性）

```javascript
function Animal(name,age){
    this.name = name;
    this.age = age;
}
Animal.prototype.eat = function(){
    console.log("吃各种吃的");
};
　　　　　　
function Cat(name,age){
　　Animal.call(this,name,age)
}

//核心代码

for(var k in Animal.prototype){
　　Cat.prototype[k] = Animal.prototype[k];//添加属性
}

Cat.prototype.constructor = Cat;
    Cat.prototype.shangShu = function(){
    console.log("猫咪可以爬树");
};

var c1 = new Cat("rose",20,"red");
console.log(c1);
```
* 补充一下:对象之间的继承:

```javascript
var obj={
    name:'jack',
    age:12,
    gender:'男',
    sayHai:function(){
    console.log('我是人')
}
}
问题：obj2想要继承obj的属性
1)拷贝继承：
var obj2={};
for(var k in obj){
    obj2[k]=obj[k];
}
2)原型继承：
function Fun(){};
Fun.prototype=obj;
var obj2=new Fun();
console.log(obj2);
```

> 6、请列举字符串操作的方法。

- charCodeAt 方法返回一个整数，代表指定位置字符的 Unicode 编码；
- charAt 方法返回指定索引位置处的字符。如果超出有效范围的索引值返回空字符串；
- slice 方法返回字符串的片段；
- substring 方法返回位于 String 对象中指定位置的子字符串。
- substr 方法返回一个从指定位置开始的指定长度的子字符串。
- indexOf 方法返回 String 对象内第一次出现子字符串位置。如果没有找到子字符串，
则返回-1；
- lastIndexOf 方法返回 String 对象中字符串最后出现的位置。如果没有匹配到子字符
串，则返回-1；
- search 方法返回与正则表达式查找内容匹配的第一个字符串的位置。
- concat 方法返回字符串值，该值包含了两个或多个提供的字符串的连接；
- split 将一个字符串分割为子字符串，然后将结果作为字符串数组返回；

> 7、Javascript 内置的常用对象有哪些？并列举该对象常用的方法？

Arguments 函数参数集合

* arguments[ ] 函数参数的数组
* Arguments 一个函数的参数和其他属性
* Arguments.callee 当前正在运行的函数
* Arguments.length 传递给函数的参数的个数

Array 数组

- length 属性 动态获取数组长度
- join() 将一个数组转成字符串。返回一个字符串。
- reverse() 将数组中各元素颠倒顺序
- delete 运算符 只能删除数组元素的值，而所占空间还在，总长度没变(arr.length)。
- shift() 删除数组中第一个元素，返回删除的那个值，并将长度减 1。
- pop() 删除数组中最后一个元素，返回删除的那个值，并将长度减 1。
- unshift() 往数组前面添加一个或多个数组元素，长度要改变。arrObj.unshift(“a” ，
“b，“c”)
- push() 往数组结尾添加一个或多个数组元素，长度要改变。arrObj.push(“a” ，“b”，
“c”)
- concat( ) 连接数组
- slice( ) 返回数组的一部分
- sort( ) 对数组元素进行排序
- splice( ) 插入、删除或替换数组的元素
- toLocaleString( ) 把数组转换成局部字符串
- toString( ) 将数组转换成一个字符串

Boolean 布尔对象

* Boolean.toString( ) 将布尔值转换成字符串
* Boolean.valueOf( ) Boolean 对象的布尔值

Date 日期时间

- Date.getDate( ) 返回一个月中的某一天
- Date.getDay( ) 返回一周中的某一天
- Date.getFullYear( ) 返回 Date 对象的年份字段
- Date.getHours( ) 返回 Date 对象的小时字段
- Date.getMilliseconds( ) 返回 Date 对象的毫秒字段
- Date.getMinutes( ) 返回 Date 对象的分钟字段
- Date.getMonth( ) 返回 Date 对象的月份字段
- Date.getSeconds( ) 返回 Date 对象的秒字段
- Date.getTime( ) 返回 Date 对象的毫秒表示

Error 异常对象

- Error.message 可以读取的错误消息
- Error.name 错误的类型
- Error.toString( ) 把 Error 对象转换成字符串
- EvalError 在不正确使用 eval()时抛出
- SyntaxError 抛出该错误用来通知语法错误
- RangeError 在数字超出合法范围时抛出
- ReferenceError 在读取不存在的变量时抛出
- TypeError 当一个值的类型错误时，抛出该异常
- URIError 由 URl 的编码和解码方法抛出

Function 函数构造器

- Function.apply( ) 将函数作为一个对象的方法调用
- Function.arguments[] 传递给函数的参数
- Function.call( ) 将函数作为对象的方法调用
- Function.caller 调用当前函数的函数
- Function.length 已声明的参数的个数
- Function.prototype 对象类的原型
- Function.toString( ) 把函数转换成字符串
        </textarea>
    </mark>
    </div>
</div>
</template>
<script>
import { Mark } from '../index'
export default {
    components: {
        Mark
    }
}
</script>