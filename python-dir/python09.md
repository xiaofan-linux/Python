# 文件处理

阅读目录
- 一、文件处理的基本流程
- 二、文件的打开模式（r模式）
- 三、文件的打开模式（w模式）
- 四、文件的打开模式（a模式）
- 五、控制文件操作内容的模式（t模式）
- 六、控制文件操作内容的模式（b模式）
- 七、文件内指针的移动
- 八、文件的修改

---
- 一、文件处理的基本流程
  - 1、什么是文件

  ```python
  # 文件是操作系统为应用程序或者用户提供的一个操作硬盘的虚拟单位
  ```

  - 2、为什么要用文件

  ```python
  # 应用程序需要经常将内存中的数据永久保存下来，而应用程序又不能直接操作硬件

  # 只能通过操作系统提供的虚拟单位去间接地操作硬盘
  ```

  - 3、文件打开过程

  ```python
  f=open('file.txt',mode='r',encoding='utf8')
  # open打开文件的过程：
    # 1、应用程序向操作系统发起系统调用open
    # 2、操作系统打开文件并返回文件句柄给应用程序
    # <_io.TextIOWrapper name='file.txt' mode='r' encoding='utf8'>
  ```
  ```python
  f1=open('D:\python_study_new\a.txt')   
  # 此时\a被转义了，如果不加r'D:\python_study_new\a.txt',是有问题的

  # open的三个参数解析：
    # 1、文件路径（相对路径或者绝对路径），r的概念，rawstring原生字符，将文件路径中的转义字符转成原生字符
    # 2、文件的打开模式
    # 3、指定字符集
  ```
    - open和with open

    ```python
    # open 打开文件需要手动回收
    # 打开一个文件包含两部分资源：操作系统打开文件+Python解释器的里定义的变量
    # 在出操作完毕一个文件时，必须把与该文件的这两部分资源一个不落的回收
      # 1、f.close()   # 关闭操作系统打开的文件（次步骤必须要做）
      # del f       # 回收Python程序的变量（Python会自动回收，这一步可以不用做）
      #　其中del f一定要发生在f.close()之后，否则就会导致操作系统打开的文件还没关闭，白白占用资源

    # with管理上下文
    # 文件使用完毕后，with会自动帮我们关闭文件
    with open('file.txt',mode='r',encoding='utf8') as f:
        f.readlines()
    ```

    - <font color=ff000>强调!!!</font>

    ```python
    open是有操作系统打开文件，那么如果我们没有为open指定编码，那么打开的文件默认字编码就是操作系统说了算，操作系统会用自己的默认编码打开文件，
    Windows下是gbk
    Linux下是utf8
    ```

- 二、文件的打开模式（r模式）

```python
# 文件的默认打开模式r
# 文件不存在，则报错
# 文件存在，将文件指针调到文件的开头

with open('file.txt',encoding='utf8') as f:
    print(f)
    # <_io.TextIOWrapper name='file.txt' mode='r' encoding='utf8'>    # 默认打开模式为r
    print(f.read())
    root:x:0:0:root:/root
    bin:x:1:1:bin
```
  - 常用内置方法

  ```Python
  # f.read() 一次性打开文件的所有内容（大文件慎用）
  with open('file.txt',encoding='utf8') as f:
      print(f.read())

  # f.readlines() 将文件所有内容以列表的形式打开，同样不适用大文件
      print(f.readlines())

  # f.readline() 每次只打开一行内容，同一时间只有一行内容被读到内存中，避免文件过大，造成内存负荷超载
  ```

- 三、文件的打开模式（w模式）

```Python
# w模式：只写模式
# 文件不存在，则创建一个空文件，并且文件指针跳到文件的开头
# 文件存在，会清空文件内容，并且将文件指针跳到文件的开头

#强调：
  # 1、如果每次都是重新打开文件，那么文件内容总会清空，指针跳到开头
  # 2、如果在打开文件不关闭的情况下，连续的写入，本次写入会基于上一次指针所在的位置开始继续写
```

  - 常用的内置方法

  ```Python
  # f.write()  从文件开头写入
  with open('file.txt',mode='w',encoding='utf8') as f:
      f.write('first\n')
      f.write('second\n')

  # f.writelines()  用于向文件中写入一序列的字符串
      # 此序列可以被for循环，循环，如list/str/tuple等
      l=['first\n','second\n']
      for i in l:
          f.write(i)

      # f.writelines(l)    # 等同于上面的for循环里的f.write

      #注意：writelines并不是一次写多行
  ```

- 四、文件的打开模式（a模式）

```python
# a模式：只追加模式  （适合写日志的情形）
# 文件不存在，则创建一个空白文件，并且文件指针跳到文件的末尾
# 文件存在，也会将文件指针跳到文件末尾

with open('file.txt',mode='a',encoding='utf8') as f:
    f.write('fourth\n')
    f.writelines(['fifth\n','sixth\n'])
```

- 五、控制文件操作内容的模式（t模式）

