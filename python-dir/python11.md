# 函数的参数

### 1、实参与形参
```python
函数的参数分为两大类：形参与实参

    形参：指的是在定义函数时，括号指定的参数,本质就是变量名
    实参：指的是在调用函数时，括号内传入的值，本质就是值

    只有在调用函数时才会在函数体内发生实参（值）与形参（变量名）的绑定关系
    该绑定关系只在调用函数时临时生效，在调用函数结束后就解除绑定
```

### 2、位置参数
```python
'''
位置形参：函数定义阶段，按照从左到右的顺序依次定义的形参，称之为位置形参
位置实参：函数调用阶段，按照从左到右的顺序依次传入的值，称之为位置实参
'''

def userinfo(name,age):
    print('姓名：%s  年龄：%s' %(name,age))

userinfo('fred',18)         # 此时就相当于格式化输出中的%s
姓名：fred  年龄：18          # 从左到右 name=fred  age=18

# userinfo('fred',18,'sa')
# typeError: userinfo() takes 2 positional arguments but 3 were give
# 值传多了

userinfo('fred')
userinfo() missing
1 required positional argument: 'age'   # 没有给age传值

userinfo(20,'fred')
姓名：20  年龄：fred  
# 由于严格按照位置传值，在不了解参数具体功能情况下，就会出现这种结果


# 总结：
   # 但凡是按照位置定义的形参，在调用时必须为其传值，多一个不行，少一个也不行
   # 在传值时，按顺序与形参一一对应
```

### 3、关键字实参
```python
'''
关键字实参：在函数调用阶段，按照key=value的形式定义的实参，称之为关键字实参
注意：
   1、关键字实参可以完全打乱顺序，但仍然可以指名道姓的为指定形参传值
   2、可以在调用函数时，关键字实参和位置实参混合使用
   3、关键字实参要跟在位置实参的后边，并且不能为一个形参传多个值

'''

def userinfo(name,age,company):
    print('姓名：{name} 年龄：{age} 公司：{company}'.format(name=name,age=age,company=company))



userinfo('fred',company='9you',age=20)
# 姓名：fred 年龄：20 公司：9you


userinfo(age=20,company='9you','fred')
SyntaxError: positional argument follows keyword argument  # 位置参数不能跟在关键字参数右边
```

### 4、默认参数
```python
'''
默认参数：在定义函数时，就已经为某些参数绑定值，称之为默认形参
注意：
   1、在定义阶段就已经有值，意味着在调用阶段可以不用为其传值
   2、默认形参必须放到位置形参后面
   3、默认形参的值只在定义阶段生效一次，在函数定义之后发生的改动无效
   4、默认形参的值通常应该为不可变类型

什么时候应该定义默认形参：
    大多数情况下都一样的，比如民族

什么时候应该定义位置形参
    大多数情况是不一样的，比如name

'''

def userinfo(name,age,company,sex='male'):
    print('姓名：{name} 年龄：{age} 公司：{company} 性别：{sex}'.format(name=name, age=age, company=company,sex=sex))

userinfo('fred',age=18,company='9you')  # 可以不用为默认形参传值
姓名：fred 年龄：18 公司：9you 性别：male

userinfo('jerry',age=18,company='9you',sex='female')
姓名：jerry 年龄：18 公司：9you 性别：female  # 也可为默认形参传值，以传的值为准

def userinfo(name,age,sex='male',company):
    print('姓名：{name} 年龄：{age} 公司：{company} 性别：{sex}'.format(name=name, age=age, company=company,sex=sex))


SyntaxError: non-default argument follows default argument # 默认形参不能在位置形参左边
```

### 5、可变长参数
```python
'''
可变长参数是在调用函数时，函数的参数个数是不固定的

然而实参终究要为形参传值的，针对两种形式的参数不固定，对应着形参也必须有两种解决方案，来分别处理溢出的位置实参与关键字实参

python中约定俗成：
   *args       # 位置形参
   *kwargs     # 关键字形参

*  会把溢出的实参存成元组，然后赋值给紧跟其后的变量名
** 会把溢出的关键字实参存成字典，然后赋值给紧跟其后的变量名
'''
```

  - 1）形参中带*
  ```python
  def userinfo(username,passwd,*args):
      print('用户名：%s' %username)
      print('密码：%s' %passwd)
      print('其他:',args)

  userinfo('root','x', '0', '0', 'root', '/root', '/bin/bash')

  用户名：root
  密码：x
  其他: ('0', '0', 'root', '/root', '/bin/bash')      
  ```

  - 2）形参中带\*   && 实参中带\*
  ```python
  '''
  实参中* 小窍门：
  但凡实参中*，都先将其打散成位置实参，然后考虑传值
  '''

  def userinfo(username,passwd,*args):
      print('用户名：%s' %username)
      print('密码：%s' %passwd)
      print('其他:',args)

  userinfo('root',*('x', '0', '0', 'root', '/root', '/bin/bash'))    #此处，只传一个位置实参，然后*后面跟了元组
  用户名：root
  密码：x
  其他: ('0', '0', 'root', '/root', '/bin/bash')       
  #处理过程：先将元组打散成位置实参，然后将ｘ传给passwd，剩下的整体传给*，并绑定给args
  ```

  - 3）形参中带\**   && 实参中带\**
  ```python
  '''
  形参中带**  溢出的关键字实参会存成字典，然后赋值给紧跟其后的变量名
  实参中带**  但凡实参中带** ，先将其打散成关键字实参，然后再考虑传值

  '''

  def userinfo(username,passwd,**kwargs):
      print('用户名：%s' %username)
      print('密码：%s' %passwd)
      print('其他：',kwargs)

  userinfo('root',**{'passwd':'x','uid':'0','gid':'0','desc':'root'})     # 实参中带** 先将打散成关键字实参，passwd=x 其他给了kwargs
  用户名：root
  密码：x
  其他： {'uid': '0', 'gid': '0', 'desc': 'root'}
  ```

  - 4）、实参中带**
  ```python
  '''
  实参中带**  但凡实参中带** ，先将其打散成关键字实参，然后再考虑传值
  '''

  def userinfo(username,passwd):
      print('用户名：%s' %username)
      print('密码：%s' %passwd)

  userinfo(**{'username':'fred','passwd':'1234','desc':'this is fred'})
  TypeError: userinfo() got an unexpected keyword argument 'desc'       
  # 不能传多也不能传少

  userinfo(**{'username':'fred','passwd':'1234'})
  用户名：fred
  密码：1234
  ```
