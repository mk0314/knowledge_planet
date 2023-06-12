<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-09 08:33:17
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-09 17:02:52
 * @FilePath: \knowledge_planet\docs\md\idea-plugin\Python\Python基础.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### Python 基础

> ### time 模块

-   time()获取时间戳
-   sleep()睡眠时间
-   ctime()将时间戳转为字符串
-   localtime()将时间戳转为元组
-   mktime()将元组转为时间戳
-   strftime()将元组的时间转为字符串

```python
s = time.strftime('%Y-%m-%d %H:%M:%S')
```

```python
import time
t = time.time() #获取时间戳
```

> ### datetime 模块

-   datetime 模块：

-   time 时间

-   date 日期

-   dateime 当前日期

-   timedelta 时间差

```python
import datetime
import  time

print(datetime.time())
print(datetime.datetime.now())
print(datetime.datetime.now().year)
print(datetime.datetime.now().month)
print(datetime.datetime.now().day)
print(datetime.datetime.now().hour)
print(datetime.datetime.now().minute)
print(datetime.datetime.now().second)
print(datetime.MAXYEAR)
print(time.time())

"时间差"
timedelta = datetime.timedelta(weeks=3)

"""
结果：
00:00:00
2023-06-09 16:40:13.004321
2023
6
9
16
40
13
9999
1686300013.0043213
21 days, 0:00:00
"""
```

> ### random 模块

-   random()表示 0 到 1 之间随机的小数
-   randrange(1, 10, 2) 表示 1~10 step= 2
-   randInt(1, 10) 表示 1~10 之间随机的整数
-   randchoice(list) 表示 list 随机选一个元素
-   randshuffle(list) 表示随机打乱列表顺序

```python
import random

print(random.random())
print(random.randint(1, 10))
print(random.randrange(1, 10, 3))
print(random.choice([1, 2, 4, 5]))
print(random.shuffle([1, 2, 4, 5]))

"""
结果：
0.8521474610355636
6
4
5
None

Process finished with exit code 0

"""
```


> ### hashlib模块

- chr() 表示Unicode码 => str
- ord() 表示str =>  Unicode码

```python
```
