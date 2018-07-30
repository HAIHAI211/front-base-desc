# front-base-desc
原型链
    创建对象有几种方法
        1、字面量{}或new Object
        2、显式的构造函数
            var M = function(){}
            var o = new M()
        3、Object.create()
            var P = {name: 'harrison'}
            var p1 = Object.create(P)
    原型、构造函数、实例、原型链
        1、构造函数也是函数，在申明该函数时，JS引擎会给其加上prototype属性，该属性在函数申明时会被初始化成一个空对象。通常称之为原型对象。
        2、1中的原型对象，如何知道自己是哪个构造函数的原型呢？原型对象都有一个constructor属性，指向自己的构造函数。
        3、每个实例都拥有__proto__这个隐藏属性指向自己的原型对象（原型对象自然也是一种实例）
        构造函数                           原型对象                         原型对象
                  --------prototype----》    ------------__proto__--------------》
                 《-------constructor---
        4、原型链的顶端是Object.prototype对象
    instanceof的原理
        假设有某个实例a，某个类型B（构造函数）
        a instanceof B 的本质是：a.__proto__ === B.prototype || a.__proto__ === B.prototype.__proto__ .... 一直到Object.prototype
    new运算符