```Python
# 不能单独使用，必须与r/w/a连用
# t模式：是默认的

# text文本模式，该模式下操作文件内容的单位都是字符串，只适用于文本文件

#强调：该模式下必须指定encoding='某种字符编码'
```

- 六、控制文件操作内容的模式（b模式）

```Python
# 不能单独使用，必须与r/w/a连用
# b模式：Bytes二级制模式，该模式下操作文件的内容的单位都是bytes 适用于所有类型的文件
# 该模式下不用指定encoding

with open('file.txt',mode='rb') as f:
    # print(f.read(),type(f.read()))
    b'\xe5\xa7\x93\xe5\x90\x8d\xef\xbc\x9afred\r\n\xe5\xb9\xb4\xe9\xbe\x84\xef\xbc\x9a20\r\n' <class 'bytes'>   

    data=f.read()
    print(data.decode(encoding='utf8'))   # 可以将二进制内容解码成指定字符集
     姓名：fred
    年龄：20
```

- 小练习

```Python
利用b模式，编写一个cp工具，要求如下：
  1. 既可以拷贝文本又可以拷贝视频，图片等文件
  2. 用户一旦参数错误，打印命令的正确使用方法，如usage: cp source_file target_file
    提示：可以用import sys，然后用sys.argv获取脚本后面跟的参数

--------

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import  sys

if len(sys.argv)  != 3:
    print('Usage: %s src_file dest_file' %sys.argv[0])
    sys.exit()

src=sys.argv[1]
dest=sys.argv[2]


with open(r'%s' %src ,mode='rb') as f_r:
    for line in f_r:
        with open(r'%s' %dest,mode='ab') as f_w:
            f_w.write(line)
```

- 七、文件内指针的移动

```Python
# read(n)在t模式下，读取是3个字符
with open('file.txt',mode='rt',encoding='utf8') as f:
    print(f.read(3))
    姓名：

# read()在b模式下，读取的是3个字节
with open('file.txt',mode='rb') as f1:
    data=f1.read(3)
    print(data.decode(encoding='utf8'))
    姓                                                  #utf8编码，一个中文字符用3个Bytes表示

# 强调：
其余所有模式下，文件内指针的移动都是以字节为单位
```
  - 文件指针操作

  ```python
  # seek() 两个参数，offset whence
    # offset：开始的字节数（偏移量）
    # whence：0/1/2      默认为0

  # 0  参照文件开头偏移（在b和t模式下都能用）
  with open('file.txt',mode='rt',encoding='utf8') as f:
      f.seek(15,0)
      print('first\n',f.read(),end='')
      first
      年龄：20
      f.seek(15,0)
      print('second\n',f.read(),end='')
      second
      年龄：20
  ```
  ```Python
  # 1  参照当前位置使用（只能在b模式用下用）
  with open('file.txt',mode='rt',encoding='utf8') as f:
      f.seek(3,1)                   #在t模式下则报错
      io.UnsupportedOperation: can't do nonzero cur-relative seeks

  with open('file.txt',mode='rb') as f:
      data=f.read(15)
      print(data.decode(encoding='utf8'),end='')
      姓名：fred              #\n没显示出来，但它确实占了2个字节

      f.seek(3,1)             # 从当前指针所在的位置偏移3个字节
      data1=f.read()
      print(data1.decode(encoding='utf8'),end='')         # 偏移3个字节后的结果：
      龄：20
    ```
    ```Python
    # 2  参照文件末尾（只能在b模式用下用）
    with open('file.txt',mode='rb') as f:
        f.seek(-13,2)        # 参照文件末尾，向后偏移13个字节
        data=f.read()
        print(data.decode(encoding='utf8'),end='')
        年龄：20
    ```

- 八、文件的修改

```python
# 文件的数据是存放于硬盘上的，因而只存在覆盖、不存在修改这么一说，我们平时看到的修改文件，都是模拟出来的效果，具体的说有两种实现方式：

# 方式1：将文件内容全部读到内存，修改完后再由内存覆盖到硬盘
import os
with open('file.txt',mode='rt',encoding='utf8') as f_r,\
    open('modfied.txt',mode='wt',encoding='utf8') as f_w:
    data=f_r.read()                                        # 全部读入内存，遇到大文件会很慢
    data=data.replace('姓名：','name:')                     # 在内存中完成修改
    f_w.write(data)                                        # 一次性写入文件

os.remove('file.txt')
os.rename('modfied.txt','file.txt')

# 方式2 将硬盘存放的该文件的内容一行一行地读入内存，修改完毕就写入新文件，最后用新文件覆盖源文（省内存，同一时间在内存中只有一行，在修改期间硬盘上同一份数据会保存两份）
import os
with open('file.txt',mode='rt',encoding='utf8') as f_r,\
    open('modfied.txt',mode='wt',encoding='utf8') as f_w:
    for line in f_r:
        if 'name' in line:
            line=line.replace('name:','姓名：')
            f_w.write(line)
        else:
            f_w.write(line)
    else:
        print('修改完了，亲')

os.remove('file.txt')
os.rename('modfied.txt','file.txt')
```
