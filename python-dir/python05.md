# Python基础-数据类型(dict)

- 一、dict(字典)


## 四、dict(字典)
```Python
# 用途：存多个种类不同的值
# 定义方式：在{}内用逗号隔开多个元素，每个元素都是key:value的形式。key对value有描述性的功能，
   # value可以是任意类型，而key必须是不可变类型且唯一
   # 即字典可以是int float tuple str  通常是字符串类型
d1={'name':'fred','age':18,'commany':'9you'}    # d=dict({'name':'fred','age':18,'commany':'9you'})
d2=dict([['nane','fred'],['age',18]])   # dict转换列表

d3=dict(x=1,y=2,z=3)   # dict转换元组

d4={}.fromkeys(('name','age','sex'),None) # 初始化字典
```
- 1、优先掌握的常用操作及内置方法
  - 1）、按key存取值

  ```Python
  d1={'name':'fred','age':18,'commany':'9you'}
  print(d1['name']) # 按key取值
  fred
  d1['name']='Li'  # 按key改值
  print(d1)
  {'name': 'Li', 'age': 18, 'commany': '9you'}

  d1['weight']=50.4  # 新增key
  print(d1)
  {'name': 'fred', 'age': 18, 'commany': '9you', 'weight': 50.4}
  ```

  - 2）、len(长度)

  ```python
  d1={'name':'fred','age':18,'commany':'9you'}
  print(len(d1))      # dict len统计的是key的个数
  ```

   - 3）成员运算（判断的是字典的key）

   ```Python
   d1={'name':'fred','age':18,'commany':'9you'}

   print('name' in d1)
   True

   # 取反：not in
   ```

   - 4）、删除

   ```Python
   # pop()删除指定key
   # 字典 pop() 方法删除字典给定键 key 所对应的值，返回值为被删除的值。key值必须给出。 否则，返回default值
   d1={'name': 'fred', 'age': 18, 'commany': '9you', 'weight': 50.4}
   print(d1.pop('sex',None)) # 如果要pop的key不存在，一定要指定默认返回值，否则会报错
   None
   print(d1)
   {'name': 'fred', 'age': 18, 'commany': '9you', 'weight': 50.4}

   print(d1.pop('weight'))  # 如果key存在，则返回key对应的值
   50.4
   print(d1)
   {'name': 'fred', 'age': 18, 'commany': '9you'}
   ```

   ```Python

   # 字典 popitem() 方法随机返回并删除字典中的一对键和值(一般删除末尾对)
   # 如果字典已经为空，却调用了此方法，就报出KeyError异常。
   dict={'name': 'fred', 'age': 18, 'commany': '9you', 'weight': 50.4}

   print(dict.popitem())  # 以元组形式返回一对键和值
   ('weight', 50.4)
   print(dict.popitem())
   ('commany', '9you')
   ```

   - 5）、修改key对应的value

   ```Python
   # update() 如果key存在，则修改其value。 如果key不存在，则新增
   # 该方法，返回值为None
   dict={'name': 'fred', 'age': 18, 'commany': '9you'}
   dict.update({'name':'Li'})
   print(dict)
   {'name': 'Li', 'age': 18, 'commany': '9you'}
   dict.update({'sex':'male'})
   print(dict)
   {'name': 'Li', 'age': 18, 'commany': '9you', 'sex': 'male'}

   # setdefault() 如果key值存在，则不修改源，并返回key的值 如果key不存在，则新增此key，并返回其对应的值
   dict={'name': 'fred', 'age': 18, 'commany': '9you'}

   print(dict.setdefault('name','Li'))
   fred
   print(dict.setdefault('sex','male'))
   male
   print(dict)
   {'name': 'fred', 'age': 18, 'commany': '9you', 'sex': 'male'}
   ```

   - 6）、keys  values  items

   ```Python
   msg_dic={
   'apple':10,
   'tesla':100000,
   'mac':3000,
   'lenovo':30000,
   'chicken':10,
   }

   print(msg_dic.items())
   [('tesla', 100000), ('mac', 3000), ('lenovo', 30000), ('apple', 10), ('chicken', 10)]     
   print(msg_dic.keys())
   ['tesla', 'mac', 'lenovo', 'apple', 'chicken']
   print(msg_dic.values())
   [100000, 3000, 30000, 10, 10]
   ```

   - 7）、循环

   ```Python
   msg_dic={
   'apple':10,
   'tesla':100000,
   }

   for key in msg_dic.keys():
       print(key)

   for values in msg_dic.values():
       print(values)

   for key,values in msg_dic.items():
       print(key,values)
   ```

   - 8）、get

   ```Python
   info={'name':'lichunke','age':18,'company':'9you'}
   print(info.get('name'))
   lichunke

   #取一个不存在的key，也不会报错，返回一个空值（也可自定义输出），代码容错性高
   info={'name':'lichunke','age':18,'company':'9you'}
   print(info.get('name11111'))
   None

   #自定义输出
   info={'name':'lichunke','age':18,'company':'9you'}
   print(info.get('name11111','null'))
   null
   ```
---
## <font color=ff0000>总结：</font>
```Python
# 1、字典是可变类型
# 2、是无序的
# 3、可以存多个值
```
