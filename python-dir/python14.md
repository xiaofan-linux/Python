# 名称空间与作用域

- #### 1、名称空间

```python
'''
名称空间：是名称与对象之间的关系，可以将命名空间看做是字典，其中的键是名称，值是对象
'''

'''
内置名称空间：存放Python解释器自带的名称，如len max sum
生命周期：在解释器启动时产生，关闭时回收
'''
print(len)
<built-in function len>

'''
全局名称空间：除了内置的与局部的名字之外的都属于全局名称空间
生命周期：在程序文件执行时，立刻产生，程序执行完毕后就回收
'''
name='root'

'''
局部名称空间：存放函数内部定义的名字
生命周国旗：在调用函数时临时生效，函数调用结束后立即回收
'''

def user():
    age=18
    return age

print(user())

print(age)
name 'age' is not defined       # 函数调用已结束，所以age和18的绑定关系也被回收了


'''
加载顺序：内置名称空间———全局名称空间————局部名称空间
查找顺序：基于当前名称空间查找  当前————上一级————上上级
假设目前在局部名称空间：查找顺序为：局部名称空间————全局名称空间————内置名称空间
强调：：：：： 函数的形参属于局部名称空间
''' def foo():
    x=4
    print(locals())        # locals()方法是打印出当前局部名称空间中的名字与value的对应关系
foo()
{'x': 4}                   # 以字典方式存储
```

- #### 2、作用域

```Python
'''
作用域:指的是名字的作用范围
分为:全局作用域和局部作用域
'''

'''
全局作用域:包含内置名称空间与全局名称空间中的名字
特点:全局有效,全局存活
'''

'''
局部作用域:只包含局部名称空间的名字
特点:局部有效,临时存活
'''

x=3333

def area():
    x=222
    def area1():
        x=111
        print('from area1 %s' %x)
    area1()
    print('from area %s' %x)

area()                 # 次函数为嵌套函数
from area1 111         # 在area1函数内部，x与111绑定，area1被调用时，area1内部有x的名字与值对应的关系，所以x此时等于111
from area 222          # area1调用结束后，x=111的绑定关系也随着解除，在area内部，x与222绑定，area被调用，所以此时x=222
print(x)
                  # area调用结束，x与222的绑定关系也随之解除，所以此时是在全局作用域里查找x对应的valve，所以此时x=3333

'''
总结：
   函数的作用域关系是在函数定义阶段就已经固定死的，与函数的调用位置无关
   即在调用函数时一定要到定义函数的位置寻找作用域关系
'''
```

- #### 3、global和nonlocal

```Python
'''
global:在局部名称空间声明其后的变量是作用于全局
'''

x=3333
def func():
    x=2222
    def func1():
        global x
        x=4444
        print('from func1 %s' %x)
    func1()
    print('from func %s' %x)


func()
from func1 4444     # 由于func1中声明了x是全局名称空间中的名字，所以它作用于本层局部作用域和全局作用域，
from func 2222      # 但不影响上层局部作用域

print(x)
               # 此时就算全局名称空间中定义了x=3333，也以global所在的局部名称空间中定义的为准
```

```Python
'''
nonlocal 在局部名称空间声明其后的变量作用于上层
'''
x=1111
def func():
    x=4444
    def func1():
        nonlocal x
        x=3333
        print('from func1 %s' %x)
    func1()
    print('from func %s' %x)


func()
from func1 3333      # 由于func1中nonlocal声明了x=3333
from func 3333       # 所以就算func中定义了x=4444，也不生效

print(x)
                 # nonlocal并未影响全局名称空间
```
