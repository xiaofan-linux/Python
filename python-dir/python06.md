# Python基础-数据类型(tuple)

- 一、tuple(元组)


## tuple(元组)

```Python
# 用途：不可变的列表
# 定义方式：在小括号内用逗号隔开的多个元素
t=('a','b','c') # t=tuple(('a','b','c'))
print(type(t))
<class 'tuple'>
```

- 1、常用操作及内置方法：
  - 1）按索引取值（正向+方向）只能取，不能存改

  ```Python
  userinfo=('bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin')
  print(userinfo[0])
  bin

  print(userinfo[0:6:2])
  ('bin', '1', 'bin')

  print(userinfo[::-1])
  ('/sbin/nologin', '/bin', 'bin', '1', '1', 'x', 'bin')

  print(userinfo[:-5:-2])
  ('/sbin/nologin', 'bin')

  userinfo[1]='bin'
  TypeError: 'tuple' object does not support item assignment
  # 元组不支持改值
  ```

  - 2）len

  ```Python
  userinfo=('bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin')
  print(len(userinfo))
  7
  ```

  - 3）成员运算

  ```Python
  userinfo=('bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin')
  print('bin' in userinfo)
  True
  print('root' not in userinfo)
  True
  ```

  - 4）循环

  ```Python
  userinfo=('bin', 'x')
  for i in userinfo:
      print(i)    
  bin
  x
  ```

  - 5）count

  ```Python
  userinfo=('bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin')
  print(userinfo.count('bin'))
  2
  ```

  - 6）index

  ```Python
  userinfo=('bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin')
  print(userinfo.index('bin'))
  0
  ```

---

## <font color=ff0000> 总结：</font>
```Python
# 1、元组是不可变类型
# 2、是有序的
# 3、可以存多个值
```
