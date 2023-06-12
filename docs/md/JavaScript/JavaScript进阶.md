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
