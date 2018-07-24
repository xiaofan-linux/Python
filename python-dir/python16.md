# 装饰器

```python
'''
装饰器是闭包函数一种应用场景
装饰器：
    装饰指的在不修改被装饰对象的前提下，为被装饰对象添加新功能
    器指的是工具

装饰器本身可以为任意可调用的对象，被装饰的对象也可以是任意可调用的对象

原则：
    写一个函数给另外一个函数添加新功能，需要遵守开放封闭的原则（对修改是封闭的，对扩展是开放的）
    1、不修改被装饰对象的源代码
    2、不修改被装饰对象的调用方式
'''
```

- #### 1、无参装饰器

```python
'''
无参装饰器
'''

import requests
import time
def get():
    response=requests.get('http://www.baidu.com')
    print('The url have %s' %(len(response.text)))

# 为get函数加上统计时间的功能
def timmer(func):
    start_time=time.time()
    func()
    stop_time=time.time()
    print('run time is %s' %(stop_time - start_time))

# timmer(get)             # 此方法虽然能实现需求，但是其改变了原对象的调用方式，pass掉

# 只能考虑使用闭包函数咯
def wrapper(func):    # func为最原始的get
    def timmer():     # 此处一定不能传值，如果传值就失去了闭包的意义
        start_time=time.time()
        func()          #此处的的func是由包在外层的wrapper传进来的
        stop_time=time.time()
        print('run time is %s' %(stop_time - start_time))
    return timmer
get=wrapper(get)   # 此时(get)为最原始的get函数，传给了func，然后将wrapper(get)重新赋值get
get()              # 此处get被伪装了，站在用户的角度上，还以为调用的是最原始的get函数，其实get调用的是wrapper，在wrapper内部为get加了统计时间的功能
# 到此为止，新功能实现了，并且遵守了开放封闭原则（未修改被装饰对象的源代码和调用方式）

'''
装饰器语法
    在被调用对象的正上方使用"@装饰器名"  
    @装饰器名   ==   get=wrapper(get)
'''

# 上面的功能可以改写为：

def wrapper(func):    # func为最原始的get
    def timmer():     # 此处一定不能传值，如果传值就失去了闭包的意义
        start_time=time.time()
       func()          #此处的的func是由包在外层的wrapper传进来的
        stop_time=time.time()
       print('run time is %s' %(stop_time - start_time))
    return timmer

@wrapper         #get=wrapper(get)
def get():
    response=requests.get('http://www.baidu.com')
    print('The url have %s' %(len(response.text)))

get()
The url have 2381
run time is 0.034737348556518555
```

- #### 2、有参装饰器

```python
'''
有参装饰器

接上面的例子，只能统计http://www.baidu.com的时间统计，功能被写死了
此时就得给装饰器传参了
'''

import requests
import time


def wrapper(func):     # 最原始的get
    def timmer(*args,**kwargs):           #给被调用对象传参   'http://www.jd.com'
        start_time=time.time()
        func(*args,**kwargs)              #get('http://www.jd.com') / home()
        stop_time=time.time()
        print('run time is %s' %(stop_time - start_time))
    return timmer                  

@wrapper
def get(url):
    response=requests.get(url)
    print('The url have %s' %(len(response.text)))

@wrapper(‘http://www.jd.com’)
def home():
    time.sleep(1)
    print('welcome access home page')

# 过程分析：
# get=wrapper(get)  # 首先将get传给wrapper，也就间接传给timmer，拿到timmer的返回值，即wrapper(get)
# print(get)
# <function wrapper.<locals>.timmer at 0x051AFDB0>

get() # 第二步，此时是给最原始的get传参，由timmer接收，并传给内部的get函数，完成新加功能并且未修改被装饰对象的源代码和调用方式

home()              

# 到此为止，可实现即可装饰有参对象和无参对象
```

```python
'''
完整版装饰器语法
'''
import requests
import time

def wrapper(func):
    def timmer(*args,**kwargs):
        start_time=time.time()
        res=func(*args,**kwargs)
        stop_time=time.time()
        print('run time is %s' %(stop_time - start_time))
        return res          # 返回源对象的返回值
    return timmer

@wrapper
def get(url):
    response=requests.get(url)
    # print
    return ('The url have %s lines' %(len(response.text)))           # 源对象有返回值

print(get('https://www.baidu.com'))
```

```python
'''为被装饰对象加上认证功能
'''

import requests
import time
current_userinfo={'user':None}           # 存储当前登录用户的信息

def auth(func):
    def wrapper(*args,**kwargs):
        if current_userinfo['user']:               # 如果current_userinfo['user']的值非空，则证明当前用户已登录，不用重复登录
            func(*args,**kwargs)
            return print(func(*args,**kwargs))
        else:                                       # 否则，从新登录
            username=input('请输入账号：').strip()
            passwd=input('请输入密码：').strip()
            if username == 'fred' and passwd == '123':
                print('welcome to login')
                current_userinfo['user']=username
                func(*args,**kwargs)
                return print(func(*args,**kwargs))
            else:
                print('用户或密码错误')
    return wrapper

@auth
def get(url):
    response=requests.get(url)
    return ('The url have %s' %(len(response.text)))

@auth
def home():
    time.sleep(1)
    return ('welcome access home page')

get('http://www.jd.com')
home()
```
