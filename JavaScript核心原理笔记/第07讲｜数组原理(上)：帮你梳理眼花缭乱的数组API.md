课前思考：

1. 数组的构造器有哪几种？
2. 哪些是改变自身的方法
3. 哪些是不改变自身的方法
4. 遍历的方法有哪些？


截至ES7规范，数组共包含33个标准的API方法和一个非标准的API方法

#### 一、Array的构造器

1. new Array()
    - 当new Array()参数为0，或参数长度大于等于2时，传入的参数将按照顺序依次成为新数组的第0至n项
    - new Array(len),参数len不是数值时，处理同上，返回一个只包含len元素一项的数组；当len为数字时，将生成一个长度为len，各项为空的数组。len最大不能超过32位无符号整型(Math.pow(2,32))，否则将抛出RangeError。
2. Array.from()
    - 只要某个对象内部设置了`迭代器`，Array.from就可以把这个对象变为数组
    - Array.from 有三个参数，其中第一个参数必选
        1. 类数组对象，必选
        2. 加工函数，新数组的每一项会经过该函数的加工再返回
        3. this作用域，表示加工函数中的this值
    
    ```javascript
    var obj = {0:'a',1:'b',2:'c',length:3}
    Array.from(obj,function(value,index){
        return value.repeat(3) // 必须指定返回值，否则返回Undefined
    },obj) // ['aaa','bbb','ccc']
    
    ```
3. Array.of()
    - 整体用的比较少，用于将参数依次转化为数组中的一项，与数组构造器功能基本一致，唯一区别是传递一个数字参数时：构造器生成长度为参数的空数组，Array.of()生成一个长度为1，内容为参数的数组
    
```javascript
Array.of(3); // [8]
new Array(3); // [empty * 8]

Array.of(3,8) // [3,8]
```

####  二、Array的判断

至少有六种方法来判断一个值是否为array

```javascript

var a = [];
// 1. 基于instanceof
a instanceof Array
// 2. 基于constructor
a.constructor === Array
// 3. 基于Object.prototype.isPrototypeOf
Array.prototype.isPrototypeOf(a)

// 4. 基于getPrototypeOf
Object.getPrototypeOf(a) === Array.prototype

// 5. 基于Object.prototype.toString
Object.prototype.toString.apply(a) === '[object Array]'

// 6. 基于ES6的isArray
Array.isArray(a)
```

#### 三、数组的基本方法

1. 改变自身的方法

    pop,push,shift,unshift,splice,sort,reverse,copyWithin,fill
    
2. 不会改变自身的方法

    concat,join,slice,toString,toLocaleString,indexOf,lastIndexOf,includes
    
3. 数组的遍历方法

    forEach,every,some,filter,map,reduce,reduceRight,find,findIndex,entries,keys,values
    
    