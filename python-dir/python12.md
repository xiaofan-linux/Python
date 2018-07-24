# 函数对象

```python
'''
函数是第一类对象，意味着函数可以当做数据去使用
'''

# 函数身为一个对象，拥有对象的三个通用属性：id type value
def userinfo():
    print('from userinfo')

print(userinfo)
<function userinfo at 0x0387AA98>

print(type(userinfo))
<class 'function'>

print(id(userinfo))
59222680
```

- #### 可以被引用，即函数可以赋值给一个变量

```python
'''
可以被引用，即函数可以赋值给一个变量
'''
def userinfo():
    print('from userinfo')

func=userinfo
print(func,userinfo)
<function userinfo at 0x051DBA98>
<function userinfo at 0x051DBA98>
```

- #### 可以当做参数传给另外一个函数

```python
'''
可以当做参数传给另外一个函数
'''

def f1():
    print('from f1')

def f2(func):
    print(func)
    f1()

f2(f1)         # f1是当做参数传给f2 ，f2内部调用了f1

<function f1 at 0x036CBA98>
from f1
```

- #### 可以当做函数的返回值

```python
'''
可以当做函数的返回值
'''

def f1():
    print('from f1')

def f2():
    return f1

res=f2()
print(res)
<function f1 at 0x0369BA98>

res()
from f1
```

- #### 可以当做容器类型（可以存多个值）的元素

```python
'''
可以当做容器类型（可以存多个值）的元素
容器对象（list、dict、set等）中可以存放任何对象，包括整数、字符串，函数也可以作存放到容器对象中
'''

def auth():
    print('from auth')

def pay():
    print('from pay')


func_dic={
    '1':auth,
    '2':pay,
}

func_dic['1']()
from auth

func_dic['2']()
from pay
```
