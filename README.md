# front-base-desc
# 原型链
    # 创建对象有几种方法
        1、字面量{}或new Object
        2、显式的构造函数
            var M = function(){}
            var o = new M()
        3、Object.create()
            var P = {name: 'harrison'}
            var p1 = Object.create(P)
    # 原型、构造函数、实例、原型链
        1、构造函数也是函数，在申明该函数时，JS引擎会给其加上prototype属性，该属性在函数申明时会被初始化成一个空对象。通常称之为原型对象。
        2、1中的原型对象，如何知道自己是哪个构造函数的原型呢？原型对象都有一个constructor属性，指向自己的构造函数。
        3、每个实例都拥有__proto__这个隐藏属性指向自己的原型对象（原型对象自然也是一种实例）
        构造函数                           原型对象                         原型对象
                  --------prototype----》    ------------__proto__--------------》
                 《-------constructor---
        4、原型链的顶端是Object.prototype对象
    # instanceof的原理
        假设有某个实例a，某个类型B（构造函数）
        a instanceof B 的本质是：a.__proto__ === B.prototype || a.__proto__ === B.prototype.__proto__ .... 一直到Object.prototype
        因此如果a继承了B，B继承了C
        那么instanceof 无法判断出a到底是B还是C的实例。这时候需要结合constructor来判断
        a instanceof B && a.__proto__.constructor === B即可判断a是否是B的实例(在原型链上并且B就是a对象的原型对象的构造函数)
    # new运算符背后发生了什么
        以 new A() 举例
        1、生成一个空对象，继承自A.prototype，类似于Object.create(A.prototype)。在此暂时称该空对象为tempA
        2、执行A构造函数，并将tempA作为函数执行的上下文，类似于A.call(tempA)
        3、如果A的执行结果会返回一个“对象”，那么该对象会取代tempA作为最终的结果，反之tempA就是最终的结果

        function fakeNew (Func) {
            const o = Object.create(Func.prototype)
            const result = Func.call(o)
            return typeof result === 'object' ? result: o
        }

# 面向对象
    # 类与实例
        类的声明
        生成实例
    # 类与继承
        如何实现继承
        继承的几种方式
