# Python基础-数据类型(int、float、str)

### 阅读目录

- 一、数字类型（init和float）
- 二、str(字符串类型)

```Python
# 可变与不可变    
    # 可变：在值改变的情况下，id不变，则证明就是在修改原值，即可变类型    
    # 不可变：在值修改的情况下，id也跟着改变，则证明没法修改原值，而是重新申请内存空间。 即不可变类型
```
---

#### 一、数字类型（init和float）
- 说明：Python中没有数字类型一说，通常我们所说的数字类型是int和float类型

###### 1、int型（整型）
```Python
# 用途：
    # 记录年龄、等级、及各种号码等
# 定义方式：
 level=10    # level=int(10) # 只能将纯数字字符串类型的数据转为init型
>>> res=int('188')
>>> print(res,type(res))
<class 'int'>
>>> int('aaaaaaaasdfsadf')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'aaaaaaaasdfsadf'
# 常用操作及内置方法  # 算出运算  # 比较运算 # 总结：  # 只能存一个值  # 不可变类型  >>> x=10
  >>> print(id(x))
  >>> x=11
  >>> print(id(x))
  1413600464
```
---
###### 2、float（浮点型）
```Python
# 用途
      # 记录工资、身高、体重等

# 定义方式
     weight=50.2      # weight=float(50.2)
# 其他同int型
```
---
#### 二、str(字符串类型)
```Python
用途：记录描述性质的状态，比如名字、爱好等
# 定义方式： 在单引号、双引号、三引号里包含的一串字符
str="'name=fred' age=15"   # str=str("'name=fred' age=15")

# 强调： # 三引号可多行 # 引号嵌套类的，里面单引号的，外面必须是双引号或三引号

# 可以将任意数据类型转换为str类型
```

