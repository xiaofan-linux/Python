# 闭包函数

```python
'''
大前提：函数的作用域关系是在函数定义时就已经固定死的，与调用位置无关
闭包函数：
    1、闭指的是：定义在函数内部的函数
    2、包指的是：该内部函数包含对其外层函数作用域名字的引用

闭包函数通常需要结合函数对象的概念，打破层级限制，将闭包函数返回到外部使用
'''

import requests                    # 要事先安装requests模块
def outter(url):
    def get():
        response=requests.get(url)
        print(len(response.text))
    return get                     # 返回get函数的内存地址

jd=outter('http://www.jd.com')      # 调用outter函数，实际是调用内部的get
jd()

baidu=outter('https://www.baidu.com')
baidu()

'''
总结：
    1、闭包函数传一次值，多次调用
    2、通过外部函数把值传给内部函数
    3、闭包的意义：返回的函数对象，不仅仅是一个函数对象，在该函数外还包裹了一层作用域，这使得无论在何处调用，都优先使用自己外层包裹的作用域
'''
```
