---
title: 7种创建对象方法
date: 2016-11-16 14:09:54
tags: [javascript,7种创建对象的方法]
---


# 7种对象的创建方法


#### 最近在复习红宝书的对象一章，红宝书中一共提到了7种创建对象的方式（这里所说的对象更偏向于面向对象编程中的对象）。7种方式分别是：

* 工厂模式
* 构造函数模式
* 原型模式
* 构造函数和原型组合模式
* 动态原型模式
* 寄生构造模式
* 稳妥构造模式

#### 首先先解释几个概念

1、 对象下面例子中所有的Person函数

2、 实例/对象实例 通过 `new Person()` or 	`Person()`返回的对象，如`var person1 = new Person()`中的person1

3、 原型对象`Person.prototype` 



### <font style="color:orange">工厂模式</font>

	function Person() {
 	  var o = new Object();
  	  o.name = 'hanmeimei';
  	  o.say = function() {
    	alert(this.name);
     }
  	  return o;
	 }
	 var person1 = Person();
	 


##### <font style="color:red">优点：</font>完成了返回一个对象的要求。


##### <font style="color:red">缺点：</font>

###### 1.无法通过constructor识别对象，以为都是来自Object，无法得知来自Person
###### 2.每次通过Person创建对象的时候，所有的say方法都是一样的，但是却存储了多次，浪费资源。


### <font style="color:orange">构造函数模式</font>

	function Person() {
  		this.name = 'hanmeimei';
  		this.say = function() {
    		alert(this.name)
  		}
	  }
	var person1 = new Person();
	 

##### <font style="color:red">优点：</font>
###### 1.通过constructor或者instanceof可以识别对象实例的类别
###### 2.可以通过new 关键字来创建对象实例，更像OO语言中创建对象实例

##### <font style="color:red">缺点：</font>

###### 多个实例的say方法都是实现一样的效果，但是却存储了很多次（两个对象实例的say方法是不同的，因为存放的地址不同）


#### <font style="color:red">注意：</font>


1. 构造函数模式隐试的在最后返回`return this` 所以在缺少new的情况下，会将属性和方法添加给全局对象，浏览器端就会添加给window对象。
2. 也可以根据`return this` 的特性调用call或者apply指定this。这一点在后面的继承有很大帮助。

### <font style="color:orange">原型模式</font>

	function Person() {}
	Person.prototype.name = 'hanmeimei';
	Person.prototype.say = function() {
 		 alert(this.name);
	}
	Person.prototype.friends = ['lilei'];
	var person1 = new Person();
	
##### <font style="color:red">优点：</font>

###### 1.say方法是共享的了，所有的实例的say方法都指向同一个。

###### 2.可以动态的添加原型对象的方法和属性，并直接反映在对象实例上。

	var person1 = new Person()
	Person.prototype.showFriends = function() {
  		console.log(this.friends)
	}
	person1.showFriends()  //['lilei']
	
##### <font style="color:red">缺点：</font>	

###### 1.出现引用的情况下会出现问题具体见下面代码：

	var person1 = new Person();
	var person2 = new Person();
	person1.friends.push('xiaoming');
	console.log(person2.friends)  //['lilei', 'xiaoming']
	
###### 因为js对引用类型的赋值都是将地址存储在变量中，所以person1和person2的friends属性指向的是同一块存储区域。


###### 2.第一次调用say方法或者name属性的时候会搜索两次，第一次是在实例上寻找say方法，没有找到就去原型对象(Person.prototype)上找say方法，找到后就会在实力上添加这些方法or属性。	


###### 3.所有的方法都是共享的，没有办法创建实例自己的属性和方法，也没有办法像构造函数那样传递参数。


#### <font style="color:red">注意：</font>

###### 1.优点②中存在一个问题就是直接通过对象字面量给`Person.prototype`进行赋值的时候会导致`constructor`改变，所以需要手动设置，其次就是通过对象字面量给`Person.prototype`进行赋值，会无法作用在之前创建的对象实例上

	var person1 = new Person()
	Person.prototype = {
			name: 'hanmeimei2',
  			setName: function(name){
      		this.name = name
  		}
	}
	person1.setName()   //Uncaught TypeError: person1.set is not a 	function(…)
	
####### 这是因为对象实例和对象原型直接是通过一个指针链接的，这个指针是一个内部属性[[Prototype]]，可以通过`__proto__`访问。我们通过对象字面量修改了Person.prototype指向的地址，然而对象实例的`__proto__`，并没有跟着一起更新，所以这就导致，实例还访问着原来的`Person.prototype`，所以建议不要通过这种方式去改变`Person.prototype`属性


### <font style="color:orange">构造函数和原型组合模式</font>


	function Person(name) {
  		this.name = name
  		this.friends = ['lilei']
	}
	Person.prototype.say = function() {
  		console.log(this.name)
	}
	var person1 = new Person('hanmeimei')
	person1.say() //hanmeimei

##### <font style="color:red">优点：</font>

1. 解决了原型模式对于引用对象的缺点
2. 解决了原型模式没有办法传递参数的缺点
3. 解决了构造函数模式不能共享方法的缺点


##### <font style="color:red">缺点：</font>


###### 和原型模式中注意①一样 （可以动态的添加原型对象的方法和属性，并直接反映在对象实例上。针对这个问题中存在一个问题就是直接通过对象字面量给Person.prototype进行赋值的时候会导致constructor改变，所以需要手动设置，其次就是通过对象字面量给Person.prototype进行赋值，会无法作用在之前创建的对象实例上）

### <font style="color:orange">动态原型模式</font>

	function Person(name) {
 		 this.name = name
  		 if(typeof this.say != 'function') {
    		Person.prototype.say = function(
    		alert(this.name)
  		}
	}

##### <font style="color:red">优点：</font>	

1. 可以在初次调用构造函数的时候就完成原型对象的修改
2. 修改能体现在所有的实例中


##### <font style="color:red">缺点：</font>

###### 红宝书都说这个方案完美了。。。。

### <font style="color:orange">寄生构造函数模式</font>

	function Person(name) {
  		var o = new Object()
 		o.name = name
 		o.say = function() {
    		alert(this.name)
 		 }
  			return o
		}
	var peron1 = new Person('hanmeimei')
	
##### <font style="color:red">优点：</font>	

###### 和工厂模式基本一样，除了多了个new操作符

##### <font style="color:red">缺点：</font>

###### 和工厂模式一样，不能区分实例的类别


### <font style="color:orange">稳妥构造模式</font>
	
	function Person(name) {
 		var o = new Object()
  		o.say = function() {
    	alert(name)
  	 }
	}
	var person1 = new Person('hanmeimei');
	person1.name  // undefined
	person1.say() //hanmeimei
	
##### <font style="color:red">优点：</font>	

###### 安全，name好像成为了私有变量，只能通过say方法去访问


##### <font style="color:red">缺点：</font>

###### 不能区分实例的类别
	
🔗原文链接: [http://alvinyuxt.github.io/2016/11/11/%E8%AF%BB%E4%B9%A6%E7%AC%94%E8%AE%B0%E4%B9%8B%E5%88%9B%E5%BB%BA%E5%AF%B9%E8%B1%A1/) by @alvinyuxt