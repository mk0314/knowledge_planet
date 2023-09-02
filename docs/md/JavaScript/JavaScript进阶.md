> ### === 和 == 区别

avaScript 中的===和==都是用于比较两个值的运算符，但它们的比较方式略有不同。

==运算符表示相等比较，它会先尝试将操作数转换为相同的类型，再进行比较。如果两个操作数类型不同，则会进行类型转换，将它们转换成相同的类型后再进行比较。这种类型转换称为隐式类型转换。例如：

```javascript
console.log(1 == '1'); // true
```

上述代码中，==运算符比较 1 和字符串"1"是否相等，由于两个操作数类型不同，JavaScript 进行了隐式类型转换，将字符串"1"转换成了数字 1，然后比较它们的值，结果为 true。

===运算符表示严格相等比较，它不进行类型转换，只有当两个操作数类型相同并且值相等时才返回 true。例如：

```javascript
console.log(1 === '1'); // false
```

由于===不进行类型转换，所以 1 和字符串"1"并不相等，结果为 false。

因此，建议在比较两个值是否相等时，使用===运算符进行严格比较，避免隐式类型转换带来的误判。只在确实需要进行类型转换时，使用==运算符进行比较。

> ### for in 、forEach、for of 区别

JavaScript 中的 for-in、forEach 和 for-of 是三种遍历数组或对象的方式，它们的使用场景和行为有所不同。

for-in：用于遍历对象的可枚举属性。for-in 语句循环遍历对象中所有可枚举属性，包括原型链上的属性。for-in 的语法如下：

```javascript
for (variable in object) {
    // code to be executed
}
```

其中，variable 是一个变量，用来存储对象中的每个属性名，object 是要遍历的对象，代码块中的语句会被执行一次，为每个可枚举属性执行一次。

forEach：用于遍历数组，对数组中的每个元素执行指定的函数。forEach 函数不返回任何值，其语法如下：

```javascript
array.forEach(function(currentValue, index, arr), thisValue)
```

其中，function 是要执行的函数，currentValue 是当前元素的值，index 是当前元素对应的索引，arr 是数组本身，thisValue 是可选参数，用来指定当调用回调函数时要使用的 this 值。

for-of：ES6 新增的一种遍历方式，用于遍历可迭代对象，如数组、字符串、Set、Map 等。for-of 遍历的是值而非键，不需要通过索引去访问数组元素。for-of 的语法如下：

```javascript
for (variable of iterable) {
    // code to be executed
}
```

其中，variable 是一个变量，用来存储当前迭代的值，iterable 是要遍历的可迭代对象，代码块中的语句会被执行一次，为每个元素执行一次。

需要注意的是，for-in 和 forEach 遍历的是元素的值，而 for-in 遍历的是对象属性的键名。此外，for-in 比其他两个方法更耗费性能，在遍历数组时会遍历所有原型链上的属性。建议在遍历数组时使用 for-of 或 forEach，而在遍历对象时使用 for-in。

> ### 手写 Promise

```js
class MyPromise {
    constructor(executor) {
        this.status = 'pending';
        this.value = null;
        this.reason = null;

        const resolve = (value) => {
            if (this.status === 'pending') {
                this.status = 'fulfilled';
                this.value = value;
            }
        };

        const reject = (reason) => {
            if (this.status === 'pending') {
                this.status = 'rejected';
                this.reason = reason;
            }
        };

        try {
            executor(resolve, reject);
        } catch (err) {
            reject(err);
        }
    }

    then(onFulfilled, onRejected) {
        if (this.status === 'fulfilled') {
            onFulfilled(this.value);
        }

        if (this.status === 'rejected') {
            onRejected(this.reason);
        }
    }

    catch(onRejected) {
        if (this.status === 'rejected') {
            onRejected(this.reason);
        }
    }
}
```

> ### call、bind、apply 的区别

call、 bind、apply 都是用来改变函数的上下文（this 指向）的方法。

它们都接收两个参数，第一个参数都是要改变上下文的对象，第二个参数都是要传递给函数的参数。

-   call 方法：call 方法允许你显示的设置函数的 this 值，并立即执行该函数，它接受一个对象作为第一个参数，这个对象成为函数执行时的 this 值，然后是参数列表，call 方法可以传递多个参数作为函数的参数。

```js
function greet(name) {
    console.log('Hello ' + name);
}

const person = { name: 'John' };

greet.call(person, 'Jack'); // 'Hello Jack'
```

#### call 函数内部做了什么

1. 函数通过**proto**原型链找到了 Function.protottype 上的 call 方法

2. 确定 this 为执行函数

3. 接下来要执行函数，但是执行函数的上下文需要传递进来的第一个参数，所以想办法改变 this 的指向

4. 正式执行函数，并返回执行结果

### call 基础版实现

```js
Function.prototype.myCall = function (context, ...args) {
    // 第一步：this就是对应的执行函数，也就是调用函数fun
    const self = this;
    // 第二步：想要执行函数时需要函数的上下文传入的上下文，想要改变调用上下文最好的办法是直接上下文对象调用函数，这时候函数内部的this就指向了上下文

    // 一个小结论 xx1.xx2 xx2的this指向了xx1

    // 使用symbol类型可以保证属性名的唯一性，而且不会被遍历枚举出来

    const symbolKey = Symbol('fun');
    content[symbolKey] = self;

    // 第三步：执行函数，并返回执行结果

    const result = context[symbolKey](...args);

    // 第四步：删除属性，防止内存泄漏

    delete content[symbolKey];

    // 返回结果
    return result;
})


// 测试
const fun = function (params) {
    let a = this.a
    console.log(a, params)
}

fun.call({a: 233}, '哈哈哈哈')
```

> ### 函数的柯里化

函数的柯里化是一种将接受多个参数的函数转换为一系列接受单个参数的函数技术

通过函数的柯里化可以将一个参数变得更加的灵活、可组合，并且更容易进行部分应用。

在函数柯里化中，函数的第一个参数是函数的执行上下文，第二个参数开始才是函数的参数。

每个函数都会返回一个新的函数，接受下一个参数，直到所有参数都被传入，然后执行函数，最终返回结果。

举个栗子：

```js
function curry(fn) {
    return function curried(...args) {
        if (args.length >= fn.length) {
            return fn(...args);
        } else {
            return function (...args2) {
                return curried(...args, ...args2);
            };
        }
    };
}

function sum(a, b, c) {
    return a + b + c;
}

const curriedSum = curry(sum);
curriedSum(1)(2)(3); // 6
```
