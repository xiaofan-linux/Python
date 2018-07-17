# Python基础-数据类型(set)

- 一、set(集合)

## set(集合)
```Python
# 作用：关系运算  去重
# 定义：大括号内逗号分隔开多个元素，
   #注意：
   # 每一个元素必须是不可变类型
   # 集合内元素不能重复（本身有去重的作用）
   # 集合元素是无序的
# s={1,2,3,4,6}    # s=set({1,2,3,4,6})
print(type(s))
<class 'set'>

# 定义空集合：
s=set()        # 注意不是 s={}  这就成字典了
```
- 1、优先掌握的内置方法和常用操作
  - 1）、关系运算

  ```Python
  basket={'apple','pear','orange','banana'}
  basket1={'peach','pear','fig','grape'}

  # 求两个菜篮子里共有的水果,即求两集合的交集
  print(basket & basket1)
  print(basket.intersection(basket1))

  # 求basket里有的水果，在basket1里没有的，即求两个集合的差集  (有方向的)
  print(basket - basket1)
  print(basket.difference(basket1))

  # 反之就是求basket1里有，而basket里没有的
  print(basket1 - basket)
  print(basket1.difference(basket))

  # 求两个菜篮子里的所有水果,即并集
  print(basket | basket1)
  print(basket.union(basket1))

  # 求没有同时在两个篮子里的水果，即对称差集
  print(basket ^ basket1)
  print(basket.symmetric_difference(basket1))
  ```

  - 2）、子集父集

  ```Python
  # 注意:只有两个集合存在包含于包含的关系是，才可以进行大小比较
  s1={1,2,3,4}
  s2={1,2}

  print(s1 >= s2)                  # s1是s2的父集
  print(s1.issuperset(s2))         # 等同于s1 >= s2

  print(s2 <= s1)                  #反过来s2是s1的子集
  print(s2.issubset(s1))           #等同于s2 <= s1
  ```

  - 3）、删除元素

  ```Python
  s={1,2,3,4}

  print(s.pop())  # 随机删除,返回被删除的元素
  print(s.discard(2))   # 指定元素删除，返回值为None   如果元素不存在，也不报错
  print(s.remove(4))    # 指定元素删除，返回值为None，如果元素不存在，则报错
  ```

  - 4）、去重

  ```Python
  # 去重：
  # 局限性：
    # 不能保证原来的元素顺序
    # 针对可变类型不能去重

  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  s1=set(userinfo)
  print(s1)
  {'x', 'bin', '/bin', '1', '/sbin/nologin'}
  ```

  - 5）、成员运算和len for循环和其他数据类型一样

  - 练习

  ```Python
  # 需求：
  #1、列表内的元素有可变类型
  #2、去重之后要保持原来顺序
  info=[
      {'name':'egon','age':18},
      {'name':'alex','age':73},
      {'name':'egon','age':18},
      {'name': 'lxx', 'age': 19},
      {'name':'egon','age':18},
      {'name':'lxx','age':19},
  ]

  s=[]

  for i in info:
      if i not in s:
          s.append(i)
  info=s
  print(info)
  [{'name': 'egon', 'age': 18}, {'name': 'alex', 'age': 73}, {'name': 'lxx', 'age': 19}]
  ```
---
## <font color=ff0000>总结:</font>
```Python
# 1、集合是无序的
# 2、是可变的
# 3、可以存多个值

# 可哈希和不可哈希

# 1、可哈希的数据类型为不可变类型
# 2、不可哈希的数据类型为可变类型
```
