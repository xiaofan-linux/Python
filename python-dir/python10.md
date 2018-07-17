# 函数

## 1、什么是函数
```python
    函数就是具备某一功能的工具
    函数的使用必须遵循先定义、后调用的原则
    事先准备工具的过程即函数的定义
    拿来就用即函数的调用

    函数分为两大类：
        内置的函数
        自定义函数
```
## 2、为何要用函数
```python
    程序的组织结构不清晰、可读性差
    日积月累冗余代码过多
    程序的可扩展性极强
```
## 3、函数的分类
```python
# 内置函数
为了方便程序开发，针对一些简单的功能，Python解释器已经定义好了的函数即内置函数，对于内置函数我们可以拿来就用而无需事先定义，如len()  sum() max()

# 自定义函数
很明显内置函数所能提供的功能有限，这就需要我们自己根据需求，事先定义好我们自己的函数来实现某个功能，以后在遇到应用场景时，调用自定义函数即可

```
## 4、定义函数
```pyhton
# 函数代码块以def关键字开头，后接函数名和小括号
# 任何传入的参数和自身变量必须放在小括号里面，参数名称可以多个
# 函数的第一行需要写函数说明
# 函数内容以冒号起始，并且缩进
# return [表达式]结束函数，选择性的返回一个值给调用方，不带表达式的return ，返回值为None
```
- 1、定义函数
  - 1.1 语法
  ```python
  def 函数名(参数1,参数2,参数3,...):
     """
     文档注释
     """
     code1
     code2
     code3
     ...
     return 返回值
  ```

  - 1.2 定义函数阶段发生哪些事:只检测语法，不执行代码
  ```python
    def foo(): # foo=函数的内存地址
       print('first')
       print('sencod')
       print(asdfsadfasdfas)
       print('third')
    foo()

    示范一；
    def bar():
       print('from bar')
    def foo():
       print('from foo')
       bar()
   foo()

    示范二；
    # 定义阶段
    def foo():
       print('from foo')
       bar()
    def bar():
       print('from bar')

    # 调用阶段
    foo()

    示范三；
    # 定义阶段
    def foo():
       print('from foo')
       bar()
    # 调用阶段
    foo()
    def bar():
       print('from bar')
  ```

## 5、有参函数、无参函数、空函数

  - 5.3 定义函数的三种形式

    - 5.3.1 无参函数
    ```python
    def func1():
         print('hello1')
         print('hello2')
         print('hello3')

     func1()
     ```

     - 5.3.2 有参函数

     ```python
      def func2(x,y):
           if x > y:
               print(x)
           else:
               print(y)
      func2(1,3)
      func2(2,3)
      func2(2,4)
      ```

      - 5.3.3 空函数

      ```python
      # 空函数的作用：在项目立项阶段，使用空函数把此项目的大体功能干先列出来，后续只需要一个个实现小功能就可以
      def get():
           pass
      def put():
           pass
      def auth():
           pass
      ```



## 6、调用函数
  - 6.1 语法：函数名()
  ```Python
  userinfo()
  ```
  - 6.2 调用函数发生什么事？:
  ```python
  根据函数名找到函数的内存地址
  函数的内存地址加括号可以触发函数体代码的运行
  ```

  - 6.3 调用函数的三种方式

  ```python
  # 语句
    def f1():
       print('from 1')
    f1()

  # 表达式形式
    def max2(x,y):
         if x > y:
             return x
         else:
             return y
    res=max(1,2)*10
    print(res)

  # 当作参数传给其他函数
    def max2(x,y):
         if x > y:
             return x
         else:
             return y
    res=max2(max2(1,2),3)
    print(res)
    ```

## 7、函数的返回值

```Python
return 是函数结束的标志，
函数内可以有多个return，但只要执行一个，函数就立即结束，并且把return后的值当做本次调用的结果返回
注意：
1、返回值没有类型限制
2、返回值没有个数限制，可以用逗号分开多个值一次返回
3、可以没有return，默认返回None

什么时候该有返回值？
     调用函数，经过一系列的操作，最后拿到一个明确的结果，则必须要有返回值
     通常有参数需要返回值，输入参数，经过计算，得到一个最终结果
什么时候不需要返回值？
     调用函数，仅仅只是执行一系列的操作，最后不需要得到什么结果，则无需有返回值
     通常无参函数不需要有返
```