- 1、优先掌握的常用操作及内置方法
  - 1）、按索引取值（正向取&反向取）  <font color=ff0000>只能取，不能存</font>

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print(userinfo[0])              # 索引号是从0开始的
  print(userinfo[-1])h userinfo[0]='b'
  # TypeError: 'str' object does  not support item assignment # str不支持修改原值
  ```

  - 2）切片，从一个大的字符串里切除一个子字符串（顾头不顾尾，步长）

  ```python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print(userinfo[0:4])      # 步长不指定，默认是1
  root                      # 顾头不顾尾：[0:4]只能取到前四个字符，第五个字符没取到
  print(userinfo[0:4:2])    # 取出索引0-4，步长为2进行取
  ro                        # 只能取到第一个字符和第三个字符，步长为2，中间隔了1个
  print(userinfo[6:])       # 从第六个字符开始取，到结束
  :0:0:root:/root:/bin/bash

  # 倒着切片，注意方向要一致
  print(userinfo[-1:-5:-1])   # 反向取值，一定要指定步长
  hsab
  print(userinfo[-1::-1])     # 从反向第一个字符到最后一个，步长为1
  hsab/nib/:toor/:toor:0:0:x:toor
  print(userinfo[::-1])       # 也可不指定头和尾，意指字符头到尾
  hsab/nib/:toor/:toor:0:0:x:toor  
  ```

  - 3）、切分split：把一个字符串按照某种分隔符切成一个列表

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print(userinfo.split(':'))      # 按照冒号切分
  ['root', 'x', '0', '0', 'root', '/root', '/bin/bash']

  # 注意：
    # split还有一个参数：最大切分次数，默认是-1，字符串中有多少分隔符，切几次     # 从左往右切
      userinfo='root:x:0:0:root:/root:/bin/bash'
      print(userinfo.split(':',1))
      ['root', 'x:0:0:root:/root:/bin/bash']
    # rsplit            # 从右往左切
      userinfo='root:x:0:0:root:/root:/bin/bash'
      print(userinfo.rsplit(':',3))
      ['root:x:0:0', 'root', '/root', '/bin/bash']
  ```

  - 4）、join 将列表按照某种分隔符组合一个字符串

  ```Python
  userinfo=['root', 'x', '0', '0', 'root', '/root', '/bin/bash']
  userinfo_join='|'.join(userinfo)   # 将userinfo列表按|,组合成一个字符串
  print(userinfo_join)
  root|x|0|0|root|/root|/bin/bash    # 组合的结果
  ```

  - 5）、len长度

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print(len(userinfo))
  31                    # 长度为31，所以只能到30 （索引是从0开始的，偷笑）
  ```

  - 6）、成员运算in和not in，判断一个字符串是否存在于大的字符串

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print('bin' in userinfo)
  True
  print('3' in userinfo)
  False

  # not in  取反
  ```

  - 7）、strip移除字符串左右两边的指定字符

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash....root'
  print(userinfo.strip('root'))
  :x:0:0:root:/root:/bin/bash....

  #规则：
  # 1、从左边开始找指定字符，直到非指定字符为止
  # 2、从右边开始找指定字符，直到非指定字符为止

  # 注意：
  # 1、strip() 默认是去除字符串左右两边的空格
  # 2、strip并不是修改原值，而是重新产生一个新值
  userinfo='root:x:0:0:root:/root:/bin/bash....root'
  print(id(userinfo))
  89149536

  userinfo=userinfo.strip('root')
  print(id(userinfo))
  88587248

  # 了解（lstrip rstrip）
  # lstrip   移除字符串左边的指定字符
  # rstrip   移除字符串右边的指定字符
  ```

  - 8）、循环

  ```Python
  userinfo='ro'
  for i in userinfo:
      print(i)
  r
  o

  # 按索引从头到尾循环

  for i in range(0,len(userinfo)):
      print(userinfo[i])
  ```
---
- 2、需要掌握的操作及内置方法
  - 1）lower upper

  ```python
  userinfo='root:x'
  print(userinfo.upper()) #将字符串中的小写字母转换为大写
  ROOT:X
  # lower  将字符串中的大写字母转换为小写
  ```

  - 2）startswitch   endswitch

  ```Python
  userinfo='root:x'
  print(userinfo.startswith('ro'))  # 判断字符串是否以指定字符开头
  True
  print(userinfo.endswith('x'))     # 判断字符串是否以指定字符结尾
  True
  ```

  - 3）、format的三种玩法

  ```Python
  print('my name is %s my age is %s' %(18,'fred'))         
  # %s的缺点，占位符和值只能按顺序匹配

  print('my name is {name} my age is {age}'.format(age=18,name='fred'))  
  #format可以不用根据顺序匹配，指定了变量名

  print('my name is {} my age is {}'.format(18,'fred'))   
   # 此种方式，和%s意义一行

  print('my name is {0}{0}{0} my age is {1}'.format(18,'fred'))
  # 可以按索引号多次匹配
  my name is 181818 my age is fred
  ```

  - 4）、replace

  ```Python
  userinfo='root:x:0:0:root:/root:/bin/bash'
  print(userinfo.replace('root','fred'))             
  # 如果不指定替换次数，默认全部替换

  fred:x:0:0:fred:/fred:/bin/bash
  print(userinfo.replace('root','fred',1))           
  # 指定替换次数之后，从左往右依次替换N次

  fred:x:0:0:root:/root:/bin/bash
  ```

  - 5）、isdigit

  ```Python
  #　判断字符串是否为纯数字
  print('fred123'.isdigit())
  False
  print('1929'.isdigit())
  True

  # 只有在字符串中包含的是纯数字的情况下才结果才为True
  ```
---
- 3、了解的操作及内置方法
  - 1）、find,rfind,index,rindex,count

  ```Python
  # find() 方法检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果包含子字符串返回开始的索引值，否则返回-1。 # 从左向右检索
    # 语法： str.find(str, beg=0, end=len(string))
    # 参数
       str 指定检索的字符串
       beg 开始索引号  默认是0
       end 结束索引号  默认是len(string)

  # rfind() 返回字符串最后一次出现的位置(从右向左查询)，如果没有匹配项则返回-1。

  # index() 方法检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，该方法与 python find()方法一样，只不过如果str不在 string中会报一个异常
  # rindex() 返回子字符串 str 在字符串中最后出现的位置，如果没有匹配的字符串会报异常，可以指定可选参数[beg:end]设置查找的区间
  # count() 方法用于统计字符串里某个字符出现的次数。可选参数为在字符串搜索的开始与结束位置

  # 注意：
     find类都是返回索引号
  ```

  - 2）、center,ljust,rjust,zfill

  ```Python
  print('我是分隔符'.center(50,'*'))
  **********************我是分隔符***********************
  print('我是分隔符'.ljust(50,'='))
  我是分隔符=============================================
  print('我是分隔符'.rjust(50,'0'))
  000000000000000000000000000000000000000000000我是分隔符
  print('我是分隔符'.zfill(50))
  000000000000000000000000000000000000000000000我是分隔符

  # zfill() ===  rjust('0')
  ```

  - 3)、end

  ```Python
  # 指定字符串后面的空格数
# 以九九乘法表为例
for x in range(1,10):
    for y in range(1,x+1):
        print('%sX%s=%s' %(x,y,x*y),end='  ')
    print()

  # 打印结果    
  1X1=1  
  2X1=2  2X2=4   # 字符结尾+2个空格
  3X1=3  3X2=6  3X3=9  
  4X1=4  4X2=8  4X3=12  4X4=16  
  5X1=5  5X2=10  5X3=15  5X4=20  5X5=25  
  6X1=6  6X2=12  6X3=18  6X4=24  6X5=30  6X6=36  
  7X1=7  7X2=14  7X3=21  7X4=28  7X5=35  7X6=42  7X7=49  
  8X1=8  8X2=16  8X3=24  8X4=32  8X5=40  8X6=48  8X7=56  8X8=64  
  9X1=9  9X2=18  9X3=27  9X4=36  9X5=45  9X6=54  9X7=63  9X8=72  9X9=81
  ```
---

## <font color=ff0000>str总结：</font>
```Python
# 1、str为不可变类型
# 2、是有序的（有索引）
# 3、只能存一个值
```
---
