在 Python 中，Iterator（迭代器）和 Generator（生成器）是两个常见的概念，它们都可以用于遍历序列或集合，并且在使用时都可以通过 for 循环来迭代获取下一个元素。

### Iterator（迭代器）

Iterator 是 Python 的一个内置类，它实现了**iter**和**next**方法，并且可以通过内置函数 iter()来创建一个迭代器对象。迭代器对象通常用于遍历数据集合，获取序列或集合中的每个元素。

```python
# 创建一个列表
my_list = [1, 2, 3, 4, 5]

# 创建一个迭代器对象
my_iter = iter(my_list)

# 使用循环获取迭代器中的元素
while True:
    try:
        item = next(my_iter)
        print(item)
    except StopIteration:
        break
```

在这个例子中，我们首先使用内置函数 iter()创建了一个迭代器对象 my_iter，然后使用循环和内置函数 next()获取迭代器中的元素。当到达迭代器的末尾时，会抛出 StopIteration 异常，此时我们通过捕获异常来结束循环。

### Generator（生成器）

Generator 是一种特殊的迭代器，它是通过函数来实现的，使用 yield 关键字来返回一个值并暂停函数的执行。和迭代器一样，生成器也可以用于遍历数据集合，获取序列或集合中的每个元素。但是，相对于迭代器而言，生成器更加灵活和高效，并且减少了许多工作量。

例如：

```python
# 创建一个生成器函数
def my_generator(n):
    for i in range(n):
        yield i ** 2

# 创建一个生成器对象
gen = my_generator(5)

# 使用循环获取生成器中的元素
for item in gen:
    print(item)
```

在这个例子中，我们定义了一个生成器函数 my_generator，并使用 yield 关键字来返回一个值并暂停函数的执行。然后我们通过 for 循环获取生成器中的元素，和迭代器类似。需要注意的是，每次使用生成器函数创建一个新的生成器对象，因此无法通过多个迭代器对象同时遍历同一个生成器。

总的来说，Iterator 和 Generator 都是在 Python 中用于遍历数据集合的一种机制，其中 Iterator 是一种基本的迭代器概念，它通常用于遍历序列或集合；Generator 则是一种特殊的生成器概念，它是通过函数来实现的，并且具有更高的灵活性和效率。

### 波非那切数列

```python
def fibonacci(n):
    a, b = 0, 1
    for i in range(n):
        yeild a
        a, b = b, a + b
fib = fibonacci(n)
for i in fib:
    print(i)

```

### 区别

1. 实现方式不同
   Iterator 是 Python 中的一个内置类，它是通过实现**iter**和**next**方法来实现的，它可以用于遍历数据集合，获取序列或集合中的每个元素。而 Generator 则是一种特殊的生成器概念，它是通过函数来实现的，使用 yield 关键字来返回一个值并暂停函数的执行。

2. 使用方式不同
   Iterator 通常需要手动创建迭代器对象并使用 while 循环或 try-except 结构来遍历数据集合，如前面提到的例子；而 Generator 则是通过调用生成器函数来创建生成器对象，然后可以使用 for 循环直接遍历数据集合，如前面提到的例子。

3. 内存占用不同
   Iterator 将整个数据集合加载到内存中，占用的内存比较大；而 Generator 则是在需要时才生成下一个元素，并且只保存当前状态，所以占用的内存比较小。

4. 遍历方式不同
   Iterator 只能进行顺序遍历，不能跳过某些元素或者倒序遍历；而 Generator 可以根据需要随时跳过某些元素或者进行倒序遍历。另外，Generator 还可以根据需要动态生成数据，而 Iterator 则不能。

总的来说：

Iterator 是一种基本的迭代器概念，通常用于遍历序列或集合。

Generator 则是一种更加高效和灵活的迭代器概念，可以动态生成数据、占用更少的内存并支持跳过元素和倒序遍历等操作。
