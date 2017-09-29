# Javascript 写法规范

## JS没有什么硬性的写法规范, 主要还是缩进, 命名之类的, 只要编辑器的风格统一即可


## 命名

常亮: 全部字母大写，单词间下划线分隔 的命名方式
示例: 
```javascript
var HTML_ENTITY = {};
```

变量: Camel命名法, 即驼峰写法
示例: 
```javascript
function stringFormat(source) {
}
```

类: Pascal命名法, 即首字母大写的驼峰写法
示例: 
```javascript
function TextNode(options) {
}
```

boolean 类型的变量使用 is 或 has 开头。
示例: 
```javascript
var isReady = false;
var hasMoreCommands = false;
```

动作执行函数, 用动词开头
示例: 
```javascript
function getData(){}
function setState(){}
```

##变量

1. 避免定义全局变量. 减少使用.
2. 使用前先定义.


## 条件
1. 明白 `==` 和 `===` 的区别, 尽量使用 `===` 来判断.


2. 尽可能使用简洁的表达式.
示例:
```javascript
// 字符串为空

// good
if (!name) {
    // ......
}

// bad
if (name === '') {
    // ......
}
```

```javascript
// 字符串非空

// good
if (name) {
    // ......
}

// bad
if (name !== '') {
    // ......
}
```

```javascript
// 数组非空

// good
if (collection.length) {
    // ......
}

// bad
if (collection.length > 0) {
    // ......
}
```

```javascript
// 布尔不成立

// good
if (!notTrue) {
    // ......
}

// bad
if (notTrue === false) {
    // ......
}
```

```javascript
// null 或 undefined

// good
if (noValue == null) {
  // ......
}

// bad
if (noValue === null || typeof noValue === 'undefined') {
  // ......
}
```

3. 尽量使用三元表达式对变量赋值. 减少 if else的使用, 特别是else.


## 类型

###类型检测
基础类型使用 typeOf判断 。对象类型检测使用 instanceof 或者 Object.prototype.String.call(Array) === "[object Array]"。判断 undefined 使用 typeof variable === 'undefined', 尽量不要直接if(aa){}
示例:

```javascript
// string
typeof variable === 'string'

// number
typeof variable === 'number'

// boolean
typeof variable === 'boolean'

// Function
typeof variable === 'function'

// Object
typeof variable === 'object'

// RegExp
variable instanceof RegExp

// Array
variable instanceof Array

// null
variable === null

// undefined
typeof variable === 'undefined'
```


###类型转换

1. 转换成 string 时，使用 + ''。
2. 转换成 number 时，通常使用 +。
示例：
```javascript
// good
+str;

// bad
Number(str);
```

3. number 去除小数点，使用 Math.floor / Math.round / Math.ceil，不使用 parseInt。
示例：
```javascript
// good
var num = 3.14;
Math.ceil(num);

// bad
var num = 3.14;
parseInt(num, 10);
```

###字符串
1. 使用 数组 或 + 拼接字符串。
解释：

使用 + 拼接字符串，如果拼接的全部是 StringLiteral，压缩工具可以对其进行自动合并的优化。所以，静态字符串建议使用 + 拼接。
在现代浏览器下，使用 + 拼接字符串，性能较数组的方式要高。
如需要兼顾老旧浏览器，应尽量使用数组拼接字符串。

示例：
```javascript
// 使用数组拼接字符串
var str = [
    // 推荐换行开始并缩进开始第一个字符串, 对齐代码, 方便阅读.
    '<ul>',
        '<li>第一项</li>',
        '<li>第二项</li>',
    '</ul>'
].join('');

// 使用 `+` 拼接字符串
var str2 = '' // 建议第一个为空字符串, 第二个换行开始并缩进开始, 对齐代码, 方便阅读
    + '<ul>',
    +    '<li>第一项</li>',
    +    '<li>第二项</li>',
    + '</ul>';
```

##函数
1.一个函数的长度控制在 50 行以内。

2.一个函数的参数控制在 6 个以内。

3.声明类时，保证 constructor 的正确性。
示例：
```javascript
function Animal(name) {
    this.name = name;
}

// 直接prototype等于对象时，需要修正constructor
Animal.prototype = {
    constructor: Animal,

    jump: function () {
        alert('animal ' + this.name + ' jump');
    }
};

// 这种方式扩展prototype则无需理会constructor
Animal.prototype.jump = function () {
    alert('animal ' + this.name + ' jump');
};
```





