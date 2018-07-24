# 函数嵌套

- #### 1、函数的嵌套调用

```python
'''
函数的嵌套调用：在调用一个函数时，其内部的代码又调用了其他的函数
'''

def sum(x,y):
    sum=x+y
    return sum

def sums(a,b,c,d):
    res=sum(a,b)
    res1=sum(c,d)
    res2=res+res1
    return res2

print(sums(10,20,30,40))
```

- #### 2、函数的嵌套定义

```python
'''
函数的嵌套定义：在一个函数的内部又定义了另外一个函数
'''

def f2():
    x=1
    def f1():
        print('from f1')
    print(x)
    f1()

f2()
```
