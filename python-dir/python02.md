# python 入门

### 编写第一个python程序

- 第一种方法
```python
1.打开“超级终端”
2.输入python，进入pyhton交互模式
$ pyhton
3.输入以下代码,按回车
>>> print('hellp world')
```
- 第二种方法
```python
1.打开编辑软件sublime
2.编写以下代码，并保存为.py结尾的文件
print('hello world')
3.打开终端，进入保存文件的目录执行以下命令
pyhton helloworld.py
```
---

### 注释

- #### 注释的作用
>* 通过用自己熟悉的语言，在程序中对某些代码进行标注说明，这就是注释的作用，能够大大增强程序的可读性

- #### 注释的分类

* 单行注释
```python
以 #开头，#右边的所有东西当做说明，而不是真正要执行的程序，起辅助说明作用
```

* 多行注释
```python
'''我是多行注释，可以写很多很多行的功能说明
        这就是我牛X指出

        哈哈哈。。。
    '''
```

---

### 变量

在程序中，有时我们需要对2个数据进行求和，那么该怎样做呢？

大家类比一下现实生活中，比如去超市买东西，往往咱们需要一个菜篮子，用来进行存储物品，等到所有的物品都购买完成后，在收银台进行结账即可

如果在
程序中，需要把2个数据，或者多个数据进行求和的话，那么就需要把这些数据先存储起来，然后把它们累加起来即可

在Python中，存储一个数据，需要一个叫做变量的东西

- 如何定义变量
```Python
# 变量(相当于门牌号，指向值所在的空间)  等号，变量值
age=18
name='shanghai'
```

- 变量的定义规范
```Python
#1. 变量名只能是 字母、数字或下划线的任意组合
#2. 变量名的第一个字符不能是数字
#3. 关键字不能声明为变量名['and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'exec', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'not', 'or', 'pass', 'print', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

- 变量的定义方式
```python
#驼峰体
AgeOfOldboy = 56
NumberOfStudents = 80
#下划线(推荐使用)
age_of_oldboy = 56
number_of_students = 80
```
