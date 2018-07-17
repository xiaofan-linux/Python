# Python基础-数据类型(list)

- 一、list(列表）


## list(列表）
```Python
# 用途：用于标识多个值，如一个人有多个爱好
# 定义方式：中括号内用逗号隔开多个任意类型的值
userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']     # userinfo=list(['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin'])

# list的工作原理：list(items)
  # 1、先定义一个空了表
  # 2、然后类似调用一个for循环，从items里取出一个值放入空列表中，循环往复直到值取干净为止
```
- 1、优先掌握的常用操作及内置方法
  - 1）、按索引存取值、切片（正向反向存取）：即可存可取

  ```Python
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(userinfo[0])
  bin
  print(userinfo[0:3])
  ['bin', 'x', '1']
  print(userinfo[0:5:2])
  ['bin', '1', 'bin']
  print(userinfo[-1])
  /sbin/nologin
  print(userinfo[-1::-1])
  ['/sbin/nologin', '/bin', 'bin', '1', '1', 'x', 'bin']
  print(userinfo[-1:-5:-2])
  ['/sbin/nologin', 'bin'

  print(id(userinfo))
  93973280
  userinfo[0]='root'   # 指定索引号修改原值
  print(userinfo[0],id(userinfo))
  root 93973280

  # 注意：此方式只能修改原值，不能新增（list有其独有的新增方法）
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  userinfo[7]='bash'
  IndexError: list assignment index out of range  # 超出了list的最大索引号
  ```

  - 2）、len(长度)

  ```Python
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(len(userinfo))
  7
  ```

  - 3）、成员运算(in  &&  not in)

  ```Python
  print('bin' in userinfo)
  True
  print('root' not in userinfo)
  True
  ```

  - 4)、追加和插入（append  && extend &&  insert ）

  ```Python
  # append()  在列表末尾添加新的元素
  # insert()  在指定索引号前插入新元素
  # extend() 函数用于在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表)

  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  userinfo.append('this is bin user')  # 此方法没有返回值，但是会修改源列表  
  print(userinfo)
  ['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin', 'this is bin user']

  userinfo.insert(0,'This is first')  # 两个参数，索引号，新元素  同样没有返回值看，但是会修改源列表
  print(userinfo)
  ['This is first', 'bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']

  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  userinfo1=['root', 'x', '0', '0', 'root', '/root', '/bin/bash']

  userinfo.extend(userinfo1[0:5:2]) # 如果不指定userinfo1的起始索引、结束索引、步长，默认将userinfo1的所有内容追加到userinfo中
  print(userinfo)
  ['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin', 'root', '0', 'root']
  ```

  - 5）、删除

  ```Python
  # 方式1：通用型删除（并非列表的独有删除方式）
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(userinfo)           
  ['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']  #删除前

  del userinfo[-1]  #次方法没有返回值       
  print(userinfo)
  ['bin', 'x', '1', '1', 'bin', '/bin']  #删除后

  # 方式2 remove
  # remove() 函数用于删除列表中某个值的第一个匹配项。
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  userinfo.remove('bin')  # 无返回值，userinfo中bin的第一个匹配项
  print(userinfo)
  ['x', '1', '1', 'bin', '/bin', '/sbin/nologin']

  # 方式3 pop
  # pop() 此方法会删除指定索引号对应的元素，并返回该元素的值
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(userinfo.pop())  # 默认删除最后一个索引（-1）
  /sbin/nologin  # 返回该元素的值
  print(userinfo)
  ['bin', 'x', '1', '1', 'bin', '/bin']
  print(userinfo.pop(0)) # 可指定索引号
  bin
  print(userinfo)
  ['x', '1', '1', 'bin', '/bin']
  ```

  - 6）、循环

  ```Python
  userinfo=['bin', 'x']     # 根据索引循环（0,len(userinfo)）
  for i in userinfo:
      print(i)
  ```
---
- 2、需要掌握的操作
  - 1）count

  ```Python
  # count() 用于统计指定元素在列表中出现的次数
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(userinfo.count('bin'))
  2
  ```
  - 2）、index

  ```Python
  # index() 函数用于从列表中找出某个值第一个匹配项的索引位置
  userinfo=['bin', 'x', '1', '1', 'bin', '/bin', '/sbin/nologin']
  print(userinfo.index('bin'))
  0
  ```
  - 3）sort

  ```Python
  # sort() 函数用于对原列表进行排序，如果指定参数，则使用比较函数指定的比较函数
  list1=[5,2,4,8,9,10]
  list1.sort()                    # 默认是升序
  print(list1)
  [2, 4, 5, 8, 9, 10]

  list1.sort(reverse=True)        # reverse=True  降序
  [10, 9, 8, 5, 4, 2]
  print(list1)
  ```

  - 练习：

  ```Python
  # 列表模拟队列 ：先进先出

  # 入队：
  list=[]
  list.append('first')
  list.append('second')
  list.append('third')
  print(list)
  ['first', 'second', 'third']

  #出队：
  print(list.pop(0))
  print(list.pop(0))
  print(list.pop(0))
  first
  second
  third

  # 列表模拟堆栈  先进后出

  # 入栈
  list=[]
  list.append('first')
  list.append('second')
  list.append('third')
  print(list)
  ['first', 'second', 'third']

  # 出栈
  print(list.pop())
  print(list.pop())
  print(list.pop())
  third
  second
  first
  ```
---

## <font color=ff0000>总结：</font>

```Python
# 1、列表类型可以存多个值
# 2、是有序的
# 3、可变类型
```
